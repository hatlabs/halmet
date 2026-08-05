---
title: Hårdvarubeskrivning
translated_from: af5172f8fb6598935bf432cd9590095fe4f40312
---

# Hårdvara

## Introduktion till ESP32

HALMET bygger på den kraftfulla mikrokontrollermodulen ESP32-WROOM-32E. ESP32 är en tvåkärnig mikrokontroller med inbyggd WiFi- och Bluetooth-anslutning. ESP32 är ett populärt val för IoT-tillämpningar tack vare sitt låga pris, sin goda uppsättning kringkretsar och att den är enkel att använda.

## Kortets funktionsblock

Kortets olika funktionsblock beskrivs nedan.

<figure markdown="span">
![](HALMET-func.jpg){ width="60%" }
<figcaption>HALMET-kortets funktionsblock.</figcaption>
</figure>

1.  NMEA 2000-anslutning samt strömförsörjning och skydd. NMEA 2000-kontakten
    har följande skyddskomponenter:
    - Självåterställande säkring på 500 mA
    - Diod för polvändningsskydd
    - TVS-dioder för överspännings- och ESD-skydd
    - Störningsfiltrering i två steg

2.  Strömförsörjning. Ett switchat nätaggregat med en maximal utström på 2 A.

3.  CAN-transceiver för NMEA 2000. RX- och TX-LED:er ger en visuell indikering
    av trafiken på CAN-bussen.

4.  I2C- och 1-Wire-gränssnitt för anslutning av ytterligare givare.

5.  Användargränssnitt. En reset-knapp, en boot-knapp som även fungerar som
    allmän knapp, en röd LED för spänningsindikering och en blå användarstyrd LED.

6.  USB 2.0-gränssnitt för programmering och felsökning.

7.  ESP32-WROOM-32E-modul med inbyggd WiFi och Bluetooth. Modulen på
    HALMET-kortet har 16 MB flashminne.

8.  Kretsar för galvanisk isolation av de digitala och analoga ingångarna.

9.  Analoga ingångar. Kortet har fyra analoga ingångar med 16 bitars upplösning
    och en maximal inspänning på 33 V. Varje ingång har skydd mot under- och
    överspänning samt lågpassfiltrering med gränsfrekvensen 160 Hz för att
    minska mätbruset.

    De analoga ingångarna har en valfri konstantströmkälla på 10 mA för aktiv
    resistansmätning. Konstantströmkällan aktiveras med CCS-bygelstiften.

    I resistansmätningsläge är den högsta resistans som kan mätas 320 Ω.

10. Digitala ingångar. HALMET har fyra digitala ingångar med en maximal
    inspänning på ±30 V. Ingångarna har en Schmitt trigger som förbättrar
    störningståligheten.


## Galvanisk isolation

Kortet har galvanisk isolation mellan de digitala och analoga ingångarna och
ESP32-mikrokontrollern. Isolationen åstadkoms med digitala isolatorer för I2C
respektive de fyra digitala ingångarna, samt med en isolerad DC/DC-omvandlare
som matar den isolerade sektionen.

Tack vare isolationen kan kortet strömförsörjas från NMEA 2000-nätverket utan
risk för jordslingor. Isolationen skyddar också mot spänningsspikar och
störningar på ingångarna.

<figure markdown="span">
![](HALMET-isolation.jpg){ width="60%" }
<figcaption>HALMET-kortets isolationsbarriär. Ingångsplintarna är isolerade från resten av
kortet, vilket innebär att de inte delar jord med kortets övriga delar.</figcaption>
</figure>

## Kontakter

<div class="row" markdown>
  <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-top.jpg){ width="100%" }
<figcaption>HALMET-kortets kontakter, ovansidan.</figcaption>
</figure>

   </div>
   <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-bottom.jpg){ width="100%" }
<figcaption>HALMET-kortets kontakter, undersidan.</figcaption>
</figure>

   </div>
</div>

### Kontakter på ovansidan

1.  NMEA 2000-kontakt. Kontakten är en 4-polig löstagbar kopplingsplint av
    Phoenix MC 3.81-kompatibel typ. Den används för att ansluta kortet till ett
    NMEA 2000-nätverk och för att strömförsörja kortet.

2.  1-Wire-stiftlist. Med 1-Wire-stiftlisten kan du ansluta 1-Wire-givare till
    kortet. Stiftlisten är 3-polig med 2,54 mm stiftavstånd. Den är inte
    monterad på kortet som standard, eftersom den kan vara i vägen för
    placeringen av panelkontakter i kapslingen.

3.  I2C-stiftlist. Med I2C-stiftlisten kan du ansluta I2C-givare till kortet.
    Stiftlisten är 4-polig med 2,54 mm stiftavstånd.

4.  Micro USB-kontakt. Kontakten används för att programmera och felsöka kortet.

5.  Obestyckade lödytor för signalerna reset (EN) och boot (IO0).

6.  GPIO-stiftlist. GPIO-stiftlisten har 2×10 stift med 2,54 mm stiftavstånd.
    Den för ut ESP32:s lediga GPIO-stift och kan även användas som JTAG-stiftlist.

7.  Stiftlist för det isolerade områdets strömförsörjning. Från stiftlisten kan
    externa enheter matas från den isolerade sektionens 3V3 och GND.

8.  Bygelstift för de analoga ingångarnas konstantströmkälla (CCS).
    Konstantströmkällan aktiveras genom att kortsluta bygelstiften med en bygel.

9.  Plintar för de analoga ingångarna. Plintarna är 2-poliga löstagbara
    kopplingsplintar av Phoenix MC 3.81-kompatibel typ. De används för att
    ansluta analoga givare till kortet.

10. Plintar för de digitala ingångarna. Plintarna är 2-poliga löstagbara
    kopplingsplintar av Phoenix MC 3.81-kompatibel typ. De används för att
    ansluta digitala givare till kortet.

### Kontakter på undersidan

11.  Lödbygel för CAN-terminering. Genom att löda ihop lödbygeln aktiveras
     CAN-bussens termineringsmotstånd på 120 Ω. Använd inte termineringsmotståndet
     i NMEA 2000-nätverk.

12.  Lödbygel för lågpassfilter. Genom att löda ihop lödbygeln aktiveras ett
     lågpassfilter på motsvarande analoga ingång. Filtrets gränsfrekvens är
     2,3 kHz. Filtret kan till exempel användas för att minska bruset i en
     varvräknarsignal.

13.  Lödbygel för pull-down-motstånd. Genom att löda ihop lödbygeln aktiveras ett
     pull-down-motstånd på 100 kΩ på motsvarande digitala ingång.
     Pull-down-motståndet kan användas för att läsa av en slutande kontakt (NO)
     som dras hög när den sluts.

14.  Lödbygel för pull-up-motstånd. Genom att löda ihop lödbygeln aktiveras ett
     pull-up-motstånd på 100 kΩ på motsvarande digitala ingång.
     Pull-up-motståndet kan användas för att läsa av en brytande kontakt (NC)
     som dras låg när den sluts.

15.  Lödbyglar för val av I2C-adress för ADS1115. Genom att löda ihop byglarna
     väljer du I2C-adressen för AD-omvandlaren ADS1115. Byglarna används för att
     undvika adresskonflikter när flera ADS1115-omvandlare är anslutna till
     samma I2C-buss. Lödytorna kan också användas för att ansluta ytterligare
     I2C-enheter till kortets isolerade område.

### GPIO-referens

HALMET reserverar ett antal GPIO-stift för ingångarnas kringkretsar. Lediga
GPIO-stift förs ut till GPIO-stiftlisten med 2×10 stift. Tabellen nedan listar
GPIO-stiften och deras funktioner.

|    GPIO | Funktion    | Anmärkningar                                       |
| ------: | :---------- | :------------------------------------------------- |
|       0 | Boot-knapp  | Går till bootloader när stiftet dras lågt          |
|       1 | TXD0        | Sänder data till USB                               |
|       2 | LED         | Röd LED på kortet                                  |
|       3 | RXD0        | Tar emot data från USB                             |
|       4 | 1-Wire DQ   | 1-Wire-datalinje                                   |
|       5 | -           | Ledigt på GPIO-stiftlisten                         |
|      12 | - / TDI     | Ledigt på GPIO-stiftlisten. Alternativt: JTAG TDI  |
|      13 | - / TCK     | Ledigt på GPIO-stiftlisten. Alternativt: JTAG TCK  |
|      14 | - / TMS     | Ledigt på GPIO-stiftlisten. Alternativt: JTAG TMS  |
|      15 | - / TDO     | Ledigt på GPIO-stiftlisten. Alternativt: JTAG TDO  |
|      16 | -           | Ledigt på GPIO-stiftlisten                         |
|      17 | -           | Ledigt på GPIO-stiftlisten                         |
|      18 | CAN RX      | Tar emot från NMEA 2000                            |
|      19 | CAN TX      | Sänder till NMEA 2000                              |
|      21 | I2C SDA     | I2C-datalinje. Används för analog ingång           |
|      22 | I2C SCL     | I2C-klocklinje. Används för analoga ingångar       |
|      23 | DI1         | Digital ingång 1                                   |
|      25 | DI2         | Digital ingång 2                                   |
|      27 | DI3         | Digital ingång 3                                   |
|      26 | DI4         | Digital ingång 4                                   |
|      32 | -           | Ledigt på GPIO-stiftlisten                         |
|      33 | -           | Ledigt på GPIO-stiftlisten                         |
|      34 | -           | Ledigt på GPIO-stiftlisten                         |
|      35 | -           | Ledigt på GPIO-stiftlisten                         |
| 36 (VP) | Endast ingång | Ledigt på GPIO-stiftlisten                       |
| 39 (VN) | Endast ingång | Ledigt på GPIO-stiftlisten                       |


## Strömförsörjning

Kortets tillåtna inspänningsområde är 5–32 V. Typisk strömförbrukning är 90 mA
vid 12 V med WiFi-modulen aktiv (motsvarar 1,1 W).

## NMEA 2000

NMEA 2000 är en allmänt spridd kommunikationsstandard för att koppla samman givare, styrenheter och displayer på båtar och fartyg. Den bygger på Controller Area Network (CAN-bussen), en fordonsbusstandard som gör det möjligt för enheter att kommunicera med varandra utan en värddator.

Kortet uppfyller NMEA 2000-standarden så länge ingen av de oisolerade kontakterna
är ansluten till andra enheter med jordreferens. Till exempel kan en
1-Wire-temperaturgivare med lång kabel användas, eftersom den inte delar jord med
andra enheter. Att däremot ansluta en I2C-AD-omvandlare till den oisolerade
I2C-kontakten skulle bryta överensstämmelsen med NMEA 2000.

TODO: NMEA 2000 GPIO-stiftkonfiguration

## Status-LED:er

På HALMET-kortet finns två knappar och två LED:er. Knapparna är märkta Reset och Boot. Reset-knappen startar om kortet genom att dra ESP32:s Enable-stift lågt. Boot-knappen är ansluten till GPIO0 och kan under enhetens uppstart användas för att tvinga modulen till nedladdningsläge (download mode). I övrigt kan den användas som en vanlig knappingång.

LED:erna är inte särskilt märkta. Den röda LED:en lyser så snart det finns 3,3 V spänning på kortet. Den blå LED:en är ansluten till GPIO2 (det stift som vanligen används för LED på ESP32-utvecklingskort). Den kan styras av användarens program för att visa enhetens tillstånd.

## 1-Wire

1-Wire är ett bussystem för kommunikation mellan enheter, utvecklat av Dallas Semiconductor som sedermera köpts upp av Maxim Integrated Products. Även om 1-Wire är ett långsamt protokoll och bara stöder hastigheter upp till 16,3 kbit/s är det mycket enkelt att implementera och fungerar över långa avstånd. Det används ofta för temperaturgivare och liknande enkla mätdon.

HALMET-kortets 1-Wire-implementering har ESD- och RF-störningsfiltrering samt lågpassfiltrering för att förbättra nätverkets tillförlitlighet.

Observera att 1-Wire-datastiftet (märkt ”DQ”) fysiskt är kopplat till GPIO4, så använd GPIO4 för all 1-Wire-data i ditt program.

## I2C

I2C (Inter-Integrated Circuit) är en mycket populär synkron seriell kommunikationsbuss som ofta används för att kommunicera med många olika kretsar. Den använder två dataledare utöver spänning och jord.

HALMET använder I2C internt för AD-omvandlaren ADS1115. I2C-bussen förs också ut till en 4-polig stiftlist för anslutning av ytterligare I2C-enheter.

I2C-bussen är ansluten till GPIO21 (SDA) och GPIO22 (SCL) på ESP32. Dessa stift är standardstiften för I2C i Arduinos ESP32-miljö, men skiljer sig från standardstiften på SH-ESP32.
