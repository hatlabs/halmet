---
title: Kom igång
translated_from: 75bcdba18bc044c04ce3e220067bf537e069ec82
---

# Kom igång

## Montering av hårdvaran

För att kontakterna ska kunna placeras friare i små kapslingar levereras HALMET-korten utan monterade stiftlister för 1-Wire och GPIO. Om du tänker använda något av dessa gränssnitt måste du löda fast stiftlisten på kortet.

Om du behöver anvisningar för att löda stiftlister på kortet kan du titta på SH-ESP32:s [monteringsanvisningar](https://docs.hatlabs.fi/sh-esp32/pages/getting-started/#revision-1-boards).

## Strömförsörjning av kortet

HALMET matas via NMEA 2000-kontakten. Om du ska ansluta HALMET till ett NMEA 2000-nätverk kan kortet matas direkt från nätverket. Anslut i så fall
NMEA 2000-ledarna till den 4-poliga löstagbara kopplingsplinten enligt figuren nedan.

<figure markdown="span">
![](halmet_n2k_input.jpg){ width="50%" }
<figcaption>Anslut NMEA 2000-ledarna till kontakten enligt figuren.</figcaption>
</figure>

Om du inte ska ansluta HALMET till ett NMEA 2000-nätverk använder du samma kontakt men ansluter bara ledare till `-` och `+`. Vilken strömkälla som helst på 5–32 V kan användas. Kortets typiska strömförbrukning med WiFi aktiverat är 0,07 A vid 12 V.

<figure markdown="span">
![](power_connector.jpg){ width="50%" }
<figcaption>Anslut matningsledarna till kontakten enligt figuren.</figcaption>
</figure>

## Kapslingar

Vid användning i båt bör HALMET alltid placeras i en vattentät kapsling.
Kortet är konstruerat för att passa i [SH-ESP32-kapslingen](https://shop.hatlabs.fi/products/sh-esp32-enclosure). Nedan finns ett exempel på ett HALMET-kort monterat i kapslingen.

<figure markdown="span">
![](halmet_small_enclosure.jpg){ width="50%" }
<figcaption>HALMET monterat i SH-ESP32-kapslingen.</figcaption>
</figure>

SH-ESP32-kapslingen har begränsat med utrymme för kontakter.
Var och en av långsidorna rymmer i praktiken bara 2–3 panelkontakter.
Om du tänker ansluta fler än några få ingångar rekommenderas en större kapsling.
Till exempel Hat Labs [kompakta SH-RPi-kapsling](https://shop.hatlabs.fi/products/compact-weatherproof-enclosure-for-raspberry-pi-and-sh-rpi-158x90x60-mm), som visas nedan, har redan gott om plats för kontakter.

<figure markdown="span">
![](medium_enclosure.jpg){ width="50%" }
<figcaption>Den kompakta SH-RPi-kapslingen ger mer plats för placering av panelkontakter.</figcaption>
</figure>


Andra lämpliga vattentäta kapslingar hittar du enkelt på vilken nätmarknadsplats som helst. Även större kopplingsdosor för utomhusbruk passar för ändamålet.

### Borra hål för panelkontakter

Kapslingarna har vanligtvis inga förborrade hål. När du borrar hål ska du
alltid använda ett koniskt borr eller en stegborr (den som ser ut som en liten julgran i metall). Vanliga metallborr biter lätt för hårt och kan spräcka kapslingens vägg.

När du planerar placeringen av hål och kontakter ska du lämna tillräckligt med plats för att dra åt kontaktmuttrarna och för själva kontaktkroppen. Om du tänker väggmontera kapslingen rekommenderas att kontakterna placeras nedåt för att minimera risken för vattenintrång.

Lämpliga hålstorlekar för olika kontakter:

- PG7-kabelgenomföring och M12-panelkontakt (NMEA 2000): 12,5 mm eller 1/2"
- SP13-panelkontakter (blåsvarta plastkontakter): 13 mm
- PG9-kabelgenomföring: 16 mm eller 5/8"

Gummi- eller silikongenomföringar ger betydligt högre kabeltäthet än panelkontakter eller kabelgenomföringar. De är dock inte lika vattentäta som panelkontakter eller kabelgenomföringar. Dessutom kräver de att kabeln fästs permanent, vilket kan göra det svårare att
serva systemet.

TODO: Lägg till en bild på en gummigenomföring.

### Löda panelkontakterna

När du löder de inre ledarna till panelkontakterna ska du alltid använda krympslang på de enskilda ledarna.
Kom alltid ihåg att trä krympslangen på ledaren _innan_ du löder...
Vanligtvis kan du först tillsätta lod i kontaktstiftets hålighet och sedan smälta lodet på nytt och föra in ledaren.
