---
title: Hardware-Beschreibung
translated_from: af5172f8fb6598935bf432cd9590095fe4f40312
---

# Hardware

## ESP32 im Überblick

HALMET basiert auf dem leistungsfähigen Mikrocontroller-Modul ESP32-WROOM-32E. Der ESP32 ist ein Dual-Core-Mikrocontroller mit integriertem WLAN und Bluetooth. Wegen seines niedrigen Preises, seiner guten Peripherieausstattung und seiner einfachen Handhabung ist der ESP32 eine beliebte Wahl für IoT-Anwendungen.

## Funktionsblöcke der Platine

Im Folgenden werden die verschiedenen Funktionsblöcke der Platine beschrieben.

<figure markdown="span">
![](HALMET-func.jpg){ width="60%" }
<figcaption>Funktionsblöcke des HALMET.</figcaption>
</figure>

1.  NMEA 2000 sowie Spannungseingang und Schutzbeschaltung. Der NMEA-2000-Anschluss
    verfügt über folgende Schutzelemente:
    - Selbstrückstellende Sicherung mit 500 mA
    - Verpolungsschutzdiode
    - TVS-Dioden zum Überspannungs- und ESD-Schutz
    - Zweistufige Störfilterung

2.  Stromversorgung. Ein Schaltnetzteil mit einem maximalen Ausgangsstrom von 2 A.

3.  CAN-Transceiver für NMEA 2000. RX- und TX-LEDs zeigen die CAN-Bus-Aktivität
    optisch an.

4.  I2C- und 1-Wire-Schnittstellen zum Anschluss weiterer Sensoren.

5.  Bedienelemente. Ein Reset-Taster, ein Taster für den Boot-Modus, der auch
    allgemein nutzbar ist, eine rote Betriebs-LED und eine blaue
    benutzerprogrammierbare LED.

6.  USB-2.0-Schnittstelle zum Programmieren und Debuggen.

7.  ESP32-WROOM-32E-Modul mit integriertem WLAN und Bluetooth. Das Modul auf der
    HALMET-Platine enthält 16 MB Flash-Speicher.

8.  Schaltung zur galvanischen Trennung der Digital- und Analogeingänge.

9.  Analogeingänge. Die Platine hat vier Analogeingänge mit 16-Bit-Auflösung und
    einer maximalen Eingangsspannung von 33 V. Jeder Eingang verfügt über einen
    Unter- und Überspannungsschutz sowie eine Tiefpassfilterung mit einer
    Grenzfrequenz von 160 Hz, um Störungen bei der Messung zu verringern.

    Die Analogeingänge besitzen eine optionale Konstantstromquelle mit 10 mA für
    die aktive Widerstandsmessung. Die Konstantstromquelle lässt sich über die
    CCS-Jumper-Stiftleisten aktivieren.

    Im Widerstandsmessbetrieb beträgt der maximal messbare Widerstand 320 Ω.

10. Digitaleingänge. HALMET hat vier Digitaleingänge mit einer maximalen
    Eingangsspannung von ±30 V. Die Eingänge verfügen über einen Schmitt-Trigger,
    der die Störfestigkeit verbessert.


## Galvanische Trennung

Die Platine ist zwischen den Digital- und Analogeingängen und dem
ESP32-Mikrocontroller galvanisch getrennt. Die Trennung wird durch
Digitalisolatoren für I2C beziehungsweise die vier Digitaleingänge sowie durch
einen galvanisch getrennten DC/DC-Wandler zur Versorgung des getrennten Bereichs
erreicht.

Dank dieser Trennung kann die Platine ohne die Gefahr von Masseschleifen aus dem
NMEA-2000-Netzwerk versorgt werden. Die Trennung schützt außerdem vor
Spannungsspitzen und Störungen an den Eingängen.

<figure markdown="span">
![](HALMET-isolation.jpg){ width="60%" }
<figcaption>Galvanische Trennstelle des HALMET. Die Eingangsanschlüsse sind vom Rest der Platine
getrennt, das heißt, sie haben keine gemeinsame Masse mit dem übrigen Teil der Platine.</figcaption>
</figure>

## Anschlüsse

<div class="row" markdown>
  <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-top.jpg){ width="100%" }
<figcaption>Anschlüsse des HALMET, Oberseite.</figcaption>
</figure>

   </div>
   <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-bottom.jpg){ width="100%" }
<figcaption>Anschlüsse des HALMET, Unterseite.</figcaption>
</figure>

   </div>
</div>

### Anschlüsse auf der Oberseite

1.  NMEA-2000-Anschluss. Der Anschluss ist ein 4-poliger steckbarer Klemmenblock,
    kompatibel zu Phoenix MC 3.81. Über ihn wird die Platine an ein
    NMEA-2000-Netzwerk angeschlossen und mit Spannung versorgt.

2.  1-Wire-Stiftleiste. An die 1-Wire-Stiftleiste lassen sich 1-Wire-Sensoren
    anschließen. Es handelt sich um eine 3-polige Stiftleiste mit 2,54 mm
    Rastermaß. Sie ist ab Werk nicht bestückt, weil sie die Platzierung der
    Einbausteckverbinder im Gehäuse behindern kann.

3.  I2C-Stiftleiste. An die I2C-Stiftleiste lassen sich I2C-Sensoren anschließen.
    Es handelt sich um eine 4-polige Stiftleiste mit 2,54 mm Rastermaß.

4.  Micro-USB-Anschluss. Der Anschluss dient zum Programmieren und Debuggen der
    Platine.

5.  Unbestückte Lötpads für die Signale Reset (EN) und Boot (IO0).

6.  GPIO-Stiftleiste. Die GPIO-Stiftleiste ist zweireihig mit 2×10 Pins und
    2,54 mm Rastermaß. Sie führt die verfügbaren GPIO-Pins des ESP32 heraus und
    lässt sich auch als JTAG-Stiftleiste nutzen.

7.  Stiftleiste für die Versorgung des getrennten Bereichs. Über sie können
    externe Geräte aus 3V3 und GND des getrennten Bereichs versorgt werden.

8.  Kontakte der Jumper-Stiftleiste für die Konstantstromquelle (CCS) der
    Analogeingänge. Die Konstantstromquelle wird aktiviert, indem die
    Jumper-Kontakte gebrückt werden.

9.  Analogeingangs-Anschlüsse. Die Anschlüsse sind 2-polige steckbare
    Klemmenblöcke, kompatibel zu Phoenix MC 3.81. Über sie werden analoge
    Sensoren an die Platine angeschlossen.

10. Digitaleingangs-Anschlüsse. Die Anschlüsse sind 2-polige steckbare
    Klemmenblöcke, kompatibel zu Phoenix MC 3.81. Über sie werden digitale
    Sensoren an die Platine angeschlossen.

### Anschlüsse auf der Unterseite

11.  Lötbrücke für den CAN-Abschlusswiderstand. Durch Schließen der Lötbrücke wird
     der Abschlusswiderstand von 120 Ω für den CAN-Bus aktiviert. Verwenden Sie
     den Abschlusswiderstand nicht in NMEA-2000-Netzwerken.

12.  Lötbrücke für den Tiefpassfilter. Durch Schließen der Lötbrücke wird der
     Tiefpassfilter am jeweiligen Analogeingang aktiviert. Der Filter hat eine
     Grenzfrequenz von 2,3 kHz. Er lässt sich zum Beispiel nutzen, um Störungen
     im Signal eines Drehzahlmessers zu verringern.

13.  Lötbrücke für den Pull-down-Widerstand. Durch Schließen der Lötbrücke wird am
     jeweiligen Digitaleingang ein Pull-down-Widerstand von 100 kΩ aktiviert. Mit
     dem Pull-down-Widerstand lässt sich ein Schließer (normally open) auslesen,
     der den Eingang im geschlossenen Zustand auf High zieht.

14.  Lötbrücke für den Pull-up-Widerstand. Durch Schließen der Lötbrücke wird am
     jeweiligen Digitaleingang ein Pull-up-Widerstand von 100 kΩ aktiviert. Mit
     dem Pull-up-Widerstand lässt sich ein Öffner (normally closed) auslesen, der
     den Eingang im geschlossenen Zustand auf Low zieht.

15.  Lötbrücken zur Auswahl der I2C-Adresse des ADS1115. Durch Schließen der
     Lötbrücken wird die I2C-Adresse des ADS1115-ADC ausgewählt. Sie dienen dazu,
     Adresskonflikte zu vermeiden, wenn mehrere ADS1115-ADCs am selben I2C-Bus
     angeschlossen sind. Die Lötpads lassen sich außerdem nutzen, um weitere
     I2C-Geräte an den getrennten Bereich der Platine anzuschließen.

### GPIO-Referenz

HALMET belegt einen Teil der GPIO-Pins für die Eingangsperipherie. Die
verfügbaren GPIO-Pins sind auf die zweireihige GPIO-Stiftleiste mit 2×10 Pins
herausgeführt. Die folgende Tabelle listet die GPIO-Pins und ihre Funktionen auf.

|    GPIO | Funktion    | Anmerkungen                                            |
| ------: | :---------- | :----------------------------------------------------- |
|       0 | Boot-Taster | Wechselt in den Bootloader, wenn auf Low gezogen        |
|       1 | TXD0        | Datenübertragung zum USB                               |
|       2 | LED         | Rote LED auf der Platine                               |
|       3 | RXD0        | Datenempfang vom USB                                   |
|       4 | 1-Wire DQ   | 1-Wire-Datenleitung                                    |
|       5 | -           | Auf der GPIO-Stiftleiste verfügbar                     |
|      12 | - / TDI     | Auf der GPIO-Stiftleiste verfügbar. Optional: JTAG TDI |
|      13 | - / TCK     | Auf der GPIO-Stiftleiste verfügbar. Optional: JTAG TCK |
|      14 | - / TMS     | Auf der GPIO-Stiftleiste verfügbar. Optional: JTAG TMS |
|      15 | - / TDO     | Auf der GPIO-Stiftleiste verfügbar. Optional: JTAG TDO |
|      16 | -           | Auf der GPIO-Stiftleiste verfügbar                     |
|      17 | -           | Auf der GPIO-Stiftleiste verfügbar                     |
|      18 | CAN RX      | Empfang von NMEA 2000                                  |
|      19 | CAN TX      | Senden an NMEA 2000                                    |
|      21 | I2C SDA     | I2C-Datenleitung. Für die Analogeingänge genutzt       |
|      22 | I2C SCL     | I2C-Taktleitung. Für die Analogeingänge genutzt        |
|      23 | DI1         | Digitaleingang 1                                       |
|      25 | DI2         | Digitaleingang 2                                       |
|      27 | DI3         | Digitaleingang 3                                       |
|      26 | DI4         | Digitaleingang 4                                       |
|      32 | -           | Auf der GPIO-Stiftleiste verfügbar                     |
|      33 | -           | Auf der GPIO-Stiftleiste verfügbar                     |
|      34 | -           | Auf der GPIO-Stiftleiste verfügbar                     |
|      35 | -           | Auf der GPIO-Stiftleiste verfügbar                     |
| 36 (VP) | Nur Eingang | Auf der GPIO-Stiftleiste verfügbar                     |
| 39 (VN) | Nur Eingang | Auf der GPIO-Stiftleiste verfügbar                     |


## Stromversorgung

Der zulässige Eingangsspannungsbereich der Platine beträgt 5–32 V. Die typische
Stromaufnahme liegt bei 90 mA bei 12 V mit aktivem WLAN-Modul (entspricht 1,1 W).

## NMEA 2000

NMEA 2000 ist ein weit verbreiteter Kommunikationsstandard, mit dem Sensoren, Bedien- und Anzeigegeräte auf Booten und Schiffen verbunden werden. Er basiert auf dem Controller Area Network (CAN-Bus), einem Fahrzeugbus-Standard, der Geräten die Kommunikation untereinander ohne Hostrechner ermöglicht.

Die Platine erfüllt den NMEA-2000-Standard, solange keiner der nicht getrennten
Anschlüsse mit anderen massebezogenen Geräten verbunden ist. Ein
1-Wire-Temperatursensor mit langem Kabel lässt sich zum Beispiel verwenden, weil
er keine gemeinsame Masse mit anderen Geräten hat. Der Anschluss eines
I2C-Analog-Digital-Wandlers an den nicht getrennten I2C-Anschluss würde die
NMEA-2000-Konformität dagegen aufheben.

TODO: NMEA-2000-GPIO-Pinbelegung

## Status-LEDs

Auf der HALMET-Platine befinden sich zwei Taster und zwei LEDs. Die beiden Taster sind mit Reset und Boot beschriftet. Der Reset-Taster startet die Platine neu, indem er den Enable-Pin des ESP32 auf Low zieht. Der Boot-Taster ist mit GPIO0 verbunden und lässt sich während des Gerätestarts nutzen, um das Modul in den Download-Modus zu zwingen. Ansonsten kann er als normaler Tastereingang verwendet werden.

Die beiden LEDs sind nicht ausdrücklich beschriftet. Die rote LED leuchtet, sobald auf der Platine 3,3 V Versorgungsspannung anliegen. Die blaue LED ist mit GPIO2 verbunden (dem Pin, der auf ESP32-Entwicklungsboards üblicherweise für eine LED genutzt wird). Sie kann von Benutzerprogrammen angesteuert werden, um den Zustand des Geräts anzuzeigen.

## 1-Wire

1-Wire ist ein Bussystem für die Gerätekommunikation, das von Dallas Semiconductor entwickelt wurde; das Unternehmen wurde inzwischen von Maxim Integrated Products übernommen. Obwohl 1-Wire ein langsames Protokoll ist und nur Geschwindigkeiten bis 16,3 kbit/s unterstützt, lässt es sich sehr einfach umsetzen und funktioniert auch über große Entfernungen. Es wird häufig für Temperatursensoren und ähnliche einfache Sensorbausteine verwendet.

Die 1-Wire-Umsetzung des HALMET verfügt über eine ESD- und HF-Störungsfilterung sowie über eine Tiefpassfilterung, um die Zuverlässigkeit des Netzwerks zu erhöhen.

Beachten Sie, dass der 1-Wire-Datenpin (Beschriftung „DQ“) physisch auf GPIO4 gelegt ist; verwenden Sie in Ihrem Programm daher GPIO4 für alle 1-Wire-Daten.

## I2C

I2C (Inter-Integrated Circuit) ist ein sehr verbreiteter synchroner serieller Kommunikationsbus, der häufig zur Anbindung unterschiedlichster ICs verwendet wird. Er nutzt zusätzlich zu Versorgungsspannung und Masse zwei Datenleitungen.

HALMET nutzt I2C intern für den Analog-Digital-Wandler ADS1115. Der I2C-Bus ist außerdem auf eine 4-polige Stiftleiste herausgeführt, um weitere I2C-Geräte anschließen zu können.

Der I2C-Bus ist mit GPIO21 (SDA) und GPIO22 (SCL) des ESP32 verbunden. Diese Pins sind die Standard-I2C-Pins in der Arduino-ESP32-Umgebung, unterscheiden sich aber von den Standard-Pins des SH-ESP32.
