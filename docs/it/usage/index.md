---
title: Utilizzo
translated_from: 62b94ac6364a19f44074c56bd610d243063e9847
---

# Utilizzo

## Casi d’uso comuni

Questa sezione contiene informazioni pratiche sulla lettura di diversi tipi di sensori e sul collegamento di HALMET ad altri dispositivi.

### Configurazione del software

HALMET è una scheda di sviluppo e non viene fornito con alcun software preinstallato.
Il software adatto va installato dall’utente. L’operazione non è difficile, ma è consigliabile una certa esperienza con schede a microcontrollore come Arduino o ESP32 Devkit.

La documentazione di HALMET presuppone l’utilizzo del [firmware di esempio per HALMET](https://github.com/hatlabs/HALMET-example-firmware). Questo firmware è basato sul framework [SensESP](https://signalk.org/SensESP/) e offre un accesso relativamente immediato alle funzioni della scheda.

La [guida introduttiva di SensESP](https://signalk.org/SensESP/pages/getting_started/) contiene istruzioni dettagliate per installare l’ambiente di sviluppo necessario a compilare e installare il firmware. Le istruzioni sono scritte per dispositivi ESP32 generici, ma valgono anche per HALMET. È sufficiente utilizzare il [firmware di esempio per HALMET](https://github.com/hatlabs/HALMET-example-firmware) al posto del modello di progetto SensESP.

Si noti che, sebbene la documentazione di SensESP presupponga l’uso di Signal K, HALMET è perfettamente utilizzabile anche come dispositivo NMEA 2000 autonomo.

Se si preferisce non usare SensESP, è possibile realizzare un firmware personalizzato con Arduino IDE o ESP-IDF. Per molti casi d’uso anche ESPHome è un’ottima soluzione.

**NOTA:** l’assegnazione dei pin GPIO su HALMET è leggermente diversa da quella dell’ESP32 Devkit e di SH-ESP32. Se si adatta un software diverso dal firmware di esempio per HALMET, occorre verificare con attenzione l’assegnazione dei pin. Per maggiori informazioni vedere il [riferimento GPIO](../hardware/index.md#riferimento-gpio).

### Uso degli ingressi digitali

HALMET ha quattro ingressi digitali. Questi ingressi possono essere utilizzati per leggere segnali di allarme digitali oppure come contatori. Questa sezione descrive l’uso degli ingressi nei diversi casi d’uso comuni. Le istruzioni presuppongono l’utilizzo del firmware di esempio per HALMET.

Gli ingressi digitali D1–D4 sono collegati rispettivamente ai pin GPIO 23, 25, 27 e 26. Gli ingressi tollerano tensioni comprese tra −32 V e +32 V. La tensione di soglia per il rilevamento di un segnale alto è di circa 1,55 V, con un’isteresi di circa 0,7 V.

### Collegamento ad allarmi digitali

Questa sezione descrive come collegare HALMET a diversi segnali di tipo on/off, come gli allarmi del motore o di sentina.

#### Configurazione dell’hardware

Di norma i vari segnali di tipo on/off, come gli allarmi del motore o di sentina, possono essere collegati direttamente agli ingressi digitali di HALMET. A seconda del tipo di segnale può essere necessario un pull-up o un pull-down.

Nella figura seguente, nell’esempio (a) è già presente una lampadina nel circuito. Quando l’interruttore è aperto, la lampadina porta a livello basso la tensione su D1. Non serve alcun pull-down aggiuntivo.[^1] Nell’esempio (b), invece, nel circuito non è presente nessun altro carico. Se l’interruttore è aperto, la tensione su D2 resta flottante e l’ingresso risulta casualmente alto o basso. In questo caso occorre abilitare la resistenza di pull-down interna chiudendo il jumper a saldare sul retro della scheda.

<figure markdown="span">
![](digin_pullup_pulldown.svg){ width="60%" }
<figcaption>Ingressi digitali in diversi casi d’uso. (a) Lampada già presente nel circuito. (b) Nessun altro carico nel circuito, l’interruttore porta il segnale a livello alto quando si chiude. (c) L’interruttore porta il segnale a livello basso quando si chiude.</figcaption>
</figure>

[^1]: Se le luci del quadro sono realizzate con LED, la caduta di tensione ai capi dei LED può non bastare a portare la tensione a un livello sufficientemente basso. In questo caso occorre abilitare la resistenza di pull-down.

<figure markdown="span">
![](solder_jumpers.jpg){ width="60%" }
<figcaption>I jumper a saldare sul retro della scheda possono essere chiusi per abilitare le resistenze di pull-up o di pull-down integrate.</figcaption>
</figure>

Analogamente, se l’interruttore porta il segnale a livello basso quando si chiude, come nell’esempio (c), può essere necessario abilitare il pull-up interno.

Infine, se gli interruttori di allarme sono normalmente chiusi (NC), il trattamento si inverte. Quando l’interruttore si apre, la tensione di ingresso viene portata a livello alto o basso a seconda del circuito. In questo caso può essere necessario abilitare il pull-up o il pull-down interno.

#### Configurazione del software

Il firmware di esempio per HALMET mette a disposizione il metodo di comodo `ConnectAlarmSender()` per configurare e collegare gli ingressi digitali. Vedere `main.cpp` a partire dalla riga 177. Sono supportati sia i segnali attivi alti sia quelli attivi bassi.

### Ingressi digitali come contatori

Gli ingressi digitali di HALMET possono essere utilizzati anche come contatori. Questo è utile, per esempio, per contare i giri del motore o gli impulsi del contacatena.

#### Configurazione dell’hardware

Di norma queste sonde sono pilotate attivamente in entrambe le direzioni, quindi non serve alcun pull-up o pull-down. Se si collega HALMET a un’uscita a bassa impedenza come il morsetto W dell’alternatore, è consigliabile aggiungere un fusibile in linea per proteggere il conduttore da cortocircuiti dovuti a sfregamento o ad altri danni. A parte questo, la sonda può essere collegata direttamente all’ingresso digitale.

Se la sorgente di impulsi è molto disturbata e il numero di giri risulta instabile, è possibile abilitare un filtro passa-basso chiudendo il jumper a saldare LP sul retro della scheda. Il filtro passa-basso ha una frequenza di taglio di circa 2,3 kHz, adatta ad applicazioni come gli ingressi collegati al morsetto W dell’alternatore.

#### Configurazione del software

Il firmware di esempio per HALMET implementa un contatore di impulsi che può essere attivato su uno qualsiasi degli ingressi digitali o su tutti. Vedere la configurazione di esempio in `main.cpp` a partire dalla riga 214.

### Uso degli ingressi analogici

HALMET ha quattro ingressi analogici, utilizzabili sia per misure passive di tensione sia per misure attive di resistenza. Questa sezione descrive l’uso degli ingressi nei diversi casi d’uso comuni.

#### Configurazione dell’hardware

Gli ingressi analogici A1–A4 sono collegati a un convertitore analogico-digitale (ADC) ADS1115. L’ADS1115 ha una risoluzione a 16 bit e una frequenza di campionamento massima di 860 campioni al secondo. Gli ingressi analogici di HALMET integrano però un filtro passa-basso molto marcato, con una frequenza di taglio di circa 160 Hz. Questo resta comunque più che sufficiente per misurare le uscite di sensori fisici come i sensori di livello del serbatoio o i sensori di pressione del motore.

Nella figura seguente, l’esempio (a) mostra un indicatore del quadro motore già presente, collegato a una sonda resistiva. Gli indicatori del quadro motore sono di solito di tipo termostatico o magnetico. In entrambi i casi l’indicatore e la sonda funzionano da partitore di tensione, e la tensione ai capi della sonda è proporzionale alla grandezza misurata. Questa tensione può essere misurata con gli ingressi analogici di HALMET senza interferire con il funzionamento dell’indicatore originale. A causa del partitore di tensione la tensione può non essere correlata linearmente alla grandezza misurata, ma è possibile compensare via software.

<figure markdown="span">
![](analog_input.svg){ width="60%" }
<figcaption>Collegamento degli ingressi analogici con e senza un indicatore già presente. (a) Con un indicatore già presente, utilizzare HALMET in modalità di misura passiva di tensione. (b) Se non è presente nessun altro dispositivo, utilizzare HALMET in modalità di misura attiva di resistenza.</figcaption>
</figure>


L’esempio (b) mostra un caso in cui l’indicatore non è presente. La sonda è collegata direttamente all’ingresso analogico di HALMET. In questo caso HALMET deve fornire la tensione di eccitazione alla sonda. HALMET realizza la misura di resistenza con un generatore di corrente costante (CCS) da 10 mA. La corrente di 10 mA produce una differenza di tensione di 1 volt ai capi di una resistenza da 100 Ω, per una resistenza massima di circa 300 Ω. Il generatore di corrente costante si abilita inserendo un jumper sulla coppia di pin del connettore a pettine CCS (generatore di corrente costante). Vedere la figura seguente.

<figure markdown="span">
![](ccs_jumpers.jpg){ width="60%" }
<figcaption>La figura mostra il generatore di corrente costante abilitato per gli ingressi analogici A2 e A4.</figcaption>
</figure>
