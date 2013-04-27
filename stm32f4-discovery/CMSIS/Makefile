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

.PHONY: libCMSIS_DSP.a

all: libCMSIS_DSP.a

%.o : %.c
	$(CC) $(CFLAGS) -c -o $@ $^

libCMSIS_DSP.a: $(OBJS)
	$(AR) -r $@ $(OBJS)

install: libCMSIS_DSP.a
	cp libCMSIS_DSP.a $(SDK)/usr/lib

clean:
	rm -f $(OBJS) libCMSIS_DSP.a 
