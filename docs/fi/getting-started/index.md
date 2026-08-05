---
title: Aloitusopas
translated_from: 75bcdba18bc044c04ce3e220067bf537e069ec82
---

# Aloitusopas

## Kortin kokoaminen

Jotta liittimet voidaan sijoittaa joustavammin pieniin koteloihin, HALMET-kortit toimitetaan ilman 1-Wire- ja GPIO-liittimiä. Jos aiot käyttää kumpaakaan näistä liitännöistä, sinun on juotettava liitin kiinni korttiin.

Jos tarvitset ohjeita nastarimojen juottamiseen, katso SH-ESP32:n [kokoamisohjeet](https://docs.hatlabs.fi/sh-esp32/pages/getting-started/#revision-1-boards).

## Kortin virransyöttö

HALMET saa käyttöjännitteensä NMEA 2000 -liittimen kautta. Jos aiot liittää HALMETin NMEA 2000 -verkkoon, kortin voi syöttää suoraan verkosta. Kytke silloin NMEA 2000 -johtimet 4-napaiseen irrotettavaan riviliittimeen alla olevan kuvan mukaisesti.

<figure markdown="span">
![](halmet_n2k_input.jpg){ width="50%" }
<figcaption>Kytke NMEA 2000 -johtimet liittimeen kuvan mukaisesti.</figcaption>
</figure>

Jos et aio liittää HALMETia NMEA 2000 -verkkoon, käytä samaa liitintä mutta kytke johtimet vain `-`- ja `+`-paikkoihin. Käyttöjännitteen voi ottaa mistä tahansa 5–32 V:n lähteestä. Kortin tyypillinen virrankulutus WiFin ollessa käytössä on 0,07 A 12 V:n jännitteellä.

<figure markdown="span">
![](power_connector.jpg){ width="50%" }
<figcaption>Kytke käyttöjännitejohtimet liittimeen kuvan mukaisesti.</figcaption>
</figure>

## Kotelot

Veneessä HALMET on aina sijoitettava vesitiiviiseen koteloon.
Kortti on suunniteltu sopimaan [SH-ESP32-koteloon](https://shop.hatlabs.fi/products/sh-esp32-enclosure). Alla on esimerkki koteloon asennetusta HALMET-kortista.

<figure markdown="span">
![](halmet_small_enclosure.jpg){ width="50%" }
<figcaption>HALMET asennettuna SH-ESP32-koteloon.</figcaption>
</figure>

SH-ESP32-kotelossa on rajallisesti tilaa liittimille.
Kummallekin pitkälle sivulle mahtuu käytännössä vain 2–3 paneeliliitintä.
Jos aiot kytkeä useampia kuin muutaman tulon, suositellaan suurempaa koteloa.
Esimerkiksi alla näkyvässä Hat Labsin [kompaktissa SH-RPi-kotelossa](https://shop.hatlabs.fi/products/compact-weatherproof-enclosure-for-raspberry-pi-and-sh-rpi-158x90x60-mm) on jo runsaasti tilaa liittimille.

<figure markdown="span">
![](medium_enclosure.jpg){ width="50%" }
<figcaption>Kompakti SH-RPi-kotelo tarjoaa enemmän tilaa paneeliliittimien sijoitteluun.</figcaption>
</figure>


Muita sopivia vesitiiviitä koteloita löytyy helposti mistä tahansa verkkokaupasta. Myös suuremmat ulkokäyttöön tarkoitetut jakorasiat sopivat tarkoitukseen.

### Reikien poraaminen paneeliliittimille

Koteloissa ei yleensä ole valmiiksi porattuja reikiä. Käytä reikiä poratessasi aina kartio- tai porrasterää (sellaista, joka näyttää pieneltä metalliselta joulukuuselta). Tavallinen metalliporanterä puree helposti liian syvälle ja voi halkaista kotelon seinämän.

Kun suunnittelet reikien ja liittimien sijoittelua, jätä riittävästi tilaa liitinmuttereiden kiristämiselle ja liittimen rungolle. Jos aiot asentaa kotelon seinälle, liittimet kannattaa sijoittaa alaspäin, jotta veden pääsy sisään on mahdollisimman epätodennäköistä.

Sopivat reikäkoot eri liittimille:

- PG7-läpivientiholkki ja M12-paneeliliitin (NMEA 2000): 12,5 mm tai 1/2"
- SP13-paneeliliittimet (sinimustat muoviliittimet): 13 mm
- PG9-läpivientiholkki: 16 mm tai 5/8"

Kumiset tai silikoniset läpivientikumit mahdollistavat huomattavasti tiheämmän kaapeloinnin kuin paneeliliittimet tai läpivientiholkit. Ne eivät kuitenkaan ole yhtä vesitiiviitä kuin paneeliliittimet tai läpivientiholkit. Lisäksi ne vaativat kaapelin pysyvän kiinnityksen, mikä voi vaikeuttaa järjestelmän huoltamista.

TODO: Lisää kuva läpivientikumista.

### Paneeliliittimien juottaminen

Kun juotat sisäisiä johtimia paneeliliittimiin, käytä aina kutistesukkaa yksittäisten johtimien päällä.
Muista aina pujottaa kutistesukka johtimeen _ennen_ juottamista...
Yleensä juotostinaa kannattaa ensin lisätä liittimen nastan koloon ja sitten sulattaa tina uudelleen ja työntää johdin paikalleen.
