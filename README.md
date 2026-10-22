# STM32G071 Development Kit
This is a minimalist development board for STMicroelectronics' STM32G071 microcontroller.
The devkit is powered from the on-board USB-C connector.
The devkit is programmed with an STLink connected to the on-board STDC14 pin header.
The devkit breaks out 32 pins to two pin headers, which are breadboard compatible.

### Motivation
After playing around with first Arduino then later ESP32, I wanted to familiarize myself with the STM32 ecosystem.
For one, I have a few other projects that would benefit from switching from ESP32 over to STM32.
Also, STM32 is much more widely used in the industry than either Arduino or ESP32; it is a boon for my resume.

However, I did not want to simply buy an official development kit, blink an LED, then let it gather dust.
So I decided to design my own development kit; as risky as it may seem, I needed to learn the hardware side of STM32 just as much as the software, and this project let me begin on both at once.

### Goals
My goal with this project was to familiarize myself with both STM32 software and hardware.
However, since this is my first foray into the STM32 ecosystem, I decided to take a minimalist approach to the design to remove as many variables as possible.

# Hardware Overview

## Microcontroller
This is the central component of the entire project.
Going into the project, I elected to eschew the older STM32 F-series microcontrollers, which were both older and less powerful, and more expensive.
I wanted to use a more modern microcontroller, but still something inexpensive and entry-level, and not designed for specific domains.
Therefore, I decided to use an STM32G0 microcontroller, which is general purpose and entry-level.
I settled on the STM32G071 specifically, because I wanted more capability than the STM32G031, but I did not need the security features of the STM32G081.

I chose the LQFP-32 package; the LQFP for its easier hand-soldering; the 32 pins because it seemed like a reasonable number of pins for a development kit.

## Power Supply
The development kit is powered with a USB-C port that exposes the power pins.
I chose not to implement USB-PD, as the 5V, 3A of USB 2.0 is plenty for the kit.

The USB voltage is regulated to 3.3V with an LDO regulator.
I originally wanted to fit a switching regulator on it, but the inductor and catch diode took up too much board space;
at any rate, I did not want to include a radiating component on the board.

## Programming
The development kit includes an STDC14 receptacle on the board, so that the user can program the microcontroller with an STLink.