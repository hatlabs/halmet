---
title: Introduktion
translated_from: 2ad10049c9c3d0b5f6fb78356500eaa25670febd
---

# Introduktion

HALMET, Hat Labs Marine Engine & Tank interface, er et udviklingskort til tilslutning af motor- og tanksensorer på både og andre køretøjer. Det kan bruges til at aflæse digitale og analoge sensorer og til at kommunikere med andre enheder via NMEA 2000, WiFi, Bluetooth, I2C, 1-Wire eller GPIO.

<figure markdown="span">
![](halmet_v1_top_photo.jpg){ width="60%" }
<figcaption>Billede af HALMET</figcaption>
</figure>

## Vigtigste funktioner

- **Fire digitale indgange**: HALMET har fire digitale indgange til aflæsning af digitale alarmsignaler eller til brug som tællere. Indgangene tåler spændinger mellem −32 V og +32 V. De digitale indgange kan bruges både til at registrere signalniveauer og til tidsvarierende signaler som motorens omdrejningstal, brændstofflow eller pulser fra en kædetæller.

- **Fire analoge indgange**: HALMET har fire analoge indgange til aflæsning af analoge sensorer. Indgangene tåler spændinger mellem −32 V og +32 V og har et måleområde fra 0 til 32 V. Indgangene er forbundet til en 16-bits analog-digital-omsætter (ADC) af typen ADS1115. De analoge indgange kan bruges både til passiv spændingsmåling og til aktiv modstandsmåling.

- **NMEA 2000-kompatibel**: HALMET er fuldt kompatibel med NMEA 2000-standarden. Kortet kan sluttes til et NMEA 2000-netværk gennem den indbyggede NMEA 2000-grænseflade.

- **I2C-, 1-Wire- og GPIO-grænseflader**: HALMET har en 4-benet I2C-grænseflade, en 3-benet 1-Wire-grænseflade og 13 tilgængelige almene ind- og udgange (GPIO).

- **WiFi og Bluetooth**: HALMET har et indbygget ESP32-WROOM-32E-modul med WiFi og Bluetooth. De understøtter både tilslutning til eksisterende WiFi-netværk og oprettelse af et WiFi-adgangspunkt, så du kan forbinde dig direkte til kortet.

- **ESP32-WROOM-32E med 16 MB flashhukommelse**: ESP32-WROOM-32E-modulet giver rigelig regnekraft og hukommelse til selv de mest krævende anvendelser. De 16 MB flashhukommelse gør det muligt at gemme store datamængder lokalt.

- **Bredt indgangsspændingsområde**: HALMET kan uden videre forsynes fra de 12 V- eller 24 V-anlæg, der normalt findes i køretøjer og både. HALMET tåler indgangsspændinger mellem 5 V og 32 V.

HALMET er åben hardware og udgives under licensen Creative Commons Attribution-ShareAlike 4.0 International.

## Anskaffelse af hardwaren

Du kan købe HALMET-kort hos [Hat Labs Oy](https://shop.hatlabs.fi). Alle designfiler er desuden tilgængelige i [GitHub-repositoriet med HALMET-hardwaren](https://github.com/hatlabs/halmet-hardware/).
