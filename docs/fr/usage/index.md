---
title: Utilisation
translated_from: 62b94ac6364a19f44074c56bd610d243063e9847
---

# Utilisation

## Cas d'usage courants

Cette section rassemble des informations pratiques sur la lecture des différents types de capteurs et sur le raccordement de HALMET à d'autres appareils.

### Configuration logicielle

HALMET est une carte de développement et n'est livré avec aucun logiciel préinstallé.
Vous devrez installer vous-même un logiciel adapté. Ce n'est pas difficile, mais une certaine expérience préalable des cartes à microcontrôleur telles que les Arduino ou les ESP32 Devkit est recommandée.

La documentation de HALMET suppose l'utilisation du [firmware d'exemple HALMET](https://github.com/hatlabs/HALMET-example-firmware). Ce firmware repose sur le framework [SensESP](https://signalk.org/SensESP/) et donne un accès relativement simple aux fonctions de la carte.

Le [guide de démarrage SensESP](https://signalk.org/SensESP/pages/getting_started/) donne des instructions détaillées pour installer l'environnement de développement nécessaire à la compilation et à l'installation du firmware. Ces instructions sont écrites pour des appareils ESP32 génériques, mais elles s'appliquent aussi à HALMET. Utilisez simplement le [firmware d'exemple HALMET](https://github.com/hatlabs/HALMET-example-firmware) à la place du modèle de projet SensESP.

Notez que, même si la documentation SensESP suppose l'utilisation de Signal K, HALMET est également parfaitement utilisable comme appareil NMEA 2000 autonome.

Si vous préférez ne pas utiliser SensESP, vous pouvez aussi créer votre propre firmware avec l'Arduino IDE ou l'ESP-IDF. Pour de nombreux cas d'usage, ESPHome est également une excellente option.

**REMARQUE :** l'affectation des broches GPIO de HALMET diffère légèrement de celle de l'ESP32 Devkit et de celle de la SH-ESP32. Si vous adaptez un logiciel autre que le firmware d'exemple HALMET, vous devrez vérifier attentivement l'affectation des broches. Voir la [référence GPIO](../hardware/index.md#reference-gpio) pour plus d'informations.

### Utilisation des entrées numériques

HALMET possède quatre entrées numériques. Ces entrées permettent de lire des signaux d'alarme numériques ou de servir de compteurs. Cette section décrit leur utilisation dans différents cas d'usage courants. Les instructions supposent l'utilisation du firmware d'exemple HALMET.

Les entrées numériques D1–D4 sont reliées respectivement aux broches GPIO 23, 25, 27 et 26. Les entrées supportent des tensions comprises entre −32 V et +32 V. La tension de seuil de détection d'un niveau haut est d'environ 1,55 V, avec une hystérésis d'environ 0,7 V.

### Raccordement aux alarmes numériques

Cette section décrit comment raccorder HALMET à différents signaux de type tout ou rien, comme les alarmes moteur ou de cale.

#### Configuration matérielle

En général, les différents signaux de type tout ou rien, comme les alarmes moteur ou de cale, peuvent être raccordés directement aux entrées numériques de HALMET. Une résistance de tirage vers le haut (pull-up) ou vers le bas (pull-down) peut être nécessaire selon le type de signal.

Sur la figure ci-dessous, dans l'exemple (a), une ampoule est déjà présente dans le circuit. Lorsque l'interrupteur est ouvert, l'ampoule tire la tension de D1 vers le bas. Aucune résistance de tirage vers le bas supplémentaire n'est nécessaire.[^1] En revanche, dans l'exemple (b), aucune autre charge n'est présente dans le circuit. Si l'interrupteur est ouvert, la tension de D2 reste flottante et l'entrée sera aléatoirement haute ou basse. Dans ce cas, il faut activer la résistance interne de tirage vers le bas en fermant le pont à souder situé au dos de la carte.

<figure markdown="span">
![](digin_pullup_pulldown.svg){ width="60%" }
<figcaption>Entrées numériques dans différents cas d'usage. (a) Éclairage déjà présent dans le circuit. (b) Aucune autre charge dans le circuit, l'interrupteur tire le signal vers le haut lorsqu'il est fermé. (c) L'interrupteur tire le signal vers le bas lorsqu'il est fermé.</figcaption>
</figure>

[^1]: Si l'éclairage du tableau est réalisé avec des LED, la chute de tension aux bornes des LED peut ne pas suffire à faire descendre la tension à un niveau assez bas. Dans ce cas, il faut activer la résistance de tirage vers le bas.

<figure markdown="span">
![](solder_jumpers.jpg){ width="60%" }
<figcaption>Les ponts à souder situés au dos de la carte peuvent être fermés pour activer les résistances intégrées de tirage vers le haut ou vers le bas.</figcaption>
</figure>

De même, si l'interrupteur tire le signal vers le bas lorsqu'il est fermé, comme dans l'exemple (c), il peut être nécessaire d'activer la résistance interne de tirage vers le haut.

Enfin, si les interrupteurs d'alarme sont normalement fermés, le traitement est inversé. À l'ouverture de l'interrupteur, la tension d'entrée sera tirée vers le haut ou vers le bas selon le circuit. Dans ce cas, il peut être nécessaire d'activer la résistance interne de tirage vers le haut ou vers le bas.

#### Configuration logicielle

Le firmware d'exemple HALMET fournit une méthode utilitaire `ConnectAlarmSender()` pour configurer et raccorder les entrées numériques. Voir `main.cpp` à partir de la ligne 177. Les signaux actifs à l'état haut comme à l'état bas sont pris en charge.

### Entrées numériques utilisées comme compteurs

Les entrées numériques de HALMET peuvent aussi servir de compteurs. C'est utile par exemple pour compter les tours du moteur ou les impulsions d'un compteur de chaîne.

#### Configuration matérielle

Ces capteurs sont généralement pilotés activement dans les deux sens, si bien qu'aucune résistance de tirage vers le haut ou vers le bas n'est nécessaire. Si vous raccordez HALMET à une sortie de faible impédance telle que la borne W de l'alternateur, il est conseillé d'ajouter un fusible en ligne pour protéger le fil des courts-circuits dus au ragage ou à d'autres dommages. À part cela, vous pouvez raccorder le capteur directement à l'entrée numérique.

Si la source d'impulsions est très bruitée, ce qui fausse la lecture du régime moteur, un filtre passe-bas peut être activé en fermant le pont à souder LP situé au dos de la carte. Le filtre passe-bas a une fréquence de coupure d'environ 2,3 kHz, ce qui convient à des applications telles que les entrées reliées à la borne W d'un alternateur.

#### Configuration logicielle

Le firmware d'exemple HALMET met en œuvre un compteur d'impulsions activable sur une entrée numérique quelconque ou sur toutes. Voir l'exemple de configuration dans `main.cpp` à partir de la ligne 214.

### Utilisation des entrées analogiques

HALMET possède quatre entrées analogiques utilisables soit pour la mesure passive de tension, soit pour la mesure active de résistance. Cette section décrit leur utilisation dans différents cas d'usage courants.

#### Configuration matérielle

Les entrées analogiques A1–A4 sont reliées à un convertisseur analogique-numérique ADS1115. L'ADS1115 offre une résolution de 16 bits et une fréquence d'échantillonnage maximale de 860 échantillons par seconde. Les entrées analogiques de HALMET comportent toutefois un filtre passe-bas puissant dont la fréquence de coupure est d'environ 160 Hz. Cela reste largement suffisant pour mesurer la sortie de capteurs physiques tels que les capteurs de niveau de réservoir ou les capteurs de pression moteur.

Sur la figure ci-dessous, l'exemple (a) montre un indicateur du tableau moteur existant raccordé à un capteur résistif. Les indicateurs de tableau moteur sont généralement soit thermostatiques, soit magnétiques. Dans les deux cas, l'indicateur et le capteur forment un diviseur de tension, et la tension aux bornes du capteur est proportionnelle à la grandeur mesurée. Cette tension peut être mesurée par les entrées analogiques de HALMET sans perturber le fonctionnement de l'indicateur d'origine. Du fait du diviseur de tension, la tension peut ne pas être corrélée linéairement à la grandeur mesurée, mais cela peut être compensé de manière logicielle.

<figure markdown="span">
![](analog_input.svg){ width="60%" }
<figcaption>Raccordement des entrées analogiques avec et sans indicateur existant. (a) Avec un indicateur existant, utilisez HALMET en mode de mesure passive de tension. (b) En l'absence de tout autre appareil, utilisez HALMET en mode de mesure active de résistance.</figcaption>
</figure>


L'exemple (b) montre un cas sans indicateur existant. Le capteur est raccordé directement à l'entrée analogique de HALMET. Dans ce cas, HALMET doit fournir la tension d'excitation du capteur. HALMET réalise la mesure de résistance au moyen d'une source de courant constant (CCS) de 10 mA. Le courant de 10 mA crée une différence de tension de 1 volt aux bornes d'une résistance de 100 Ω, soit une résistance maximale d'environ 300 Ω. La source de courant constant s'active en plaçant un cavalier sur la paire de broches du connecteur à cavalier CCS. Voir la figure ci-dessous.

<figure markdown="span">
![](ccs_jumpers.jpg){ width="60%" }
<figcaption>La figure montre la source de courant constant activée pour les entrées analogiques A2 et A4.</figcaption>
</figure>
