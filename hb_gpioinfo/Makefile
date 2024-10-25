CROSS_COMPILE = /opt/gcc-arm-11.2-2022.02-x86_64-aarch64-none-linux-gnu/bin/aarch64-none-linux-gnu-
CC = $(CROSS_COMPILE)gcc
STRIP = $(CROSS_COMPILE)strip

CFLAGS = -Wall -I./
LDFLAGS = ./libgpiod.a

TARGET = hb_gpioinfo

SRCS = gpioinfo.c tools-common.c

OBJS = $(SRCS:.c=.o)

PREFIX = ../debian/usr/bin/

all: $(TARGET)

$(TARGET): $(OBJS)
	$(CC) -o $@ $(OBJS) $(LDFLAGS)
	$(STRIP) $@

%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

install: $(TARGET)
	install -d $(PREFIX)
	install -m 0755 $(TARGET) $(PREFIX)

clean:
	rm -f $(OBJS) $(TARGET)
	rm -f $(PREFIX)$(TARGET)

.PHONY: all clean install
