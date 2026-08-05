---
title: Käyttö
translated_from: 62b94ac6364a19f44074c56bd610d243063e9847
---

# Käyttö

## Yleisiä käyttötapauksia

Tässä osiossa on käytännön tietoa erityyppisten antureiden lukemisesta ja HALMETin liittämisestä muihin laitteisiin.

### Ohjelmiston asennus

HALMET on kehityskortti, eikä siinä ole valmiiksi asennettua ohjelmistoa.
Sopiva ohjelmisto pitää asentaa itse. Se ei ole vaikeaa, mutta aiempi kokemus mikro-ohjainkorteista, kuten Arduinosta tai ESP32 Devkitistä, on suositeltavaa.

HALMETin dokumentaatiossa oletetaan, että käytössä on [HALMETin esimerkkifirmware](https://github.com/hatlabs/HALMET-example-firmware). Se perustuu [SensESP](https://signalk.org/SensESP/)-kehykseen ja tarjoaa suhteellisen suoraviivaisen pääsyn kortin ominaisuuksiin.

[SensESP:n aloitusopas](https://signalk.org/SensESP/pages/getting_started/) sisältää yksityiskohtaiset ohjeet firmwaren kääntämiseen ja asentamiseen tarvittavan kehitysympäristön asennukseen. Ohjeet on kirjoitettu yleisille ESP32-laitteille, mutta ne pätevät myös HALMETiin. Käytä vain [HALMETin esimerkkifirmwarea](https://github.com/hatlabs/HALMET-example-firmware) SensESP:n projektipohjan sijaan.

Huomaa, että vaikka SensESP:n dokumentaatiossa oletetaan Signal K:n käyttö, HALMET on täysin käyttökelpoinen myös itsenäisenä NMEA 2000 -laitteena.

Jos et halua käyttää SensESP:tä, voit myös tehdä oman firmwaresi Arduino IDE:llä tai ESP-IDF:llä. Moniin käyttötapauksiin myös ESPHome on erinomainen vaihtoehto.

**HUOMAA:** HALMETin GPIO-nastojen käyttö poikkeaa hieman sekä ESP32 Devkitin että SH-ESP32:n nastajärjestyksestä. Jos otat käyttöön jotain muuta ohjelmistoa kuin HALMETin esimerkkifirmwaren, nastojen käyttö on tarkistettava. Lisätietoja on [GPIO-taulukossa](../hardware/index.md#gpio-taulukko).

### Digitaalitulojen käyttö

HALMETissa on neljä digitaalituloa. Niitä voi käyttää digitaalisten hälytyssignaalien lukemiseen tai laskureina. Tässä osiossa kuvataan tulojen käyttö erilaisissa yleisissä käyttötapauksissa. Ohjeissa oletetaan, että käytössä on HALMETin esimerkkifirmware.

Digitaalitulot D1–D4 on kytketty GPIO-nastoihin 23, 25, 27 ja 26 tässä järjestyksessä. Tulot kestävät jännitteitä −32 V:n ja +32 V:n välillä. Korkean signaalin havaitsemisen kynnysjännite on noin 1,55 V ja hystereesi noin 0,7 V.

### Liittäminen digitaalisiin hälytyksiin

Tässä osiossa kuvataan, miten HALMET liitetään erilaisiin päälle/pois-tyyppisiin signaaleihin, kuten moottori- tai pilssihälytyksiin.

#### Laitteiston asennus

Yleensä erilaiset päälle/pois-tyyppiset signaalit, kuten moottori- tai pilssihälytykset, voidaan kytkeä suoraan HALMETin digitaalituloihin. Ylös- tai alasveto voi olla tarpeen signaalityypistä riippuen.

Alla olevan kuvan esimerkissä (a) piirissä on jo hehkulamppu. Kun kytkin on auki, hehkulamppu vetää D1:n jännitteen alas. Erillistä alasvetoa ei tarvita.[^1] Esimerkissä (b) piirissä ei sen sijaan ole muuta kuormaa. Jos kytkin on auki, D2:n jännite jää kelluvaksi ja tulo on satunnaisesti joko korkea tai matala. Tässä tapauksessa sisäinen alasvetovastus on otettava käyttöön sulkemalla kortin takapuolen juotossilta.

<figure markdown="span">
![](digin_pullup_pulldown.svg){ width="60%" }
<figcaption>Digitaalitulot eri käyttötapauksissa. (a) Piirissä on jo lamppu. (b) Piirissä ei ole muuta kuormaa, kytkin vetää signaalin korkeaksi sulkeutuessaan. (c) Kytkin vetää signaalin matalaksi sulkeutuessaan.</figcaption>
</figure>

[^1]: Jos paneelin valot on toteutettu LEDeillä, LEDien yli oleva jännitehäviö ei välttämättä riitä vetämään jännitettä riittävän alas. Tällöin alasvetovastus on otettava käyttöön.

<figure markdown="span">
![](solder_jumpers.jpg){ width="60%" }
<figcaption>Kortin takapuolen juotossillat voidaan sulkea, jolloin sisäänrakennetut ylös- tai alasvetovastukset tulevat käyttöön.</figcaption>
</figure>

Vastaavasti jos kytkin vetää signaalin matalaksi sulkeutuessaan kuten esimerkissä (c), sisäinen ylösveto voi olla tarpeen ottaa käyttöön.

Jos hälytyskytkimet ovat avautuvia, tilanne on päinvastainen. Kun kytkin avautuu, tulojännite vedetään ylös tai alas piiristä riippuen. Tällöin sisäinen ylös- tai alasveto voi olla tarpeen ottaa käyttöön.

#### Ohjelmiston asennus

HALMETin esimerkkifirmware tarjoaa `ConnectAlarmSender()`-apumetodin digitaalitulojen määrittämiseen ja kytkemiseen. Katso `main.cpp` riviltä 177 eteenpäin. Sekä aktiivisesti korkeat että aktiivisesti matalat signaalit ovat tuettuja.

### Digitaalitulot laskureina

HALMETin digitaalituloja voi käyttää myös laskureina. Tämä on hyödyllistä esimerkiksi moottorin kierrosten tai ketjulaskurin pulssien laskemiseen.

#### Laitteiston asennus

Yleensä tällaisia antureita ohjataan aktiivisesti molempiin suuntiin, joten ylös- tai alasvetoa ei tarvita. Jos liität HALMETin matalaimpedanssiseen lähtöön, kuten laturin W-napaan, on suositeltavaa lisätä linjasulake suojaamaan johdinta hankautumisesta tai muusta vauriosta johtuvilta oikosuluilta. Muuten anturin voi kytkeä suoraan digitaalituloon.

Jos pulssilähde on hyvin häiriöinen ja kierroslukulukema heittelee, alipäästösuotimen voi ottaa käyttöön sulkemalla kortin takapuolen LP-juotossillan. Alipäästösuotimen rajataajuus on noin 2,3 kHz, mikä sopii esimerkiksi laturin W-navan kaltaisiin tuloihin.

#### Ohjelmiston asennus

HALMETin esimerkkifirmware toteuttaa pulssilaskurin, jonka voi ottaa käyttöön millä tahansa digitaalitulolla tai kaikilla. Katso esimerkkiasetukset tiedostosta `main.cpp` riviltä 214 eteenpäin.

### Analogiatulojen käyttö

HALMETissa on neljä analogiatuloa, joita voi käyttää joko passiiviseen jännitemittaukseen tai aktiiviseen vastusmittaukseen. Tässä osiossa kuvataan tulojen käyttö erilaisissa yleisissä käyttötapauksissa.

#### Laitteiston asennus

Analogiatulot A1–A4 on kytketty ADS1115-AD-muuntimeen. ADS1115:n erotuskyky on 16 bittiä ja suurin näytteenottotaajuus 860 näytettä sekunnissa. HALMETin analogiatuloissa on kuitenkin voimakas alipäästösuodin, jonka rajataajuus on noin 160 Hz. Se riittää silti hyvin fysikaalisten anturien, kuten tankin pinta-anturien tai moottorin paineanturien, lukemiseen.

Alla olevan kuvan esimerkissä (a) on moottoripaneelin mittari kytkettynä vastusanturiin. Moottoripaneelin mittarit ovat rakenteeltaan yleensä joko termostaattisia tai magneettisia. Kummassakin tapauksessa mittari ja anturi toimivat jännitteenjakajana, ja anturin yli oleva jännite on verrannollinen mitattavaan suureeseen. Tämän jännitteen voi mitata HALMETin analogiatuloilla häiritsemättä alkuperäisen mittarin toimintaa. Jännitteenjakajan takia jännite ei välttämättä korreloi lineaarisesti mitattavan suureen kanssa, mutta tämän voi kompensoida ohjelmallisesti.

<figure markdown="span">
![](analog_input.svg){ width="60%" }
<figcaption>Analogiatulojen kytkeminen olemassa olevan mittarin kanssa ja ilman. (a) Kun mittari on jo olemassa, käytä HALMETia passiivisessa jännitemittaustilassa. (b) Kun muuta laitetta ei ole, käytä HALMETia aktiivisessa vastusmittaustilassa.</figcaption>
</figure>


Esimerkissä (b) mittaria ei ole. Anturi on kytketty suoraan HALMETin analogiatuloon. Tällöin HALMETin on tuotettava anturille herätejännite. HALMET toteuttaa vastusmittauksen 10 mA:n vakiovirtalähteellä. 10 mA:n virta synnyttää 100 ohmin vastuksen yli 1 voltin jännite-eron, joten suurin mitattava vastus on noin 300 ohmia. Vakiovirtalähde otetaan käyttöön asettamalla hyppy CCS-hyppyliittimen (vakiovirtalähde) nastapariin. Katso alla oleva kuva.

<figure markdown="span">
![](ccs_jumpers.jpg){ width="60%" }
<figcaption>Kuvassa vakiovirtalähde on otettu käyttöön analogiatuloille A2 ja A4.</figcaption>
</figure>
