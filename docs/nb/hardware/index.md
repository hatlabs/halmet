---
title: Maskinvarebeskrivelse
translated_from: 96f96c3aff8d2a33ab2f1b59c0dbb8747c8ed3e2
---

# Maskinvare

## Introduksjon til ESP32

HALMET bygger på den kraftige mikrokontrollermodulen ESP32-WROOM-32E. ESP32 er en tokjernet mikrokontroller med innebygd WiFi og Bluetooth. ESP32 er et populært valg for IoT-anvendelser på grunn av lav pris, et godt utvalg av periferienheter og enkel bruk.

## Kortets funksjonsblokker

De ulike funksjonsblokkene på kortet er beskrevet nedenfor.

<figure markdown="span">
![](HALMET-func.jpg){ width="60%" }
<figcaption>Funksjonsblokker på HALMET.</figcaption>
</figure>

1.  NMEA 2000 og strøminngang med vern. NMEA 2000-kontakten har følgende
    vernkomponenter:
    - Selvtilbakestillende sikring på 500 mA
    - Diode for polvendingsvern
    - TVS-dioder for overspenningsvern og ESD-vern
    - Totrinns filtrering av elektrisk støy

2.  Strømforsyning. En switchet strømforsyning med maksimal utgangsstrøm på 2 A.

3.  CAN-transceiver for NMEA 2000. RX- og TX-LED-er gir en visuell indikasjon på
    aktiviteten på CAN-bussen.

4.  I2C- og 1-Wire-grensesnitt for tilkobling av flere sensorer.

5.  Brukergrensesnitt. En resetknapp, en boot-knapp som også kan brukes til
    generelle formål, en rød strøm-LED og en blå brukerprogrammerbar LED.

6.  USB 2.0-grensesnitt for programmering og feilsøking.

7.  ESP32-WROOM-32E-modul med innebygd WiFi og Bluetooth. Modulen på
    HALMET-kortet har 16 MB flashminne.

8.  Kretser for galvanisk isolasjon av de digitale og analoge inngangene.

9.  Analoge innganger. Kortet har fire analoge innganger med 16 bits oppløsning
    og en maksimal inngangsspenning på 33 V. Hver inngang har underspennings- og
    overspenningsvern samt lavpassfiltrering med en grensefrekvens på 160 Hz for
    å redusere målestøy.

    De analoge inngangene har en valgfri konstantstrømkilde på 10 mA for aktiv
    motstandsmåling. Konstantstrømkilden kan aktiveres med CCS-jumperpinnene.

    I motstandsmålingsmodus er den største motstanden som kan måles, 300 Ω.

10. Digitale innganger. HALMET har fire digitale innganger med en maksimal
    inngangsspenning på ±32 V. Inngangene har en Schmitt trigger som bedrer
    støyimmuniteten.


## Galvanisk isolasjon

Kortet har galvanisk isolasjon mellom de digitale og analoge inngangene og
ESP32-mikrokontrolleren. Isolasjonen er realisert med digitale isolatorer for
henholdsvis I2C og de fire digitale inngangene, og med en isolert DC/DC-omformer
som forsyner den isolerte seksjonen.

Takket være isolasjonen kan kortet forsynes fra NMEA 2000-nettverket uten fare
for jordsløyfer. Isolasjonen gir også vern mot spenningsspisser og støy på
inngangene.

<figure markdown="span">
![](HALMET-isolation.jpg){ width="60%" }
<figcaption>HALMETs isolasjonsbarriere. Inngangsklemmene er isolert fra resten av kortet
og har dermed ikke felles jord med resten av kortet.</figcaption>
</figure>

## Kontakter

<div class="row" markdown>
  <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-top.jpg){ width="100%" }
<figcaption>HALMETs kontakter, oversiden.</figcaption>
</figure>

   </div>
   <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-bottom.jpg){ width="100%" }
<figcaption>HALMETs kontakter, undersiden.</figcaption>
</figure>

   </div>
</div>

### Kontakter på oversiden

1.  NMEA 2000-kontakt. Kontakten er en 4-pinners pluggbar koblingsklemme som er
    kompatibel med Phoenix MC 3,81. Den brukes til å koble kortet til et
    NMEA 2000-nettverk og til å forsyne kortet med strøm.

2.  1-Wire-pinneliste. 1-Wire-pinnelisten kan brukes til å koble 1-Wire-sensorer
    til kortet. Den er en 3-pinners pinneliste med 2,54 mm senteravstand.
    Pinnelisten er ikke montert på kortet fra fabrikk, fordi den kan komme i
    veien for plasseringen av panelkontaktene i kabinettet.

3.  I2C-pinneliste. I2C-pinnelisten kan brukes til å koble I2C-sensorer til
    kortet. Den er en 4-pinners pinneliste med 2,54 mm senteravstand.

4.  Micro USB-kontakt. Kontakten brukes til å programmere og feilsøke kortet.

5.  Ubestykkede loddeflater for reset- (EN) og boot-signalene (IO0).

6.  GPIO-pinneliste. GPIO-pinnelisten har 2×10 pinner og 2,54 mm senteravstand.
    Den fører ut de tilgjengelige GPIO-pinnene på ESP32 og kan også brukes som
    JTAG-pinneliste.

7.  Pinneliste for strøm i det isolerte området. Pinnelisten kan brukes til å
    forsyne eksterne enheter fra 3V3 og GND i den isolerte seksjonen.

8.  Jumperpinner for konstantstrømkilden (CCS) til de analoge inngangene.
    Konstantstrømkilden aktiveres ved å sette en jumper over pinnene.

9.  Koblingsklemmer for de analoge inngangene. Klemmene er 2-pinners pluggbare
    koblingsklemmer som er kompatible med Phoenix MC 3,81. De brukes til å koble
    analoge sensorer til kortet.

10. Koblingsklemmer for de digitale inngangene. Klemmene er 2-pinners pluggbare
    koblingsklemmer som er kompatible med Phoenix MC 3,81. De brukes til å koble
    digitale sensorer til kortet.

### Kontakter på undersiden

11.  Loddebro for CAN-terminering. Loddebroen kan loddes sammen for å aktivere
     termineringsmotstanden på 120 Ω for CAN-bussen. Ikke bruk
     termineringsmotstanden i NMEA 2000-nettverk.

12.  Loddebro for lavpassfilter. Loddebroen kan loddes sammen for å aktivere et
     lavpassfilter på den aktuelle analoge inngangen. Filteret har en
     grensefrekvens på 2,3 kHz. Filteret kan for eksempel brukes til å redusere
     støy i et turtellersignal.

13.  Loddebro for pull-down-motstand. Loddebroen kan loddes sammen for å
     aktivere en pull-down-motstand på 100 kΩ på den aktuelle digitale
     inngangen. Pull-down-motstanden kan brukes til å lese av en normalt åpen
     (NO) bryter som trekkes høy når den lukkes.

14.  Loddebro for pull-up-motstand. Loddebroen kan loddes sammen for å aktivere
     en pull-up-motstand på 100 kΩ på den aktuelle digitale inngangen.
     Pull-up-motstanden kan brukes til å lese av en normalt lukket (NC) bryter
     som trekkes lav når den lukkes.

15.  Loddebroer for valg av I2C-adresse for ADS1115. Loddebroene loddes sammen
     for å velge I2C-adressen til AD-omformeren ADS1115. De brukes til å unngå
     adressekonflikter når flere ADS1115-omformere er koblet til samme I2C-buss.
     Loddeflatene kan også brukes til å koble flere I2C-enheter til det isolerte
     området på kortet.

### GPIO-oversikt

HALMET reserverer en del GPIO-pinner til periferienhetene for inngangene. De ledige
GPIO-pinnene er ført ut til GPIO-pinnelisten med 2×10 pinner. Tabellen nedenfor
viser GPIO-pinnene og funksjonene deres.

|    GPIO | Funksjon    | Merknader                                          |
| ------: | :---------- | :------------------------------------------------- |
|       0 | Boot-knapp  | Går til bootloader når den trekkes lav             |
|       1 | TXD0        | Sender data til USB                                |
|       2 | LED         | Rød LED på kortet                                  |
|       3 | RXD0        | Mottar data fra USB                                |
|       4 | 1-Wire DQ   | Datalinje for 1-Wire                               |
|       5 | -           | Ledig på GPIO-pinnelisten                          |
|      12 | - / TDI     | Ledig på GPIO-pinnelisten. Eventuelt: JTAG TDI     |
|      13 | - / TCK     | Ledig på GPIO-pinnelisten. Eventuelt: JTAG TCK     |
|      14 | - / TMS     | Ledig på GPIO-pinnelisten. Eventuelt: JTAG TMS     |
|      15 | - / TDO     | Ledig på GPIO-pinnelisten. Eventuelt: JTAG TDO     |
|      16 | -           | Ledig på GPIO-pinnelisten                          |
|      17 | -           | Ledig på GPIO-pinnelisten                          |
|      18 | CAN RX      | Mottak fra NMEA 2000                               |
|      19 | CAN TX      | Sending til NMEA 2000                              |
|      21 | I2C SDA     | Datalinje for I2C. Brukes til analog inngang       |
|      22 | I2C SCL     | Klokkelinje for I2C. Brukes til analoge innganger  |
|      23 | DI1         | Digital inngang DI1                                |
|      25 | DI2         | Digital inngang DI2                                |
|      27 | DI3         | Digital inngang DI3                                |
|      26 | DI4         | Digital inngang DI4                                |
|      32 | -           | Ledig på GPIO-pinnelisten                          |
|      33 | -           | Ledig på GPIO-pinnelisten                          |
|      34 | -           | Ledig på GPIO-pinnelisten                          |
|      35 | -           | Ledig på GPIO-pinnelisten                          |
| 36 (VP) | Bare inngang | Ledig på GPIO-pinnelisten                        |
| 39 (VN) | Bare inngang | Ledig på GPIO-pinnelisten                        |


## Strømforsyning

Det tillatte inngangsspenningsområdet for kortet er 5–32 V. Typisk strømforbruk
er 90 mA ved 12 V når WiFi-modulen er aktiv (tilsvarer 1,1 W).

## NMEA 2000

NMEA 2000 er en utbredt kommunikasjonsstandard som brukes til å koble sammen sensorer, styreenheter og skjermenheter på båter og skip. Den bygger på Controller Area Network (CAN-bussen), en standard for kjøretøybusser som lar enheter kommunisere med hverandre uten en vertsdatamaskin.

Kortet er i samsvar med NMEA 2000-standarden så lenge ingen av de uisolerte
kontaktene er koblet til andre enheter med felles jordreferanse. En
1-Wire-temperatursensor med lang kabel kan for eksempel brukes, siden den ikke
har felles jord med andre enheter. Å koble en I2C-AD-omformer til den uisolerte
I2C-pinnelisten vil derimot bryte samsvaret med NMEA 2000.

TODO: GPIO-pinnebelegg for NMEA 2000

## Status-LED-er

Det er to knapper og to LED-er på HALMET-kortet. Knappene er merket `Reset` og `Boot`. `Reset`-knappen tilbakestiller kortet ved å trekke Enable-pinnen på ESP32 lav. `Boot`-knappen er koblet til GPIO0 og kan brukes under oppstart av enheten til å tvinge modulen i nedlastingsmodus (download mode). Ellers kan den brukes som en vanlig knappeinngang.

De to LED-ene er ikke merket. Den røde LED-en lyser når det er 3,3 V spenning på kortet. Den blå LED-en er koblet til GPIO2 (pinnen som vanligvis brukes til LED på ESP32-utviklingskort). Den kan styres av brukerprogrammer for å vise tilstanden til enheten.

## 1-Wire

1-Wire er et bussystem for kommunikasjon mellom enheter, utviklet av Dallas Semiconductor, som senere er kjøpt opp av Maxim Integrated Products. Selv om 1-Wire er en langsom protokoll som bare støtter hastigheter opp til 16,3 kbps, er den svært enkel å implementere og kan brukes over lange avstander. Den brukes ofte til temperatursensorer og lignende enkle måleenheter.

HALMETs 1-Wire-implementasjon har ESD- og RF-støyfiltrering samt lavpassfiltrering for å bedre påliteligheten i nettverket.

Merk at datapinnen for 1-Wire (merket «DQ») fysisk er koblet til GPIO4, så bruk GPIO4 for alle 1-Wire-data i programmet ditt.

## I2C

I2C (Inter-Integrated Circuit) er en svært populær synkron seriell kommunikasjonsbuss som ofte brukes til å kommunisere med en rekke ulike integrerte kretser. Den bruker to datalinjer i tillegg til spenning og jord.

HALMET bruker I2C internt til AD-omformeren ADS1115. I2C-bussen er også ført ut til en 4-pinners pinneliste for tilkobling av flere I2C-enheter.

I2C-bussen er koblet til GPIO21 (SDA) og GPIO22 (SCL) på ESP32. Disse pinnene er standardpinnene for I2C i Arduino ESP32-miljøet, men de skiller seg fra standardpinnene på SH-ESP32.
