CC ?= gcc
CFLAGS ?= -std=c11 -Wall -Wextra -O2
INCDIR = inc
SRC_DIR = src
BUILD = build
TARGET = $(BUILD)/cbuffer_demo

.PHONY: all clean run
all:$(TARGET)

$(BUILD):
	@mkdir -p $(BUILD)

$(TARGET): $(SRC_DIR)/main.c | $(BUILD)
	$(CC) $(CFLAGS) -I$(INCDIR) $(SRC_DIR)/main.c -o $@

run: $(TARGET)
	$(TARGET)

clean:
	rm -rf $(BUILD)
