# Minimum CMake version required
cmake_minimum_required(VERSION 3.15)

# Project name and version
project(AVRProject VERSION 1.0 LANGUAGES C)

# Define the target processor
set(MCU atmega128)

# Define the source files
set(SRC src/main.c)

set(TOOLPATH /home/rdy/00_workgit/atmega128/avr8-gnu-toolchain-linux_x86_64/bin/)
set(CMAKE_OBJCOPY ${TOOLPATH}avr-objcopy)
message("-> TOOLPATH:" ${TOOLPATH})
message("-> CMAKE_OBJCOPY:" ${CMAKE_OBJCOPY})

# Set the compiler flags for AVR-GCC
# Use set(CMAKE_C_FLAGS ...) or add_compile_options or target_compile_options
set(CMAKE_C_COMPILER ${TOOLPATH}avr-gcc)
set(CMAKE_C_FLAGS "-mmcu=${MCU} -Os")
set(CMAKE_EXE_LINKER_FLAGS "-mmcu=${MCU}")
message("-> CMAKE_C_COMPILER:" ${CMAKE_C_COMPILER})





# Define the output file
set(OUTPUT ${CMAKE_BINARY_DIR}/${PROJECT_NAME})
message("-> CMAKE_BINARY_DIR:" ${CMAKE_BINARY_DIR})
message("-> OUTPUT:" ${OUTPUT})

# Add the executable
add_executable(AVRProject.elf ${SRC})

# Add a custom command to generate the hex file
add_custom_command(
    TARGET AVRProject.elf
    POST_BUILD
    COMMAND ${CMAKE_OBJCOPY} -O ihex AVRProject.elf AVRProject.hex
    COMMENT "Generating ${OUTPUT}.hex"
)
message("-> CMAKE_stop")

# Add a custom target for cleaning the build files
#add_custom_target(clean_all
#    COMMAND ${CMAKE_COMMAND} -E remove ${OUTPUT}.elf ${OUTPUT}.hex
#    COMMENT "Cleaning build files"
#)
