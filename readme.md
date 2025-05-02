# LCD1602 Bare Metal Driver

A lightweight, bare-metal driver implementation for HD44780-compatible LCD1602 displays, designed for STM32 microcontrollers.

## Overview

This project provides a simple yet robust driver for controlling LCD1602 displays directly from STM32 microcontrollers without relying on HAL libraries or an RTOS. The implementation uses direct GPIO manipulation for maximum control and educational value.

## Features

- 4-bit LCD communication (DB4–DB7)
- Busy flag polling (reads LCD status on D7 pin)
- Full LCD initialization sequence
- Commands: Clear display, set cursor, print strings
- Low-level GPIO manipulation
- SysTick-based millisecond and microsecond delay functions

## 📷 Demo Output

![20250429_234704](https://github.com/user-attachments/assets/a0686275-b08d-4bc1-9532-a011ab9a734b)


## Hardware Connections

Connect your LCD1602 to the STM32 as follows:

| LCD Pin | STM32 Pin | Function |
|---------|-----------|----------|
| RS      | PA0       | Register Select |
| RW      | PA10      | Read/Write |
| E       | PA1       | Enable |
| D4      | PA4       | Data bit 4 |
| D5      | PA5       | Data bit 5 |
| D6      | PA6       | Data bit 6 |
| D7      | PA8       | Data bit 7 |
| VSS     | GND       | Ground |
| VDD     | 5V/3.3V   | Power supply |
| V0      | Potentiometer | Contrast adjustment |
| A       | 5V/3.3V   | Backlight + |
| K       | GND       | Backlight - |



## Building and Flashing

This project is designed to be built with standard ARM GCC toolchain.

1. Clone the repository
2. Build using make:
   ```
   make
   ```
3. Flash to your STM32 using ST-Link or similar:
   ```
   make flash
   ```

## Dependencies

- ARM GCC toolchain
- ST-Link utilities (for flashing)

## Educational Goals

This project is designed to deepen understanding of:

-LCD command timing and protocol

- Bit-banging GPIOs on Cortex-M4

- Bare-metal development (without HAL)

- ARM memory-mapped I/O

- SysTick timer usage for precise delay

## License

This project is released under the MIT License - see the LICENSE file for details.
