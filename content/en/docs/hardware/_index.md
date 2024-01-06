---
linkTitle: Hardware
title: Hardware Description
weight: 400
---

## ESP32 Introduction

HALMET is based on the powerful ESP32-WROOM-32E microcontroller module. The ESP32 is a dual-core microcontroller with built-in WiFi and Bluetooth connectivity. The ESP32 is a popular choice for IoT applications due to its low cost, good set of peripherals, and ease of use.

## GPIO Reference

HALMET reserves a number of GPIO pins for the input peripherals. Available GPIO pins
are broken out to the 2x10 pin GPIO header. The following table lists the GPIO pins
and their functions.

| GPIO | Function | Notes |
|-----:|:---------|:------|
| 0    | Boot button    | Enter bootloader when pulled low |
| 1    | TXD0  | Transmit data to USB |
| 2   | LED  | Onboard red LED |
| 3   | RXD0  | Receive data from USB |
| 4   | 1-Wire DQ | 1-Wire data line |
| 5   | - | Available on the GPIO header |
| 12  | - / TDI | Available on the GPIO header. Optionally: JTAG TDI |
| 13  | - / TCK | Available on the GPIO header. Optionally: JTAG TCK |
| 14  | - / TMS | Available on the GPIO header. Optionally: JTAG TMS |
| 15  | - / TDO | Available on the GPIO header. Optionally: JTAG TDO |
| 16  | - | Available on the GPIO header |
| 17  | - | Available on the GPIO header |
| 18  | CAN RX | Receive from NMEA 2000 |
| 19  | CAN TX | Transmit to NMEA 2000 |
| 21  | I2C SDA | I2C data line. Used for analog input |
| 22  | I2C SCL | I2C clock line. Used for analog inputs |
| 23  | DI1 | Digital Input 1 |
| 25  | DI2 | Digital Input 2 |
| 27  | DI3 | Digital Input 3 |
| 26  | DI4 | Digital Input 4 |
| 32  | - | Available on the GPIO header |
| 33  | - | Available on the GPIO header |
| 34  | - | Available on the GPIO header |
| 35  | - | Available on the GPIO header |
| 36 (VP) | Input only | Available on the GPIO header |
| 39 (VN) | Input only | Available on the GPIO header |

## Tour Around the Board

TODO

## Connectors

TODO

## Power Supply

TODO

## NMEA 2000

TODO

## Status LEDs

TODO

## 1-Wire

TODO

## I2C

TODO