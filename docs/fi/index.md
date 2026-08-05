---
title: Johdanto
translated_from: 2ad10049c9c3d0b5f6fb78356500eaa25670febd
---

# Johdanto

HALMET (Hat Labs Marine Engine & Tank interface) on kehityskortti moottori- ja tankkianturien liittämiseen veneissä ja muissa ajoneuvoissa. Sillä voi lukea digitaalisia ja analogisia antureita sekä liittyä muihin laitteisiin NMEA 2000-, WiFi-, Bluetooth-, I2C-, 1-Wire- tai GPIO-liitäntöjen kautta.

<figure markdown="span">
![](halmet_v1_top_photo.jpg){ width="60%" }
<figcaption>Kuva HALMETista</figcaption>
</figure>

## Tärkeimmät ominaisuudet

- **Neljä digitaalituloa**: HALMETissa on neljä digitaalituloa digitaalisten hälytyssignaalien lukemiseen tai laskureiksi. Tulot kestävät jännitteitä -32 V:n ja +32 V:n välillä. Digitaalituloilla voi havaita sekä signaalitasoja että ajassa muuttuvia signaaleja, kuten moottorin kierroslukua, polttoaineen virtausta tai ketjulaskurin pulsseja.

- **Neljä analogiatuloa**: HALMETissa on neljä analogiatuloa analogisten antureiden lukemiseen. Tulot kestävät jännitteitä -32 V:n ja +32 V:n välillä, ja mittausalue on 0–32 V. Tulot on kytketty 16-bittiseen ADS1115-AD-muuntimeen. Analogiatuloja voi käyttää sekä passiiviseen jännitemittaukseen että aktiiviseen vastusmittaukseen.

- **NMEA 2000 -yhteensopiva**: HALMET on täysin yhteensopiva NMEA 2000 -standardin kanssa. Kortin voi liittää NMEA 2000 -verkkoon sisäänrakennetun NMEA 2000 -liitännän kautta.

- **I2C-, 1-Wire- ja GPIO-liitännät**: HALMETissa on 4-nastainen I2C-liitäntä, 3-nastainen 1-Wire-liitäntä ja 13 vapaata yleiskäyttöistä tulo-/lähtönastaa (GPIO).

- **WiFi- ja Bluetooth-yhteydet**: HALMETissa on integroitu ESP32-WROOM-32E-moduuli, jossa on WiFi- ja Bluetooth-yhteydet. Ne mahdollistavat sekä liittymisen olemassa oleviin WiFi-verkkoihin että WiFi-tukiaseman luomisen, jolloin korttiin voi ottaa yhteyden suoraan.

- **ESP32-WROOM-32E ja 16 Mt flash-muistia**: ESP32-WROOM-32E-moduuli tarjoaa runsaasti laskentatehoa ja muistia vaativimpiinkin sovelluksiin. 16 megatavun flash-muistiin voi tallentaa suuria määriä dataa paikallisesti.

- **Laaja käyttöjännitealue**: HALMETia voi syöttää turvallisesti ajoneuvoissa ja veneissä yleisestä 12 V:n tai 24 V:n järjestelmästä. HALMET kestää 5 V:n ja 32 V:n väliset syöttöjännitteet.

HALMET on avointa laitteistoa, lisensoitu Creative Commons Nimeä-JaaSamoin 4.0 Kansainvälinen -lisenssillä.

## Laitteiston hankkiminen

HALMET-kortteja voi ostaa [Hat Labs Oy:ltä](https://shop.hatlabs.fi). Kaikki suunnittelutiedostot ovat myös saatavilla [HALMETin laitteistorepositoriossa GitHubissa](https://github.com/hatlabs/halmet-hardware/).
