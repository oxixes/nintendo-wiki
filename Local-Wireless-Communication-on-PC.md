Because [LDN](LDN-Protocol) operates at the data link layer, it cannot be emulated with normal network sockets. Instead, one must put the network card into monitor mode and use a low-level networking library such as [libpcap](https://www.tcpdump.org/).

This page is intended to provide a simple guide to get started with local wireless communication.

This guide is written for Linux users and was tested on a system running Ubuntu. If you are using a different operating system, this guide is probably less useful for you.

1. [Enabling monitor mode](#enabling-monitor-mode)
2. [Disabling monitor mode](#disabling-monitor-mode)
3. [Receiving packets with libpcap](#receiving-packets-with-libpcap)

### Enabling monitor mode
By default, the network interface is in managed mode, which means that it only accepts packets that are intended for your PC:

![](https://www.dropbox.com/s/ef3rijbwos9hsos/iwconfig_managed.png?raw=1)

In monitor mode, the network interface receives all packets that are sent through the air:

![](https://www.dropbox.com/s/md7v0ip370i1a3e/enable_monitor_mode.png?raw=1)

If you start wireshark now, you will probably see a huge number of packets, maybe even thousands of packets per seconds, because we are capturing ALL packets that are sent through the air.

### Disabling monitor mode
Because we had to disable the network-manager service, you cannot access the internet while in monitor mode. To disable monitor mode, run the following commands:

![](https://www.dropbox.com/s/xxbu81kpe6aseur/enable_managed_mode.png?raw=1)

### Receiving packets with libpcap
Libpcap provides low-level networking functions. Here's an example that scans for action frames sent by Nintendo devices in LDN mode. Make sure that the wireless interface is in monitor mode before running this.

```c
#include <pcap.h>

#include <stdio.h>
#include <stdint.h>
#include <stdbool.h>

// See https://www.radiotap.org/
struct radiotap_header {
    uint8_t it_version;
    uint8_t it_pad;
    uint16_t it_len;
    uint32_t it_present;
};

// See IEEE 802.11 specification
struct ieee80211_header {
    uint16_t frame_control;
    uint16_t duration;
    uint8_t address1[6];
    uint8_t address2[6];
    uint8_t address3[6];
    uint16_t sequence;
};

enum ieee80211_frame_type {
    IEEE80211_TYPE_MANAGEMENT = 0
};

enum ieee80211_management_subtype {
    IEEE80211_MANAGEMENT_ACTION = 13
};

enum ieee80211_action_category {
    IEEE80211_ACTION_VENDOR_SPECIFIC = 127
};

uint16_t swap16(uint16_t value) {
    return (value >> 8) | (value << 8);
}

void process_ieee80211_packet(const uint8_t *data, size_t size) {
    size -= 4; // Remove frame checksum

    // Parse IEEE 802.11 frame header
    struct ieee80211_header *header = (struct ieee80211_header *)data;
    data += sizeof(struct ieee80211_header);
    size -= sizeof(struct ieee80211_header);

    uint16_t frame_control = swap16(header->frame_control);

    // Ignore packets with an invalid version number
    int version = (frame_control >> 8) & 3;
    if (version != 0) return;

    // Check if we received an action frame
    int type = (frame_control >> 10) & 3;
    int subtype = frame_control >> 12;
    if (type == IEEE80211_TYPE_MANAGEMENT && subtype == IEEE80211_MANAGEMENT_ACTION) {
        // Skip the HT control field if present
        if ((frame_control >> 7) & 1) {
            data += 4;
            size -= 4;
        }

        // Check if we received a vendor-specific action frame
        if (data[0] == IEEE80211_ACTION_VENDOR_SPECIFIC) {
            // Check if the organizationally unique identifier belongs to Nintendo
            if (data[1] == 0 && data[2] == 0x22 && data[3] == 0xAA) {
                printf("Received action frame from Nintendo device: ");
                for (size_t i = 0; i < size; i++) {
                    printf("%02x", data[i]);
                }
                printf("\n");
            }
        }
    }
}

void process_radiotap_packet(const uint8_t *data, size_t size) {
    struct radiotap_header *radio = (struct radiotap_header *)data;
    process_ieee80211_packet(data + radio->it_len, size - radio->it_len);
}

bool main_loop(pcap_t *p) {
    struct pcap_pkthdr header;
    while (true) {
        const uint8_t *data = pcap_next(p, &header);
        if (!data) {
            printf("pcap_next failed: %s\n", pcap_geterr(p));
            return false;
        }
        
        process_radiotap_packet(data, header.caplen);
    }
    return true;
}

pcap_t *init_pcap() {
    char error[PCAP_ERRBUF_SIZE];
    pcap_t *p = pcap_create("wlp2s0", error);
    if (!p) {
        printf("pcap_create failed: %s\n", error);
        return NULL;
    }
    
    int result = pcap_set_immediate_mode(p, 1);
    if (result != 0) {
        printf("pcap_set_immediate_mode failed: %s\n", pcap_geterr(p));
        pcap_close(p);
        return NULL;
    }
    
    result = pcap_activate(p);
    if (result < 0) {
        printf("pcap_activate failed: %s\n", pcap_geterr(p));
        pcap_close(p);
        return NULL;
    }
    
    return p;
}

int main() {
    pcap_t *p = init_pcap();
    if (p) {
        main_loop(p);
        pcap_close(p);
    }
    return 0;
}
```