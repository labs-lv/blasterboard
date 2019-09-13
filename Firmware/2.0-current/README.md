### Firmware version 2.0
---

_REV B_ cards are flashed with this firmware.

This is a major firmware update after learning the internals of the original SB2.0 firmware. 

* All commands (00f-FFh) are implemented and follow the logic of the original card now. I did not notice any changes in software behaivor, but it is safer like this anyway.
* RESET startup time is reduced to a minimum, so the BlasterBoard's DSP is more tolerant to faster machines than the original card now.
* DMA playback routine was completely rewritten to eliminate clicks on machines with slower (<8MHz) ISA speed and on fast machines like Pentium 3. However, BB's routine differs from the SB's. The SB2.0 internal timer interrupt works like this:

		1. Send DMA request
		2. Wait for the DMA controller to finish putting requested sample to external register IC
		3. Read sample from external register
		4. Write sample to the DAC
		5. Return

	This routine waits for the DMA controller to finish transfer operation, but DMA response time varies and delta times between writing samples to the DAC varies as well and sample clock is not precise, which degrades sound quality.
	To prevent this BlasterBoard uses additional external register (74HC574) exclusively for DMA transfers, so DMA does its job in the background while DSP is waiting for the next timer interrupt. This allows writing samples in precise intervals as it should be:

		1. Read sample from external register
		2. Write sample to the DAC
		3. Send DMA request for the next sample
		4. Return (DMA transfer happens in the background and sample is ready for step 1)

* Some bugs fixed for smoother direct PCM playback (10h command) and other minor fixes



	





