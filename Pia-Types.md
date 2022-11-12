[Pia](Pia-Overview) > Types
---

This page describes common data structures that are used by the Pia library.

1. [InetAddress](#inetaddress)
2. [StationAddress](#stationaddress)
3. [StationLocation](#stationlocation)
4. [StationConnectionInfo](#stationconnectioninfo)
5. [StationInfo](#stationinfo)

## InetAddress
In version 5.11, a new encoding was introduced that is capable of representing IPv6 addresses. Even later Pia version still use the old encoding sometimes. Which encoding is used depends on the context.

#### Old version
This structure can only represent IPv4 addresses.

| Offset | Size | Description |
| --- | -- | --- |
| 0x0 | 4 | Address |
| 0x4 | 2 | Port |

#### New version
This structure can represent both IPv4 and IPv6 addresses.

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 16 | Address |
| 0x10 | 2 | Port |

## StationAddress
In version 5.x, which [InetAddress](#inetaddress) encoding is used depends on the context. In version 6.x, the new encoding is always used.

*Up to 4.10:*

| Type | Description |
| --- | --- |
| [InetAddress](#inetaddress) | Address |
| Uint16 | Extension id |

*5.2 - 6.23:*

| Type | Description |
| --- | --- |
| [InetAddress](#inetaddress) | Address |

## StationLocation
The station location holds information that allows Pia to connect to a given station.

Up to Pia version 5.9, a station location contained either a public or a private address. In Pia 5.10 and later, it contains both.

*Up to 4.10:*

| Type | Description |
| --- | --- |
| [StationAddress](#stationaddress) | Station address |
| Uint32 | [Constant id] |
| Uint32 | [Variable id] |
| Uint32 | [Service variable id] |
| Uint8 | Url type (1=prudp 2=prudps 3=udp) |
| Uint8 | sid |
| Uint8 | stream |
| Uint8 | natm |
| Uint8 | natf |
| Uint8 | type |
| Uint8 | probeinit |

*5.2 - 5.9:*

| Type | Description |
| --- | --- |
| [StationAddress](#stationaddress) | Station address |
| Uint64 | [Constant id] |
| Uint32 | [Variable id] |
| Uint32 | [Service variable id] |
| Uint8 | Url type (1=prudp 2=prudps 3=udp) |
| Uint8 | sid |
| Uint8 | stream |
| Uint8 | natm |
| Uint8 | natf |
| Uint8 | type |
| Uint8 | probeinit |
| [InetAddress](#inetaddress) | Relay address |

*5.10:*

| Type | Description |
| --- | --- |
| [InetAddress](#inetaddress) | Public address |
| [InetAddress](#inetaddress) | Private address |
| [InetAddress](#inetaddress) | Relay address |
| Uint64 | [Constant id] |
| Uint32 | [Variable id] |
| Uint32 | [Service variable id] |
| Uint8 | `0x3`: natf<br>`0xC`: natm |
| Uint8 | type |
| Uint8 | probeinit |
| Uint8 | Is private address available |

*5.11 - 5.43:*

| Type | Description |
| --- | --- |
| Uint8 | Size of public address |
| Uint8 | Size of local address |
| [InetAddress](#inetaddress) | Public address (encoding depends on size) |
| [InetAddress](#inetaddress) | Private address (encoding depends on size) |
| [InetAddress](#inetaddress) | Relay address (old encoding) |
| Uint64 | [Constant id] |
| Uint32 | [Variable id] |
| Uint32 | [Service variable id] |
| Uint8 | `0x3`: natf<br>`0xC`: natm |
| Uint8 | type |
| Uint8 | probeinit |
| Uint8 | Is private address available |

## StationConnectionInfo
Up to Pia 5.9, a [station location](#stationlocation) contained either a public or private address. The station connection info contains both.

In Pia version 5.10, the station connection info structure was removed, and a single [station location](#stationlocation) contains both the public and private address of a station.

| Type | Description |
| --- | --- |
| [StationLocation](#stationlocation) | Public location |
| [StationLocation](#stationlocation) | Private location |

## StationInfo
*Up to 5.9:*

| Type | Description |
| --- | --- |
| [StationConnectionInfo](#stationconnectioninfo) | Connection info |
| Uint8 | Station index |
| | Padding such that the size becomes a multiple of 4 bytes. |

*5.10 and later:*

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 0x3E | [StationLocation](#stationlocation). If it takes up less than 0x3E bytes the remaining bytes are filled with 0's. |
| 0x3E | 1 | Station index |
| 0x3F | 1 | Padding |

[Constant id]: Pia-Terminology#constant-id
[Variable id]: Pia-Terminology#variable-id
[Service variable id]: Pia-Terminology#service-variable-id