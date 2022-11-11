[Pia](Pia-Overview) > Terminology
---

This page describes common terms that are used by the Pia library.

1. [Station](#station)
2. [Constant id](#constant-id)
3. Variable id
4. Service variable id

## Station
A station is just a console. Note that one station may carry multiple players.

## Constant ID
The constant id uniquely identifies a station, and never changes, even across sessions.

* **NEX:** The constant id is the same as your principal id (pid).
* **LDN:** The constant id is generated from your MAC address: `mac[2] << 56 | mac[4] << 48 | mac[5] << 40 | mac[3] << 32 | mac[1] << 24 | mac[0] << 16`.
