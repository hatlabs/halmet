---
title: Introducción
translated_from: 864a9f606fb309bc3e706c3231d0ec7208b25eed
---

# Introducción

HALMET, la interfaz Hat Labs Marine Engine & Tank, es una placa de desarrollo para conectar sensores de motor y de tanque en embarcaciones y otros vehículos. Permite leer sensores digitales y analógicos, así como conectarse a otros dispositivos mediante las interfaces NMEA 2000, WiFi, Bluetooth, I2C, 1-Wire o GPIO.

<figure markdown="span">
![](halmet_v1_top_photo.jpg){ width="60%" }
<figcaption>Imagen de HALMET</figcaption>
</figure>

## Características principales

- **Cuatro entradas digitales**: HALMET tiene cuatro entradas digitales para leer señales de alarma digitales o para usarlas como contadores. Las entradas toleran tensiones de entre −32 V y +32 V. Las entradas digitales sirven tanto para detectar niveles de señal como señales variables en el tiempo, como las revoluciones del motor, el caudal de combustible o los impulsos del contador de cadena.

- **Cuatro entradas analógicas**: HALMET tiene cuatro entradas analógicas para leer sensores analógicos. Las entradas toleran tensiones de entre −32 V y +32 V, con un rango de medición de 0 a 33 V. Las entradas están conectadas a un convertidor analógico-digital ADS1115 de 16 bits. Las entradas analógicas se pueden usar tanto para medición pasiva de tensión como para medición activa de resistencia.

- **Compatible con NMEA 2000**: HALMET es totalmente compatible con el estándar NMEA 2000. La placa se puede conectar a una red NMEA 2000 mediante la interfaz NMEA 2000 integrada.

- **Interfaces I2C, 1-Wire y GPIO**: HALMET tiene una interfaz I2C de 4 pines, una interfaz 1-Wire de 3 pines y 13 puertos de entrada/salida de propósito general (GPIO) disponibles.

- **Conectividad WiFi y Bluetooth**: HALMET incorpora un módulo ESP32-WROOM-32E con conectividad WiFi y Bluetooth. Ambas permiten tanto conectarse a redes WiFi existentes como crear un punto de acceso WiFi para conectarse directamente a la placa.

- **ESP32-WROOM-32E con 16 MB de memoria flash**: el módulo ESP32-WROOM-32E ofrece potencia de proceso y memoria de sobra incluso para las aplicaciones más exigentes. Los 16 MB de memoria flash permiten almacenar localmente grandes cantidades de datos.

- **Amplio rango de tensión de entrada**: HALMET se puede alimentar con seguridad desde el sistema de 12 V o 24 V habitual en vehículos y embarcaciones. HALMET tolera tensiones de entrada de entre 5 V y 32 V.

HALMET es hardware abierto, con licencia Creative Commons Atribución-CompartirIgual 4.0 Internacional.

## Adquisición del hardware

Las placas HALMET se pueden comprar en [Hat Labs Oy](https://shop.hatlabs.fi). Todos los archivos de diseño están disponibles además en el [repositorio de hardware de HALMET en GitHub](https://github.com/hatlabs/halmet-hardware/).
