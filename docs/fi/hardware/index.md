---
title: Laitteiston kuvaus
translated_from: 96f96c3aff8d2a33ab2f1b59c0dbb8747c8ed3e2
---

# Laitteisto

## ESP32 lyhyesti

HALMET perustuu tehokkaaseen ESP32-WROOM-32E-mikro-ohjainmoduuliin. ESP32 on kaksiytiminen mikro-ohjain, jossa on sisäänrakennetut WiFi- ja Bluetooth-yhteydet. ESP32 on suosittu valinta IoT-sovelluksiin edullisuutensa, hyvän oheislaitevalikoimansa ja helppokäyttöisyytensä ansiosta.

## Kortin toiminnalliset lohkot

Kortin eri toiminnalliset lohkot kuvataan alla.

<figure markdown="span">
![](HALMET-func.jpg){ width="60%" }
<figcaption>HALMETin toiminnalliset lohkot.</figcaption>
</figure>

1.  NMEA 2000 -liitäntä sekä käyttöjännitteen syöttö ja suojaus. NMEA 2000
    -liittimessä on seuraavat suojaukset:
    - 500 mA:n itsestään palautuva sulake
    - Napaisuussuojausdiodi
    - Ylijännite- ja ESD-suojaukseen tarkoitetut TVS-diodit
    - Kaksivaiheinen häiriösuodatus

2.  Teholähde. Hakkuriteholähde, jonka suurin lähtövirta on 2 A.

3.  CAN-lähetinvastaanotin NMEA 2000:ta varten. RX- ja TX-LEDit näyttävät
    CAN-väylän liikenteen.

4.  I2C- ja 1-Wire-liitännät lisäantureiden liittämiseen.

5.  Käyttöliittymä. Reset-painike, boot-tilan painike (myös yleiskäyttöinen),
    punainen virran LED ja sininen käyttäjän ohjattava LED.

6.  USB 2.0 -liitäntä ohjelmointiin ja virheenjäljitykseen.

7.  ESP32-WROOM-32E-moduuli sisäänrakennetuilla WiFi- ja Bluetooth-yhteyksillä.
    HALMET-kortin moduulissa on 16 Mt flash-muistia.

8.  Digitaali- ja analogiatulojen galvaaninen erotus.

9.  Analogiatulot. Kortissa on neljä analogiatuloa, joiden erotuskyky on 16
    bittiä ja suurin tulojännite 33 V. Jokaisessa tulossa on ali- ja
    ylijännitesuojaus sekä alipäästösuodatus, jonka rajataajuus on 160 Hz
    mittaushäiriöiden vähentämiseksi.

    Analogiatuloissa on valinnainen 10 mA:n vakiovirtalähde aktiivista
    vastusmittausta varten. Vakiovirtalähteen voi ottaa käyttöön
    CCS-hyppyliittimillä.

    Vastusmittaustilassa suurin mitattava vastus on 300 ohmia.

10. Digitaalitulot. HALMETissa on neljä digitaalituloa, joiden suurin tulojännite
    on ±32 V. Tuloissa on Schmitt trigger parantamassa häiriönsietoa.


## Galvaaninen erotus

Kortissa on galvaaninen erotus digitaali- ja analogiatulojen sekä
ESP32-mikro-ohjaimen välillä. Erotus on toteutettu digitaalisilla erottimilla
I2C:lle ja neljälle digitaalitulolle sekä erotetulla DC/DC-muuntimella, joka
syöttää erotettua osaa.

Erotuksen ansiosta kortin voi syöttää NMEA 2000 -verkosta ilman maasilmukoiden
riskiä. Erotus suojaa myös tuloihin kohdistuvilta jännitepiikeiltä ja häiriöiltä.

<figure markdown="span">
![](HALMET-isolation.jpg){ width="60%" }
<figcaption>HALMETin erotusraja. Tuloliittimet on erotettu muusta kortista, eli niillä
ei ole yhteistä maata kortin muun osan kanssa.</figcaption>
</figure>

## Liittimet

<div class="row" markdown>
  <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-top.jpg){ width="100%" }
<figcaption>HALMETin liittimet, yläpuoli.</figcaption>
</figure>

   </div>
   <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-bottom.jpg){ width="100%" }
<figcaption>HALMETin liittimet, alapuoli.</figcaption>
</figure>

   </div>
</div>

### Yläpuolen liittimet

1.  NMEA 2000 -liitin. Liitin on 4-napainen Phoenix MC 3.81 -yhteensopiva
    irrotettava riviliitin. Sillä kortti liitetään NMEA 2000 -verkkoon ja
    syötetään käyttöjännite.

2.  1-Wire-liitin. 1-Wire-liittimeen voi kytkeä 1-Wire-antureita korttiin.
    Liitin on 3-nastainen, nastaväli 2,54 mm. Liitintä ei ole asennettu korttiin
    valmiiksi, koska se voi haitata kotelon paneeliliittimien sijoittelua.

3.  I2C-liitin. I2C-liittimeen voi kytkeä I2C-antureita korttiin. Liitin on
    4-nastainen, nastaväli 2,54 mm.

4.  Micro USB -liitin. Liitintä käytetään kortin ohjelmointiin ja
    virheenjäljitykseen.

5.  Kalustamattomat juotospisteet reset- (EN) ja boot-signaaleille (IO0).

6.  GPIO-liitin. GPIO-liitin on 2×10-nastainen, nastaväli 2,54 mm. Liitin tuo
    esiin ESP32:n vapaat GPIO-nastat, ja sitä voi käyttää myös JTAG-liittimenä.

7.  Erotetun alueen käyttöjännitteen liitin. Liittimestä voi syöttää ulkoisia
    laitteita erotetun osan 3V3- ja GND-navoista.

8.  Analogiatulojen vakiovirtalähteen (CCS) hyppyliittimen nastat.
    Vakiovirtalähteen saa käyttöön oikosulkemalla nastat hypyllä.

9.  Analogiatulojen liittimet. Liittimet ovat 2-napaisia Phoenix MC 3.81
    -yhteensopivia irrotettavia riviliittimiä. Niillä kytketään analogiset
    anturit korttiin.

10. Digitaalitulojen liittimet. Liittimet ovat 2-napaisia Phoenix MC 3.81
    -yhteensopivia irrotettavia riviliittimiä. Niillä kytketään digitaaliset
    anturit korttiin.

### Alapuolen liittimet

11.  CAN-päätevastuksen juotossilta. Sillan sulkeminen ottaa käyttöön CAN-väylän
     120 ohmin päätevastuksen. Älä käytä päätevastusta NMEA 2000 -verkoissa.

12.  Alipäästösuotimen juotossilta. Sillan sulkeminen ottaa käyttöön
     alipäästösuotimen kyseisellä analogiatulolla. Suotimen rajataajuus on
     2,3 kHz. Suodinta voi käyttää esimerkiksi kierroslukusignaalin häiriöiden
     vähentämiseen.

13.  Alasvetovastuksen juotossilta. Sillan sulkeminen ottaa käyttöön 100 kohmin
     alasvetovastuksen kyseisellä digitaalitulolla. Alasvetovastusta voi käyttää
     sulkeutuvan kytkimen lukemiseen, kun kytkin vetää jännitteen korkeaksi
     sulkeutuessaan.

14.  Ylösvetovastuksen juotossilta. Sillan sulkeminen ottaa käyttöön 100 kohmin
     ylösvetovastuksen kyseisellä digitaalitulolla. Ylösvetovastusta voi käyttää
     avautuvan kytkimen lukemiseen, kun kytkin vetää jännitteen matalaksi
     sulkeutuessaan.

15.  ADS1115:n I2C-osoitteen valinnan juotossillat. Silloilla valitaan
     ADS1115-AD-muuntimen I2C-osoite. Niillä vältetään osoitteiden törmäykset,
     kun samaan I2C-väylään on kytketty useita ADS1115-muuntimia. Juotospisteitä
     voi käyttää myös lisä-I2C-laitteiden kytkemiseen kortin erotetulle alueelle.

### GPIO-taulukko

HALMET varaa osan GPIO-nastoista tulo-oheislaitteille. Vapaat GPIO-nastat on tuotu
esiin 2×10-nastaiseen GPIO-liittimeen. Seuraavassa taulukossa on lueteltu
GPIO-nastat ja niiden toiminnot.

|    GPIO | Toiminto    | Huomautukset                                       |
| ------: | :---------- | :------------------------------------------------- |
|       0 | Boot-painike | Siirtyy käynnistyslataajaan, kun vedetään matalaksi |
|       1 | TXD0        | Datan lähetys USB:hen                              |
|       2 | LED         | Kortin punainen LED                                |
|       3 | RXD0        | Datan vastaanotto USB:stä                          |
|       4 | 1-Wire DQ   | 1-Wiren datalinja                                  |
|       5 | -           | Vapaa GPIO-liittimessä                             |
|      12 | - / TDI     | Vapaa GPIO-liittimessä. Vaihtoehtoisesti: JTAG TDI |
|      13 | - / TCK     | Vapaa GPIO-liittimessä. Vaihtoehtoisesti: JTAG TCK |
|      14 | - / TMS     | Vapaa GPIO-liittimessä. Vaihtoehtoisesti: JTAG TMS |
|      15 | - / TDO     | Vapaa GPIO-liittimessä. Vaihtoehtoisesti: JTAG TDO |
|      16 | -           | Vapaa GPIO-liittimessä                             |
|      17 | -           | Vapaa GPIO-liittimessä                             |
|      18 | CAN RX      | Vastaanotto NMEA 2000:sta                          |
|      19 | CAN TX      | Lähetys NMEA 2000:een                              |
|      21 | I2C SDA     | I2C:n datalinja. Käytössä analogiatuloille         |
|      22 | I2C SCL     | I2C:n kellolinja. Käytössä analogiatuloille        |
|      23 | DI1         | Digitaalitulo 1                                    |
|      25 | DI2         | Digitaalitulo 2                                    |
|      27 | DI3         | Digitaalitulo 3                                    |
|      26 | DI4         | Digitaalitulo 4                                    |
|      32 | -           | Vapaa GPIO-liittimessä                             |
|      33 | -           | Vapaa GPIO-liittimessä                             |
|      34 | -           | Vapaa GPIO-liittimessä                             |
|      35 | -           | Vapaa GPIO-liittimessä                             |
| 36 (VP) | Vain tulo   | Vapaa GPIO-liittimessä                             |
| 39 (VN) | Vain tulo   | Vapaa GPIO-liittimessä                             |


## Teholähde

Kortin sallittu syöttöjännitealue on 5–32 V. Tyypillinen virrankulutus on 90 mA
12 V:n jännitteellä WiFi-moduulin ollessa käytössä (vastaa 1,1 W:n tehoa).

## NMEA 2000

NMEA 2000 on laajalti käytetty tiedonsiirtostandardi, jolla liitetään antureita, ohjaimia ja näyttölaitteita veneissä ja laivoissa. Se perustuu CAN-väylään (Controller Area Network), joka on ajoneuvoväylästandardi ja mahdollistaa laitteiden keskinäisen viestinnän ilman isäntätietokonetta.

Kortti täyttää NMEA 2000 -standardin vaatimukset niin kauan kuin yhtäkään erottamatonta liitintä ei ole kytketty muihin maahan kytkettyihin laitteisiin. Esimerkiksi 1-Wire-lämpötila-anturia, jossa on pitkä kaapeli, voi käyttää, koska sillä ei ole yhteistä maata muiden laitteiden kanssa. Sen sijaan I2C-AD-muuntimen kytkeminen erottamattomaan I2C-liittimeen rikkoisi NMEA 2000 -yhteensopivuuden.

TODO: NMEA 2000:n GPIO-nastajärjestys

## Tila-LEDit

HALMET-kortilla on kaksi painiketta ja kaksi LEDiä. Painikkeet on merkitty tunnuksilla Reset ja Boot. Reset-painike käynnistää kortin uudelleen vetämällä ESP32:n Enable-nastan matalaksi. Boot-painike on kytketty GPIO0:aan, ja sillä voi pakottaa moduulin lataustilaan laitteen käynnistyksen aikana. Muulloin sitä voi käyttää tavallisena painiketulona.

LEDejä ei ole erikseen merkitty. Punainen LED palaa aina, kun kortilla on 3,3 V:n käyttöjännite. Sininen LED on kytketty GPIO2:een (nasta, jota ESP32-kehityskorteissa yleisesti käytetään LEDille). Käyttäjän ohjelmat voivat ohjata sitä osoittamaan laitteen tilaa.

## 1-Wire

1-Wire on Dallas Semiconductorin suunnittelema laiteväyläjärjestelmä; yhtiön on sittemmin ostanut Maxim Integrated Products. Vaikka 1-Wire on hidas protokolla ja tukee vain enintään 16,3 kbit/s:n nopeuksia, se on hyvin yksinkertainen toteuttaa ja toimii pitkilläkin etäisyyksillä. Sitä käytetään yleisesti lämpötila-antureissa ja muissa yksinkertaisissa mittalaitteissa.

HALMETin 1-Wire-toteutuksessa on ESD- ja RF-häiriösuodatus sekä alipäästösuodatus verkon luotettavuuden parantamiseksi.

Huomaa, että 1-Wiren datanasta (merkintä ”DQ”) on fyysisesti kytketty GPIO4:ään, joten käytä ohjelmassasi GPIO4:ää kaikelle 1-Wire-datalle.

## I2C

I2C (Inter-Integrated Circuit) on hyvin suosittu synkroninen sarjaliikenneväylä, jota käytetään yleisesti useiden erilaisten piirien liittämiseen. Se käyttää kahta datajohdinta käyttöjännitteen ja maan lisäksi.

HALMET käyttää I2C:tä sisäisesti ADS1115-AD-muuntimelle. I2C-väylä on tuotu myös 4-nastaiseen liittimeen lisä-I2C-laitteiden kytkemistä varten.

I2C-väylä on kytketty ESP32:n nastoihin GPIO21 (SDA) ja GPIO22 (SCL). Nämä ovat Arduinon ESP32-ympäristön oletusnastat I2C:lle, mutta poikkeavat SH-ESP32:n oletusnastoista.
