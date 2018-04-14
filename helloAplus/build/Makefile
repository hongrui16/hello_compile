PWD			= $(shell pwd)

BIN_DIR 	= $(PWD)/../bin/
SRC_DIR 	= $(PWD)/../src/src/
INC_DIR 	= $(PWD)/../src/inc/
TEST_DIR 	= $(PWD)/../test/
LIB_DIR		= $(PWD)/../lib/
INCLUDE_DIR	= $(PWD)/../include/

SRCS		= $(wildcard $(SRC_DIR)*.c)
OBJECT 		= $(SRCS:.c=.o)

LIB_OBJ 	= libhelloAplus.a
LIB_SO_OBJ 	= libhelloAplusso.so

BIN_OBJ 	= demo
BIN_SO_OBJ 	= demoso

TEST_SRC	 = $(wildcard $(TEST_DIR)*.c)
TEST_OBJECT  = $(TEST_SRC:.c=.o)

TARGET_OBJS	 = ./*.o $(BIN_DIR)* $(SRC_DIR)*.o $(TEST_DIR)*.o

RM 			= rm -rf
CC 			= gcc
AR 			= ar cr

CFLAG		= -I$(INC_DIR)
CFLAG		+= -I$(INCLUDE_DIR)

SHARED 		= -shared 
FPIC 		= -fPIC
WALL 		= -Wall
DYNAMIC 	= -rdynamic
	

.PHONY:all
all:$(LIB_SO_OBJ) $(BIN_SO_OBJ)	

$(LIB_SO_OBJ):$(OBJECT)
	$(CC) -o $(LIB_SO_OBJ) $(OBJECT) $(WALL) $(DYNAMIC) $(SHARED) -L. -L$(LIB_DIR) -lhelloA 
#	@echo $(shell pwd)
	mv $(LIB_SO_OBJ) $(BIN_DIR)

$(BIN_SO_OBJ):$(TEST_OBJECT)
	$(CC) -o $(BIN_SO_OBJ) $(TEST_OBJECT) -L$(BIN_DIR) -lhelloAplusso
	mv $(BIN_SO_OBJ) $(BIN_DIR)

$(OBJECT):$(SRCS) 
	$(CC) $(WALL) $(FPIC) $(CFLAG) -o $@ -c $<
#	@echo $(shell pwd)

$(TEST_OBJECT):$(TEST_SRC) 
	$(CC) $(WALL) $(FPIC) $(CFLAG) -o $@ -c $<

.PHONY:clean
clean:
	$(RM) $(TARGET_OBJS)



#*********************************************************************
# copyright :
# Author    : HongRui
# Date	    : 2018-4-8
# Version   : V1.0
#
#
#
#**********************************************************************