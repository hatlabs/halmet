---
title: Einführung
translated_from: 864a9f606fb309bc3e706c3231d0ec7208b25eed
---

# Einführung

HALMET, das Hat Labs Marine Engine & Tank interface, ist ein Entwicklungsboard zum Anschluss von Motor- und Tanksensoren auf Booten und in anderen Fahrzeugen. Damit lassen sich digitale und analoge Sensoren auslesen sowie Verbindungen zu anderen Geräten über NMEA 2000, WLAN, Bluetooth, I2C, 1-Wire oder GPIO herstellen.

<figure markdown="span">
![](halmet_v1_top_photo.jpg){ width="60%" }
<figcaption>Abbildung des HALMET</figcaption>
</figure>

## Wichtigste Merkmale

- **Vier Digitaleingänge**: HALMET besitzt vier Digitaleingänge zum Lesen digitaler Alarmsignale oder zur Verwendung als Zähler. Die Eingänge vertragen Spannungen zwischen −32 V und +32 V. Mit den Digitaleingängen lassen sich sowohl Signalpegel als auch zeitlich veränderliche Signale wie Motordrehzahl, Kraftstoffdurchfluss oder Impulse eines Kettenzählers erfassen.

- **Vier Analogeingänge**: HALMET besitzt vier Analogeingänge zum Auslesen analoger Sensoren. Die Eingänge vertragen Spannungen zwischen −32 V und +32 V bei einem Messbereich von 0 bis 33 V. Sie sind mit einem ADS1115-Analog-Digital-Wandler mit 16-Bit-Auflösung verbunden. Die Analogeingänge eignen sich sowohl für passive Spannungsmessungen als auch für aktive Widerstandsmessungen.

- **NMEA-2000-kompatibel**: HALMET ist vollständig kompatibel mit dem NMEA-2000-Standard. Über die integrierte NMEA-2000-Schnittstelle lässt sich die Platine an ein NMEA-2000-Netzwerk anschließen.

- **I2C-, 1-Wire- und GPIO-Schnittstellen**: HALMET verfügt über eine 4-polige I2C-Schnittstelle, eine 3-polige 1-Wire-Schnittstelle und 13 frei verfügbare Allzweck-Ein-/Ausgänge (GPIOs).

- **WLAN- und Bluetooth-Konnektivität**: HALMET besitzt ein integriertes ESP32-WROOM-32E-Modul mit WLAN und Bluetooth. Damit lässt sich die Platine sowohl mit vorhandenen WLAN-Netzwerken verbinden als auch ein eigener WLAN-Access-Point für den direkten Zugriff auf die Platine aufspannen.

- **ESP32-WROOM-32E mit 16 MB Flash**: Das ESP32-WROOM-32E-Modul bietet reichlich Rechenleistung und Speicher auch für anspruchsvollste Anwendungen. Der 16 MB große Flash-Speicher erlaubt es, große Datenmengen lokal zu speichern.

- **Weiter Eingangsspannungsbereich**: HALMET kann sicher aus dem in Fahrzeugen und Booten üblichen 12-V- oder 24-V-Bordnetz versorgt werden. HALMET verträgt Eingangsspannungen zwischen 5 V und 32 V.

HALMET ist Open Hardware (offene Hardware) und steht unter der Lizenz Creative Commons Attribution-ShareAlike 4.0 International.

## Hardware beziehen

HALMET-Platinen können Sie bei [Hat Labs Oy](https://shop.hatlabs.fi) kaufen. Alle Designdateien sind außerdem im [GitHub-Repository der HALMET-Hardware](https://github.com/hatlabs/halmet-hardware/) verfügbar.
