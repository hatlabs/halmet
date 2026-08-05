---
title: Innledning
translated_from: 864a9f606fb309bc3e706c3231d0ec7208b25eed
---

# Innledning

HALMET, Hat Labs Marine Engine & Tank interface, er et utviklingskort for tilkobling av motor- og tankgivere på båter og andre kjøretøy. Det kan brukes til å lese digitale og analoge sensorer, og til å koble til andre enheter via NMEA 2000, WiFi, Bluetooth, I2C, 1-Wire eller GPIO.

<figure markdown="span">
![](halmet_v1_top_photo.jpg){ width="60%" }
<figcaption>Bilde av HALMET</figcaption>
</figure>

## Viktigste egenskaper

- **Fire digitale innganger**: HALMET har fire digitale innganger for lesing av digitale alarmsignaler eller for bruk som tellere. Inngangene tåler spenninger mellom −32 V og +32 V. De digitale inngangene kan brukes både til å registrere signalnivåer og til signaler som varierer over tid, for eksempel motorens turtall, drivstoffstrøm eller pulser fra en kjettingteller.

- **Fire analoge innganger**: HALMET har fire analoge innganger for lesing av analoge sensorer. Inngangene tåler spenninger mellom −32 V og +32 V, med et måleområde på 0–33 V. Inngangene er koblet til en 16 bits AD-omformer av typen ADS1115. De analoge inngangene kan brukes både til passiv spenningsmåling og til aktiv motstandsmåling.

- **NMEA 2000-kompatibel**: HALMET er fullt kompatibel med NMEA 2000-standarden. Kortet kan kobles til et NMEA 2000-nettverk gjennom det innebygde NMEA 2000-grensesnittet.

- **I2C-, 1-Wire- og GPIO-grensesnitt**: HALMET har et 4-pinners I2C-grensesnitt, et 3-pinners 1-Wire-grensesnitt og 13 tilgjengelige generelle inn- og utgangsporter (GPIO).

- **WiFi og Bluetooth**: HALMET har en integrert ESP32-WROOM-32E-modul med WiFi og Bluetooth. Dette gjør det mulig både å koble seg til eksisterende WiFi-nettverk og å opprette et WiFi-aksesspunkt slik at du kan koble deg direkte til kortet.

- **ESP32-WROOM-32E med 16 MB flashminne**: ESP32-WROOM-32E-modulen gir rikelig med regnekraft og minne selv til de mest krevende bruksområdene. Med 16 MB flashminne kan du lagre store datamengder lokalt.

- **Bredt inngangsspenningsområde**: HALMET kan trygt forsynes fra det 12 V- eller 24 V-anlegget som er vanlig i kjøretøy og båter. HALMET tåler inngangsspenninger mellom 5 V og 32 V.

HALMET er åpen maskinvare, lisensiert under Creative Commons Attribution-ShareAlike 4.0 International-lisensen.

## Skaffe maskinvaren

Du kan kjøpe HALMET-kort fra [Hat Labs Oy](https://shop.hatlabs.fi). Alle designfiler er også tilgjengelige i [GitHub-repositoriet for HALMET-maskinvaren](https://github.com/hatlabs/halmet-hardware/).
