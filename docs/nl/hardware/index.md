---
title: Hardwarebeschrijving
translated_from: af5172f8fb6598935bf432cd9590095fe4f40312
---

# Hardware

## De ESP32 in het kort

De HALMET is gebaseerd op de krachtige microcontrollermodule ESP32-WROOM-32E. De ESP32 is een microcontroller met twee kernen en ingebouwde wifi- en Bluetooth-verbinding. De ESP32 is een populaire keuze voor IoT-toepassingen dankzij de lage prijs, het goede aanbod aan randapparatuur en het gebruiksgemak.

## Functionele blokken van de print

De verschillende functionele blokken van de print worden hieronder beschreven.

<figure markdown="span">
![](HALMET-func.jpg){ width="60%" }
<figcaption>De functionele blokken van de HALMET.</figcaption>
</figure>

1.  NMEA 2000-aansluiting en voedingsingang met beveiliging. De NMEA 2000-connector
    heeft de volgende beveiligingselementen:

    - Zelfherstellende zekering van 500 mA
    - Ompoolbeveiligingsdiode
    - TVS-diodes voor overspannings- en ESD-beveiliging
    - Tweetraps storingsfiltering

2.  Voeding. Een schakelende voeding met een maximale uitgangsstroom van 2 A.

3.  CAN-transceiver voor NMEA 2000. RX- en TX-leds geven het verkeer op de
    CAN-bus zichtbaar weer.

4.  I2C- en 1-Wire-aansluitingen voor het aansluiten van extra sensoren.

5.  Gebruikersinterface. Een resetknop, een knop voor de bootmodus die ook als
    algemene knop dienstdoet, een rode voedings-led en een blauwe, door de
    gebruiker programmeerbare led.

6.  USB 2.0-aansluiting voor programmeren en debuggen.

7.  ESP32-WROOM-32E-module met ingebouwde wifi en Bluetooth. De module op de
    HALMET-print bevat 16 MB flashgeheugen.

8.  Schakeling voor de galvanische scheiding van de digitale en analoge ingangen.

9.  Analoge ingangen. De print heeft vier analoge ingangen met een 16-bits
    resolutie en een maximale ingangsspanning van 33 V. Elke ingang heeft een
    onderspannings- en overspanningsbeveiliging en een laagdoorlaatfilter met een
    afsnijfrequentie van 160 Hz om de meetruis te beperken.

    De analoge ingangen hebben een optionele constantstroombron van 10 mA voor
    actieve weerstandsmeting. De constantstroombron kan met de
    CCS-jumperheaders worden ingeschakeld.

    In de weerstandsmeetmodus is de maximaal meetbare weerstand 320 Ω.

10. Digitale ingangen. De HALMET heeft vier digitale ingangen met een maximale
    ingangsspanning van ±30 V. De ingangen bevatten een Schmitt trigger die de
    ruisongevoeligheid verbetert.


## Galvanische scheiding

De print heeft een galvanische scheiding tussen de digitale en analoge ingangen
enerzijds en de ESP32-microcontroller anderzijds. De scheiding is gerealiseerd met
digitale isolatoren voor respectievelijk I2C en de vier digitale ingangen, en met
een gescheiden DC/DC-omzetter die het gescheiden deel voedt.

Dankzij deze scheiding kan de print vanuit het NMEA 2000-netwerk worden gevoed
zonder risico op aardlussen. De scheiding beschermt de ingangen bovendien tegen
spanningspieken en ruis.

<figure markdown="span">
![](HALMET-isolation.jpg){ width="60%" }
<figcaption>De scheidingsbarrière van de HALMET. De ingangsconnectoren zijn gescheiden van
de rest van de print, wat betekent dat ze geen gemeenschappelijke massa met de rest van
de print delen.</figcaption>
</figure>

## Connectoren

<div class="row" markdown>
  <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-top.jpg){ width="100%" }
<figcaption>De connectoren van de HALMET, bovenzijde.</figcaption>
</figure>

   </div>
   <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-bottom.jpg){ width="100%" }
<figcaption>De connectoren van de HALMET, onderzijde.</figcaption>
</figure>

   </div>
</div>

### Connectoren aan de bovenzijde

1.  NMEA 2000-connector. De connector is een 4-polig steekbaar klemmenblok dat
    compatibel is met Phoenix MC 3.81. Via deze connector wordt de print op een
    NMEA 2000-netwerk aangesloten en gevoed.

2.  1-Wire-pinheader. Met de 1-Wire-pinheader kunt u 1-Wire-sensoren op de print
    aansluiten. De connector is een 3-pins pinheader met 2,54 mm steek. De
    pinheader is standaard niet op de print gemonteerd, omdat hij de plaatsing van
    de paneelconnectoren van de behuizing kan hinderen.

3.  I2C-pinheader. Met de I2C-pinheader kunt u I2C-sensoren op de print
    aansluiten. De connector is een 4-pins pinheader met 2,54 mm steek.

4.  Micro-USB-connector. Deze connector wordt gebruikt om de print te programmeren
    en te debuggen.

5.  Niet-bestukte soldeereilanden voor de reset- (EN) en boot-signalen (IO0).

6.  GPIO-pinheader. De GPIO-pinheader is een 2×10-pins pinheader met 2,54 mm
    steek. Hij brengt de beschikbare GPIO-pinnen van de ESP32 naar buiten en kan
    ook als JTAG-pinheader worden gebruikt.

7.  Voedingspinheader van het gescheiden deel. Via deze pinheader kunt u externe
    apparaten voeden vanaf 3V3 en GND van het gescheiden deel.

8.  Contacten van de jumperheader voor de constantstroombron (CCS) van de analoge
    ingangen. De constantstroombron wordt ingeschakeld door de jumpercontacten
    door te verbinden.

9.  Connectoren van de analoge ingangen. Het zijn 2-polige steekbare klemmenblokken
    die compatibel zijn met Phoenix MC 3.81. Hiermee sluit u analoge sensoren op de
    print aan.

10. Connectoren van de digitale ingangen. Het zijn 2-polige steekbare klemmenblokken
    die compatibel zijn met Phoenix MC 3.81. Hiermee sluit u digitale sensoren op de
    print aan.

### Connectoren aan de onderzijde

11.  Soldeerbrug voor de CAN-afsluitweerstand. Door de brug dicht te solderen
     schakelt u de afsluitweerstand van 120 Ω voor de CAN-bus in. Gebruik de
     afsluitweerstand niet in NMEA 2000-netwerken.

12.  Soldeerbrug voor het laagdoorlaatfilter. Door de brug dicht te solderen
     schakelt u een laagdoorlaatfilter in op de bijbehorende analoge ingang. Het
     filter heeft een afsnijfrequentie van 2,3 kHz. Het filter kan bijvoorbeeld
     worden gebruikt om de ruis in een toerentellersignaal te verminderen.

13.  Soldeerbrug voor de pull-downweerstand. Door de brug dicht te solderen
     schakelt u een pull-downweerstand van 100 kΩ in op de bijbehorende digitale
     ingang. Met de pull-downweerstand kunt u een maakcontact (NO) uitlezen dat bij
     sluiten hoog wordt getrokken.

14.  Soldeerbrug voor de pull-upweerstand. Door de brug dicht te solderen schakelt
     u een pull-upweerstand van 100 kΩ in op de bijbehorende digitale ingang. Met
     de pull-upweerstand kunt u een verbreekcontact (NC) uitlezen dat bij sluiten
     laag wordt getrokken.

15.  Soldeerbruggen voor de keuze van het I2C-adres van de ADS1115. Door de bruggen
     dicht te solderen kiest u het I2C-adres van de analoog-digitaalomzetter
     (AD-omzetter) ADS1115. Zo voorkomt u adresconflicten wanneer er meerdere
     ADS1115-omzetters op dezelfde I2C-bus zijn aangesloten. De soldeereilanden
     kunnen ook worden gebruikt om extra I2C-apparaten op het gescheiden deel van
     de print aan te sluiten.

### GPIO-overzicht

De HALMET reserveert een aantal GPIO-pinnen voor de ingangsperiferie. De beschikbare
GPIO-pinnen zijn naar de 2×10-pins GPIO-pinheader gebracht. De volgende tabel geeft
de GPIO-pinnen en hun functies.

|    GPIO | Functie     | Opmerkingen                                          |
| ------: | :---------- | :--------------------------------------------------- |
|       0 | Bootknop    | Gaat naar de bootloader wanneer laag getrokken       |
|       1 | TXD0        | Data verzenden naar USB                              |
|       2 | LED         | Rode led op de print                                 |
|       3 | RXD0        | Data ontvangen van USB                               |
|       4 | 1-Wire DQ   | 1-Wire-datalijn                                      |
|       5 | -           | Beschikbaar op de GPIO-pinheader                     |
|      12 | - / TDI     | Beschikbaar op de GPIO-pinheader. Optioneel: JTAG TDI |
|      13 | - / TCK     | Beschikbaar op de GPIO-pinheader. Optioneel: JTAG TCK |
|      14 | - / TMS     | Beschikbaar op de GPIO-pinheader. Optioneel: JTAG TMS |
|      15 | - / TDO     | Beschikbaar op de GPIO-pinheader. Optioneel: JTAG TDO |
|      16 | -           | Beschikbaar op de GPIO-pinheader                     |
|      17 | -           | Beschikbaar op de GPIO-pinheader                     |
|      18 | CAN RX      | Ontvangst van NMEA 2000                              |
|      19 | CAN TX      | Verzending naar NMEA 2000                            |
|      21 | I2C SDA     | I2C-datalijn. Gebruikt voor de analoge ingang        |
|      22 | I2C SCL     | I2C-kloklijn. Gebruikt voor de analoge ingangen      |
|      23 | DI1         | Digitale ingang 1                                    |
|      25 | DI2         | Digitale ingang 2                                    |
|      27 | DI3         | Digitale ingang 3                                    |
|      26 | DI4         | Digitale ingang 4                                    |
|      32 | -           | Beschikbaar op de GPIO-pinheader                     |
|      33 | -           | Beschikbaar op de GPIO-pinheader                     |
|      34 | -           | Beschikbaar op de GPIO-pinheader                     |
|      35 | -           | Beschikbaar op de GPIO-pinheader                     |
| 36 (VP) | Alleen ingang | Beschikbaar op de GPIO-pinheader                   |
| 39 (VN) | Alleen ingang | Beschikbaar op de GPIO-pinheader                   |


## Voeding

Het toegestane ingangsspanningsbereik van de print is 5–32 V. Het typische
stroomverbruik is 90 mA bij 12 V met de wifi-module actief (komt overeen met 1,1 W).

## NMEA 2000

NMEA 2000 is een alomtegenwoordige communicatiestandaard waarmee sensoren, bedieningsapparatuur en displays op boten en schepen met elkaar worden verbonden. De standaard is gebaseerd op het Controller Area Network (CAN-bus), een voertuigbusstandaard die is ontworpen om apparaten zonder tussenkomst van een hostcomputer met elkaar te laten communiceren.

De print voldoet aan de NMEA 2000-standaard zolang geen van de niet-gescheiden
connectoren is verbonden met andere apparaten die naar massa gerefereerd zijn. Zo
kan een 1-Wire-temperatuursensor met een lange kabel wel worden gebruikt, omdat die
geen gemeenschappelijke massa met andere apparaten deelt. Het aansluiten van een
AD-omzetter met I2C op de niet-gescheiden I2C-connector doorbreekt de conformiteit
met NMEA 2000 echter wel.

TODO: NMEA 2000 GPIO-pinbezetting

## Status-leds

Op de HALMET-print zitten twee knoppen en twee leds. De twee knoppen zijn gemarkeerd met “Reset” en “Boot”. De Reset-knop start de print opnieuw op door de Enable-pin van de ESP32 laag te trekken. De Boot-knop is verbonden met GPIO0 en kan tijdens het opstarten van het apparaat worden gebruikt om de module in de downloadmodus te dwingen. Verder kan hij als gewone knopingang worden gebruikt.

De twee leds zijn niet apart gemarkeerd. De rode led brandt zodra er 3,3 V op de print staat. De blauwe led is verbonden met GPIO2 (de pin die op ESP32-ontwikkelborden gewoonlijk voor een led wordt gebruikt). Gebruikersprogramma's kunnen hem aansturen om de toestand van het apparaat aan te geven.

## 1-Wire

1-Wire is een communicatiebussysteem voor apparaten, ontworpen door Dallas Semiconductor, dat inmiddels is overgenomen door Maxim Integrated Products. Hoewel 1-Wire een traag protocol is dat slechts snelheden tot 16,3 kbit/s ondersteunt, is het heel eenvoudig te implementeren en bruikbaar over grote afstanden. Het wordt veel gebruikt voor temperatuursensoren en vergelijkbare eenvoudige meetapparatuur.

De 1-Wire-implementatie van de HALMET bevat ESD- en RF-storingsfiltering en daarnaast laagdoorlaatfiltering om de betrouwbaarheid van het netwerk te verbeteren.

Let op: de datapin van 1-Wire (de opdruk “DQ”) is fysiek gekoppeld aan GPIO4; gebruik in uw programma dus GPIO4 voor alle 1-Wire-data.

## I2C

I2C (Inter-Integrated Circuit) is een zeer populaire synchrone seriële communicatiebus die veel wordt gebruikt om allerlei verschillende IC's aan te sturen. De bus gebruikt twee datadraden, naast voeding en massa.

De HALMET gebruikt I2C intern voor de ADS1115-AD-omzetter. De I2C-bus is ook naar een 4-pins pinheader gebracht om extra I2C-apparaten aan te sluiten.

De I2C-bus is verbonden met GPIO21 (SDA) en GPIO22 (SCL) van de ESP32. Dit zijn de standaard I2C-pinnen in de Arduino-ESP32-omgeving, maar ze wijken af van de standaardpinnen van de SH-ESP32.
