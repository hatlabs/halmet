---
title: Användning
translated_from: 0d5855d63a22b19308b3b70c9481dfc441864197
---

# Användning

## Vanliga användningsfall

Det här avsnittet innehåller praktisk information om hur du läser olika typer av givare och ansluter HALMET till andra enheter.

### Programvaruinstallation

HALMET är ett utvecklingskort och levereras utan förinstallerad programvara.
Du måste själv installera lämplig programvara. Det är inte svårt, men viss tidigare erfarenhet av mikrokontrollerkort som Arduino eller ESP32 Devkit rekommenderas.

HALMETs dokumentation utgår från att du använder [HALMETs exempelfirmware](https://github.com/hatlabs/HALMET-example-firmware). Den bygger på ramverket [SensESP](https://signalk.org/SensESP/) och ger relativt enkel tillgång till kortets funktioner.

[SensESPs guide för att komma igång](https://signalk.org/SensESP/pages/getting_started/) innehåller detaljerade anvisningar för att installera den utvecklingsmiljö som behövs för att kompilera och installera firmware. Anvisningarna är skrivna för generiska ESP32-enheter, men de gäller även HALMET. Använd bara [HALMETs exempelfirmware](https://github.com/hatlabs/HALMET-example-firmware) i stället för SensESPs projektmall.

Observera att även om SensESPs dokumentation utgår från Signal K är HALMET fullt användbar också som fristående NMEA 2000-enhet.

Om du inte vill använda SensESP kan du också skapa en egen firmware med Arduino IDE eller ESP-IDF. För många användningsfall är även ESPHome ett utmärkt alternativ.

**OBS:** GPIO-stiftens användning på HALMET skiljer sig något från stiftindelningen på både ESP32 Devkit och SH-ESP32. Om du anpassar någon annan programvara än HALMETs exempelfirmware måste du kontrollera stiftindelningen. Se [GPIO-referensen](../hardware/index.md#gpio-referens) för mer information.

### Använda de digitala ingångarna

HALMET har fyra digitala ingångar. De kan användas för att läsa digitala larmsignaler eller som räknare. Det här avsnittet beskriver hur ingångarna används i olika vanliga fall. Anvisningarna utgår från HALMETs exempelfirmware.

De digitala ingångarna D1–D4 är anslutna till GPIO-stiften 23, 25, 27 respektive 26. Ingångarna tål spänningar mellan −32 V och +32 V. Tröskelspänningen för att detektera en hög signal är cirka 1,55 V, med en hysteres på cirka 0,7 V.

### Ansluta digitala larm

Det här avsnittet beskriver hur HALMET ansluts till olika på/av-signaler, till exempel motor- eller länslarm.

#### Hårdvaruinstallation

Vanligtvis kan olika på/av-signaler som motor- eller länslarm anslutas direkt till HALMETs digitala ingångar. En pull-up eller pull-down kan behövas beroende på signaltypen.

I figuren nedan, i exempel (a), finns redan en glödlampa i kretsen. När strömbrytaren är öppen drar glödlampan ned spänningen på D1. Ingen extra pull-down behövs.[^1] I exempel (b) finns däremot ingen annan last i kretsen. Om strömbrytaren är öppen blir spänningen på D2 flytande och ingången blir slumpmässigt antingen hög eller låg. I det fallet måste det inbyggda pull-down-motståndet aktiveras genom att lödbygeln på kortets baksida löds ihop.

<figure markdown="span">
![](digin_pullup_pulldown.svg){ width="60%" }
<figcaption>Digitala ingångar i olika användningsfall. (a) Det finns redan en lampa i kretsen. (b) Ingen annan last i kretsen, strömbrytaren drar signalen hög när den sluts. (c) Strömbrytaren drar signalen låg när den sluts.</figcaption>
</figure>

[^1]: Om panelbelysningen är gjord med lysdioder räcker spänningsfallet över lysdioderna kanske inte till för att dra ned spänningen till en tillräckligt låg nivå. Då måste pull-down-motståndet aktiveras.

<figure markdown="span">
![](solder_jumpers.jpg){ width="60%" }
<figcaption>Lödbyglarna på kortets baksida kan lödas ihop för att aktivera de inbyggda pull-up- eller pull-down-motstånden.</figcaption>
</figure>

På samma sätt kan det inbyggda pull-up-motståndet behöva aktiveras om strömbrytaren drar signalen låg när den sluts, som i exempel (c).

Slutligen, om larmkontakterna är brytande (NC), är hanteringen omvänd. När kontakten öppnar dras ingångsspänningen upp eller ned beroende på kretsen. Då kan det inbyggda pull-up- eller pull-down-motståndet behöva aktiveras.

#### Programvaruinstallation

HALMETs exempelfirmware har hjälpmetoden `ConnectAlarmSender()` för att konfigurera och ansluta digitala ingångar. Se `main.cpp` från rad 177 och framåt. Både aktivt höga och aktivt låga signaler stöds.

### Digitala ingångar som räknare

HALMETs digitala ingångar kan också användas som räknare. Det är användbart till exempel för att räkna motorns varv eller pulser från en kättingräknare.

#### Hårdvaruinstallation

Sådana givare drivs vanligtvis aktivt i båda riktningarna, så ingen pull-up eller pull-down behövs. Om du ansluter HALMET till en utgång med låg impedans, till exempel generatorns W-uttag, är det klokt att sätta en linjesäkring i serie för att skydda ledaren mot kortslutning på grund av skavning eller andra skador. I övrigt kan du ansluta givaren direkt till den digitala ingången.

Om pulskällan är mycket brusig och varvtalsavläsningen hoppar kan ett lågpassfilter aktiveras genom att LP-lödbygeln på kortets baksida löds ihop. Lågpassfiltrets gränsfrekvens är cirka 2,3 kHz, vilket bör passa för tillämpningar som ingångar från generatorns W-uttag.

#### Programvaruinstallation

HALMETs exempelfirmware innehåller en pulsräknare som kan aktiveras på någon av eller alla de digitala ingångarna. Se exempelkonfigurationen i `main.cpp` från rad 214 och framåt.

### Använda de analoga ingångarna

HALMET har fyra analoga ingångar som kan användas antingen för passiv spänningsmätning eller för aktiv resistansmätning. Det här avsnittet beskriver hur ingångarna används i olika vanliga fall.

#### Hårdvaruinstallation

De analoga ingångarna A1–A4 är anslutna till en AD-omvandlare av typen ADS1115. ADS1115 har 16 bitars upplösning och en högsta samplingsfrekvens på 860 sampel per sekund. HALMETs analoga ingångar har dock ett kraftigt lågpassfilter med en gränsfrekvens på cirka 160 Hz. Det räcker ändå gott och väl för att mäta utsignaler från fysiska givare, till exempel tanknivågivare eller motorns tryckgivare.

I figuren nedan visar exempel (a) en befintlig mätare i motorpanelen ansluten till en resistiv givare. Mätarna i motorpaneler är oftast antingen termostatiska eller magnetiska. I båda fallen fungerar mätaren och givaren som en spänningsdelare, och spänningen över givaren är proportionell mot den uppmätta storheten. Den spänningen kan mätas med HALMETs analoga ingångar utan att den ursprungliga mätarens funktion störs. På grund av spänningsdelaren korrelerar spänningen kanske inte linjärt med den uppmätta storheten, men det kan kompenseras i programvaran.

<figure markdown="span">
![](analog_input.svg){ width="60%" }
<figcaption>Anslutning av analoga ingångar med och utan en befintlig mätare. (a) Med en befintlig mätare, använd HALMET i läget för passiv spänningsmätning. (b) När ingen annan enhet finns, använd HALMET i läget för aktiv resistansmätning.</figcaption>
</figure>


Exempel (b) visar ett fall utan befintlig mätare. Givaren ansluts direkt till HALMETs analoga ingång. Då måste HALMET ge matningsspänning till givaren. HALMET utför resistansmätningen med en konstantströmkälla på 10 mA. Strömmen på 10 mA ger en spänningsskillnad på 1 volt över en resistans på 100 Ω, vilket ger en största resistans på cirka 300 Ω. Konstantströmkällan aktiveras genom att en bygel sätts över stiftparet på CCS-bygelstiften (constant current source, konstantströmkälla). Se figuren nedan.

<figure markdown="span">
![](ccs_jumpers.jpg){ width="60%" }
<figcaption>Figuren visar konstantströmkällan aktiverad för de analoga ingångarna A2 och A4.</figcaption>
</figure>
