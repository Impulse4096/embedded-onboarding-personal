# We first set up the compiler and archiver tool with flags
CC      ?= gcc
AR      ?= ar
ARFLAGS ?= rcs

# We set up the flag with c11 standard, all warnings and extra warnings, and optimization level 2
# We set variables for our inc src and build files
CFLAGS  ?= -std=c11 -Wall -Wextra -O2
INCDIR   = inc
SRC_DIR  = src
BUILD    = build

# We set up our object and library files to variables
OBJS     = $(BUILD)/cbuf.o
LIB      = $(BUILD)/libcbuf.a

# We do the same for our demo object and target files
DEMOOBJ  = $(BUILD)/main.o
TARGET   = $(BUILD)/cbuffer_demo

#We declare that these are commands not files
.PHONY: all clean run

# Build everything
all: $(TARGET)

# Ensure build dir exists if not already
$(BUILD):
	@mkdir -p $(BUILD)

# first making sure build exists and we have our source files then we build our object files with our compiler
$(BUILD)/%.o: $(SRC_DIR)/%.c | $(BUILD)
	$(CC) $(CFLAGS) -I$(INCDIR) -c $< -o $@

# Build static library from object files
$(LIB): $(OBJS)
	$(AR) $(ARFLAGS) $@ $^

# Link the demo with library to create finally executable
$(TARGET): $(DEMOOBJ) $(LIB)
	$(CC) $(CFLAGS) $(DEMOOBJ) -L$(BUILD) -lcbuf -o $@

# Run the demo
run: $(TARGET)
	@./$(TARGET)

# Basically remove all files when rebuilding
clean:
	rm -rf $(BUILD)

