# Directories
SRC_DIR := src
INC_DIR := inc
TEST_DIR := tests
BUILD_DIR := build

# Tools & flags
CC := gcc
CFLAGS := -std=c11 -Wall -Wextra -Werror -I$(INC_DIR)

# Sources/objects
SRC      := $(wildcard $(SRC_DIR)/*.c)
OBJ      := $(patsubst $(SRC_DIR)/%.c,$(BUILD_DIR)/%.o,$(SRC))
TEST_SRC := $(wildcard $(TEST_DIR)/*.c)
TEST_OBJ := $(patsubst $(TEST_DIR)/%.c,$(BUILD_DIR)/%.o,$(TEST_SRC))

# Targets
all: $(BUILD_DIR)/libcbuf.a $(BUILD_DIR)/tests

$(BUILD_DIR):
	mkdir -p $@

# Compile library sources
$(BUILD_DIR)/%.o: $(SRC_DIR)/%.c | $(BUILD_DIR)
	$(CC) $(CFLAGS) -c $< -o $@

# Compile test sources
$(BUILD_DIR)/%.o: $(TEST_DIR)/%.c | $(BUILD_DIR)
	$(CC) $(CFLAGS) -c $< -o $@

# Static library
$(BUILD_DIR)/libcbuf.a: $(OBJ)
	ar rcs $@ $^

# Link test runner
$(BUILD_DIR)/tests: $(TEST_OBJ) $(BUILD_DIR)/libcbuf.a
	$(CC) $^ -o $@

test: $(BUILD_DIR)/tests
	./$(BUILD_DIR)/tests

run: test

clean:
	rm -rf $(BUILD_DIR)

.PHONY: all test run clean
