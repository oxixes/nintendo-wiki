[[Pia Protocols]] > Local Protocol
---

| Message Type | Description |
| --- | --- |
| 0x11 | [Update session](#update-session-message) |
| 0x12 | Destroy network |
| 0x13 | Start host migration |
| 0x21 | Update session ack |

### Version numbers
| Pia version | Version |
| --- | --- |
| 5.19 - 5.43 | 0 |

## Local message header
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | Version number (1) |
| 0x1 | 1 | Message type |
| 0x2 | 2 | Payload size |
| 0x4 | 6 | Unknown |
| 0xA | 2 | Padding |

## Update session message
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 12 | [Local message header](#local-message-header) |
| 0xC | 4 | Sequence id |
| 0x10 | 4 | Network id |
| 0x14 | 4 | Host variable id |
| 0x18 | 4 | Host service variable id |
| 0x1C | 4 | Padding |
| 0x20 | 8 | Host constant id |
| 0x28 | 1 | Allow participating state |
| 0x29 | 7 | Padding |
| 0x30 | | [Payload](#update-session-payload) |

### Update session payload
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 8 x 9 | [Local nodes](#local-node) |
| 0x48 | 1 | Unknown |

## Local node
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 8 | [Local address](#local-address) |
| 0x8 | 1 | Unknown |

## Local address
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 6 | [Inet address](Pia-Types#inetaddress) |
| 0x6 | 2 | Extension address |