---
title: Aan de slag
translated_from: 75bcdba18bc044c04ce3e220067bf537e069ec82
---

# Aan de slag

## De hardware monteren

Om connectoren in kleine behuizingen flexibeler te kunnen plaatsen, worden HALMET-printen geleverd zonder gemonteerde 1-Wire- of GPIO-pinheaders. Wilt u een van deze interfaces gebruiken, dan moet u de pinheaders zelf op de print solderen.

Hebt u instructies nodig voor het solderen van pinheaders op de print, kijk dan bij de [montage-instructies](https://docs.hatlabs.fi/sh-esp32/pages/getting-started/#revision-1-boards) van de SH-ESP32.

## De print voeden

De HALMET wordt gevoed via de NMEA 2000-connector. Sluit u de HALMET aan op een NMEA 2000-netwerk, dan kunt u de print rechtstreeks vanuit het netwerk voeden. Sluit in dat
geval de aders van de NMEA 2000-kabel aan op het 4-pins steekbare klemmenblok, zoals in de volgende afbeelding.

<figure markdown="span">
![](halmet_n2k_input.jpg){ width="50%" }
<figcaption>Sluit de aders van de NMEA 2000-kabel aan op het klemmenblok zoals weergegeven.</figcaption>
</figure>

Sluit u de HALMET niet aan op een NMEA 2000-netwerk, gebruik dan hetzelfde klemmenblok maar sluit alleen aders aan op de posities `-` en `+`. Elke voedingsbron van 5–32 V voldoet. Het typische stroomverbruik van de print met actieve wifi is 0,07 A bij 12 V.

<figure markdown="span">
![](power_connector.jpg){ width="50%" }
<figcaption>Sluit de voedingsaders aan op het klemmenblok zoals weergegeven.</figcaption>
</figure>

## Behuizingen

Voor gebruik aan boord hoort de HALMET altijd in een waterdichte behuizing te zitten.
De print is ontworpen om in de [SH-ESP32-behuizing](https://shop.hatlabs.fi/products/sh-esp32-enclosure) te passen. Hieronder ziet u een voorbeeld van een HALMET-print die in deze behuizing is gemonteerd.

<figure markdown="span">
![](halmet_small_enclosure.jpg){ width="50%" }
<figcaption>De HALMET gemonteerd in de SH-ESP32-behuizing.</figcaption>
</figure>

In de SH-ESP32-behuizing is maar beperkt ruimte voor connectoren.
Op elke lange zijde passen in de praktijk slechts 2–3 paneelconnectoren.
Wilt u meer dan een paar ingangen aansluiten, dan is een grotere behuizing aan te raden.
De [compacte SH-RPi-behuizing](https://shop.hatlabs.fi/products/compact-weatherproof-enclosure-for-raspberry-pi-and-sh-rpi-158x90x60-mm) van Hat Labs, hieronder afgebeeld, biedt bijvoorbeeld al ruim voldoende plaats voor connectoren.

<figure markdown="span">
![](medium_enclosure.jpg){ width="50%" }
<figcaption>De compacte SH-RPi-behuizing biedt meer ruimte voor het plaatsen van paneelconnectoren.</figcaption>
</figure>


Andere geschikte waterdichte behuizingen zijn eenvoudig te vinden op elke online marktplaats. Ook grotere lasdozen voor buitengebruik voldoen voor dit doel.

### Gaten boren voor paneelconnectoren

De behuizingen hebben meestal geen voorgeboorde gaten. Gebruik bij het boren
altijd een conische boor of een trapboor (die eruitziet als een klein metalen kerstboompje). Gewone metaalboren happen al snel te veel en kunnen de wand van de behuizing doen scheuren.

Houd bij het bepalen van de plaats van de gaten en de connectoren voldoende vrije ruimte aan voor het aandraaien van de wartelmoeren en voor het huis van de connector. Wilt u de behuizing aan de wand monteren, plaats de connectoren dan bij voorkeur omlaag gericht, om de kans op binnendringend water zo klein mogelijk te maken.

Geschikte gatmaten voor de verschillende connectoren:

- PG7-kabelwartel en M12-paneelconnector (NMEA 2000): 12,5 mm of 1/2 inch
- SP13-paneelconnectoren (blauwzwarte kunststof connectoren): 13 mm
- PG9-kabelwartel: 16 mm of 5/8 inch

Met doorvoertules van rubber of silicone kunt u aanzienlijk meer kabels op dezelfde ruimte kwijt dan met paneelconnectoren of kabelwartels. Ze zijn echter niet zo waterdicht als paneelconnectoren of kabelwartels. Bovendien moet de kabel er permanent in worden vastgezet, wat het onderhoud aan
het systeem lastiger kan maken.

TODO: Een afbeelding van een doorvoertule toevoegen.

### De paneelconnectoren solderen

Gebruik bij het solderen van de interne aders aan de paneelconnectoren altijd krimpkous om de afzonderlijke aders.
Denk eraan de krimpkous _vóór_ het solderen over de ader te schuiven...
Meestal kunt u eerst soldeer in de pinholte van de connector aanbrengen, dat soldeer vervolgens opnieuw laten smelten en de ader erin steken.
