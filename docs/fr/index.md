---
title: Introduction
translated_from: 864a9f606fb309bc3e706c3231d0ec7208b25eed
---

# Introduction

HALMET, la Hat Labs Marine Engine & Tank interface, est une carte de développement destinée au raccordement des capteurs moteur et de réservoir sur les bateaux et autres véhicules. Elle permet de lire des capteurs numériques et analogiques, ainsi que de communiquer avec d'autres appareils via les interfaces NMEA 2000, WiFi, Bluetooth, I2C, 1-Wire ou GPIO.

<figure markdown="span">
![](halmet_v1_top_photo.jpg){ width="60%" }
<figcaption>Photo de HALMET</figcaption>
</figure>

## Principales caractéristiques

- **Quatre entrées numériques** : HALMET dispose de quatre entrées numériques pour lire des signaux d'alarme numériques ou pour servir de compteurs. Les entrées supportent des tensions comprises entre −32 V et +32 V. Les entrées numériques permettent aussi bien de détecter des niveaux de signal que des signaux variables dans le temps, comme le régime moteur, le débit de carburant ou les impulsions d'un compteur de chaîne.

- **Quatre entrées analogiques** : HALMET dispose de quatre entrées analogiques pour lire des capteurs analogiques. Les entrées supportent des tensions comprises entre −32 V et +32 V, avec une plage de mesure de 0 à 33 V. Elles sont reliées à un convertisseur analogique-numérique ADS1115 de 16 bits. Les entrées analogiques permettent aussi bien la mesure passive de tension que la mesure active de résistance.

- **Compatible NMEA 2000** : HALMET est entièrement compatible avec la norme NMEA 2000. La carte peut être raccordée à un réseau NMEA 2000 par l'interface NMEA 2000 intégrée.

- **Interfaces I2C, 1-Wire et GPIO** : HALMET possède une interface I2C à 4 broches, une interface 1-Wire à 3 broches et 13 ports d'entrée/sortie à usage général (GPIO) disponibles.

- **Connectivité WiFi et Bluetooth** : HALMET intègre un module ESP32-WROOM-32E doté de la connectivité WiFi et Bluetooth. Celle-ci permet aussi bien de se connecter à des réseaux WiFi existants que de créer un point d'accès WiFi pour se connecter directement à la carte.

- **ESP32-WROOM-32E avec 16 Mo de flash** : le module ESP32-WROOM-32E offre une puissance de calcul et une mémoire largement suffisantes, même pour les applications les plus exigeantes. Les 16 Mo de flash permettent de stocker localement de grandes quantités de données.

- **Large plage de tension d'entrée** : HALMET peut être alimenté en toute sécurité par le réseau 12 V ou 24 V couramment utilisé sur les véhicules et les bateaux. HALMET supporte des tensions d'entrée comprises entre 5 V et 32 V.

HALMET est du matériel libre (open hardware), sous licence Creative Commons Attribution-ShareAlike 4.0 International.

## Se procurer le matériel

Vous pouvez acheter des cartes HALMET auprès de [Hat Labs Oy](https://shop.hatlabs.fi). Tous les fichiers de conception sont également disponibles dans le [dépôt GitHub du matériel HALMET](https://github.com/hatlabs/halmet-hardware/).
