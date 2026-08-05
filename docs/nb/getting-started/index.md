---
title: Kom i gang
translated_from: 75bcdba18bc044c04ce3e220067bf537e069ec82
---

# Kom i gang

## Montering av maskinvaren

For å gi mer fleksibel plassering av kontaktene i små kabinetter leveres HALMET-kortene uten 1-Wire- og GPIO-pinnelister montert. Hvis du planlegger å bruke ett av disse grensesnittene, må du lodde pinnelisten fast på kortet.

Hvis du trenger veiledning i å lodde pinnelister på kortet, kan du se [monteringsanvisningen](https://docs.hatlabs.fi/sh-esp32/pages/getting-started/#revision-1-boards) for SH-ESP32.

## Strømforsyning til kortet

HALMET forsynes med strøm gjennom NMEA 2000-kontakten. Hvis du skal koble HALMET til et NMEA 2000-nettverk, kan du forsyne kortet direkte fra nettverket. Koble i så fall NMEA 2000-ledningene til den 4-pinners pluggbare koblingsklemmen som vist i figuren nedenfor.

<figure markdown="span">
![](halmet_n2k_input.jpg){ width="50%" }
<figcaption>Koble NMEA 2000-ledningene til kontakten som vist.</figcaption>
</figure>

Hvis du ikke skal koble HALMET til et NMEA 2000-nettverk, bruker du den samme kontakten, men kobler bare ledninger til `-` og `+`. Enhver strømkilde på 5–32 V kan brukes. Typisk strømforbruk for kortet med WiFi aktivt er 0,07 A ved 12 V.

<figure markdown="span">
![](power_connector.jpg){ width="50%" }
<figcaption>Koble strømledningene til kontakten som vist.</figcaption>
</figure>

## Kabinetter

Ved bruk i båt bør HALMET alltid plasseres i et vanntett kabinett.
Kortet er laget for å passe i [SH-ESP32-kabinettet](https://shop.hatlabs.fi/products/sh-esp32-enclosure). Nedenfor ser du et eksempel på et HALMET-kort montert i kabinettet.

<figure markdown="span">
![](halmet_small_enclosure.jpg){ width="50%" }
<figcaption>HALMET montert i SH-ESP32-kabinettet.</figcaption>
</figure>

SH-ESP32-kabinettet har begrenset plass til kontakter.
Hver av langsidene har i praksis bare plass til 2–3 panelkontakter.
Hvis du har tenkt å koble til mer enn noen få innganger, anbefales et større kabinett.
For eksempel har [det kompakte SH-RPi-kabinettet](https://shop.hatlabs.fi/products/compact-weatherproof-enclosure-for-raspberry-pi-and-sh-rpi-158x90x60-mm) fra Hat Labs, vist nedenfor, allerede rikelig med plass til kontakter.

<figure markdown="span">
![](medium_enclosure.jpg){ width="50%" }
<figcaption>Det kompakte SH-RPi-kabinettet gir mer plass til plassering av panelkontakter.</figcaption>
</figure>


Andre egnede vanntette kabinetter er lette å finne i en hvilken som helst nettbutikk. Større koblingsbokser for utendørs bruk egner seg også til formålet.

### Bore hull for panelkontakter

Kabinettene har vanligvis ikke ferdigborede hull. Når du borer hull, bruker du alltid et konisk bor eller et trinnbor (det som ser ut som et lite juletre i metall). Vanlige metallbor kan lett bite for hardt og sprekke kabinettveggen.

Når du planlegger plasseringen av hull og kontakter, må du la det være nok plass til å stramme kontaktmutrene og til selve kontakthuset. Hvis du planlegger å veggmontere kabinettet, anbefales det å plassere kontaktene vendt nedover for å redusere faren for vanninntrengning.

Passende hullstørrelser for ulike kontakter:

- PG7-kabelgjennomføring og M12-panelkontakt (NMEA 2000): 12,5 mm eller 1/2"
- SP13-panelkontakter (blåsvarte plastkontakter): 13 mm
- PG9-kabelgjennomføring: 16 mm eller 5/8"

Gummigjennomføringer eller silikongjennomføringer gir vesentlig høyere kabeltetthet enn panelkontakter og kabelgjennomføringer. De er imidlertid ikke like vanntette som panelkontakter og kabelgjennomføringer. I tillegg krever de permanent kabelfeste, noe som kan gjøre service på systemet vanskeligere.

TODO: Legg til et bilde av en gummigjennomføring.

### Lodde panelkontaktene

Når du lodder de innvendige ledningene til panelkontaktene, bruker du alltid krympestrømpe på hver enkelt ledning.
Husk alltid å tre krympestrømpen på ledningen _før_ du lodder...
Vanligvis kan du først fylle litt loddetinn i pinnehulrommet i kontakten og deretter smelte loddetinnet på nytt og føre ledningen inn.
