cmake_minimum_required(VERSION 2.6)
project(Chip8_Tools)

# Versioning
set(Chip8_Tools_VERSION_MAJOR 1)
set(Chip8_Tools_VERSION_MINOR 2)
set(Chip8_Tools_VERSION_PATCH 1)
set(Chip8_Tools_ADDR "https://github.com/cheukyin699/chip-8-tools/")

# Extra options
option(GCOV "Adds flags for gcov" OFF)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x -Os -Wall")

if (GCOV)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fprofile-arcs -ftest-coverage")
endif ()

include_directories("${PROJECT_BINARY_DIR}")

enable_testing()
add_subdirectory("${PROJECT_SOURCE_DIR}/emulator")
add_subdirectory("${PROJECT_SOURCE_DIR}/disassembler")
add_subdirectory("${PROJECT_SOURCE_DIR}/assembler")


# Configuring
configure_file("${PROJECT_SOURCE_DIR}/inc/config.h.in"
               "${PROJECT_BINARY_DIR}/config.h")

# Testing using CTest
add_test(NAME AssemblerDisassemblerInverse
         COMMAND ${PROJECT_SOURCE_DIR}/tests/assembler-disassembler-cycle.sh 
                 ${PROJECT_SOURCE_DIR}/)
