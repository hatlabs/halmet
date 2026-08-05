---
title: Prise en main
translated_from: 75bcdba18bc044c04ce3e220067bf537e069ec82
---

# Prise en main

## Assemblage du matériel

Afin de permettre un placement plus souple des connecteurs dans les petits boîtiers, les cartes HALMET sont livrées sans les connecteurs 1-Wire ni GPIO. Si vous prévoyez d'utiliser l'une de ces interfaces, vous devrez souder le connecteur correspondant sur la carte.

Si vous avez besoin d'instructions pour souder des barrettes de broches sur la carte, consultez les [instructions d'assemblage](https://docs.hatlabs.fi/sh-esp32/pages/getting-started/#revision-1-boards) de la SH-ESP32.

## Alimentation de la carte

HALMET est alimenté par le connecteur NMEA 2000. Si vous prévoyez de raccorder HALMET à un réseau NMEA 2000, vous pouvez alimenter la carte directement depuis le réseau. Dans ce cas, raccordez les fils NMEA 2000 au bornier débrochable à 4 broches comme le montre la figure suivante.

<figure markdown="span">
![](halmet_n2k_input.jpg){ width="50%" }
<figcaption>Raccordez les fils NMEA 2000 au connecteur comme indiqué.</figcaption>
</figure>

Si vous ne prévoyez pas de raccorder HALMET à un réseau NMEA 2000, utilisez le même connecteur mais ne câblez que les emplacements `-` et `+`. Toute source d'alimentation de 5–32 V convient. La consommation de courant typique de la carte, WiFi actif, est de 0,07 A sous 12 V.

<figure markdown="span">
![](power_connector.jpg){ width="50%" }
<figcaption>Raccordez les fils d'alimentation au connecteur comme indiqué.</figcaption>
</figure>

## Boîtiers

À bord d'un bateau, HALMET doit toujours être placé dans un boîtier étanche.
La carte est conçue pour s'adapter au [boîtier SH-ESP32](https://shop.hatlabs.fi/products/sh-esp32-enclosure). Voir ci-dessous un exemple de carte HALMET installée dans le boîtier.

<figure markdown="span">
![](halmet_small_enclosure.jpg){ width="50%" }
<figcaption>HALMET installé dans le boîtier SH-ESP32.</figcaption>
</figure>

Le boîtier SH-ESP32 offre peu de place pour les connecteurs.
Chacun des grands côtés ne peut accueillir en pratique que 2–3 connecteurs de panneau.
Si vous comptez raccorder plus de quelques entrées, un boîtier plus grand est recommandé.
Par exemple, le [boîtier compact SH-RPi](https://shop.hatlabs.fi/products/compact-weatherproof-enclosure-for-raspberry-pi-and-sh-rpi-158x90x60-mm) de Hat Labs, illustré ci-dessous, dispose déjà d'une place largement suffisante pour les connecteurs.

<figure markdown="span">
![](medium_enclosure.jpg){ width="50%" }
<figcaption>le boîtier compact SH-RPi offre plus de place pour l'implantation des connecteurs de panneau.</figcaption>
</figure>


D'autres boîtiers étanches adaptés se trouvent facilement sur n'importe quelle place de marché en ligne. Les grandes boîtes de dérivation d'extérieur conviennent également.

### Perçage des trous pour les connecteurs de panneau

Les boîtiers n'ont généralement pas de trous prépercés. Pour percer, utilisez toujours un foret conique ou un foret étagé (celui qui ressemble à un petit sapin de Noël métallique). Les forets à métaux ordinaires mordent facilement trop fort et peuvent fissurer la paroi du boîtier.

Lorsque vous planifiez l'emplacement des trous et des connecteurs, laissez suffisamment de place pour serrer les écrous des connecteurs et pour le corps du connecteur. Si vous prévoyez une fixation murale du boîtier, il est recommandé d'orienter les connecteurs vers le bas afin de limiter les risques d'infiltration d'eau.

Tailles de trous adaptées aux différents connecteurs :

- presse-étoupe PG7 et connecteur de panneau M12 (NMEA 2000) : 12,5 mm ou 1/2"
- connecteurs de panneau SP13 (connecteurs plastiques bleu-noir) : 13 mm
- presse-étoupe PG9 : 16 mm ou 5/8"

Les passe-fils en caoutchouc ou en silicone permettent des densités de câbles nettement plus élevées que les connecteurs de panneau ou les presse-étoupes. Ils ne sont toutefois pas aussi étanches que les connecteurs de panneau ou les presse-étoupes. De plus, ils exigent une fixation permanente du câble, ce qui peut compliquer l'entretien du système.

TODO : Ajouter une photo d'un passe-fil.

### Soudure des connecteurs de panneau

Lorsque vous soudez les fils internes aux connecteurs de panneau, utilisez toujours de la gaine thermorétractable sur chacun des fils.
Pensez toujours à enfiler la gaine thermorétractable sur les fils _avant_ de souder…
En général, vous pouvez d'abord déposer de la soudure dans la cavité de la broche du connecteur, puis refondre la soudure et y insérer le fil.
