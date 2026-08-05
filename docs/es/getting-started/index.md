---
title: Primeros pasos
translated_from: 75bcdba18bc044c04ce3e220067bf537e069ec82
---

# Primeros pasos

## Montaje del hardware

Para permitir una colocación más flexible de los conectores en carcasas pequeñas, las placas HALMET se entregan sin los conectores de pines 1-Wire ni GPIO montados. Si se va a utilizar alguna de estas interfaces, es necesario soldar los conectores de pines a la placa.

Las [instrucciones de montaje del hardware](https://docs.hatlabs.fi/sh-esp32/pages/getting-started/#revision-1-boards) del SH-ESP32 explican cómo soldar los pines de un conector a la placa.

## Alimentación de la placa

HALMET se alimenta a través del conector NMEA 2000. Si HALMET se va a conectar a una red NMEA 2000, la placa se puede alimentar directamente desde la red. En ese
caso, conectar los cables NMEA 2000 al bloque de terminales enchufable de 4 pines como se muestra en la figura siguiente.

<figure markdown="span">
![](halmet_n2k_input.jpg){ width="50%" }
<figcaption>Conectar los cables NMEA 2000 al conector como se muestra.</figcaption>
</figure>

Si HALMET no se va a conectar a una red NMEA 2000, se utiliza el mismo conector pero se conectan cables solo a las posiciones `-` y `+`. Sirve cualquier fuente de alimentación de 5–32 V. El consumo de corriente típico de la placa con la WiFi activa es de 0,07 A a 12 V.

<figure markdown="span">
![](power_connector.jpg){ width="50%" }
<figcaption>Conectar los cables de alimentación al conector como se muestra.</figcaption>
</figure>

## Carcasas

Para el uso a bordo, HALMET debe alojarse siempre en una carcasa estanca.
La placa está diseñada para encajar en la [carcasa SH-ESP32](https://shop.hatlabs.fi/products/sh-esp32-enclosure). A continuación se muestra un ejemplo de una placa HALMET instalada en la carcasa.

<figure markdown="span">
![](halmet_small_enclosure.jpg){ width="50%" }
<figcaption>HALMET instalado en la carcasa SH-ESP32.</figcaption>
</figure>

La carcasa SH-ESP32 dispone de un espacio limitado para conectores.
En la práctica, cada uno de los lados largos solo admite 2–3 conectores de panel.
Si se van a conectar más de unas pocas entradas, se recomienda una carcasa mayor.
Por ejemplo, la [carcasa compacta para SH-RPi](https://shop.hatlabs.fi/products/compact-weatherproof-enclosure-for-raspberry-pi-and-sh-rpi-158x90x60-mm) de Hat Labs, mostrada abajo, ya ofrece espacio de sobra para conectores.

<figure markdown="span">
![](medium_enclosure.jpg){ width="50%" }
<figcaption>La carcasa compacta para SH-RPi ofrece más espacio para colocar los conectores de panel.</figcaption>
</figure>


Otras carcasas estancas adecuadas se encuentran fácilmente en cualquier tienda en línea. Las cajas de conexiones de exterior de mayor tamaño también sirven para este fin.

### Perforación de los agujeros para los conectores de panel

Las carcasas no suelen traer orificios pretaladrados. Al taladrar,
utilizar siempre una broca cónica o escalonada (la que parece un pequeño árbol de Navidad metálico). Las brocas normales para metal pueden morder con demasiada fuerza y agrietar la pared de la carcasa.

Al planificar la colocación de los agujeros y los conectores, dejar espacio suficiente para apretar las tuercas del conector y para el cuerpo del conector. Si la carcasa se va a montar en pared, se recomienda orientar los conectores hacia abajo para reducir al mínimo la entrada de agua.

Tamaños de agujero adecuados para los distintos conectores:

- Prensaestopas PG7 y conector de panel M12 (NMEA 2000): 12,5 mm o 1/2″
- Conectores de panel SP13 (conectores de plástico azul y negro): 13 mm
- Prensaestopas PG9: 16 mm o 5/8″

Los pasacables de goma o silicona permiten densidades de cable mucho mayores que los conectores de panel o los prensaestopas. Sin embargo, no son tan estancos como los conectores de panel o los prensaestopas. Además, obligan a fijar el cable de forma permanente, lo que puede dificultar
el mantenimiento del sistema.

TODO: añadir una imagen de un pasacables.

### Soldadura de los conectores de panel

Al soldar los cables internos a los conectores de panel, utilizar siempre tubo termorretráctil en cada uno de los cables.
Recordar siempre que el tubo termorretráctil se desliza sobre el cable _antes_ de soldar…
Normalmente conviene aplicar primero estaño en la cavidad del pin del conector y después volver a fundirlo e insertar el cable.
