# TOOLS
CC ?= gcc
# OPTIONS
LEVEL ?= 3
DEBUG ?= -DNDEBUG
WARNINGS ?= -Wall -Werror -Wpedantic -Wunused-result -D_FORTIFY_SOURCE=2
CFLAGS ?= -std=gnu11 $(WARNINGS) $(DEBUG) -O$(LEVEL)

# SOURCE
SRC := main.c lista.c
# ARTIFACT
PROG := main
LAB  := 05

# GENERAL COMMANDS
.PHONY: all run clean debug zip

all: $(PROG)

run: $(PROG)
	./$(PROG)

zip: $(LAB).zip

debug: LEVEL = 0
debug: DEBUG = -DDEBUG
debug: CFLAGS += -ggdb3
debug: clean all

clean:
	rm -rf *.o $(PROG) *.zip

$(LAB).zip: makefile $(SRC) $(wildcard *.h)
	zip -J $@ $^


# BUILDING
$(PROG): $(SRC:.c=.o)
	$(CC) $(CFLAGS) $^ -o $@

%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@
