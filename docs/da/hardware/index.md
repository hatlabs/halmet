---
title: Hardwarebeskrivelse
translated_from: 66f9306e0980490684ef1cb989b75a230f6600df
---

# Hardware

## Introduktion til ESP32

HALMET er baseret på det kraftfulde mikrocontrollermodul ESP32-WROOM-32E. ESP32 er en dobbeltkernet mikrocontroller med indbygget WiFi og Bluetooth. ESP32 er et populært valg til IoT-applikationer på grund af den lave pris, det gode udvalg af perifere enheder og den enkle anvendelse.

## Kortets funktionsblokke

Kortets forskellige funktionsblokke er beskrevet nedenfor.

<figure markdown="span">
![](HALMET-func.jpg){ width="60%" }
<figcaption>HALMETs funktionsblokke.</figcaption>
</figure>

1.  NMEA 2000 samt strømindgang og beskyttelse. NMEA 2000-stikket har følgende
    beskyttelseselementer:
    - 500 mA selvgendannende sikring
    - Diode til beskyttelse mod omvendt polaritet
    - TVS-dioder til overspændings- og ESD-beskyttelse
    - Totrins støjfiltrering

2.  Strømforsyning. En switchmode-strømforsyning med en maksimal udgangsstrøm på 2 A.

3.  CAN-transceiver til NMEA 2000. RX- og TX-LED'er giver en visuel indikation af
    aktiviteten på CAN-bussen.

4.  I2C- og 1-Wire-grænseflader til tilslutning af yderligere sensorer.

5.  Brugergrænseflade. En reset-knap, en knap til boot-tilstand og generelle formål,
    en rød strøm-LED og en blå brugerprogrammerbar LED.

6.  USB 2.0-grænseflade til programmering og fejlfinding.

7.  ESP32-WROOM-32E-modul med indbygget WiFi og Bluetooth. Modulet på HALMET-kortet
    indeholder 16 MB flashhukommelse.

8.  Kredsløb til galvanisk adskillelse af de digitale og analoge indgange.

9.  Analoge indgange. Kortet har fire analoge indgange med 16-bits opløsning og en
    maksimal indgangsspænding på 33 V. Hver indgang har beskyttelse mod under- og
    overspænding samt lavpasfiltrering med en knækfrekvens på 160 Hz, som reducerer
    målestøjen.

    De analoge indgange har en valgfri konstantstrømkilde på 10 mA til aktiv
    modstandsmåling. Konstantstrømkilden kan aktiveres med CCS-jumperstiklisterne.

    I modstandsmåletilstand er den største modstand, der kan måles, 320 ohm.

10. Digitale indgange. HALMET har fire digitale indgange med en maksimal
    indgangsspænding på ±30 V. Indgangene har en Schmitt trigger, der forbedrer
    støjimmuniteten.


## Galvanisk adskillelse

Kortet har galvanisk adskillelse mellem de digitale og analoge indgange og
ESP32-mikrocontrolleren. Adskillelsen er opnået med digitale isolatorer til
henholdsvis I2C og de fire digitale indgange samt med en adskilt DC/DC-omformer,
der forsyner den adskilte del.

Takket være adskillelsen kan kortet forsynes fra NMEA 2000-netværket uden risiko
for jordsløjfer. Adskillelsen beskytter også mod spændingsspidser og støj på
indgangene.

<figure markdown="span">
![](HALMET-isolation.jpg){ width="60%" }
<figcaption>HALMETs isolationsbarriere. Indgangsstikkene er adskilt fra resten af kortet,
hvilket betyder, at de ikke har fælles jordforbindelse med resten af kortet.</figcaption>
</figure>

## Stik

<div class="row" markdown>
  <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-top.jpg){ width="100%" }
<figcaption>HALMETs stik, oversiden.</figcaption>
</figure>

   </div>
   <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-bottom.jpg){ width="100%" }
<figcaption>HALMETs stik, undersiden.</figcaption>
</figure>

   </div>
</div>

### Stik på oversiden

1.  NMEA 2000-stik. Stikket er en 4-benet aftagelig klemrække, der er kompatibel
    med Phoenix MC 3.81. Stikket bruges til at forbinde kortet til et
    NMEA 2000-netværk og til at forsyne kortet.

2.  1-Wire-stikliste. 1-Wire-stiklisten kan bruges til at forbinde 1-Wire-sensorer
    til kortet. Den er en 3-benet stikliste med 2,54 mm benafstand. Stiklisten er
    ikke monteret på kortet fra fabrikken, fordi den kan komme i vejen for
    placeringen af kabinettets panelstik.

3.  I2C-stikliste. I2C-stiklisten kan bruges til at forbinde I2C-sensorer til
    kortet. Den er en 4-benet stikliste med 2,54 mm benafstand.

4.  Micro USB-stik. Stikket bruges til programmering og fejlfinding af kortet.

5.  Ubestykkede loddeflader til reset- (EN) og boot-signalerne (IO0).

6.  GPIO-stikliste. GPIO-stiklisten er en 2×10-benet stikliste med 2,54 mm
    benafstand. Stiklisten fører ESP32'ens ledige GPIO-ben ud og kan også bruges
    som JTAG-stikliste.

7.  Stikliste til forsyning af det adskilte område. Stiklisten kan bruges til at
    forsyne eksterne enheder fra 3V3 og GND i den adskilte del.

8.  Jumperkontakter til konstantstrømkilden (CCS) til de analoge indgange.
    Konstantstrømkilden kan aktiveres ved at kortslutte jumperkontakterne.

9.  Stik til analoge indgange. Stikkene er 2-benede aftagelige klemrækker, der er
    kompatible med Phoenix MC 3.81. Stikkene bruges til at forbinde analoge
    sensorer til kortet.

10. Stik til digitale indgange. Stikkene er 2-benede aftagelige klemrækker, der er
    kompatible med Phoenix MC 3.81. Stikkene bruges til at forbinde digitale
    sensorer til kortet.

### Stik på undersiden

11.  Loddejumper til CAN-terminering. Loddejumperen kan kortsluttes for at aktivere
     termineringsmodstanden på 120 ohm til CAN-bussen. Brug ikke
     termineringsmodstanden i NMEA 2000-netværk.

12.  Loddejumper til lavpasfilter. Loddejumperen kan kortsluttes for at aktivere et
     lavpasfilter på den pågældende analoge indgang. Filteret har en knækfrekvens
     på 2,3 kHz. Filteret kan for eksempel bruges til at reducere støj i signalet
     fra en omdrejningstæller.

13.  Loddejumper til pull-down-modstand. Loddejumperen kan kortsluttes for at
     aktivere en pull-down-modstand på 100 kohm på den pågældende digitale indgang.
     Pull-down-modstanden kan bruges til at aflæse en normalt åben (NO) kontakt,
     som trækkes høj, når den er sluttet.

14.  Loddejumper til pull-up-modstand. Loddejumperen kan kortsluttes for at aktivere
     en pull-up-modstand på 100 kohm på den pågældende digitale indgang.
     Pull-up-modstanden kan bruges til at aflæse en normalt sluttet (NC) kontakt,
     som trækkes lav, når den er sluttet.

15.  Loddejumpere til valg af ADS1115'ens I2C-adresse. Loddejumperne kan kortsluttes
     for at vælge I2C-adressen på analog-digital-omsætteren (ADC) ADS1115.
     Loddejumperne bruges til at undgå adressekonflikter, når der er forbundet flere
     ADS1115-AD-omsættere til den samme I2C-bus. Loddefladerne kan også bruges til
     at forbinde yderligere I2C-enheder til kortets adskilte område.

### GPIO-oversigt

HALMET reserverer et antal GPIO-ben til de perifere indgangsenheder. Ledige GPIO-ben
er ført ud til den 2×10-benede GPIO-stikliste. Følgende tabel viser GPIO-benene og
deres funktioner.

|    GPIO | Funktion    | Bemærkninger                                       |
| ------: | :---------- | :------------------------------------------------- |
|       0 | Boot-knap   | Går i bootloader, når benet trækkes lavt           |
|       1 | TXD0        | Sender data til USB                                |
|       2 | LED         | Rød LED på kortet                                  |
|       3 | RXD0        | Modtager data fra USB                              |
|       4 | 1-Wire DQ   | 1-Wire-datalinje                                   |
|       5 | -           | Ledig på GPIO-stiklisten                           |
|      12 | - / TDI     | Ledig på GPIO-stiklisten. Alternativt: JTAG TDI    |
|      13 | - / TCK     | Ledig på GPIO-stiklisten. Alternativt: JTAG TCK    |
|      14 | - / TMS     | Ledig på GPIO-stiklisten. Alternativt: JTAG TMS    |
|      15 | - / TDO     | Ledig på GPIO-stiklisten. Alternativt: JTAG TDO    |
|      16 | -           | Ledig på GPIO-stiklisten                           |
|      17 | -           | Ledig på GPIO-stiklisten                           |
|      18 | CAN RX      | Modtager fra NMEA 2000                             |
|      19 | CAN TX      | Sender til NMEA 2000                               |
|      21 | I2C SDA     | I2C-datalinje. Bruges til analog indgang           |
|      22 | I2C SCL     | I2C-klokkelinje. Bruges til analoge indgange       |
|      23 | DI1         | Digital indgang 1                                  |
|      25 | DI2         | Digital indgang 2                                  |
|      27 | DI3         | Digital indgang 3                                  |
|      26 | DI4         | Digital indgang 4                                  |
|      32 | -           | Ledig på GPIO-stiklisten                           |
|      33 | -           | Ledig på GPIO-stiklisten                           |
|      34 | -           | Ledig på GPIO-stiklisten                           |
|      35 | -           | Ledig på GPIO-stiklisten                           |
| 36 (VP) | Kun indgang | Ledig på GPIO-stiklisten                           |
| 39 (VN) | Kun indgang | Ledig på GPIO-stiklisten                           |


## Strømforsyning

Det tilladte indgangsspændingsområde på kortet er 5–32 V. Det typiske strømforbrug er
90 mA ved 12 V med WiFi-modulet aktivt (svarer til 1,1 W).

## NMEA 2000

NMEA 2000 er en udbredt kommunikationsstandard, der bruges til at forbinde sensorer, styreenheder og displayenheder på både og skibe. Den bygger på Controller Area Network (CAN-bussen), som er en køretøjsbusstandard, der er udviklet, så enheder kan kommunikere indbyrdes uden en værtscomputer.

Kortet overholder NMEA 2000-standarden, så længe ingen af de ikke-adskilte stik er forbundet til andre enheder med fælles jordreference. En 1-Wire-temperatursensor med et langt kabel kan for eksempel bruges, fordi den ikke har fælles jordforbindelse med andre enheder. Derimod ville det bryde overensstemmelsen med NMEA 2000 at forbinde en I2C-AD-omsætter til det ikke-adskilte I2C-stik.

TODO: NMEA 2000-benforbindelser til GPIO

## Status-LED'er

Der er to knapper og to LED'er på HALMET-kortet. De to knapper er mærket Reset og Boot. Reset-knappen genstarter kortet ved at trække ESP32'ens Enable-ben lavt. Boot-knappen er forbundet til GPIO0 og kan bruges under opstart af enheden til at tvinge modulet i download-tilstand. Ellers kan den bruges som en almindelig knapindgang.

De to LED'er er ikke udtrykkeligt mærket. Den røde LED lyser, når der er 3,3 V forsyning på kortet. Den blå LED er forbundet til GPIO2 (det ben, der almindeligvis bruges til LED på ESP32-udviklingskort). Den kan styres af brugerprogrammer og vise enhedens tilstand.

## 1-Wire

1-Wire er et bussystem til kommunikation mellem enheder, udviklet af Dallas Semiconductor, som siden er blevet opkøbt af Maxim Integrated Products. Selvom 1-Wire er en langsom protokol, der kun understøtter hastigheder op til 16,3 kbit/s, er den meget enkel at implementere og kan bruges over lange afstande. Den bruges almindeligvis til temperatursensorer og lignende enkle måleenheder.

HALMETs 1-Wire-implementering har ESD- og RF-støjfiltrering samt lavpasfiltrering, der forbedrer netværkets pålidelighed.

Bemærk, at 1-Wire-databenet (mærket »DQ«) fysisk er forbundet til GPIO4, så brug GPIO4 til alle 1-Wire-data i dit program.

## I2C

I2C (Inter-Integrated Circuit) er en meget udbredt synkron seriel kommunikationsbus, der almindeligvis bruges til at forbinde en række forskellige IC'er. Den bruger to dataledninger ud over spænding og jordforbindelse.

HALMET bruger I2C internt til AD-omsætteren ADS1115. I2C-bussen er også ført ud til en 4-benet stikliste, så der kan forbindes yderligere I2C-enheder.

I2C-bussen er forbundet til GPIO21 (SDA) og GPIO22 (SCL) på ESP32'en. Disse ben er standardbenene til I2C i Arduinos ESP32-miljø, men de er forskellige fra standardbenene på SH-ESP32.
