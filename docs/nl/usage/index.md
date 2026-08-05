---
title: Gebruik
translated_from: 0d5855d63a22b19308b3b70c9481dfc441864197
---

# Gebruik

## Veelvoorkomende toepassingen

Dit onderdeel bevat praktische informatie over het uitlezen van verschillende typen sensoren en over het aansluiten van de HALMET op andere apparaten.

### Software installeren

De HALMET is een ontwikkelbord en wordt zonder vooraf geïnstalleerde software geleverd.
U installeert de geschikte software zelf. Dat is niet moeilijk, maar enige ervaring met microcontrollerborden zoals Arduino of ESP32 Devkit is wel aan te raden.

In de HALMET-documentatie wordt uitgegaan van de [HALMET-voorbeeldfirmware](https://github.com/hatlabs/HALMET-example-firmware). Deze firmware is gebaseerd op het framework [SensESP](https://signalk.org/SensESP/) en geeft betrekkelijk eenvoudig toegang tot de mogelijkheden van de print.

De [SensESP Getting Started Guide](https://signalk.org/SensESP/pages/getting_started/) bevat uitgebreide instructies voor het installeren van de ontwikkelomgeving die u nodig hebt om de firmware te compileren en te installeren. Die instructies zijn geschreven voor gewone ESP32-apparaten, maar gelden ook voor de HALMET. Gebruik alleen de [HALMET-voorbeeldfirmware](https://github.com/hatlabs/HALMET-example-firmware) in plaats van het projectsjabloon van SensESP.

Let op: hoewel in de SensESP-documentatie het gebruik van Signal K wordt verondersteld, is de HALMET ook volledig bruikbaar als zelfstandig NMEA 2000-apparaat.

Wilt u SensESP liever niet gebruiken, dan kunt u ook eigen firmware maken met de Arduino IDE of ESP-IDF. Voor veel toepassingen is ESPHome eveneens een uitstekende keuze.

**LET OP:** de GPIO-pintoewijzingen van de HALMET wijken licht af van de pintoewijzingen van zowel de ESP32 Devkit als de SH-ESP32. Past u andere software aan dan de HALMET-voorbeeldfirmware, dan moet u de pintoewijzingen zorgvuldig controleren. Zie het [GPIO-overzicht](../hardware/index.md#gpio-overzicht) voor meer informatie.

### De digitale ingangen gebruiken

De HALMET heeft vier digitale ingangen. Deze ingangen kunt u gebruiken voor het lezen van digitale alarmsignalen of als tellers. Dit onderdeel beschrijft het gebruik van de ingangen in verschillende veelvoorkomende situaties. In de instructies wordt uitgegaan van de HALMET-voorbeeldfirmware.

De digitale ingangen D1–D4 zijn aangesloten op respectievelijk GPIO-pin 23, 25, 27 en 26. De ingangen verdragen spanningen tussen −32 V en +32 V. De drempelspanning voor het detecteren van een hoog signaal bedraagt ongeveer 1,55 V, met een hysterese van ongeveer 0,7 V.

### Aansluiten op digitale alarmen

Dit onderdeel beschrijft hoe u de HALMET aansluit op verschillende aan/uit-signalen, zoals motor- of bilgealarmen.

#### De hardware aansluiten

Aan/uit-signalen zoals motor- of bilgealarmen kunt u meestal rechtstreeks op de digitale ingangen van de HALMET aansluiten. Afhankelijk van het signaaltype kan een pull-up of pull-down nodig zijn.

In de afbeelding hieronder zit in voorbeeld (a) al een controlelampje in het circuit. Als de schakelaar open is, trekt het controlelampje de spanning op D1 omlaag. Een extra pull-down is dan niet nodig.[^1] In voorbeeld (b) zit er echter geen andere belasting in het circuit. Als de schakelaar open is, blijft de spanning op D2 zweven en leest de ingang willekeurig hoog of laag. In dat geval moet u de interne pull-downweerstand inschakelen door de soldeerbrug aan de achterzijde van de print dicht te solderen.

<figure markdown="span">
![](digin_pullup_pulldown.svg){ width="60%" }
<figcaption>Digitale ingangen in verschillende situaties. (a) Er zit al een lampje in het circuit. (b) Geen andere belasting in het circuit; de schakelaar trekt het signaal hoog wanneer hij sluit. (c) De schakelaar trekt het signaal laag wanneer hij sluit.</figcaption>
</figure>

[^1]: Is de paneelverlichting met leds uitgevoerd, dan is de spanningsval over de leds mogelijk niet groot genoeg om de spanning ver genoeg omlaag te trekken. In dat geval moet de pull-downweerstand worden ingeschakeld.

<figure markdown="span">
![](solder_jumpers.jpg){ width="60%" }
<figcaption>De soldeerbruggen aan de achterzijde van de print kunnen worden dichtgesoldeerd om de ingebouwde pull-up- of pull-downweerstanden in te schakelen.</figcaption>
</figure>

Trekt de schakelaar het signaal laag wanneer hij sluit, zoals in voorbeeld (c), dan kan het op dezelfde manier nodig zijn de interne pull-up in te schakelen.

Zijn de alarmschakelaars ten slotte verbreekcontacten (NC), dan is de aanpak precies omgekeerd. Wanneer de schakelaar opent, wordt de ingangsspanning omhoog of omlaag getrokken, afhankelijk van het circuit. Ook dan kan het nodig zijn de interne pull-up of pull-down in te schakelen.

#### De software instellen

De HALMET-voorbeeldfirmware biedt de hulpmethode `ConnectAlarmSender()` voor het instellen en aansluiten van digitale ingangen. Zie `main.cpp` vanaf regel 177. Zowel actief hoge als actief lage signalen worden ondersteund.

### Digitale ingangen als tellers

De digitale ingangen van de HALMET kunt u ook als tellers gebruiken. Dat is bijvoorbeeld handig om motoromwentelingen of pulsen van een kettingteller te tellen.

#### De hardware aansluiten

Dergelijke gevers worden meestal in beide richtingen actief aangestuurd, zodat een pull-up of pull-down niet nodig is. Sluit u de HALMET aan op een uitgang met lage impedantie, zoals de W-klem van de dynamo, dan is het verstandig een kabelzekering op te nemen om de ader te beschermen tegen kortsluiting door schuren of andere beschadiging. Verder kunt u de gever rechtstreeks op de digitale ingang aansluiten.

Is de pulsbron erg ruisig, waardoor het toerental onrustig wordt weergegeven, dan kunt u een laagdoorlaatfilter inschakelen door de LP-soldeerbrug aan de achterzijde van de print dicht te solderen. Het laagdoorlaatfilter heeft een afsnijfrequentie van ongeveer 2,3 kHz, wat geschikt zou moeten zijn voor toepassingen zoals ingangen op de W-klem van de dynamo.

#### De software instellen

De HALMET-voorbeeldfirmware bevat een pulsteller die u op één of op alle digitale ingangen kunt inschakelen. Zie de voorbeeldconfiguratie in `main.cpp` vanaf regel 214.

### De analoge ingangen gebruiken

De HALMET heeft vier analoge ingangen die u kunt gebruiken voor passieve spanningsmetingen of voor actieve weerstandsmetingen. Dit onderdeel beschrijft het gebruik van de ingangen in verschillende veelvoorkomende situaties.

#### De hardware aansluiten

De analoge ingangen A1–A4 zijn aangesloten op een ADS1115-analoog-digitaalomzetter. De ADS1115 heeft een 16-bits resolutie en een maximale bemonsteringsfrequentie van 860 samples per seconde. De analoge ingangen van de HALMET bevatten echter een sterk laagdoorlaatfilter met een afsnijfrequentie van ongeveer 160 Hz. Dat is nog steeds ruim voldoende om de uitgangssignalen van fysieke sensoren te meten, zoals tankniveausensoren of motordruksensoren.

In de afbeelding hieronder toont voorbeeld (a) een bestaande meter op het motorpaneel die op een weerstandsgever is aangesloten. Meters op een motorpaneel zijn meestal thermostatisch of magnetisch uitgevoerd. In beide gevallen vormen de meter en de gever samen een spanningsdeler, en is de spanning over de gever evenredig met de gemeten grootheid. Die spanning kunt u met de analoge ingangen van de HALMET meten zonder de werking van de oorspronkelijke meter te verstoren. Door de spanningsdeler hoeft de spanning niet lineair samen te hangen met de gemeten grootheid, maar dat kunt u in de software compenseren.

<figure markdown="span">
![](analog_input.svg){ width="60%" }
<figcaption>Analoge ingangen aansluiten met en zonder bestaande meter. (a) Is er al een meter aanwezig, gebruik de HALMET dan in de modus passieve spanningsmeting. (b) Is er geen ander apparaat aanwezig, gebruik de HALMET dan in de modus actieve weerstandsmeting.</figcaption>
</figure>


Voorbeeld (b) toont een situatie zonder bestaande meter. De gever is rechtstreeks op de analoge ingang van de HALMET aangesloten. In dat geval moet de HALMET zelf de excitatiespanning voor de gever leveren. De HALMET voert de weerstandsmeting uit met een constantstroombron van 10 mA. Die stroom van 10 mA levert over een weerstand van 100 Ω een spanningsverschil van 1 volt op, wat neerkomt op een maximale weerstand van ongeveer 300 Ω. U schakelt de constantstroombron in door een jumper op het pinpaar van de CCS-jumperheader (constant current source) te plaatsen. Zie de afbeelding hieronder.

<figure markdown="span">
![](ccs_jumpers.jpg){ width="60%" }
<figcaption>De afbeelding toont de constantstroombron ingeschakeld voor de analoge ingangen A2 en A4.</figcaption>
</figure>
