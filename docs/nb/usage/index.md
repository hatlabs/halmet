---
title: Bruk
translated_from: 62b94ac6364a19f44074c56bd610d243063e9847
---

# Bruk

## Vanlige bruksområder

Denne delen inneholder praktisk informasjon om hvordan du leser ulike typer sensorer og kobler HALMET til andre enheter.

### Programvareoppsett

HALMET er et utviklingskort, og det leveres uten forhåndsinstallert programvare.
Du må installere egnet programvare selv. Dette er ikke vanskelig, men noe erfaring med mikrokontrollerkort som Arduino eller ESP32 Devkit er anbefalt.

HALMET-dokumentasjonen forutsetter at du bruker [eksempelfirmwaren for HALMET](https://github.com/hatlabs/HALMET-example-firmware). Denne firmwaren er basert på rammeverket [SensESP](https://signalk.org/SensESP/) og gir relativt enkel tilgang til funksjonene på kortet.

[Kom i gang-veiledningen for SensESP](https://signalk.org/SensESP/pages/getting_started/) gir detaljerte instruksjoner for å sette opp utviklingsmiljøet som trengs for å kompilere og installere firmwaren. Instruksjonene er skrevet for generiske ESP32-enheter, men de gjelder også for HALMET. Bruk bare [eksempelfirmwaren for HALMET](https://github.com/hatlabs/HALMET-example-firmware) i stedet for prosjektmalen til SensESP.

Merk at selv om SensESP-dokumentasjonen forutsetter at Signal K brukes, er HALMET også fullt brukbar som en frittstående NMEA 2000-enhet.

Hvis du foretrekker å ikke bruke SensESP, kan du også lage din egen firmware med Arduino IDE eller ESP-IDF. For mange bruksområder er ESPHome også et utmerket alternativ.

**MERK:** GPIO-pinnebelegget på HALMET skiller seg litt fra pinnebelegget på både ESP32 Devkit og SH-ESP32. Hvis du tilpasser annen programvare enn eksempelfirmwaren for HALMET, må du kontrollere pinnebelegget nøye. Se [GPIO-oversikten](../hardware/index.md#gpio-oversikt) for mer informasjon.

### Bruke digitale innganger

HALMET har fire digitale innganger. Disse inngangene kan brukes til å lese digitale alarmsignaler eller som tellere. Denne delen beskriver hvordan du bruker inngangene i ulike vanlige bruksområder. Instruksjonene forutsetter at du bruker eksempelfirmwaren for HALMET.

De digitale inngangene D1–D4 er koblet til henholdsvis GPIO-pinne 23, 25, 27 og 26. Inngangene tåler spenninger mellom −32 V og +32 V. Terskelspenningen for å registrere et høyt signal er om lag 1,55 V, med en hysterese på omtrent 0,7 V.

### Tilkobling til digitale alarmer

Denne delen beskriver hvordan du kobler HALMET til ulike av/på-signaler, for eksempel motor- eller lensealarmer.

#### Maskinvareoppsett

Vanligvis kan ulike av/på-signaler som motor- eller lensealarmer kobles direkte til de digitale inngangene på HALMET. En pull-up eller pull-down kan være nødvendig, avhengig av signaltypen.

I figuren nedenfor, i eksempel (a), finnes det allerede en lyspære i kretsen. Når bryteren er åpen, trekker lyspæra spenningen på D1 ned. Ingen ekstra pull-down er nødvendig.[^1] I eksempel (b) finnes det derimot ingen annen last i kretsen. Hvis bryteren er åpen, blir spenningen på D2 flytende, og inngangen blir tilfeldig enten høy eller lav. Da må den innebygde pull-down-motstanden aktiveres ved å lodde sammen loddebroen på undersiden av kortet.

<figure markdown="span">
![](digin_pullup_pulldown.svg){ width="60%" }
<figcaption>Digitale innganger i ulike bruksområder. (a) Det finnes allerede et lys i kretsen. (b) Ingen annen last i kretsen, bryteren trekker signalet høyt når den lukkes. (c) Bryteren trekker signalet lavt når den lukkes.</figcaption>
</figure>

[^1]: Hvis panellysene er laget med LED-er, er spenningsfallet over LED-ene kanskje ikke stort nok til å trekke spenningen tilstrekkelig lavt. Da må pull-down-motstanden aktiveres.

<figure markdown="span">
![](solder_jumpers.jpg){ width="60%" }
<figcaption>Loddebroene på undersiden av kortet kan loddes sammen for å aktivere de innebygde pull-up- eller pull-down-motstandene.</figcaption>
</figure>

På samme måte kan det være nødvendig å aktivere den innebygde pull-up-motstanden hvis bryteren trekker signalet lavt når den lukkes, som i eksempel (c).

Til slutt, hvis alarmbryteren er normalt lukket (NC), er behandlingen omvendt. Når bryteren åpner, blir inngangsspenningen trukket opp eller ned, avhengig av kretsen. Da kan det være nødvendig å aktivere den innebygde pull-up- eller pull-down-motstanden.

#### Programvareoppsett

Eksempelfirmwaren for HALMET har en praktisk metode `ConnectAlarmSender()` for å konfigurere og koble til digitale innganger. Se `main.cpp` fra linje 177 og utover. Både aktivt høye og aktivt lave signaler støttes.

### Digitale innganger som tellere

De digitale inngangene på HALMET kan også brukes som tellere. Det er nyttig for eksempel til å telle motorens omdreininger eller pulser fra en kjettingteller.

#### Maskinvareoppsett

Vanligvis drives slike givere aktivt i begge retninger, så verken pull-up eller pull-down er nødvendig. Hvis du kobler HALMET til en lavimpedansutgang som generatorens W-uttak, er det lurt å sette inn en linjesikring som beskytter lederen mot kortslutning på grunn av gnaging eller andre skader. Utover det kan du koble giveren direkte til den digitale inngangen.

Hvis pulskilden har mye elektrisk støy slik at turtallet leses feil, kan du aktivere et lavpassfilter ved å lodde sammen LP-loddebroen på undersiden av kortet. Lavpassfilteret har en grensefrekvens på om lag 2,3 kHz, noe som bør passe til bruksområder som innganger fra generatorens W-uttak.

#### Programvareoppsett

Eksempelfirmwaren for HALMET har en pulsteller som kan aktiveres på én eller alle de digitale inngangene. Se eksempelkonfigurasjonen i `main.cpp` fra linje 214 og utover.

### Bruke analoge innganger

HALMET har fire analoge innganger som kan brukes enten til passiv spenningsmåling eller til aktiv motstandsmåling. Denne delen beskriver hvordan du bruker inngangene i ulike vanlige bruksområder.

#### Maskinvareoppsett

De analoge inngangene A1–A4 er koblet til en AD-omformer av typen ADS1115. ADS1115 har 16 bits oppløsning og en maksimal samplingsfrekvens på 860 samplinger per sekund. De analoge inngangene på HALMET har likevel et kraftig lavpassfilter med en grensefrekvens på om lag 160 Hz. Det er fortsatt mer enn nok til å måle utgangssignaler fra fysiske sensorer, for eksempel tankgivere eller trykkgivere på motoren.

I figuren nedenfor viser eksempel (a) en eksisterende måler i motorpanelet koblet til en resistiv giver. Målere i motorpanelet er som regel enten termostatiske eller magnetiske. I begge tilfeller danner måleren og giveren en spenningsdeler, og spenningen over giveren er proporsjonal med den målte størrelsen. Denne spenningen kan måles med de analoge inngangene på HALMET uten å forstyrre funksjonen til den opprinnelige måleren. På grunn av spenningsdeleren korrelerer spenningen ikke nødvendigvis lineært med den målte størrelsen, men dette kan kompenseres i programvaren.

<figure markdown="span">
![](analog_input.svg){ width="60%" }
<figcaption>Tilkobling av analoge innganger med og uten en eksisterende måler. (a) Når det allerede finnes en måler, bruker du HALMET i modus for passiv spenningsmåling. (b) Når ingen annen enhet er til stede, bruker du HALMET i modus for aktiv motstandsmåling.</figcaption>
</figure>


Eksempel (b) viser et tilfelle uten en eksisterende måler. Giveren kobles direkte til den analoge inngangen på HALMET. Da må HALMET levere matespenning til giveren. HALMET utfører motstandsmålingen med en konstantstrømkilde på 10 mA. Strømmen på 10 mA gir en spenningsforskjell på 1 volt over en motstand på 100 Ω, altså en maksimal motstand på omtrent 300 Ω. Konstantstrømkilden aktiveres ved å sette en jumper over pinneparet på CCS-pinnelisten (konstantstrømkilde). Se figuren nedenfor.

<figure markdown="span">
![](ccs_jumpers.jpg){ width="60%" }
<figcaption>Figuren viser konstantstrømkilden aktivert for de analoge inngangene A2 og A4.</figcaption>
</figure>
