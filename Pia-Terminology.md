[Pia](Pia-Overview) > Terminology
---

This page describes common terms that are used by the Pia library.

1. [Station](#station)
2. [Constant id](#constant-id)
3. [Variable id](#variable-id)
4. [Service variable id](#service-variable-id)

## Station
A station is just a console. Note that one station may carry multiple players.

## Constant ID
The constant id uniquely identifies a station, and never changes, even across sessions. The constant id depends on the network type:

* **NEX:** The constant id is the same as your principal id (pid).
* **LDN:** The constant id is generated from your MAC address: `mac[2] << 56 | mac[4] << 48 | mac[5] << 40 | mac[3] << 32 | mac[1] << 24 | mac[0] << 16`.

## Variable ID
The variable id uniquely identifies a station in the current session. Unlike the [constant id](#constant-id), it may change across sessions. The variable id is just a random number that is generated at the start of the session.

## Service Variable ID
Like the [variable id](#variable-id), the service variable id uniquely identifies a station in the current session but may change across sessions. The service variable id depends on the network type:

* **NEX:** The services variable id is your Rendez-Vous connection id (RVCID). This is received from the server when the client registers itself with the [secure connection protocol](Secure-Protocol).
* **LDN:** The service variable id is the CRC32 hash of your MAC address.