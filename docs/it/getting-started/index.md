---
title: Primi passi
translated_from: 75bcdba18bc044c04ce3e220067bf537e069ec82
---

# Primi passi

## Assemblaggio dell’hardware

Per consentire una disposizione più flessibile dei connettori nelle custodie di piccole dimensioni, le schede HALMET vengono fornite senza i connettori a pettine 1-Wire e GPIO montati. Se si intende utilizzare una di queste due interfacce, occorre saldare alla scheda il relativo connettore a pettine.

Per le istruzioni sulla saldatura dei connettori a pettine sulla scheda, consultare le [istruzioni di assemblaggio](https://docs.hatlabs.fi/sh-esp32/pages/getting-started/#revision-1-boards) di SH-ESP32.

## Alimentazione della scheda

HALMET viene alimentato attraverso il connettore NMEA 2000. Se si intende collegare HALMET a una rete NMEA 2000, la scheda può essere alimentata direttamente dalla rete. In tal caso, collegare i conduttori NMEA 2000 alla morsettiera estraibile a 4 pin come mostrato nella figura seguente.

<figure markdown="span">
![](halmet_n2k_input.jpg){ width="50%" }
<figcaption>Collegare i conduttori NMEA 2000 al connettore come mostrato.</figcaption>
</figure>

Se non si intende collegare HALMET a una rete NMEA 2000, utilizzare lo stesso connettore collegando i conduttori solo alle posizioni `-` e `+`. È possibile utilizzare qualsiasi sorgente di alimentazione da 5–32 V. L’assorbimento di corrente tipico della scheda con il WiFi attivo è di 0,07 A a 12 V.

<figure markdown="span">
![](power_connector.jpg){ width="50%" }
<figcaption>Collegare i conduttori di alimentazione al connettore come mostrato.</figcaption>
</figure>

## Custodie

Per l’uso su un’imbarcazione, HALMET va sempre collocato in una custodia impermeabile.
La scheda è progettata per adattarsi alla [custodia SH-ESP32](https://shop.hatlabs.fi/products/sh-esp32-enclosure). Di seguito un esempio di scheda HALMET installata nella custodia.

<figure markdown="span">
![](halmet_small_enclosure.jpg){ width="50%" }
<figcaption>HALMET installato nella custodia SH-ESP32.</figcaption>
</figure>

La custodia SH-ESP32 offre uno spazio limitato per i connettori.
Ciascuno dei lati lunghi può ospitare in pratica solo 2–3 connettori da pannello.
Se si intende collegare più di qualche ingresso, è consigliabile una custodia più grande.
Per esempio la [custodia compatta SH-RPi](https://shop.hatlabs.fi/products/compact-weatherproof-enclosure-for-raspberry-pi-and-sh-rpi-158x90x60-mm) di Hat Labs, mostrata di seguito, offre già ampio spazio per i connettori.

<figure markdown="span">
![](medium_enclosure.jpg){ width="50%" }
<figcaption>La custodia compatta SH-RPi offre più spazio per la disposizione dei connettori da pannello.</figcaption>
</figure>


Altre custodie impermeabili adatte si trovano facilmente in qualsiasi negozio online. Anche le cassette di derivazione da esterno di dimensioni maggiori sono adatte allo scopo.

### Foratura per i connettori da pannello

Le custodie di solito non hanno fori predisposti. Per praticare i fori,
utilizzare sempre una punta conica o una punta a gradini (quella che sembra un piccolo albero di Natale metallico). Le normali punte per metallo tendono a mordere troppo e possono incrinare la parete della custodia.

Nel pianificare la disposizione dei fori e dei connettori, lasciare spazio sufficiente per serrare i dadi dei connettori e per il corpo del connettore. Se si prevede il montaggio a parete della custodia, è consigliabile orientare i connettori verso il basso per ridurre al minimo la possibilità di infiltrazioni d’acqua.

Diametri dei fori adatti ai vari connettori:

- Pressacavo PG7 e connettore da pannello M12 (NMEA 2000): 12,5 mm o 1/2"
- Connettori da pannello SP13 (connettori di plastica blu e nera): 13 mm
- Pressacavo PG9: 16 mm o 5/8"

I passacavi in gomma o in silicone consentono densità di cablaggio molto più elevate rispetto ai connettori da pannello o ai pressacavi. Non sono però impermeabili quanto i connettori da pannello o i pressacavi. Richiedono inoltre un fissaggio permanente del cavo, il che può rendere
più difficile la manutenzione dell’impianto.

TODO: Aggiungere una foto di un passacavo in gomma.

### Saldatura dei connettori da pannello

Quando si saldano i conduttori interni ai connettori da pannello, utilizzare sempre la guaina termorestringente sui singoli conduttori.
Ricordare sempre di infilare la guaina sui conduttori _prima_ di saldare...
Di solito conviene depositare prima lo stagno nella cavità del pin del connettore, poi rifondere lo stagno e inserire il conduttore.
