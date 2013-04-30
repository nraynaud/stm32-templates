# put your *.o targets here, make should handle the rest!

SRCS = main.c

# all the files will be generated with this name (main.elf, main.bin, main.hex, etc)

PROJ_NAME=main

# that's it, no need to change anything below this line!

###################################################

CC=/Users/nraynaud/dev/STM32F4.platform/Developer/usr/bin/arm-none-eabi-gcc
OBJCOPY=/Users/nraynaud/dev/STM32F4.platform/Developer/usr/bin/arm-none-eabi-objcopy

CFLAGS  = -g3 -Wall -Tstm32_flash.ld 
CFLAGS += -DARM_MATH_CM4
CFLAGS += -D__FPU_PRESENT=1
CFLAGS += -mcpu=cortex-m4 -mthumb -mfloat-abi=hard -mfpu=fpv4-sp-d16
CFLAGS += -ffunction-sections
CFLAGS += -mfloat-abi=hard -mfpu=fpv4-sp-d16
CFLAGS += -include stm32f4xx_conf.h

###################################################

vpath %.c src

ROOT=$(shell pwd)

CFLAGS += -Iinc -Ilib -Ilib/inc 
CFLAGS += -Ilib/inc/core -Ilib/inc/peripherals 

SRCS += lib/startup_stm32f4xx.s # add startup file to build

OBJS = $(SRCS:.c=.o)

###################################################

.PHONY: lib proj install clean CMSIS USB_OTG USB_Device
.DEFAULT_GOAL := all

all: lib CMSIS USB_OTG USB_Device proj

lib:
	$(MAKE) -C lib
CMSIS:
	$(MAKE) -C CMSIS
USB_OTG:
	$(MAKE) -C USB_OTG
USB_Device:
	$(MAKE) -C USB_Device

proj: 	$(PROJ_NAME).elf

$(PROJ_NAME).elf: $(SRCS)
	$(CC) $(CFLAGS) $^ -o $@ -Llib -lstm32f4
	$(OBJCOPY) -O ihex $(PROJ_NAME).elf $(PROJ_NAME).hex
	$(OBJCOPY) -O binary $(PROJ_NAME).elf $(PROJ_NAME).bin

install:
	$(MAKE) -C lib install
	$(MAKE) -C CMSIS install
	$(MAKE) -C USB_OTG install
	$(MAKE) -C USB_Device install
clean:
	$(MAKE) -C lib clean
	$(MAKE) -C CMSIS clean
	$(MAKE) -C USB_OTG clean
	$(MAKE) -C USB_Device clean
	rm -f *.o
	rm -f $(PROJ_NAME).elf
	rm -f $(PROJ_NAME).hex
	rm -f $(PROJ_NAME).bin
