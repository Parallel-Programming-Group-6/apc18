CC := gcc
CFLAGS := -Wall -O3
LDFLAGS := -lrt

ifeq ($(DEBUG),1)
  CFLAGS := $(CFLAGS) -g
  LDFLAGS := $(LDFLAGS) 
else ifeq ($(PROFILE),1)
  CFLAGS := $(CFLAGS) -DNDEBUG -pg -fprofile-arcs -ftest-coverage
  LDFLAGS := $(LDFLAGS) -pg -fprofile-arcs -ftest-coverage
endif


all: rollingsum

main.o: main.c
	$(CC) $(CFLAGS) -c main.c

ktiming.o: ktiming.c
	$(CC) $(CFLAGS) -c ktiming.c

sim.o: sum.c
	$(CC) $(CFLAGS) -c sum.c

rollingsum: main.o ktiming.o sum.o
	$(CC) -o rollingsum main.o ktiming.o sum.o $(LDFLAGS)

clean:
	rm -f rollingsum *.o
