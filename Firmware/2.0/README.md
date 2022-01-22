### Firmware version 2.0
---

This is a major firmware update after studying the internals of the disassembled SB 2.0 firmware. 

* Firmware behaviour is now as close to the original SB 2.0 firmware as the schematic allows.
* RESET startup time is reduced to a minimum, so the BlasterBoard's DSP is more tolerant to faster machines than the original card now.
* DMA playback routine was completely rewritten to eliminate clicks on machines with slower (<8MHz) ISA speed and on fast machines like Pentium 3. However, BB's routine differs from the SB's. The SB2.0 internal timer interrupt works like this:
* Some bugs fixed for smoother direct PCM playback (10h command) and other minor fixes



	





