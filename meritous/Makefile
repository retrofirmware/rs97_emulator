#
#   Makefile
#
#   Copyright 2007, 2008 Lancer-X/ASCEAI
#
#   This file is part of Meritous.
#
#   Meritous is free software: you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation, either version 3 of the License, or
#   (at your option) any later version.
#
#   Meritous is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with Meritous.  If not, see <http://www.gnu.org/licenses/>.
#

CC		:= mipsel-linux-gcc
STRIP		:= mipsel-linux-strip
#CC		:= gcc
#STRIP		:= strip
SYSROOT		:= $(shell $(CC) --print-sysroot)
CFLAGS		:= $(shell $(SYSROOT)/usr/bin/sdl-config --cflags) -Wall -g -DWITH_HOME_DIR
LDFLAGS		:= $(shell $(SYSROOT)/usr/bin/sdl-config --libs) -lSDL_image -lSDL_mixer -lz -lm
TARGET		:= meritous.elf

ifdef DEBUG
	CFLAGS	+= -ggdb
else
	CFLAGS	+= -O2
endif

OBJS = 	src/levelblit.o \
		src/mapgen.o \
		src/demon.o \
		src/gamemap.o \
		src/tiles.o \
		src/save.o \
		src/help.o \
		src/audio.o \
		src/boss.o \
		src/ending.o
#
default:	meritous

%.o:		%.c
		${CC} -c -o $@ $? ${CFLAGS}

meritous:	${OBJS}
		${CC} -o ${TARGET} $+ ${LDFLAGS}
ifndef DEBUG
		${STRIP} ${TARGET}
endif

clean:		
		rm -f ${OBJS} ${TARGET}

