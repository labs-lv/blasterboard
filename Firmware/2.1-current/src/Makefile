ifeq ($(OS),Windows_NT)
	avrasm := avrasm2
	delcmd := del ..\*.hex
else
	UNAME_S := $(shell uname -s)
	ifeq ($(UNAME_S),Linux)
		avrasm := avra
		delcmd := rm ../*.hex
	endif
endif

all:
	$(delcmd)
	$(avrasm) -fI -o ../bb-2_1.hex main.aa
uart:
	$(delcmd)
	$(avrasm) -fI -D UART_ENABLE -o ../bb-2_1-uart.hex main.aa




