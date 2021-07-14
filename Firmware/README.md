### Firmware for the BlasterBoard
---

_ANY BOARD REVISION WILL WORK WITH ANY FIRMWARE VERSION_

Compiled images are in Intel HEX format and require a hardware IC programmer for flashing.

A folder with '-current' suffix contains the latest official firmware:

	fuses.bin	- ATmega328P MCU fuse settings for the firmware (or see fuses-pic.png)
	bb-?_?.hex	- A compiled firmware in Intel HEX format for writing into the ATmega328P MCU

### Debug-enabled firmware
---

In order to intercept the communication between the software and sound hardware some firmware versions (with '-uart' suffix) are compiled with extra code which outputs this information on the PB1 pin of the ATmega328P MCU in UART format at the baud rate of 2.0 MHz. This UART code has some performance impact on the MCU and thus is not present in regular firmware images without the '-uart' suffix.
Data from PB1 is read from H1 header near the ATmega MCU on the PCB. To read the data use any USB-UART adapter like FT232RL. The terminal application should be set to HEX display. Incoming bytes from the PB1 pin has the following meaning (all hex):

	AA 	- The MCU was reset
	CC xx	- Prefix CC (incoming command) followed by an incoming command byte xx from the ISA bus
	DD yy	- Prefix DD (incoming data) folowed by an incoming data byte yy from the ISA bus
	FF zz	- Prefix FF (outgoing byte) followed by an outgoing byte zz from the MCU to the ISA bus

### BlasterBoard-specific commands
---

The official BlasterBoard firmware utilizes a specific command for acquiring BlasterBoard's firmware version:

***E5h - acquire BlasterBoard firmware version***

Syntax:

	WRITE	E5h
	READ	BYTE major firmware version
	READ	BYTE minor firmware version

It also should be used to detect the BlasterBoard card - if sending E5h command does not give any response then the BlasterBoard is not present in the system.
	
Software which already use BlasterBoard-specific abilities (sampling rate up to 62500Hz) is a module player Mod Master:
https://www.vogons.org/viewtopic.php?f=62&t=66350 




