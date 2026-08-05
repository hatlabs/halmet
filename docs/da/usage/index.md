---
title: Brug
translated_from: 62b94ac6364a19f44074c56bd610d243063e9847
---

# Brug

## Almindelige anvendelser

Dette afsnit indeholder praktiske oplysninger om aflæsning af forskellige typer sensorer og om at forbinde HALMET til andre enheder.

### Opsætning af software

HALMET er et udviklingskort, og der er ingen software installeret på forhånd.
Du skal selv installere den software, du vil bruge. Det er ikke svært, men det anbefales, at du har lidt erfaring med mikrocontrollerkort som Arduino eller ESP32 Devkit.

HALMET-dokumentationen forudsætter, at du bruger [HALMETs eksempelfirmware](https://github.com/hatlabs/HALMET-example-firmware). Denne firmware bygger på [SensESP](https://signalk.org/SensESP/)-frameworket og giver forholdsvis enkel adgang til kortets funktioner.

[SensESPs introduktionsvejledning](https://signalk.org/SensESP/pages/getting_started/) indeholder detaljerede instruktioner til opsætning af det udviklingsmiljø, der skal bruges til at kompilere og installere firmwaren. Instruktionerne er skrevet til almindelige ESP32-enheder, men de gælder også for HALMET. Brug blot [HALMETs eksempelfirmware](https://github.com/hatlabs/HALMET-example-firmware) i stedet for SensESPs projektskabelon.

Bemærk, at selvom SensESP-dokumentationen forudsætter brug af Signal K, kan HALMET også fint bruges som en selvstændig NMEA 2000-enhed.

Hvis du helst vil undgå SensESP, kan du også skrive din egen firmware med Arduino IDE eller ESP-IDF. Til mange formål er ESPHome også et udmærket valg.

**BEMÆRK:** Anvendelsen af GPIO-benene på HALMET afviger en smule fra benforbindelserne på både ESP32 Devkit og SH-ESP32. Hvis du tilpasser anden software end HALMETs eksempelfirmware, skal du kontrollere benforbindelserne en ekstra gang. Se [GPIO-oversigten](../hardware/index.md#gpio-oversigt) for flere oplysninger.

### Brug af de digitale indgange

HALMET har fire digitale indgange. Indgangene kan bruges til at læse digitale alarmsignaler eller som tællere. Dette afsnit beskriver, hvordan indgangene bruges i forskellige almindelige situationer. Vejledningen forudsætter, at du bruger HALMETs eksempelfirmware.

De digitale indgange D1–D4 er forbundet til henholdsvis GPIO-ben 23, 25, 27 og 26. Indgangene tåler spændinger mellem −32 V og +32 V. Tærskelspændingen for at registrere et højt signal er cirka 1,55 V, med en hysterese på cirka 0,7 V.

### Tilslutning til digitale alarmer

Dette afsnit beskriver, hvordan HALMET tilsluttes forskellige til/fra-signaler som for eksempel motor- eller lænsealarmer.

#### Opsætning af hardware

Til/fra-signaler som motor- eller lænsealarmer kan normalt tilsluttes HALMETs digitale indgange direkte. Afhængigt af signaltypen kan en pull-up eller pull-down være nødvendig.

På figuren nedenfor er der i eksempel (a) allerede en glødepære i kredsløbet. Når kontakten er åben, trækker pæren spændingen på D1 ned. Der er ikke brug for en ekstra pull-down.[^1] I eksempel (b) er der derimod ingen anden belastning i kredsløbet. Er kontakten åben, bliver spændingen på D2 flydende, og indgangen bliver tilfældigt enten høj eller lav. I det tilfælde skal den indbyggede pull-down-modstand aktiveres ved at kortslutte loddejumperen på bagsiden af kortet.

<figure markdown="span">
![](digin_pullup_pulldown.svg){ width="60%" }
<figcaption>Digitale indgange i forskellige situationer. (a) Der er allerede en lampe i kredsløbet. (b) Ingen anden belastning i kredsløbet; kontakten trækker signalet højt, når den sluttes. (c) Kontakten trækker signalet lavt, når den sluttes.</figcaption>
</figure>

[^1]: Hvis panelets lamper er lavet med lysdioder, er spændingsfaldet over lysdioderne måske ikke stort nok til at trække spændingen tilstrækkeligt langt ned. I så fald skal pull-down-modstanden aktiveres.

<figure markdown="span">
![](solder_jumpers.jpg){ width="60%" }
<figcaption>Loddejumperne på bagsiden af kortet kan lukkes, så de indbyggede pull-up- eller pull-down-modstande aktiveres.</figcaption>
</figure>

På samme måde kan det være nødvendigt at aktivere den indbyggede pull-up, hvis kontakten trækker signalet lavt, når den sluttes, som i eksempel (c).

Endelig gælder det modsatte, hvis alarmkontakterne er normalt sluttede. Når kontakten åbner, bliver indgangsspændingen trukket op eller ned afhængigt af kredsløbet. Også her kan det være nødvendigt at aktivere den indbyggede pull-up eller pull-down.

#### Opsætning af software

HALMETs eksempelfirmware indeholder hjælpemetoden `ConnectAlarmSender()` til at konfigurere og tilslutte digitale indgange. Se `main.cpp` fra linje 177 og frem. Både aktivt høje og aktivt lave signaler understøttes.

### Digitale indgange som tællere

HALMETs digitale indgange kan også bruges som tællere. Det er nyttigt til for eksempel at tælle motorens omdrejninger eller pulser fra en kædetæller.

#### Opsætning af hardware

Sådanne givere drives normalt aktivt i begge retninger, så der er ikke brug for pull-up eller pull-down. Hvis du forbinder HALMET til en udgang med lav impedans som for eksempel generatorens W-klemme, er det en god idé at montere en ledningssikring, så ledningen beskyttes mod kortslutninger som følge af skamfiling eller andre skader. Ellers kan giveren tilsluttes direkte til den digitale indgang.

Hvis pulskilden støjer meget, så omdrejningstallet aflæses forkert, kan et lavpasfilter aktiveres ved at kortslutte LP-loddejumperen på bagsiden af kortet. Lavpasfilteret har en knækfrekvens på cirka 2,3 kHz, hvilket bør passe til anvendelser som indgange fra generatorens W-klemme.

#### Opsætning af software

HALMETs eksempelfirmware indeholder en pulstæller, der kan aktiveres på en enkelt eller på alle de digitale indgange. Se eksempelkonfigurationen i `main.cpp` fra linje 214 og frem.

### Brug af de analoge indgange

HALMET har fire analoge indgange, som kan bruges enten til passiv spændingsmåling eller til aktiv modstandsmåling. Dette afsnit beskriver, hvordan indgangene bruges i forskellige almindelige situationer.

#### Opsætning af hardware

De analoge indgange A1–A4 er forbundet til en analog-digital-omsætter (ADC) af typen ADS1115. ADS1115 har 16-bits opløsning og en maksimal samplingfrekvens på 860 målinger pr. sekund. HALMETs analoge indgange har dog et kraftigt lavpasfilter med en knækfrekvens på cirka 160 Hz. Det er stadig rigeligt til at måle udgangssignalet fra fysiske sensorer som tankniveausensorer eller trykgivere på motoren.

På figuren nedenfor viser eksempel (a) et eksisterende instrument i motorpanelet forbundet til en modstandsgiver. Instrumenter i motorpaneler er som regel enten termostatiske eller magnetiske. I begge tilfælde virker instrumentet og giveren som en spændingsdeler, og spændingen over giveren er proportional med den målte størrelse. Denne spænding kan måles med HALMETs analoge indgange, uden at det forstyrrer det oprindelige instruments funktion. På grund af spændingsdeleren følger spændingen måske ikke lineært den målte størrelse, men det kan kompenseres i softwaren.

<figure markdown="span">
![](analog_input.svg){ width="60%" }
<figcaption>Tilslutning af analoge indgange med og uden et eksisterende instrument. (a) Er der allerede et instrument, skal HALMET bruges i tilstanden passiv spændingsmåling. (b) Er der ingen anden enhed, skal HALMET bruges i tilstanden aktiv modstandsmåling.</figcaption>
</figure>


Eksempel (b) viser et tilfælde uden et eksisterende instrument. Giveren er forbundet direkte til HALMETs analoge indgang. Her skal HALMET selv levere excitationsspændingen (den spænding, der driver giveren). HALMET udfører modstandsmålingen med en konstantstrømkilde på 10 mA. De 10 mA giver en spændingsforskel på 1 volt over en modstand på 100 ohm, hvilket svarer til en største målbar modstand på cirka 300 ohm. Konstantstrømkilden aktiveres ved at sætte en jumper på benparret i CCS-jumperstiklisten (konstantstrømkilde). Se figuren nedenfor.

<figure markdown="span">
![](ccs_jumpers.jpg){ width="60%" }
<figcaption>Figuren viser konstantstrømkilden aktiveret for de analoge indgange A2 og A4.</figcaption>
</figure>
