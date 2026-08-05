---
title: Erste Schritte
translated_from: 75bcdba18bc044c04ce3e220067bf537e069ec82
---

# Erste Schritte

## Hardware-Montage

Damit sich die Anschlüsse in kleinen Gehäusen flexibler platzieren lassen, werden HALMET-Platinen ohne montierte 1-Wire- und GPIO-Stiftleisten ausgeliefert. Wenn Sie eine dieser Schnittstellen nutzen möchten, müssen Sie die Stiftleiste selbst auf die Platine löten.

Eine Anleitung zum Auflöten von Stiftleisten finden Sie in der [Montageanleitung](https://docs.hatlabs.fi/sh-esp32/pages/getting-started/#revision-1-boards) des SH-ESP32.

## Stromversorgung der Platine

HALMET wird über den NMEA-2000-Anschluss mit Spannung versorgt. Wenn Sie HALMET an ein NMEA-2000-Netzwerk anschließen, können Sie die Platine direkt aus dem Netzwerk versorgen. Schließen Sie in diesem Fall die NMEA-2000-Adern wie in der folgenden Abbildung gezeigt an den 4-poligen steckbaren Klemmenblock an.

<figure markdown="span">
![](halmet_n2k_input.jpg){ width="50%" }
<figcaption>Schließen Sie die NMEA-2000-Adern wie gezeigt an den Klemmenblock an.</figcaption>
</figure>

Wenn Sie HALMET nicht an ein NMEA-2000-Netzwerk anschließen, verwenden Sie denselben Klemmenblock, belegen aber nur die Positionen `-` und `+`. Als Spannungsquelle eignet sich jede Quelle von 5–32 V. Die typische Stromaufnahme der Platine beträgt bei aktivem WLAN 0,07 A bei 12 V.

<figure markdown="span">
![](power_connector.jpg){ width="50%" }
<figcaption>Schließen Sie die Versorgungsadern wie gezeigt an den Klemmenblock an.</figcaption>
</figure>

## Gehäuse

Für den Einsatz an Bord sollte HALMET immer in ein wasserdichtes Gehäuse eingebaut werden.
Die Platine ist passend für das [SH-ESP32-Gehäuse](https://shop.hatlabs.fi/products/sh-esp32-enclosure) ausgelegt. Unten sehen Sie ein Beispiel für eine im Gehäuse montierte HALMET-Platine.

<figure markdown="span">
![](halmet_small_enclosure.jpg){ width="50%" }
<figcaption>HALMET im SH-ESP32-Gehäuse montiert.</figcaption>
</figure>

Das SH-ESP32-Gehäuse bietet nur begrenzt Platz für Anschlüsse.
Jede der Längsseiten nimmt praktisch nur 2–3 Einbausteckverbinder auf.
Wenn Sie mehr als einige wenige Eingänge anschließen möchten, empfiehlt sich ein größeres Gehäuse.
Das unten gezeigte [kompakte SH-RPi-Gehäuse](https://shop.hatlabs.fi/products/compact-weatherproof-enclosure-for-raspberry-pi-and-sh-rpi-158x90x60-mm) von Hat Labs bietet zum Beispiel bereits reichlich Raum für Anschlüsse.

<figure markdown="span">
![](medium_enclosure.jpg){ width="50%" }
<figcaption>Das kompakte SH-RPi-Gehäuse bietet mehr Platz für die Anordnung der Einbausteckverbinder.</figcaption>
</figure>


Weitere geeignete wasserdichte Gehäuse finden sich problemlos auf jedem Online-Marktplatz. Auch größere Abzweigdosen für den Außenbereich eignen sich für diesen Zweck.

### Bohrungen für Einbausteckverbinder

Die Gehäuse sind in der Regel nicht vorgebohrt. Verwenden Sie zum Bohren immer einen Kegel- oder Stufenbohrer (den, der wie ein kleiner Weihnachtsbaum aus Metall aussieht). Normale Metallbohrer greifen leicht zu stark und können die Gehäusewand aufreißen.

Lassen Sie bei der Planung der Bohrungen und Anschlusspositionen genügend Platz zum Festziehen der Überwurfmuttern und für den Körper des Steckverbinders. Wenn Sie das Gehäuse zur Wandmontage vorsehen, sollten die Anschlüsse nach unten zeigen, damit möglichst wenig Wasser eindringen kann.

Geeignete Bohrungsdurchmesser für die verschiedenen Anschlüsse:

- PG7-Kabelverschraubung und M12-Einbausteckverbinder (NMEA 2000): 12,5 mm oder 1/2 Zoll
- SP13-Einbausteckverbinder (blau-schwarze Kunststoffsteckverbinder): 13 mm
- PG9-Kabelverschraubung: 16 mm oder 5/8 Zoll

Kabeltüllen aus Gummi oder Silikon erlauben deutlich höhere Kabeldichten als Einbausteckverbinder oder Kabelverschraubungen. Sie sind allerdings nicht so wasserdicht wie Einbausteckverbinder oder Kabelverschraubungen. Zudem erfordern sie eine dauerhafte Kabelbefestigung, was die Wartung des Systems erschweren kann.

TODO: Bild einer Kabeltülle ergänzen.

### Löten der Einbausteckverbinder

Verwenden Sie beim Anlöten der internen Adern an die Einbausteckverbinder immer Schrumpfschlauch auf den einzelnen Adern.
Denken Sie daran, den Schrumpfschlauch _vor_ dem Löten auf die Ader zu schieben …
Meist können Sie zuerst Lot in den Lötbecher des Kontakts geben und dann das Lot erneut aufschmelzen und die Ader einführen.
