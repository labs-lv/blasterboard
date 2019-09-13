### LABS BlasterBoard firmware repository
---

_ALL FIRMWARE VERSIONS ARE COMPATIBLE WITH ANY BOARD REVISION._

Compiled firmware images are in .HEX format and can be flashed with any compatible programmer.
Do it at your own risk.

The firmware consists of several files:

	fuses.bin		- ATmega328P MCU fuse settings for the firmware
	bb-fmwr-???.hex		- A recommended image for regular use
	bb-fmwr-???-uart.hex	- Debug-enabled image, not recommeneded for regular use for speed reasons

### Debug-enabled firmware
---

UART version has extra code which outputs debug data to PB1 pin
of the ATmega328P MCU in UART format. Internal software UART is set to 1MHz
baud rate and has some impact on firmware performance, so it is not recommended
for regular BlasterBoard use. Data from PB1 can be read via H1 pin header found near the ATmega MCU.
To read data use FT232RL UART-to-USB adapter or anything like it, connecting PB1<->RX and GND<->GND pins. The COM terminal application should be set to HEX display. Incoming bytes from MCU are the following (hex):

	AA 	- sent on power up and reset 
	CC xx	- incoming command xx		PC->ISA
	DD xx	- incoming data xx		PC->ISA
	FF xx	- outgoing data	xx		ISA->PC

### Additional commands
---

BlasterBoard's firmware version can be read with a BB-specific command E5h:

	WRITE	E5h
	READ	Major version byte
	READ	Minor version byte

It is also used to detect BlasterBoard - if writing E5h does not give any response then BB is not present.
	





