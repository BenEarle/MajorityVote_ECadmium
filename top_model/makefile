CC=g++
CFLAGS=-std=c++17
COMPILE_TARGET=NUCLEO_F401RE
FLASH_TARGET=NODE_F401RE
EXECUTABLE_NAME=MAJ_VOTE_TOP

INCLUDRT_ARM_MBED=-I ../../cadmium/include
INCLUDEDESTIMES=-I ../../cadmium/DESTimes/include

embedded:
	mbed compile --target $(COMPILE_TARGET) --toolchain GCC_ARM --profile ../cadmium.json

flash:
	sudo cp ../BUILD/$(COMPILE_TARGET)/GCC_ARM-CADMIUM/*.bin /media/$(USER)/$(FLASH_TARGET)/
	$(info *** FLASH WILL TAKE ~15 Seconds! DO NOT RESET WHILE COM PORT LED IS FLASHING! ***)

all: main.o
	$(CC) -g -o $(EXECUTABLE_NAME) main.o 

main.o: main.cpp
	$(CC) -g -c $(CFLAGS) $(INCLUDRT_ARM_MBED) $(INCLUDEDESTIMES) main.cpp -o main.o

clean:
	rm -f $(EXECUTABLE_NAME) *.o *~

eclean:
	rm -rf ../BUILD
