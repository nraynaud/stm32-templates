include /Users/nraynaud/dev/STM32F4.platform/Developer/Share/Makefile

###########################################


SRCDIR := DSP_Lib/Source

SRCS := $(wildcard $(SRCDIR)/BasicMathFunctions/*.c)
SRCS += $(wildcard $(SRCDIR)/ComplexMathFunctions/*.c)
SRCS += $(wildcard $(SRCDIR)/ControllerFunctions/*.c)
SRCS += $(wildcard $(SRCDIR)/FastMathFunctions/*.c)
SRCS += $(wildcard $(SRCDIR)/FilteringFunctions/*.c)
SRCS += $(wildcard $(SRCDIR)/MatrixFunctions/*.c)
SRCS += $(wildcard $(SRCDIR)/StatisticsFunctions/*.c)
SRCS += $(wildcard $(SRCDIR)/SupportFunctions/*.c)
SRCS += $(wildcard $(SRCDIR)/TransformFunctions/*.c)


OBJS = $(SRCS:.c=.o)
PRJ := CMSIS_DSP
LIBNAME := lib$(PRJ).a
.DEFAULT_GOAL := $(LIBNAME)

all: $(LIBNAME)

%.o : %.c
	$(CC) $(CPPFLAGS) $(CFLAGS) -c -o $@ $^

$(LIBNAME): $(OBJS)
	$(AR) -r $@ $(OBJS)

install: $(LIBNAME)
	cp $(LIBNAME) $(SDK)/usr/lib

clean:
	rm -f $(OBJS) $(LIBNAME)
