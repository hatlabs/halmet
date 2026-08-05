---
title: Kom godt i gang
translated_from: 75bcdba18bc044c04ce3e220067bf537e069ec82
---

# Kom godt i gang

## Samling af hardwaren

For at stikkene kan placeres mere frit i små kabinetter, leveres HALMET-kortene uden 1-Wire- og GPIO-stiklisterne monteret. Hvis du regner med at bruge en af disse grænseflader, skal du selv lodde stiklisten fast på kortet.

Har du brug for en vejledning i at lodde stikben fast på kortet, kan du se SH-ESP32'ens [vejledning til samling af hardwaren](https://docs.hatlabs.fi/sh-esp32/pages/getting-started/#revision-1-boards).

## Strømforsyning af kortet

HALMET forsynes gennem NMEA 2000-stikket. Hvis du skal slutte HALMET til et NMEA 2000-netværk, kan du forsyne kortet direkte fra netværket. Tilslut i så fald NMEA 2000-ledningerne til den 4-benede aftagelige klemrække som vist på figuren nedenfor.

<figure markdown="span">
![](halmet_n2k_input.jpg){ width="50%" }
<figcaption>Tilslut NMEA 2000-ledningerne til stikket som vist.</figcaption>
</figure>

Hvis du ikke skal slutte HALMET til et NMEA 2000-netværk, skal du bruge det samme stik, men kun tilslutte ledninger til `-` og `+`. Enhver strømforsyning på 5–32 V kan bruges. Kortets typiske strømforbrug med WiFi aktiveret er 0,07 A ved 12 V.

<figure markdown="span">
![](power_connector.jpg){ width="50%" }
<figcaption>Tilslut forsyningsledningerne til stikket som vist.</figcaption>
</figure>

## Kabinetter

Om bord på en båd bør HALMET altid placeres i et vandtæt kabinet.
Kortet er konstrueret, så det passer i [SH-ESP32-kabinettet](https://shop.hatlabs.fi/products/sh-esp32-enclosure). Nedenfor ses et eksempel på et HALMET-kort monteret i kabinettet.

<figure markdown="span">
![](halmet_small_enclosure.jpg){ width="50%" }
<figcaption>HALMET monteret i SH-ESP32-kabinettet.</figcaption>
</figure>

SH-ESP32-kabinettet har begrænset plads til stik.
Hver af langsiderne kan i praksis kun rumme 2–3 panelstik.
Hvis du regner med at tilslutte mere end nogle få indgange, anbefales et større kabinet.
For eksempel har Hat Labs' [kompakte SH-RPi-kabinet](https://shop.hatlabs.fi/products/compact-weatherproof-enclosure-for-raspberry-pi-and-sh-rpi-158x90x60-mm), som ses nedenfor, rigelig plads til stik.

<figure markdown="span">
![](medium_enclosure.jpg){ width="50%" }
<figcaption>Det kompakte SH-RPi-kabinet giver mere plads til placering af panelstik.</figcaption>
</figure>


Andre egnede vandtætte kabinetter er nemme at finde i enhver netbutik. Større samledåser til udendørs brug kan også bruges til formålet.

### Boring af huller til panelstik

Kabinetterne har normalt ingen forborede huller. Brug altid et konisk bor eller et trinbor (det, der ligner et lille juletræ af metal), når du borer huller. Almindelige metalbor bider let for hårdt og kan revne kabinetvæggen.

Når du planlægger placeringen af huller og stik, skal du sørge for plads nok til at spænde stikkenes møtrikker og til selve stikhuset. Hvis du planlægger at vægmontere kabinettet, anbefales det at vende stikkene nedad, så risikoen for indtrængende vand bliver mindst mulig.

Passende hulstørrelser til forskellige stik:

- PG7-kabelforskruning og M12-panelstik (NMEA 2000): 12,5 mm eller 1/2"
- SP13-panelstik (de blåsorte plaststik): 13 mm
- PG9-kabelforskruning: 16 mm eller 5/8"

Gennemføringstyller af gummi eller silikone giver plads til væsentligt flere kabler end panelstik eller kabelforskruninger. De er dog ikke lige så vandtætte som panelstik eller kabelforskruninger. Desuden kræver de, at kablet monteres permanent, hvilket kan gøre det vanskeligere at servicere systemet.

TODO: Tilføj et billede af en gennemføringstyl.

### Lodning af panelstikkene

Brug altid krympeflex på de enkelte ledere, når du lodder de indvendige ledninger til panelstikkene.
Husk altid at trække krympeflexen ind på ledningen, _inden_ du lodder...
Som regel kan du først fylde loddetin i stikbenets hulrum og derefter smelte tinnet igen og føre lederen ind.
