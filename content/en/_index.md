---
type: docs
title: Introduction
linkTitle: "Home"
weight: 1
cascade:
# cf: https://www.docsy.dev/docs/adding-content/content/#alternative-site-structure
  - type: "docs"
    no_list: true
    _target:
    path: "/**"
---

HALMET, the Hat Labs Marine Engine & Tank interface, is a development board for connecting engine and tank sensors on boats and other vehicles. It can be used for reading digital and analog sensors, as well as for connecting to other devices using NMEA 2000, WiFi, Bluetooth, I2C, 1-Wire, or GPIO interfaces. 

{{< imgrel halmet_v1_top_photo.jpg "60%" >}}
HALMET image
{{< /imgrel >}}

## Key Features

- **Four digital inputs**: HALMET has four digital inputs for reading digital alarm signals or as counters. The inputs tolerate voltages between -32 V and +32 V. The digital inputs can be used both for detecting signal levels as well as time-varying signals such as engine RPM, fuel flow or chain counter pulses.

- **Four analog inputs**: HALMET has four analog inputs for reading analog sensors. The inputs tolerate voltages between -32 V and +32 V, with a measurement range of 0 to 32 V. The inputs are connected to a 16-bit ADS1115 analog-to-digital converter. The analog inputs can be used both for passive voltage measurements as well as active resistance measurements.

- **NMEA 2000 compatible**: HALMET is fully compatible with the NMEA 2000 standard. The board can be connected to a NMEA 2000 network using the built-in NMEA 2000 interface.

- **I2C, 1-Wire, and GPIO interfaces**: HALMET has a 4-pin I2C interface, a 3-pin 1-Wire interface, and a 13 available general-purpose input/output ports (GPIOs).

- **WiFi and Bluetooth connectivity**: HALMET has an integrated ESP32-WROOM-32E module with WiFi and Bluetooth connectivity. These support both connecting to existing WiFi networks as well as creating a WiFi access point for connecting to the board directly.

- **ESP32-WROOM-32E with 16 MB flash**: The ESP32-WROOM-32E module provides plenty of processing power and memory for even the most demanding applications. The 16 MB flash allows storing large amounts of data locally.

- **Wide voltage range input**: HALMET can be safely powered using the 12 V or 24 V power system commonly found in vehicles and boats. HALMET can tolerate input voltages between 5 V and 32 V.

HALMET is open hardware, licensed under the Creative Commons Attribution-ShareAlike 4.0 International license.

## Getting the Hardware

You can purchase HALMET boards from [Hat Labs Oy](https://shop.hatlabs.fi). All design files are also available at the [HALMET hardware GitHub repository](https://github.com/hatlabs/halmet-hardware/).
