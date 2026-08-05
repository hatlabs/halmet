---
title: Verwendung
translated_from: 0d5855d63a22b19308b3b70c9481dfc441864197
---

# Verwendung

## Häufige Anwendungsfälle

Dieser Abschnitt enthält praktische Hinweise zum Auslesen verschiedener Sensortypen und zum Anschluss von HALMET an andere Geräte.

### Software-Einrichtung

HALMET ist ein Entwicklungsboard und wird ohne vorinstallierte Software ausgeliefert.
Passende Software müssen Sie selbst installieren. Das ist nicht schwierig, etwas Vorerfahrung mit Mikrocontroller-Boards wie Arduino oder ESP32 Devkits ist aber empfehlenswert.

Die HALMET-Dokumentation geht von der [HALMET-Beispiel-Firmware](https://github.com/hatlabs/HALMET-example-firmware) aus. Diese Firmware basiert auf dem Framework [SensESP](https://signalk.org/SensESP/) und bietet einen recht unkomplizierten Zugriff auf die Funktionen der Platine.

Der [SensESP-Einstiegsleitfaden](https://signalk.org/SensESP/pages/getting_started/) enthält ausführliche Anweisungen zur Einrichtung der Entwicklungsumgebung, die zum Kompilieren und Installieren der Firmware nötig ist. Die Anleitung ist für allgemeine ESP32-Geräte geschrieben, gilt aber ebenso für HALMET. Verwenden Sie lediglich die [HALMET-Beispiel-Firmware](https://github.com/hatlabs/HALMET-example-firmware) anstelle der SensESP-Projektvorlage.

Beachten Sie, dass die SensESP-Dokumentation zwar von der Verwendung von Signal K ausgeht, HALMET aber ebenso als eigenständiges NMEA-2000-Gerät nutzbar ist.

Wenn Sie SensESP nicht verwenden möchten, können Sie auch eine eigene Firmware mit der Arduino IDE oder ESP-IDF erstellen. Für viele Anwendungsfälle ist auch ESPHome eine sehr gute Wahl.

**HINWEIS:** Die Belegung der GPIO-Pins auf HALMET weicht leicht von der Belegung des ESP32 Devkit und des SH-ESP32 ab. Wenn Sie andere Software als die HALMET-Beispiel-Firmware anpassen, müssen Sie die Pin-Belegung genau prüfen. Weitere Informationen finden Sie in der [GPIO-Referenz](../hardware/index.md#gpio-referenz).

### Digitaleingänge verwenden

HALMET besitzt vier Digitaleingänge. Diese Eingänge lassen sich zum Lesen digitaler Alarmsignale oder als Zähler verwenden. Dieser Abschnitt beschreibt die Verwendung der Eingänge in verschiedenen häufigen Anwendungsfällen. Die Anleitung geht von der HALMET-Beispiel-Firmware aus.

Die Digitaleingänge D1–D4 sind mit den GPIO-Pins 23, 25, 27 und 26 verbunden. Die Eingänge vertragen Spannungen zwischen −32 V und +32 V. Die Schwellenspannung für die Erkennung eines High-Signals liegt bei etwa 1,55 V, die Hysterese bei etwa 0,7 V.

### Anschluss an digitale Alarme

Dieser Abschnitt beschreibt, wie HALMET an verschiedene Ein/Aus-Signale wie Motor- oder Bilgenalarme angeschlossen wird.

#### Hardware-Einrichtung

In der Regel lassen sich Ein/Aus-Signale wie Motor- oder Bilgenalarme direkt an die Digitaleingänge von HALMET anschließen. Je nach Signaltyp kann ein Pull-up oder Pull-down erforderlich sein.

In der Abbildung unten enthält der Stromkreis in Beispiel (a) bereits eine Glühlampe. Bei geöffnetem Schalter zieht die Glühlampe die Spannung an D1 nach unten. Ein zusätzlicher Pull-down ist nicht erforderlich.[^1] In Beispiel (b) befindet sich dagegen keine weitere Last im Stromkreis. Ist der Schalter geöffnet, liegt D2 auf undefiniertem Potenzial und der Eingang wird zufällig als High oder Low gelesen. In diesem Fall muss der interne Pull-down-Widerstand aktiviert werden, indem die Lötbrücke auf der Unterseite der Platine geschlossen wird.

<figure markdown="span">
![](digin_pullup_pulldown.svg){ width="60%" }
<figcaption>Digitaleingänge in verschiedenen Anwendungsfällen. (a) Bereits vorhandene Lampe im Stromkreis. (b) Keine weitere Last im Stromkreis, der Schalter zieht das Signal beim Schließen nach High. (c) Der Schalter zieht das Signal beim Schließen nach Low.</figcaption>
</figure>

[^1]: Sind die Paneelleuchten mit LEDs ausgeführt, reicht der Spannungsabfall über den LEDs möglicherweise nicht aus, um die Spannung weit genug nach unten zu ziehen. In diesem Fall muss der Pull-down-Widerstand aktiviert werden.

<figure markdown="span">
![](solder_jumpers.jpg){ width="60%" }
<figcaption>Die Lötbrücken auf der Unterseite der Platine lassen sich schließen, um die eingebauten Pull-up- oder Pull-down-Widerstände zu aktivieren.</figcaption>
</figure>

Ebenso kann der interne Pull-up erforderlich sein, wenn der Schalter das Signal beim Schließen nach Low zieht wie in Beispiel (c).

Handelt es sich bei den Alarmschaltern schließlich um Öffner (normally closed), kehrt sich die Betrachtung um. Beim Öffnen des Schalters wird die Eingangsspannung je nach Stromkreis nach oben oder nach unten gezogen. Auch in diesem Fall kann der interne Pull-up oder Pull-down erforderlich sein.

#### Software-Einrichtung

Die HALMET-Beispiel-Firmware stellt die Hilfsmethode `ConnectAlarmSender()` zum Konfigurieren und Anschließen der Digitaleingänge bereit. Siehe `main.cpp` ab Zeile 177. Sowohl aktiv-High- als auch aktiv-Low-Signale werden unterstützt.

### Digitaleingänge als Zähler

Die Digitaleingänge von HALMET lassen sich auch als Zähler verwenden. Das ist zum Beispiel nützlich, um Motorumdrehungen oder Impulse eines Kettenzählers zu zählen.

#### Hardware-Einrichtung

Solche Geber werden meist in beide Richtungen aktiv getrieben, sodass weder Pull-up noch Pull-down nötig ist. Wenn Sie HALMET an einen niederohmigen Ausgang wie die W-Klemme der Lichtmaschine anschließen, empfiehlt es sich, eine Leitungssicherung einzufügen, die die Leitung vor Kurzschlüssen durch Scheuern oder andere Beschädigungen schützt. Ansonsten können Sie den Geber direkt an den Digitaleingang anschließen.

Ist die Impulsquelle stark gestört und liefert dadurch fehlerhafte Drehzahlwerte, lässt sich ein Tiefpassfilter aktivieren, indem die LP-Lötbrücke auf der Unterseite der Platine geschlossen wird. Der Tiefpassfilter hat eine Grenzfrequenz von etwa 2,3 kHz, was für Anwendungen wie den Anschluss an die W-Klemme der Lichtmaschine geeignet sein sollte.

#### Software-Einrichtung

Die HALMET-Beispiel-Firmware enthält einen Impulszähler, der sich auf einzelnen oder allen Digitaleingängen aktivieren lässt. Die Beispielkonfiguration finden Sie in `main.cpp` ab Zeile 214.

### Analogeingänge verwenden

HALMET besitzt vier Analogeingänge, die sich entweder für passive Spannungsmessungen oder für aktive Widerstandsmessungen nutzen lassen. Dieser Abschnitt beschreibt die Verwendung der Eingänge in verschiedenen häufigen Anwendungsfällen.

#### Hardware-Einrichtung

Die Analogeingänge A1–A4 sind mit einem ADS1115-Analog-Digital-Wandler verbunden. Der ADS1115 hat eine 16-Bit-Auflösung und eine maximale Abtastrate von 860 Messwerten pro Sekunde. Die Analogeingänge von HALMET enthalten allerdings einen kräftigen Tiefpassfilter mit einer Grenzfrequenz von etwa 160 Hz. Das reicht für die Messung physikalischer Sensorsignale wie Tankfüllstands- oder Motordrucksensoren immer noch mehr als aus.

In der Abbildung unten zeigt Beispiel (a) ein vorhandenes Motorinstrument, das an einen Widerstandsgeber angeschlossen ist. Motorinstrumente sind meist entweder thermostatisch oder magnetisch aufgebaut. In beiden Fällen bilden Anzeigeinstrument und Geber einen Spannungsteiler, und die Spannung über dem Geber ist proportional zur gemessenen Größe. Diese Spannung lässt sich mit den Analogeingängen von HALMET messen, ohne die Funktion des ursprünglichen Anzeigeinstruments zu beeinträchtigen. Wegen des Spannungsteilers korreliert die Spannung möglicherweise nicht linear mit der gemessenen Größe; das lässt sich jedoch in der Software kompensieren.

<figure markdown="span">
![](analog_input.svg){ width="60%" }
<figcaption>Anschluss der Analogeingänge mit und ohne vorhandenes Anzeigeinstrument. (a) Bei einem vorhandenen Anzeigeinstrument verwenden Sie HALMET in der passiven Spannungsmessung. (b) Ist kein weiteres Gerät vorhanden, verwenden Sie HALMET in der aktiven Widerstandsmessung.</figcaption>
</figure>


Beispiel (b) zeigt den Fall ohne vorhandenes Anzeigeinstrument. Der Geber ist direkt an den Analogeingang von HALMET angeschlossen. In diesem Fall muss HALMET die Speisespannung für den Geber bereitstellen. HALMET führt die Widerstandsmessung mit einer Konstantstromquelle von 10 mA durch. Der Strom von 10 mA erzeugt über einem Widerstand von 100 Ω eine Spannungsdifferenz von 1 V, woraus sich ein maximal messbarer Widerstand von etwa 300 Ω ergibt. Die Konstantstromquelle wird aktiviert, indem ein Jumper auf das Stiftpaar der CCS-Stiftleiste (constant current source) gesteckt wird. Siehe die Abbildung unten.

<figure markdown="span">
![](ccs_jumpers.jpg){ width="60%" }
<figcaption>Die Abbildung zeigt die für die Analogeingänge A2 und A4 aktivierte Konstantstromquelle.</figcaption>
</figure>
