include /Users/nraynaud/dev/STM32F4.platform/Developer/Share/Makefile

###########################################
PRJ := USB_Device
LIBNAME := lib$(PRJ).a
.DEFAULT_GOAL := $(LIBNAME)

SRCDIR := Core/src

SRCS := $(wildcard $(SRCDIR)/*.c)

CFLAGS += -ICore/inc -I../USB_OTG/inc

OBJS = $(SRCS:.c=.o)

all: $(LIBNAME)

%.o : %.c
	$(CC) $(CPPFLAGS) $(CFLAGS) -c -o $@ $^

$(LIBNAME): $(OBJS)
	$(AR) -r $@ $(OBJS)

install: $(LIBNAME)
	cp $(LIBNAME) $(SDK)/usr/lib
	cp -r Core/inc $(SDK)/usr/include/$(PRJ)

clean:
	rm -f $(OBJS) $(LIBNAME) 
