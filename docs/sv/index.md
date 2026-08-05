---
title: Introduktion
translated_from: 864a9f606fb309bc3e706c3231d0ec7208b25eed
---

# Introduktion

HALMET (Hat Labs Marine Engine & Tank interface) är ett utvecklingskort för att ansluta motor- och tankgivare på båtar och andra fordon. Det kan användas för att läsa digitala och analoga givare och för att ansluta till andra enheter via gränssnitten NMEA 2000, WiFi, Bluetooth, I2C, 1-Wire eller GPIO.

<figure markdown="span">
![](halmet_v1_top_photo.jpg){ width="60%" }
<figcaption>Bild på HALMET</figcaption>
</figure>

## Viktigaste egenskaper

- **Fyra digitala ingångar**: HALMET har fyra digitala ingångar för att läsa digitala larmsignaler eller för att användas som räknare. Ingångarna tål spänningar mellan −32 V och +32 V. De digitala ingångarna kan användas både för att detektera signalnivåer och för tidsvarierande signaler som motorns varvtal, bränsleflöde eller pulser från en kättingräknare.

- **Fyra analoga ingångar**: HALMET har fyra analoga ingångar för att läsa analoga givare. Ingångarna tål spänningar mellan −32 V och +32 V, med ett mätområde på 0–33 V. Ingångarna är anslutna till en 16-bitars ADS1115-AD-omvandlare. De analoga ingångarna kan användas både för passiv spänningsmätning och för aktiv resistansmätning.

- **NMEA 2000-kompatibel**: HALMET är fullt kompatibel med standarden NMEA 2000. Kortet kan anslutas till ett NMEA 2000-nätverk via det inbyggda NMEA 2000-gränssnittet.

- **I2C-, 1-Wire- och GPIO-gränssnitt**: HALMET har ett 4-poligt I2C-gränssnitt, ett 3-poligt 1-Wire-gränssnitt och 13 tillgängliga generella in- och utgångar (GPIO).

- **WiFi- och Bluetooth-anslutning**: HALMET har en integrerad ESP32-WROOM-32E-modul med WiFi och Bluetooth. De gör det möjligt både att ansluta till befintliga WiFi-nätverk och att skapa en WiFi-accesspunkt för att ansluta direkt till kortet.

- **ESP32-WROOM-32E med 16 MB flash**: ESP32-WROOM-32E-modulen ger gott om processorkraft och minne även för de mest krävande tillämpningarna. Med 16 MB flashminne kan stora datamängder lagras lokalt.

- **Brett inspänningsområde**: HALMET kan matas säkert från det 12 V- eller 24 V-system som är vanligt i fordon och båtar. HALMET tål inspänningar mellan 5 V och 32 V.

HALMET är öppen hårdvara och licensieras under Creative Commons Erkännande-DelaLika 4.0 Internationell.

## Skaffa hårdvaran

Du kan köpa HALMET-kort från [Hat Labs Oy](https://shop.hatlabs.fi). Alla konstruktionsfiler finns också i [GitHub-repositoriet för HALMET-hårdvaran](https://github.com/hatlabs/halmet-hardware/).
