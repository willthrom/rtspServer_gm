GMLIB=/home/athlom/camera/gm_lib_2015-01-09-IPCAM/gm_graph/gm_lib

CROSS_COMPILE=/usr/src/arm-linux-3.3/toolchain_gnueabi-4.4.0_ARMv5TE/usr/bin/arm-unknown-linux-uclibcgnueabi-
AS	=$(CROSS_COMPILE)as
LD	=$(CROSS_COMPILE)ld
CC	=$(CROSS_COMPILE)gcc
CPP	=$(CC) -E
AR	=$(CROSS_COMPILE)ar
NM	=$(CROSS_COMPILE)nm
STRIP	=$(CROSS_COMPILE)strip
OBJCOPY =$(CROSS_COMPILE)objcopy
OBJDUMP =$(CROSS_COMPILE)objdump
RANLIB	=$(CROSS_COMPILE)ranlib

ifeq ($(shell find $(GMLIB)/../ -name gmlib.mak),)
    sinclude /usr/src/arm-linux-3.3/linux-3.3-fa/cross_compiler_def
else
    sinclude $(GMLIB)/gmlib.mak
endif

uclibc=$(shell echo $(CROSS_COMPILE)|grep uclib)
ifeq ($(uclibc),)
    LIBRTSP=librtsp_glibc.a
else
    LIBRTSP=librtsp.a
endif


CC=$(CROSS_COMPILE)gcc
CPP=$(CC) -E
LD=$(CROSS_COMPILE)ld
AS=$(CROSS_COMPILE)as
MAKE=make
LINK =			$(CROSS_COMPILE)g++
LINK_OPTS =		
CONSOLE_LINK_OPTS =	$(LINK_OPTS)
LIBRARY_LINK =		$(CROSS_COMPILE)ar cr 
LIBRARY_LINK_OPTS =	$(LINK_OPTS)


LDFLAGS +=  -L$(GMLIB)/lib -lpthread -lm -lrt -lgm
CFLAGS += -I$(GMLIB)/inc
CFLAGS += -c -Wall -I$(GMLIB)/inc

EXECUTABLE=rtsp_basic
SOURCES=rtspd.c
OBJECTS=$(SOURCES:.c=.o)


all: $(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS) 
	$(LINK) $(LDFLAGS) $(OBJECTS) ${LIBS} $(LIBRTSP) -o $@

.cpp.o: 
	$(LINK) $(CFLAGS) $<  -o $@



clean:
	rm -f $(OBJECTS)



