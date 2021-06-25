### Firmware version 2.0
---

_REV B_ and up kits are flashed with this firmware.

This is a major firmware update after learning the internals of the original SB2.0 firmware. 

* All commands (00f-FFh) are implemented and follow the logic of the original card now.
* RESET startup time is reduced to a minimum, so the BlasterBoard's DSP became more tolerant to faster machines than the original card.
* DMA playback routine was completely rewritten to eliminate clicks on machines with slower (<8MHz) ISA speed and on fast machines like Pentium 3. 
* Some bugs fixed for smoother direct PCM playback (10h command) and other minor fixes



	





