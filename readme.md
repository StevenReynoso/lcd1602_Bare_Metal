# LCD1602 Bare Metal Driver

A lightweight, bare-metal driver implementation for HD44780-compatible LCD1602 displays, designed for STM32 microcontrollers.

## Overview

This project provides a simple yet robust driver for controlling LCD1602 displays directly from STM32 microcontrollers without relying on HAL libraries or an RTOS. The implementation uses direct GPIO manipulation for maximum control and educational value.

## Features

- Complete bare-metal implementation
- 4-bit interface mode support
- Custom character creation
- Display control functions (on/off, cursor, blink)
- Busy flag polling for reliable operation
- Utility functions for positioning and text display

## Hardware Connections

Connect your LCD1602 to the STM32 as follows:

| LCD Pin | STM32 Pin | Function |
|---------|-----------|----------|
| RS      | PA0       | Register Select |
| RW      | PA2       | Read/Write |
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

## API Reference

### Initialization

```c
void lcd_init(void);
```
Initializes the LCD in 4-bit mode.

### Display Control

```c
void lcd_clear(void);
```
Clears the display and returns cursor to home position.

```c
void lcd_home(void);
```
Returns cursor to home position (0,0).

```c
void lcd_display_on(uint8_t cursor, uint8_t blink);
```
Turns on the display with options for cursor and blink.

```c
void lcd_display_off(void);
```
Turns off the display.

### Cursor Control

```c
void lcd_set_cursor(uint8_t row, uint8_t col);
```
Positions the cursor at the specified row and column.

### Data Writing

```c
void lcd_write_char(char c);
```
Writes a single character at the current cursor position.

```c
void lcd_write_string(const char *str);
```
Writes a string at the current cursor position.

### Custom Characters

```c
void lcd_create_char(uint8_t location, const uint8_t *pattern);
```
Creates a custom character at the specified location (0-7).

## Usage Example

```c
int main(void) {
    // Initialize system clock and GPIO
    system_init();
    gpio_init();
    
    // Initialize LCD
    lcd_init();
    lcd_clear();
    lcd_display_on(1, 0);  // Display on, cursor on, blink off
    
    // Write a message
    lcd_set_cursor(0, 0);
    lcd_write_string("Hello, World!");
    lcd_set_cursor(1, 0);
    lcd_write_string("LCD1602 Demo");
    
    while (1) {
        // Main loop
    }
}
```

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

## License

This project is released under the MIT License - see the LICENSE file for details.
