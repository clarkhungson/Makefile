# http://eslinuxprogramming.blogspot.com/2015/06/makefile-part-2.html

.PHONY: all, install, clean

TARGET = sum

# File lists: .h, .c, .cpp
HDRS += sum.h
CSRCS += main.c sum.c
CPPSRCS += 

# Build dir
OBJSDIR = ./build

# Objs list
OBJS := $(patsubst %.cpp, $(OBJSDIR)/%.o, $(CPPSRCS))
OBJS += $(patsubst %.c, $(OBJSDIR)/%.o, $(CSRCS))

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
	@$(CXX) $(OBJS) -o $@ $(LDFLAGS)

$(OBJSDIR)/%.o: %.c $(HDRS)
	@echo " [CC] $@"
	@mkdir -p $(shell dirname $@)
	@$(CXX) -c $< -o $@ $(CFLAGS)

install:
	cp -rf ${TARGET} /usr/local/bin

clean:
	rm -rf ${OBJDIR}/*.o
	rm -rf ${TARGET}


# sum: main.o sum.o
# 	gcc -o sum main.o sum.o
# main.o: main.c sum.h
# 	gcc -c main.c
# sum.o: sum.c sum.h
# 	gcc -c sum.c
# clean:
# 	rm *.o
# 	rm sum
