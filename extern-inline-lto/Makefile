DEBUG ?= 1
HEADERS = x.h
SOURCES = x.c main.c
OBJECTS = $(SOURCES:.c=.o)


ifeq ($(DEBUG),1)
CFLAGS_DEBUG = -O0 -g
else
CFLAGS_DEBUG = -O3 -g
endif

%.o: %.c
	$(CC) $(CFLAGS) $(CFLAGS_DEBUG) -c -o $@ $< -flto

test: $(OBJECTS)
	$(CC) $(CFLAGS) $(CFLAGS_DEBUG) -o test $^ -flto

clean:
	@rm -vf *.o
	@rm -vf test

show: $(OBJECTS) test
	$(foreach file, $(OBJECTS), nm $(file);)
	nm test | grep XXX || true
