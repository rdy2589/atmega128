# AVR ATmega VSCode Project

This is a basic setup for developing AVR ATmega projects using Visual Studio Code.

## Prerequisites

- [Visual Studio Code](https://code.visualstudio.com/)
- [AVR-GCC Toolchain](https://www.microchip.com/mplab/avr-support/avr-and-arm-toolchains-c-compilers)
- [AVRDUDE](http://savannah.nongnu.org/projects/avrdude/)

## Project Structure

```
.
├── .vscode
│   ├── launch.json
│   └── tasks.json
├── src
│   └── main.c
├── Makefile
└── README.md
```

## Build and Upload

1. Open the project in Visual Studio Code.
2. Build the project using `Ctrl+Shift+B`.
3. Upload the hex file to the microcontroller using the configured task.