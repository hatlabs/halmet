---
title: Introduzione
translated_from: 2ad10049c9c3d0b5f6fb78356500eaa25670febd
---

# Introduzione

HALMET, la Hat Labs Marine Engine & Tank interface, è una scheda di sviluppo per collegare sensori di motore e di serbatoio su imbarcazioni e altri veicoli. Può essere utilizzato per leggere sensori digitali e analogici e per collegarsi ad altri dispositivi tramite le interfacce NMEA 2000, WiFi, Bluetooth, I2C, 1-Wire o GPIO.

<figure markdown="span">
![](halmet_v1_top_photo.jpg){ width="60%" }
<figcaption>Immagine di HALMET</figcaption>
</figure>

## Caratteristiche principali

- **Quattro ingressi digitali**: HALMET ha quattro ingressi digitali per leggere segnali di allarme digitali o per l’impiego come contatori. Gli ingressi tollerano tensioni comprese tra −32 V e +32 V. Gli ingressi digitali permettono di rilevare sia i livelli del segnale sia segnali variabili nel tempo, come il regime del motore, la portata del carburante o gli impulsi del contacatena.

- **Quattro ingressi analogici**: HALMET ha quattro ingressi analogici per la lettura di sensori analogici. Gli ingressi tollerano tensioni comprese tra −32 V e +32 V, con un intervallo di misura da 0 a 32 V. Gli ingressi sono collegati a un convertitore analogico-digitale (ADC) ADS1115 a 16 bit. Gli ingressi analogici possono essere utilizzati sia per misure passive di tensione sia per misure attive di resistenza.

- **Compatibile con NMEA 2000**: HALMET è pienamente compatibile con lo standard NMEA 2000. La scheda può essere collegata a una rete NMEA 2000 attraverso l’interfaccia NMEA 2000 integrata.

- **Interfacce I2C, 1-Wire e GPIO**: HALMET dispone di un’interfaccia I2C a 4 pin, di un’interfaccia 1-Wire a 3 pin e di 13 porte di ingresso/uscita generiche (GPIO) libere.

- **Connettività WiFi e Bluetooth**: HALMET integra un modulo ESP32-WROOM-32E con connettività WiFi e Bluetooth. Queste permettono sia di collegarsi a reti WiFi esistenti sia di creare un access point WiFi per collegarsi direttamente alla scheda.

- **ESP32-WROOM-32E con 16 MB di memoria flash**: il modulo ESP32-WROOM-32E offre potenza di calcolo e memoria in abbondanza anche per le applicazioni più esigenti. I 16 MB di memoria flash permettono di memorizzare localmente grandi quantità di dati.

- **Ampio intervallo di tensione di ingresso**: HALMET può essere alimentato in sicurezza dall’impianto a 12 V o 24 V comunemente presente su veicoli e imbarcazioni. HALMET tollera tensioni di ingresso comprese tra 5 V e 32 V.

HALMET è hardware aperto, distribuito con licenza Creative Commons Attribution-ShareAlike 4.0 International.

## Come procurarsi l’hardware

Le schede HALMET si possono acquistare da [Hat Labs Oy](https://shop.hatlabs.fi). Tutti i file di progetto sono disponibili anche nel [repository GitHub dell’hardware HALMET](https://github.com/hatlabs/halmet-hardware/).
