---
title: Description du matériel
translated_from: 96f96c3aff8d2a33ab2f1b59c0dbb8747c8ed3e2
---

# Matériel

## Présentation de l'ESP32

HALMET repose sur le puissant module microcontrôleur ESP32-WROOM-32E. L'ESP32 est un microcontrôleur double cœur doté d'une connectivité WiFi et Bluetooth intégrée. L'ESP32 est un choix répandu pour les applications IoT grâce à son faible coût, à son bon ensemble de périphériques et à sa simplicité d'utilisation.

## Blocs fonctionnels de la carte

Les différents blocs fonctionnels de la carte sont décrits ci-dessous.

<figure markdown="span">
![](HALMET-func.jpg){ width="60%" }
<figcaption>Blocs fonctionnels de la carte HALMET.</figcaption>
</figure>

1.  Entrée NMEA 2000 et alimentation, avec leurs protections. Le connecteur
    NMEA 2000 comporte les éléments de protection suivants :
    - Fusible réarmable de 500 mA
    - Diode de protection contre l'inversion de polarité
    - Diodes TVS de protection contre les surtensions et les décharges électrostatiques (ESD)
    - Filtrage du bruit à deux étages

2.  Alimentation. Une alimentation à découpage dont le courant de sortie maximal est de 2 A.

3.  Émetteur-récepteur CAN pour NMEA 2000. Des LED RX et TX indiquent
    visuellement l'activité du bus CAN.

4.  Interfaces I2C et 1-Wire pour raccorder des capteurs supplémentaires.

5.  Interface utilisateur. Un bouton Reset (réinitialisation), un bouton Boot
    servant aussi de bouton à usage général, une LED d'alimentation rouge et une LED bleue programmable par l'utilisateur.

6.  Interface USB 2.0 pour la programmation et le débogage.

7.  Module ESP32-WROOM-32E avec WiFi et Bluetooth intégrés. Le module monté sur la carte
    HALMET dispose de 16 Mo de mémoire flash.

8.  Circuits d'isolation galvanique des entrées numériques et analogiques.

9.  Entrées analogiques. La carte comporte quatre entrées analogiques d'une résolution de
    16 bits et d'une tension d'entrée maximale de 33 V. Chaque entrée dispose d'une protection
    contre les sous-tensions et les surtensions, ainsi que d'un filtrage passe-bas dont la
    fréquence de coupure est de 160 Hz, afin de réduire le bruit de mesure.

    Les entrées analogiques disposent en option d'une source de courant constant (CCS) de
    10 mA pour la mesure active de résistance. La source de courant constant s'active à
    l'aide des connecteurs à cavalier CCS.

    En mode de mesure de résistance, la résistance maximale mesurable est de 300 Ω.

10. Entrées numériques. HALMET comporte quatre entrées numériques dont la tension d'entrée
    maximale est de ±32 V. Les entrées intègrent un Schmitt trigger pour améliorer l'immunité au bruit.


## Isolation galvanique

La carte assure une isolation galvanique entre les entrées numériques et analogiques
d'une part et le microcontrôleur ESP32 d'autre part. L'isolation repose sur des
isolateurs numériques, respectivement pour l'I2C et pour les quatre entrées numériques,
ainsi que sur un convertisseur DC/DC isolé qui alimente la partie isolée.

Grâce à cette isolation, la carte peut être alimentée par le réseau NMEA 2000 sans
risque de boucles de masse. L'isolation protège également des pics de tension et du
bruit sur les entrées.

<figure markdown="span">
![](HALMET-isolation.jpg){ width="60%" }
<figcaption>Barrière d'isolation de la carte HALMET. Les connecteurs d'entrée sont isolés du reste
de la carte : ils ne partagent donc pas de masse commune avec elle.</figcaption>
</figure>

## Connecteurs

<div class="row" markdown>
  <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-top.jpg){ width="100%" }
<figcaption>Connecteurs de la carte HALMET, face supérieure.</figcaption>
</figure>

   </div>
   <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-bottom.jpg){ width="100%" }
<figcaption>Connecteurs de la carte HALMET, face inférieure.</figcaption>
</figure>

   </div>
</div>

### Connecteurs de la face supérieure

1.  Connecteur NMEA 2000. Il s'agit d'un bornier débrochable à 4 broches compatible
    Phoenix MC 3.81. Il sert à raccorder la carte à un réseau NMEA 2000 et à
    l'alimenter.

2.  Connecteur 1-Wire. Le connecteur 1-Wire permet de raccorder des capteurs 1-Wire à
    la carte. Il s'agit d'un connecteur à 3 broches au pas de 2,54 mm. Il n'est pas
    monté sur la carte par défaut, car il peut gêner l'emplacement des connecteurs de
    panneau du boîtier.

3.  Connecteur I2C. Le connecteur I2C permet de raccorder des capteurs I2C à la carte.
    Il s'agit d'un connecteur à 4 broches au pas de 2,54 mm.

4.  Connecteur Micro USB. Il sert à la programmation et au débogage de la carte.

5.  Pastilles non implantées pour les signaux Reset (EN) et Boot (IO0).

6.  Connecteur GPIO. Il s'agit d'un connecteur à 2×10 broches au pas de 2,54 mm. Il rend
    accessibles les broches GPIO libres de l'ESP32 et peut aussi servir de connecteur JTAG.

7.  Connecteur d'alimentation de la zone isolée. Il permet d'alimenter des appareils
    externes depuis les broches 3V3 et GND de la partie isolée.

8.  Contacts du connecteur à cavalier de la source de courant constant (CCS) des entrées
    analogiques. La source de courant constant s'active en court-circuitant les contacts
    du cavalier.

9.  Connecteurs des entrées analogiques. Ce sont des borniers débrochables à 2 broches
    compatibles Phoenix MC 3.81. Ils servent à raccorder des capteurs analogiques à la
    carte.

10. Connecteurs des entrées numériques. Ce sont des borniers débrochables à 2 broches
    compatibles Phoenix MC 3.81. Ils servent à raccorder des capteurs numériques à la
    carte.

### Connecteurs de la face inférieure

11.  Pont à souder de terminaison CAN. Le court-circuiter active la résistance de
     terminaison de 120 Ω du bus CAN. N'utilisez pas cette résistance de terminaison
     sur les réseaux NMEA 2000.

12.  Pont à souder du filtre passe-bas. Le court-circuiter active un filtre passe-bas
     sur l'entrée analogique correspondante. La fréquence de coupure du filtre est de
     2,3 kHz. Ce filtre permet par exemple de réduire le bruit d'un signal de
     compte-tours.

13.  Pont à souder de la résistance de tirage vers le bas (pull-down). Le court-circuiter
     active une résistance de tirage vers le bas de 100 kΩ sur l'entrée numérique
     correspondante. Cette résistance permet de lire un interrupteur normalement ouvert
     qui met l'entrée à l'état haut lorsqu'il se ferme.

14.  Pont à souder de la résistance de tirage vers le haut (pull-up). Le court-circuiter
     active une résistance de tirage vers le haut de 100 kΩ sur l'entrée numérique
     correspondante. Cette résistance permet de lire un interrupteur normalement fermé
     qui met l'entrée à l'état bas lorsqu'il se ferme.

15.  Ponts à souder de sélection de l'adresse I2C de l'ADS1115. Les court-circuiter permet
     de choisir l'adresse I2C du convertisseur analogique-numérique ADS1115. Ils servent à
     éviter les conflits d'adresses lorsque plusieurs convertisseurs ADS1115 sont raccordés
     au même bus I2C. Ces pastilles peuvent aussi servir à raccorder d'autres appareils I2C
     à la zone isolée de la carte.

### Référence GPIO

HALMET réserve un certain nombre de broches GPIO aux périphériques d'entrée. Les broches
GPIO libres sont rendues accessibles sur le connecteur GPIO à 2×10 broches. Le tableau
suivant récapitule les broches GPIO et leurs fonctions.

|    GPIO | Fonction    | Remarques                                          |
| ------: | :---------- | :------------------------------------------------- |
|       0 | Bouton Boot | Entre dans le bootloader à l'état bas              |
|       1 | TXD0        | Émission de données vers l'USB                     |
|       2 | LED         | LED rouge de la carte                              |
|       3 | RXD0        | Réception de données depuis l'USB                  |
|       4 | 1-Wire DQ   | Ligne de données 1-Wire                            |
|       5 | -           | Disponible sur le connecteur GPIO                  |
|      12 | - / TDI     | Disponible sur le connecteur GPIO. En option : JTAG TDI |
|      13 | - / TCK     | Disponible sur le connecteur GPIO. En option : JTAG TCK |
|      14 | - / TMS     | Disponible sur le connecteur GPIO. En option : JTAG TMS |
|      15 | - / TDO     | Disponible sur le connecteur GPIO. En option : JTAG TDO |
|      16 | -           | Disponible sur le connecteur GPIO                  |
|      17 | -           | Disponible sur le connecteur GPIO                  |
|      18 | CAN RX      | Réception depuis NMEA 2000                         |
|      19 | CAN TX      | Émission vers NMEA 2000                            |
|      21 | I2C SDA     | Ligne de données I2C. Utilisée pour l'entrée analogique |
|      22 | I2C SCL     | Ligne d'horloge I2C. Utilisée pour les entrées analogiques |
|      23 | DI1         | Entrée numérique 1                                 |
|      25 | DI2         | Entrée numérique 2                                 |
|      27 | DI3         | Entrée numérique 3                                 |
|      26 | DI4         | Entrée numérique 4                                 |
|      32 | -           | Disponible sur le connecteur GPIO                  |
|      33 | -           | Disponible sur le connecteur GPIO                  |
|      34 | -           | Disponible sur le connecteur GPIO                  |
|      35 | -           | Disponible sur le connecteur GPIO                  |
| 36 (VP) | Entrée seule | Disponible sur le connecteur GPIO                 |
| 39 (VN) | Entrée seule | Disponible sur le connecteur GPIO                 |


## Alimentation

La plage de tension d'entrée admissible de la carte est de 5–32 V. La consommation de
courant typique est de 90 mA sous 12 V avec le module WiFi actif (soit 1,1 W).

## NMEA 2000

NMEA 2000 est un standard de communication omniprésent, utilisé pour relier capteurs, organes de commande et afficheurs à bord des bateaux et des navires. Il repose sur le bus CAN (Controller Area Network), un standard de bus pour véhicules conçu pour permettre aux appareils de communiquer entre eux sans ordinateur hôte.

La carte est conforme au standard NMEA 2000 tant qu'aucun des connecteurs non isolés
n'est raccordé à d'autres appareils référencés à la masse. Un capteur de température
1-Wire à câble long peut par exemple être utilisé, car il ne partage pas de masse commune
avec les autres appareils. En revanche, raccorder un convertisseur analogique-numérique
I2C au connecteur I2C non isolé romprait la conformité NMEA 2000.

TODO : brochage GPIO NMEA 2000

## LED d'état

La carte HALMET comporte deux boutons et deux LED. Les deux boutons portent les marquages Reset et Boot. Le bouton Reset redémarre la carte en mettant à l'état bas la broche Enable de l'ESP32. Le bouton Boot est relié à GPIO0 et permet, pendant le démarrage de l'appareil, de forcer le module en mode de téléchargement. Le reste du temps, il peut servir d'entrée bouton ordinaire.

Les deux LED ne portent pas de marquage. La LED rouge est allumée dès que la carte est alimentée en 3,3 V. La LED bleue est reliée à GPIO2 (la broche habituellement utilisée pour la LED sur les cartes de développement ESP32). Les programmes de l'utilisateur peuvent la commander pour indiquer l'état de l'appareil.

## 1-Wire

1-Wire est un système de bus de communication entre appareils, conçu par Dallas Semiconductor, société depuis rachetée par Maxim Integrated Products. Bien que 1-Wire soit un protocole lent, limité à 16,3 kbit/s, il est très simple à mettre en œuvre et fonctionne sur de longues distances. Il est couramment utilisé pour les capteurs de température et d'autres dispositifs de mesure simples.

L'implémentation 1-Wire de la carte HALMET comporte un filtrage des perturbations ESD et RF ainsi qu'un filtrage passe-bas, afin d'améliorer la fiabilité du réseau.

Notez que la broche de données 1-Wire (marquée « DQ ») est physiquement reliée à GPIO4 : dans votre programme, utilisez donc GPIO4 pour toutes les données 1-Wire.

## I2C

I2C (Inter-Integrated Circuit) est un bus de communication série synchrone très répandu, couramment utilisé pour dialoguer avec toutes sortes de circuits intégrés. Il utilise deux fils de données, en plus de l'alimentation et de la masse.

HALMET utilise l'I2C en interne pour le convertisseur analogique-numérique ADS1115. Le bus I2C est également rendu accessible sur un connecteur à 4 broches, pour raccorder d'autres appareils I2C.

Le bus I2C est relié à GPIO21 (SDA) et GPIO22 (SCL) sur l'ESP32. Ce sont les broches I2C par défaut de l'environnement Arduino ESP32, mais elles diffèrent des broches par défaut du SH-ESP32.
