include /Users/nraynaud/dev/STM32F4.platform/Developer/Share/Makefile

###########################################
PRJ := USB_OTG
LIBNAME := lib$(PRJ).a
.DEFAULT_GOAL := $(LIBNAME)
SRCDIR := src

SRCS := $(wildcard $(SRCDIR)/*.c)

CFLAGS := -Iinc $(CFLAGS)

OBJS = $(SRCS:.c=.o)

all: $(LIBNAME)

%.o : %.c
	$(CC) $(CFLAGS) -c -o $@ $^

$(LIBNAME): $(OBJS)
	$(AR) -r $@ $(OBJS)

install: $(LIBNAME)
	cp $(LIBNAME) $(SDK)/usr/lib
	cp -r inc $(SDK)/usr/include/$(PRJ)

clean:
	rm -f $(OBJS) $(LIBNAME) 
