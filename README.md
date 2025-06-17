# STM32 Nucleo F446RE UART LED Toggle Example

## Overview

This project demonstrates how to control an onboard LED on the STM32 Nucleo F446RE board via UART commands using interrupt-driven UART reception.

The program initializes UART2 at 115200 baud rate and configures a GPIO pin connected to an LED as output. It listens for incoming UART data and toggles or turns off the LED based on received characters:

- Sending character `'b'` toggles the LED.
- Sending character `'c'` turns the LED off.

UART communication feedback messages are sent back for user confirmation.

## Features

- UART2 configured at 115200 baud, 8N1 format, no flow control.
- Interrupt-based UART receive with HAL library.
- GPIO output to control onboard LED.
- LED toggle and off commands via UART input.
- Feedback message transmission via UART.

## Hardware

- STM32 Nucleo F446RE Development Board
- Onboard LED connected to GPIO PA6 (configurable)
- UART2 pins for communication (usually PA2 = TX, PA3 = RX)

## Software Requirements

- STM32CubeIDE or compatible STM32 development environment.
- STM32 HAL libraries.
- Standard C libraries.

## Code Structure

- `main.c`: Contains initialization, main loop, UART interrupt callback, and system configuration.
- `MX_GPIO_Init()`: Initializes GPIO pins including the LED pin.
- `MX_USART2_UART_Init()`: Configures UART2 peripheral.
- `HAL_UART_RxCpltCallback()`: UART interrupt callback that processes incoming data and toggles or switches off the LED accordingly.
- `SystemClock_Config()`: Configures the system clock to use HSE with PLL for 168 MHz CPU clock.

## Usage

1. Flash the firmware to your STM32 Nucleo F446RE board.
2. Open a serial terminal on your PC (e.g., PuTTY, Tera Term, CoolTerm) configured for:
   - Baud rate: 115200
   - Data bits: 8
   - Parity: None
   - Stop bits: 1
3. Send the following characters over UART:
   - `b` — Toggle the LED.
   - `c` — Turn the LED off.
4. Observe the LED behavior and UART feedback messages.

## Notes

- UART reception is interrupt-driven and automatically restarted after each received byte.
- Modify `GPIO_PIN_6` in the code if your LED is connected to a different pin.
- Ensure your serial terminal sends raw ASCII characters.

## License

This software uses STMicroelectronics HAL libraries and is provided "AS-IS" without warranty.

## Author
 Deva Nanda S
