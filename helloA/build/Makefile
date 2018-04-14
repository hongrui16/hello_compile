PWD			= $(shell pwd)

BIN_DIR 	= $(PWD)/../bin/
SRC_DIR 	= $(PWD)/../src/src/
INC_DIR 	= $(PWD)/../src/inc/
TEST_DIR 	= $(PWD)/../test/


SRCS		= $(wildcard $(SRC_DIR)*.c)
OBJECT 		= $(SRCS:.c=.o)

LIB_OBJ 	= libhelloA.a
LIB_SO_OBJ 	= libhelloAso.so

BIN_OBJ 	= demo
BIN_SO_OBJ 	= demoso

TEST_SRC	 = $(wildcard $(TEST_DIR)*.c)
TEST_OBJECT  = $(TEST_SRC:.c=.o)

TARGET_OBJS	 = ./*.o $(BIN_DIR)* $(SRC_DIR)*.o $(TEST_DIR)*.o
LIB_PULS_DIR = $(PWD)/../../helloAplus/lib/

RM 			= rm -rf
CC 			= gcc
AR 			= ar cr

CFLAG		= -I$(INC_DIR)
SHARED 		= -shared 
FPIC 		= -fPIC
WALL 		= -Wall
DYNAMIC 	= -rdynamic

	

.PHONY:all
all:$(LIB_OBJ) $(LIB_SO_OBJ) $(BIN_OBJ) $(BIN_SO_OBJ)
$(BIN_OBJ):$(TEST_OBJECT)
	$(CC) -o $(BIN_OBJ) $(TEST_OBJECT) $(BIN_DIR)$(LIB_OBJ)
	mv $(BIN_OBJ) $(BIN_DIR)
	
$(BIN_SO_OBJ):$(TEST_OBJECT)
	$(CC) -o $(BIN_SO_OBJ) $(TEST_OBJECT) -L$(BIN_DIR) -lhelloAso
	mv $(BIN_SO_OBJ) $(BIN_DIR)

	
$(LIB_OBJ):$(OBJECT)
	$(AR) $(LIB_OBJ) $(OBJECT)
	cp $(LIB_OBJ) $(LIB_PULS_DIR)
	mv $(LIB_OBJ) $(BIN_DIR)

$(LIB_SO_OBJ):$(OBJECT)
	$(CC) -o $(LIB_SO_OBJ) $(OBJECT) $(WALL) $(DYNAMIC) $(SHARED) 
#	@echo $(shell pwd)
	mv $(LIB_SO_OBJ) $(BIN_DIR)

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
