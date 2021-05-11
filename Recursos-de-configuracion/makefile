#
#
# Makefile to generate sysInfoGroup.so
# 
# usage:
# "make" : generate library
# "make clean" : remove *.o , *.so
#

CC=gcc
LDFLAGS= `net-snmp-config --cflags`

#PROG= sysInfoGroup.so
#SRCS= sysInfoGroup.c 
PROG= cpuUsage.so
SRCS= cpuUsage.c
OBJS= $(SRCS:.c=.o)

PROG2= memoryUsage.so
SRCS2= memoryUsage.c
OBJS2= $(SRCS2:.c=.o)

# shared library flags (assumes gcc)
DLFLAGS=-fPIC -shared -Wno-unused-result

all: $(PROG) $(PROG2)

$(PROG): $(OBJS)
	$(CC) -o $@ $(OBJS) $(LDFLAGS) $(DLFLAGS)
	rm -f $(OBJS)

$(PROG2): $(OBJS2)
	$(CC) -o $@ $(OBJS2) $(LDFLAGS) $(DLFLAGS)
	rm -f $(OBJS2)

.c.o:
	@if test "$(CC)" = "" ; then \
	echo "La variable de entorno CC debe establecerse con la ruta del compilador" ; \
	exit 1 ; \
	fi
	$(CC) -o $@ -c $< -g $(LDFLAGS) $(DLFLAGS)

clean:
	rm -f $(OBJS) $(PROG) 
	rm -f $(OBJS2) $(PROG2) 

