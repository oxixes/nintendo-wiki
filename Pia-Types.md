[Pia](Pia-Overview) > Types
---

This page describes common data structures that are used by the Pia library.

1. [InetAddress](#inetaddress)
2. [StationAddress](#stationaddress)
3. [StationLocation](#stationlocation)
4. [StationConnectionInfo](#stationconnectioninfo)
5. [ReliableSlidingWindow](#reliableslidingwindow)

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
The station location holds information that allows Pia to connect to a given station. Many fields are directly taken from a [station url](NEX-Common-Types#stationurl), when NEX is used.

Up to Pia version 5.9, a station location contained either a public or a private address. In Pia 5.10 and later, it contains both.

*Up to 4.10:*

| Type | Description |
| --- | --- |
| [StationAddress](#stationaddress) | Station address |
| Uint32 | [Constant id] (PID) |
| Uint32 | [Variable id] (CID) |
| Uint32 | [Service variable id] (RVCID) |
| Uint8 | [URL type](#url-type) |
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
| Uint64 | [Constant id] (PID) |
| Uint32 | [Variable id] (CID) |
| Uint32 | [Service variable id] (RVCID) |
| Uint8 | [URL type](#url-type) |
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
| Uint64 | [Constant id] (PID) |
| Uint32 | [Variable id] (CID) |
| Uint32 | [Service variable id] (RVCID) |
| Uint8 | `0x3`: natf<br>`0xC`: natm |
| Uint8 | type |
| Uint8 | probeinit |
| Uint8 | Is private address available |

*5.11 - 5.43:*

| Type | Description |
| --- | --- |
| Uint8 | Size of public address |
| Uint8 | Size of private address |
| [InetAddress](#inetaddress) | Public address (encoding depends on size) |
| [InetAddress](#inetaddress) | Private address (encoding depends on size) |
| [InetAddress](#inetaddress) | Relay address (old encoding) |
| Uint64 | [Constant id] (PID) |
| Uint32 | [Variable id] (CID) |
| Uint32 | [Service variable id] (RVCID) |
| Uint8 | `0x3`: natf<br>`0xC`: natm |
| Uint8 | type |
| Uint8 | probeinit |
| Uint8 | Is private address available |

*6.16 - 6.23:*

| Type | Description |
| --- | --- |
| Uint8 | Address size |
| [StationAddress](#stationaddress) | Address |
| Uint64 | Unknown |
| Uint16 | Unknown |
| Uint8 | Unknown |

### URL Type
The URL type depends on the scheme of the given station url. It is always 0 or 1 in practice.

| Value | Scheme |
| --- | --- |
| 0 | Invalid |
| 1 | `prudp` |
| 2 | `prudps` |
| 3 | `udp` |

## StationConnectionInfo
Up to Pia 5.9, a [station location](#stationlocation) contained either a public or private address. The station connection info contains both.

In Pia version 5.10, the station connection info structure was removed, and a single [station location](#stationlocation) contains both the public and private address of a station.

| Type | Description |
| --- | --- |
| [StationLocation](#stationlocation) | Public location |
| [StationLocation](#stationlocation) | Private location |

## ReliableSlidingWindow
A reliable sliding window is used by various protocols to ensure that all messages arrive in the correct order. Large messages are fragmented. When a reliable sliding window is used, the following header is added to messages:

*5.9:*

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 2 | [Flags](#flags) |
| 0x2 | 2 | Payload size |
| 0x4 | 4 | Padding |
| 0x8 | 4 | Sequence id |
| 0xC | 4 | Acknowledgement id |
| 0x10 | 8 | Extra acknowledgements |

### Flags
| Flag | Description |
| --- | --- |
| 1 | Unknown (always set) |
| 2 | Last fragment |

[Constant id]: Pia-Terminology#constant-id
[Variable id]: Pia-Terminology#variable-id
[Service variable id]: Pia-Terminology#service-variable-id