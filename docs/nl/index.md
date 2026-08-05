---
title: Inleiding
translated_from: 864a9f606fb309bc3e706c3231d0ec7208b25eed
---

# Inleiding

HALMET, de Hat Labs Marine Engine & Tank interface, is een ontwikkelbord voor het aansluiten van motor- en tanksensoren op boten en andere voertuigen. De print kan digitale en analoge sensoren uitlezen en verbinding maken met andere apparaten via NMEA 2000-, wifi-, Bluetooth-, I2C-, 1-Wire- of GPIO-interfaces.

<figure markdown="span">
![](halmet_v1_top_photo.jpg){ width="60%" }
<figcaption>Afbeelding van de HALMET</figcaption>
</figure>

## Belangrijkste kenmerken

- **Vier digitale ingangen**: de HALMET heeft vier digitale ingangen voor het lezen van digitale alarmsignalen of voor gebruik als tellers. De ingangen verdragen spanningen tussen −32 V en +32 V. Met de digitale ingangen kunt u zowel signaalniveaus als in de tijd variërende signalen detecteren, zoals motortoerental, brandstofdebiet of pulsen van een kettingteller.

- **Vier analoge ingangen**: de HALMET heeft vier analoge ingangen voor het uitlezen van analoge sensoren. De ingangen verdragen spanningen tussen −32 V en +32 V, met een meetbereik van 0 tot 33 V. De ingangen zijn aangesloten op een ADS1115-analoog-digitaalomzetter met een 16-bits resolutie. De analoge ingangen zijn geschikt voor zowel passieve spanningsmetingen als actieve weerstandsmetingen.

- **NMEA 2000-compatibel**: de HALMET is volledig compatibel met de NMEA 2000-standaard. De print kan via de ingebouwde NMEA 2000-interface op een NMEA 2000-netwerk worden aangesloten.

- **I2C-, 1-Wire- en GPIO-interfaces**: de HALMET heeft een 4-pins I2C-interface, een 3-pins 1-Wire-interface en 13 beschikbare universele in-/uitgangspoorten (GPIO's).

- **Wifi- en Bluetooth-verbindingen**: de HALMET heeft een geïntegreerde ESP32-WROOM-32E-module met wifi en Bluetooth. Daarmee kan de print zowel verbinding maken met bestaande wifi-netwerken als zelf een wifi-accesspoint opzetten, zodat u rechtstreeks verbinding met de print kunt maken.

- **ESP32-WROOM-32E met 16 MB flashgeheugen**: de ESP32-WROOM-32E-module biedt ruim voldoende rekenkracht en geheugen voor zelfs de meest veeleisende toepassingen. In het flashgeheugen van 16 MB kunnen grote hoeveelheden gegevens lokaal worden opgeslagen.

- **Groot ingangsspanningsbereik**: de HALMET kan veilig worden gevoed uit het 12 V- of 24 V-systeem dat in voertuigen en boten gebruikelijk is. De HALMET verdraagt ingangsspanningen tussen 5 V en 32 V.

HALMET is open hardware, uitgebracht onder de licentie Creative Commons Naamsvermelding-GelijkDelen 4.0 Internationaal.

## De hardware aanschaffen

HALMET-printen koopt u bij [Hat Labs Oy](https://shop.hatlabs.fi). Alle ontwerpbestanden zijn ook beschikbaar in de [GitHub-repository met HALMET-hardware](https://github.com/hatlabs/halmet-hardware/).
