[Pia](Pia-Overview) > [Protocols](Pia-Protocols) > Station Protocol
---

The difference between the reliable and unreliable protocol is that the reliable protocol wraps messages in a [reliable sliding window](#reliable-sliding-window). The reliable protocol is not used by Pia however, and support for it was removed in version *5.6*.

| Port | Description |
| --- | --- |
| 0 | Unreliable |
| 1 | Reliable |

The first byte of each packet indicates the message type.

| Type | Description |
| --- | --- |
| 1 | [Connection request](#connection-request) |
| 2 | [Connection response](#connection-response) |
| 3 | [Disconnection request](#disconnection-request) |
| 4 | [Disconnection response](#disconnection-response) |
| 5 | [Ack](#ack) |
| 6 | Relay connection request |
| 7 | Relay connection response |

### Version numbers

| Pia Version | Version |
| --- | --- |
| 3.3 - 3.6 | 2 |
| 3.7 - 3.10 | 3 |
| 4.5 - 4.10 | 5 |
| 5.2 - 5.6 | 7 |
| 5.7 - 5.9 | 8 |
| 5.10 - 5.18 | 9 |

In version 5.19, the `StationProtocol` was renamed to `MeshStationProtocol` and version numbers start at 0 again:

| Pia Version | Version |
| --- | --- |
| 5.19 - 5.23 | 0 |
| 5.24 - 5.26 | 1 |
| 5.27 - 5.43 | 2 |

## Connection request
*3.3 - 4.10:*

| Type | Description |
| --- | --- |
| Uint8 | Message type  (1) |
| Uint8 | Connection id |
| Uint8 | [Version number](#version-numbers) |
| Uint8 | Is inverse connection request |
| [StationConnectionInfo] | Station connection info |
| Uint32 | Ack id |

*5.2 - 5.6:*

| Type | Description |
| --- | --- |
| Uint8 | Message type  (1) |
| Uint8 | Connection id |
| Uint8 | [Version number](#version-numbers) |
| Uint8 | Is inverse connection request |
| Uint64 | [Constant id] |
| [StationConnectionInfo] | Station connection info |
| Uint32 | Ack id |

*5.7 - 5.9:*

| Type | Description |
| --- | --- |
| Uint8 | Message type  (1) |
| Uint8 | Connection id |
| Uint8 | [Version number](#version-numbers) |
| Uint8 | Is inverse connection request |
| Uint64 | [Constant id] |
| Uint32 | [Variable id]
| Uint8 | Inverse connection id |
| [StationConnectionInfo] | Station connection info |
| Uint32 | Ack id |

*5.10 - 5.18:*

| Type | Description |
| --- | --- |
| Uint8 | Message type  (1) |
| Uint8 | Connection id |
| Uint8 | [Version number](#version-numbers) |
| Uint8 | Is inverse connection request |
| Uint64 | [Constant id] |
| Uint32 | [Variable id]
| Uint8 | Inverse connection id |
| [StationLocation] | Station location |
| Uint32 | Ack id |

*5.19 - 5.23:*

| Type | Description |
| --- | --- |
| Uint8 | Message type  (1) |
| Uint8 | Number of available protocols (N) |
| Uint8 (N*2) | [Protocol list](#protocol-list) |
| Uint8 | Connection id |
| Uint8 | Is inverse connection request |
| Uint64 | [Constant id] |
| Uint32 | [Variable id]
| Uint8 | Inverse connection id |
| [StationLocation] | Station location |
| Uint32 | Ack id |

*5.24 - 5.26:* Unknown

*5.27 - 5.43:*

| Type | Description |
| --- | --- |
| Uint8 | Message type (1) |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint64 | [Constant id] |
| Uint32 | [Variable id] |
| Uint8 | Number of available protocols (N) |
| Uint8 (N*2) | [Protocol list](#protocol-list) |
| Uint16 | Unknown |
| [StationLocation] | Station location |
| Bytes (32) | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Number of players (P) |
| PlayerInfo (xP) | Players |
| Uint32 | Ack id |

### Protocol List
The protocol list contains the following for every available protocol.

| Type | Description |
| --- | --- |
| Uint8 | Protocol id |
| Uint8 | Protocol version |

## Connection response
A connection response can either [accept](#connection-response-accepted) or [deny](#connection-response-denying) the connection request. This is indicated by the [connection result](#connection-result).

### Connection response (accepted)

| Type | Description |
| --- | --- |
| Uint8 | Message type (2) |
| Uint8 | [Result](#connection-result) |
| Uint8 | Version |
| Uint8 | Always 3 on Wii U, and 4 on Switch. |
| | Version-dependent data |
| Uint32 | Ack id |

*Version 2 - 5:*

| Type | Description |
| --- | --- |
| Uint8 (x32) | Identification token (ascii) |
| Uint16 (x16) | Name (utf16-be) |
| Uint8 | Name length |
| Uint8 | Language |

*Version 7 - 9:*

| Type | Description |
| --- | --- |
| Uint8 | Unknown (0, 1 or 2) |
| Uint64 | NEX principal id (pid). *Only present in version 8 and 9.* |
| Uint32 | NEX connection id (cid). *Only present in version 8 and 9.* |
| Uint8 (x32) | Identification token (ascii) |
| Uint32 | Session id |
| Uint8 | Number of players |
| Uint8 | Number of participants. This is either 1 or equal to the number of players, depending on whether each player should count as a participant in the session. |
| Uint8 | Number of non-zero player infos |
| [Player info](#player-info) (x4) | Player info |

#### Player info
| Type | Description |
| --- | --- |
| Bytes (80) | Player name |
| Uint8 | Player name encoding (1=utf8, 2=utf16) |
| Bytes (40) | Account name |
| Uint8 | Account name encoding (1=utf8, 2=utf16) |
| Uint8 | Language |
| Bytes (64) | Play history registration key |
| Uint64 | Unknown |

### Connection response (denying)
*3.3 - 5.6:*

| Type | Description |
| --- | --- |
| Uint8 | Message type (2) |
| Uint8 | [Connection result](#connection-result) |
| Uint8 | [Version number](#version-numbers) |
| Uint8 | Always 0 |

*5.7 - 5.18:*

| Type | Description |
| --- | --- |
| Uint8 | Message type (2) |
| Uint8 | [Connection result](#connection-result) |
| Uint8 | [Version number](#version-numbers) |
| Uint8 | Always 0 |
| Uint8 | Always 0 |
| Uint64 | [Constant id] |
| Uint32 | [Variable id] |

*5.19 - 5.23:*

| Type | Description |
| --- | --- |
| Uint8 | Message type (2) |
| Uint8 | [Connection result](#connection-result) |
| Uint8 | Protocol id that has unexpected protocol version |
| Uint8 | Expected protocol version |
| Uint16 | Always 0 |
| Uint64 | [Constant id] |
| Uint32 | [Variable id] |

*5.27 - 5.43:*

| Type | Description |
| --- | --- |
| Uint8 | Message type (2) |
| Uint8 | [Connection result](#connection-result) |
| Uint8 | Always 0 |
| Uint64 | [Constant id] |
| Uint32 | [Variable id] |

### Connection result
| Value | Description |
| --- | --- |
| 0 | Accepted |
| 1 | Connection denied |
| 2 | Incompatible version |

## Disconnection request
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | Message type |

## Disconnection response
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | Message type |

## Ack
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | Message type |
| 0x1 | 3 | Padding |
| 0x4 | 4 | Ack id |

[Constant id]: Pia-Terminology#constant-id
[Variable id]: Pia-Terminology#variable-id

[StationConnectionInfo]: Pia-Types#stationconnectioninfo
[StationLocation]: Pia-Types#stationlocation
[IdentificationInfo]: Pia-Types#identificationinfo