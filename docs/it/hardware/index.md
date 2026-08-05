---
title: Descrizione dell’hardware
translated_from: 66f9306e0980490684ef1cb989b75a230f6600df
---

# Hardware

## Introduzione all’ESP32

HALMET è basato sul potente modulo microcontrollore ESP32-WROOM-32E. L’ESP32 è un microcontrollore dual-core con connettività WiFi e Bluetooth integrata. L’ESP32 è una scelta molto diffusa per le applicazioni IoT grazie al costo contenuto, al buon corredo di periferiche e alla facilità d’uso.

## Blocchi funzionali della scheda

Di seguito sono descritti i diversi blocchi funzionali della scheda.

<figure markdown="span">
![](HALMET-func.jpg){ width="60%" }
<figcaption>Blocchi funzionali dell’HALMET.</figcaption>
</figure>

1.  Ingresso NMEA 2000 e di alimentazione con relative protezioni. Il connettore
    NMEA 2000 dispone dei seguenti elementi di protezione:
    - Fusibile autoripristinante da 500 mA
    - Diodo di protezione contro l’inversione di polarità
    - Diodi TVS di protezione contro le sovratensioni e le scariche elettrostatiche (ESD)
    - Filtraggio dei disturbi a due stadi

2.  Alimentatore. Un alimentatore switching con corrente di uscita massima di 2 A.

3.  Transceiver CAN per NMEA 2000. I LED RX e TX forniscono un’indicazione visiva
    dell’attività del bus CAN.

4.  Interfacce I2C e 1-Wire per il collegamento di sensori aggiuntivi.

5.  Interfaccia utente. Un pulsante Reset, un pulsante Boot / pulsante generico, un
    LED rosso di alimentazione e un LED blu programmabile dall’utente.

6.  Interfaccia USB 2.0 per la programmazione e il debug.

7.  Modulo ESP32-WROOM-32E con WiFi e Bluetooth integrati. Il modulo montato sulla
    scheda HALMET dispone di 16 MB di memoria flash.

8.  Circuiti di isolamento galvanico per gli ingressi digitali e analogici.

9.  Ingressi analogici. La scheda dispone di quattro ingressi analogici con
    risoluzione a 16 bit e tensione di ingresso massima di 33 V. Ogni ingresso è
    dotato di protezione contro le sottotensioni e le sovratensioni e di un
    filtraggio passa-basso con frequenza di taglio a 160 Hz per ridurre i disturbi
    di misura.

    Gli ingressi analogici dispongono di un generatore di corrente costante (CCS)
    opzionale da 10 mA per la misura attiva di resistenza. Il generatore di corrente
    costante si abilita tramite i connettori a pettine per jumper CCS.

    In modalità di misura di resistenza, la resistenza massima misurabile è 320 Ω.

10. Ingressi digitali. HALMET dispone di quattro ingressi digitali con tensione di
    ingresso massima di ±30 V. Gli ingressi sono dotati di uno Schmitt trigger per
    migliorare l’immunità ai disturbi.


## Isolamento galvanico

La scheda presenta un isolamento galvanico tra gli ingressi digitali e analogici e
il microcontrollore ESP32. L’isolamento è realizzato con isolatori digitali,
rispettivamente per il bus I2C e per i quattro ingressi digitali, e con un
convertitore DC/DC isolato che alimenta la sezione isolata.

Grazie a questo isolamento, la scheda può essere alimentata dalla rete NMEA 2000
senza rischio di anelli di massa. L’isolamento protegge inoltre dai picchi di
tensione e dai disturbi presenti sugli ingressi.

<figure markdown="span">
![](HALMET-isolation.jpg){ width="60%" }
<figcaption>Barriera di isolamento dell’HALMET. I connettori di ingresso sono isolati dal resto
della scheda, ovvero non condividono una massa comune con il resto della scheda.</figcaption>
</figure>

## Connettori

<div class="row" markdown>
  <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-top.jpg){ width="100%" }
<figcaption>Connettori dell’HALMET, lato superiore.</figcaption>
</figure>

   </div>
   <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-bottom.jpg){ width="100%" }
<figcaption>Connettori dell’HALMET, lato inferiore.</figcaption>
</figure>

   </div>
</div>

### Connettori del lato superiore

1.  Connettore NMEA 2000. Si tratta di una morsettiera estraibile a 4 pin
    compatibile Phoenix MC 3,81. Il connettore serve a collegare la scheda a una
    rete NMEA 2000 e ad alimentarla.

2.  Connettore a pettine 1-Wire. Il pettine 1-Wire consente di collegare sensori
    1-Wire alla scheda. Il connettore è un pettine a 3 pin con passo 2,54 mm. Il
    pettine non è montato sulla scheda di serie, perché può interferire con il
    posizionamento dei connettori da pannello della custodia.

3.  Connettore a pettine I2C. Il pettine I2C consente di collegare sensori I2C alla
    scheda. Il connettore è un pettine a 4 pin con passo 2,54 mm.

4.  Connettore Micro USB. Il connettore serve per la programmazione e il debug della
    scheda.

5.  Piazzole libere per i segnali di reset (EN) e di boot (IO0).

6.  Connettore a pettine GPIO. Il pettine GPIO è un connettore a 2 × 10 pin con
    passo 2,54 mm. Il pettine rende disponibili i pin GPIO liberi dell’ESP32 e può
    essere usato anche come connettore JTAG.

7.  Connettore a pettine di alimentazione dell’area isolata. Il pettine consente di
    alimentare dispositivi esterni dai contatti 3V3 e GND della sezione isolata.

8.  Contatti del pettine per jumper del generatore di corrente costante (CCS) degli
    ingressi analogici. Il generatore di corrente costante si abilita
    cortocircuitando i contatti del jumper.

9.  Connettori degli ingressi analogici. I connettori sono morsettiere estraibili a
    2 pin compatibili Phoenix MC 3,81. Servono a collegare sensori analogici alla
    scheda.

10. Connettori degli ingressi digitali. I connettori sono morsettiere estraibili a
    2 pin compatibili Phoenix MC 3,81. Servono a collegare sensori digitali alla
    scheda.

### Connettori del lato inferiore

11.  Jumper a saldare della terminazione CAN. Chiudendo il jumper a saldare si
     abilita la resistenza di terminazione da 120 Ω del bus CAN. Non utilizzare la
     resistenza di terminazione con le reti NMEA 2000.

12.  Jumper a saldare del filtro passa-basso. Chiudendo il jumper a saldare si
     abilita un filtro passa-basso sul rispettivo ingresso analogico. Il filtro ha
     una frequenza di taglio di 2,3 kHz e può essere usato ad esempio per ridurre i
     disturbi in un segnale del contagiri.

13.  Jumper a saldare della resistenza di pull-down. Chiudendo il jumper a saldare si
     abilita una resistenza di pull-down da 100 kΩ sul rispettivo ingresso digitale.
     La resistenza di pull-down consente di leggere un interruttore normalmente
     aperto (NA) che alla chiusura viene portato a livello alto.

14.  Jumper a saldare della resistenza di pull-up. Chiudendo il jumper a saldare si
     abilita una resistenza di pull-up da 100 kΩ sul rispettivo ingresso digitale.
     La resistenza di pull-up consente di leggere un interruttore normalmente chiuso
     (NC) che alla chiusura viene portato a livello basso.

15.  Jumper a saldare per la selezione dell’indirizzo I2C dell’ADS1115. Chiudendo i
     jumper a saldare si seleziona l’indirizzo I2C del convertitore
     analogico-digitale (ADC) ADS1115. Servono a evitare conflitti di indirizzo
     quando allo stesso bus I2C sono collegati più ADC ADS1115. Le piazzole possono
     essere usate anche per collegare ulteriori dispositivi I2C all’area isolata
     della scheda.

### Riferimento GPIO

HALMET riserva alcuni pin GPIO per le periferiche di ingresso. I pin GPIO liberi sono
portati sul pettine GPIO a 2 × 10 pin. La tabella seguente elenca i pin GPIO e le
rispettive funzioni.

|    GPIO | Funzione     | Note                                                    |
| ------: | :----------- | :------------------------------------------------------ |
|       0 | Pulsante Boot | Entra nel bootloader quando è portato a livello basso  |
|       1 | TXD0         | Trasmissione dati verso USB                             |
|       2 | LED          | LED rosso sulla scheda                                  |
|       3 | RXD0         | Ricezione dati da USB                                   |
|       4 | 1-Wire DQ    | Linea dati 1-Wire                                       |
|       5 | -            | Disponibile sul pettine GPIO                            |
|      12 | - / TDI      | Disponibile sul pettine GPIO. In alternativa: JTAG TDI  |
|      13 | - / TCK      | Disponibile sul pettine GPIO. In alternativa: JTAG TCK  |
|      14 | - / TMS      | Disponibile sul pettine GPIO. In alternativa: JTAG TMS  |
|      15 | - / TDO      | Disponibile sul pettine GPIO. In alternativa: JTAG TDO  |
|      16 | -            | Disponibile sul pettine GPIO                            |
|      17 | -            | Disponibile sul pettine GPIO                            |
|      18 | CAN RX       | Ricezione da NMEA 2000                                  |
|      19 | CAN TX       | Trasmissione verso NMEA 2000                            |
|      21 | I2C SDA      | Linea dati I2C. Usata per gli ingressi analogici        |
|      22 | I2C SCL      | Linea di clock I2C. Usata per gli ingressi analogici    |
|      23 | DI1          | Ingresso digitale 1                                     |
|      25 | DI2          | Ingresso digitale 2                                     |
|      27 | DI3          | Ingresso digitale 3                                     |
|      26 | DI4          | Ingresso digitale 4                                     |
|      32 | -            | Disponibile sul pettine GPIO                            |
|      33 | -            | Disponibile sul pettine GPIO                            |
|      34 | -            | Disponibile sul pettine GPIO                            |
|      35 | -            | Disponibile sul pettine GPIO                            |
| 36 (VP) | Solo ingresso | Disponibile sul pettine GPIO                           |
| 39 (VN) | Solo ingresso | Disponibile sul pettine GPIO                           |


## Alimentazione

L’intervallo di tensione di ingresso ammesso sulla scheda è 5–32 V. L’assorbimento
di corrente tipico è di 90 mA a 12 V con il modulo WiFi attivo (corrisponde a 1,1 W).

## NMEA 2000

NMEA 2000 è uno standard di comunicazione diffusissimo, usato per collegare sensori, dispositivi di controllo e display su imbarcazioni e navi. Si basa sul Controller Area Network (bus CAN), uno standard di bus per veicoli progettato per consentire ai dispositivi di comunicare tra loro senza un computer host.

La scheda è conforme allo standard NMEA 2000 finché nessuno dei connettori non
isolati è collegato ad altri dispositivi riferiti a massa. Ad esempio, è possibile
utilizzare un sensore di temperatura 1-Wire con un cavo lungo, poiché non condivide
una massa comune con altri dispositivi. Collegare invece un convertitore
analogico-digitale I2C al connettore I2C non isolato farebbe decadere la conformità
NMEA 2000.

TODO: piedinatura GPIO di NMEA 2000

## LED di stato

Sulla scheda HALMET sono presenti due pulsanti e due LED. I due pulsanti sono contrassegnati con “Reset” e “Boot”. Il pulsante Reset riavvia la scheda portando a livello basso il pin Enable dell’ESP32. Il pulsante Boot è collegato a GPIO0 e, durante l’accensione del dispositivo, consente di forzare il modulo in modalità download. Negli altri casi può essere usato come normale ingresso a pulsante.

I due LED non sono contrassegnati esplicitamente. Il LED rosso è acceso ogni volta che sulla scheda è presente l’alimentazione a 3,3 V. Il LED blu è collegato a GPIO2 (il pin comunemente usato per il LED sulle schede di sviluppo ESP32). Può essere controllato dai programmi dell’utente per segnalare lo stato del dispositivo.

## 1-Wire

1-Wire è un sistema di bus per la comunicazione tra dispositivi progettato da Dallas Semiconductor, poi acquisita da Maxim Integrated Products. Sebbene 1-Wire sia un protocollo lento, che supporta velocità fino a soli 16,3 kbit/s, è molto semplice da implementare e può essere usato su lunghe distanze. È comunemente impiegato per sensori di temperatura e altri dispositivi di rilevamento altrettanto semplici.

L’implementazione 1-Wire dell’HALMET dispone di filtraggio ESD e dei disturbi RF, oltre a un filtraggio passa-basso, per migliorare l’affidabilità della rete.

Si noti che il pin dati 1-Wire (contrassegnato con “DQ”) è fisicamente mappato su GPIO4: nel proprio programma occorre quindi usare GPIO4 per tutti i dati 1-Wire.

## I2C

I2C (Inter-Integrated Circuit) è un bus di comunicazione seriale sincrono molto diffuso, comunemente usato per interfacciarsi con numerosi circuiti integrati diversi. Utilizza due conduttori dati oltre all’alimentazione e alla massa.

HALMET utilizza il bus I2C internamente per il convertitore analogico-digitale ADS1115. Il bus I2C è portato anche su un pettine a 4 pin per il collegamento di ulteriori dispositivi I2C.

Il bus I2C è collegato a GPIO21 (SDA) e GPIO22 (SCL) dell’ESP32. Questi sono i pin I2C predefiniti nell’ambiente Arduino ESP32, ma sono diversi dai pin predefiniti di SH-ESP32.
