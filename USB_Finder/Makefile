#
#The following make pc linux library
#
TARGET_EBOOT=libusbfinder.so

CC=g++
LD=ld
OBJ_EBOOT=./.obj_linux

VPATH=./
INCLUDE_EBOOT=

SOURCES = $(foreach path, $(subst :, , $(VPATH)), $(wildcard $(path)/*.cpp))
OBJTMP = $(notdir $(SOURCES:.cpp=.o))

OBJECTS_EBOOT = $(patsubst %, $(OBJ_EBOOT)/%, $(OBJTMP))

CFLAGS=-g -Wall -fPIC -fvisibility="hidden"

LDFLAGS=

$(OBJ_EBOOT)/%.o:%.cpp
	mkdir -p $(OBJ_EBOOT)
	$(CC) -c $< -o $@ $(CFLAGS)  $(INCLUDE_EBOOT)

TARGET_EBOOT:$(OBJECTS_EBOOT)
	$(CC) -shared -o $(TARGET_EBOOT) $(OBJECTS_EBOOT) $(LDFLAGS)

all: TARGET_EBOOT

clean:
	-rm -rf $(TARGET_EBOOT) 
	-rm -rf $(OBJ_EBOOT)

