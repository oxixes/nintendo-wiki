ENL is Nintendo's private peer-to-peer framework that's used by many first-party games, such as Mario Kart 8, Splatoon 2 and Super Mario Maker 2. Check out the pages about [PIA](PIA-Overview) for details on how a peer-to-peer session is set up. Once the session is ready, ENL sends all packets through the [unreliable protocol](Unreliable-Protocol).

To transmit game-data, games can register content transporters to ENL. ENL also implements a few content transporters on its own.

A message consists of one or more records, terminated by a record with type 255.

## Record Header
| Type | Description |
| --- | --- |
| Uint8 | Record type |
| Uint16 | Record size |
| Bytes | Record data |

| Record Type | Description |
| --- | --- |
| 0 - 31 | Game-specific |
| 253 | [System request info](#system-request-info) |
| 254 | [System information](#system-information) |
| 255 | End record |

## System request info
Clients can use this to request a specific record from another client. Every non-zero bit in the record mask indicates a record type that the client wants to receive. The least significant bit represents record type 0, and the most significant bit represents record type 31.

On the Switch, a new field was added that lets a client request a system-record. Here, bit 0 represents record type 253, and bit 1 represents record type 254.

*Wii U:*

| Type | Description |
| --- | --- |
| Uint32 | Record mask (games) |

*Switch:*

| Type | Description |
| --- | --- |
| Uint32 | Record mask (games) |
| Uint32 | Record mask (system) |

## System information
*Wii U:*

| Type | Description |
| --- | --- |
| Uint32 | Connected AID bitmap |
| Uint32 | Disconnected AID bitmap |
| Uint32 | Unknown |
| Uint32 | Received AID bitmap |
| Uint64 | Session time |
| Uint32 | Principal id |
| Uint32 | Unknown |
| ... | Unknown |

*Switch:*

| Type | Description |
| --- | --- |
| Uint64 | Connected AID bitmap |
| Uint64 | Disconnected AID bitmap |
| Uint64 | Unknown |
| Uint64 | Received AID bitmap |
| Uint64 | Session time |
| Uint64 | Principal id |
| ... | Unknown |