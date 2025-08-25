Circular Buffer Library
A simple and modular C library for working with circular buffers (ring buffers).
Implements enqueue/dequeue, size checks, and wraparound handling.

Features
Dynamically allocated circular buffer
Functions for initialization, cleanup, put (enqueue), get (dequeue)
Check if buffer is empty or full
Read multiple items at once
Lightweight, dependency-free, portable C

section-01/circular-buffer-lib/ 
├── inc/ # Header files (public API) - contains function prototypes - basically like an api you can use 
├── src/ # Source files (implementation) - actual implementatation of the functions to make the circular buffer library work 
├── tests/ # Unit tests - used to test each function in our source file to make sure program run as intended 
├── Makefile # Build automation - Automates the build process with a command so you don't have to do it step by step 
└── README.md # Project documentation - Tells you what's going on in this project. You are currently in it right now.

Build Instructions
make        # build the library and tests
make clean  # remove build artifacts
make test   # run unit tests (if defined in Makefile)
make run    # alternative test target
