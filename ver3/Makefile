# http://eslinuxprogramming.blogspot.com/2015/06/makefile-part-2.html

# to avoid conflicts between the TARGET name and the file name (exampe: all vs all.c)
.PHONY: all, install, clean

TARGET := sum

# file list: include file mk and main c file
-include ./src/src.mk
CSRCS += main.c


# Build dir
OBJSDIR = ./build

# Objs list
OBJS := $(patsubst %.cpp, $(OBJSDIR)/%.o, $(CPPSRCS))
OBJS += $(patsubst %.c, $(OBJSDIR)/%.o, $(CSRCS))

INCDIR += -I./src
# Flags
CFLAGS += -I./include -DDEBUG -Wall -g
LDFLAGS += -L./lib -lm

# compile
CC := gcc
CXX := g++

all: ${TARGET}
${TARGET} : $(OBJS)
	# @echo ${OBJS}
	# @echo " [CC] $@ $< $* $?"
	@echo " [CXX] $@ $< $* $?"
	@echo " [LINK] $@"	
	@mkdir -p $(shell dirname $@)
	@$(CXX) $(OBJS) -o $@ $(LDFLAGS) ${INCDIR}

$(OBJSDIR)/%.o: %.c $(HDRS)
	@echo " [CC] $@"
	@mkdir -p $(shell dirname $@)
	@$(CXX) -c $< -o $@ $(CFLAGS) ${INCDIR}

install:
	cp -rf ${TARGET} /usr/local/bin

clean:
	rm -rf ${OBJSDIR}/*.o
	rm -rf ${TARGET}
	rm -rf ${OBJSDIR}/*


# sum: main.o sum.o
# 	gcc -o sum main.o sum.o
# main.o: main.c sum.h
# 	gcc -c main.c
# sum.o: sum.c sum.h
# 	gcc -c sum.c
# clean:
# 	rm *.o
# 	rm sum
