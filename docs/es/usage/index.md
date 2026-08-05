---
title: Uso
translated_from: 0d5855d63a22b19308b3b70c9481dfc441864197
---

# Uso

## Casos de uso habituales

En esta sección se ofrece información práctica sobre la lectura de distintos tipos de sensores y sobre la conexión de HALMET a otros dispositivos.

### Configuración del software

HALMET es una placa de desarrollo y no incluye ningún software preinstalado.
Es necesario instalar el software adecuado. Aunque no es difícil, se recomienda tener experiencia previa con placas de microcontrolador como Arduino o los ESP32 Devkit.

La documentación de HALMET da por supuesto el uso del [firmware de ejemplo de HALMET](https://github.com/hatlabs/HALMET-example-firmware). Este firmware se basa en el framework [SensESP](https://signalk.org/SensESP/) y ofrece un acceso relativamente sencillo a las funciones de la placa.

La [guía de primeros pasos de SensESP](https://signalk.org/SensESP/pages/getting_started/) contiene instrucciones detalladas para instalar el entorno de desarrollo necesario para compilar e instalar el firmware. Las instrucciones están escritas para dispositivos ESP32 genéricos, pero también son aplicables a HALMET. Basta con usar el [firmware de ejemplo de HALMET](https://github.com/hatlabs/HALMET-example-firmware) en lugar de la plantilla de proyecto de SensESP.

Conviene tener en cuenta que, aunque la documentación de SensESP da por supuesto el uso de Signal K, HALMET también se puede utilizar perfectamente como dispositivo NMEA 2000 autónomo.

Si se prefiere no usar SensESP, también se puede crear un firmware propio con Arduino IDE o ESP-IDF. Para muchos casos de uso, ESPHome es asimismo una opción excelente.

**NOTA:** la asignación de los pines GPIO de HALMET difiere ligeramente de la del ESP32 Devkit y de la del SH-ESP32. Si se adapta cualquier software distinto del firmware de ejemplo de HALMET, es necesario comprobar la asignación de pines. Más información en la [referencia de GPIO](../hardware/index.md#referencia-de-gpio).

### Uso de las entradas digitales

HALMET tiene cuatro entradas digitales. Estas entradas se pueden usar para leer señales de alarma digitales o como contadores. En esta sección se describe el uso de las entradas en distintos casos de uso habituales. Las instrucciones dan por supuesto el uso del firmware de ejemplo de HALMET.

Las entradas digitales D1–D4 están conectadas a los pines GPIO 23, 25, 27 y 26, respectivamente. Las entradas toleran tensiones de entre −32 V y +32 V. La tensión de umbral para detectar una señal alta es de unos 1,55 V, con una histéresis de unos 0,7 V.

### Conexión a alarmas digitales

En esta sección se describe cómo conectar HALMET a distintas señales de todo o nada, como las alarmas de motor o de sentina.

#### Configuración del hardware

Normalmente, las distintas señales de todo o nada, como las alarmas de motor o de sentina, se pueden conectar directamente a las entradas digitales de HALMET. Según el tipo de señal, puede hacer falta una resistencia de pull-up (a positivo) o de pull-down (a masa).

En la figura siguiente, en el ejemplo (a) el circuito ya incluye una bombilla. Cuando el interruptor está abierto, la bombilla lleva la tensión de D1 a nivel bajo. No hace falta ninguna resistencia de pull-down adicional.[^1] En cambio, en el ejemplo (b) no hay ninguna otra carga en el circuito. Si el interruptor está abierto, la tensión de D2 queda flotante y la entrada estará aleatoriamente a nivel alto o bajo. En ese caso hay que activar la resistencia interna de pull-down cerrando el puente de soldadura de la cara inferior de la placa.

<figure markdown="span">
![](digin_pullup_pulldown.svg){ width="60%" }
<figcaption>Entradas digitales en distintos casos de uso. (a) El circuito ya incluye una luz. (b) No hay ninguna otra carga en el circuito; el interruptor lleva la señal a nivel alto al cerrarse. (c) El interruptor lleva la señal a nivel bajo al cerrarse.</figcaption>
</figure>

[^1]: Si las luces del panel están hechas con LED, la caída de tensión en los LED puede no bastar para llevar la tensión a un nivel suficientemente bajo. En ese caso hay que activar la resistencia de pull-down.

<figure markdown="span">
![](solder_jumpers.jpg){ width="60%" }
<figcaption>Los puentes de soldadura de la cara inferior de la placa se pueden cerrar para activar las resistencias integradas de pull-up o de pull-down.</figcaption>
</figure>

Del mismo modo, si el interruptor lleva la señal a nivel bajo al cerrarse, como en el ejemplo (c), puede ser necesario activar la resistencia interna de pull-up.

Por último, si los interruptores de alarma son normalmente cerrados (NC), el tratamiento se invierte. Al abrirse el interruptor, la tensión de entrada se lleva a nivel alto o bajo según el circuito. En ese caso puede ser necesario activar la resistencia interna de pull-up o de pull-down.

#### Configuración del software

El firmware de ejemplo de HALMET ofrece el método auxiliar `ConnectAlarmSender()` para configurar y conectar las entradas digitales. Véase `main.cpp` a partir de la línea 177. Se admiten tanto las señales activas a nivel alto como las activas a nivel bajo.

### Entradas digitales como contadores

Las entradas digitales de HALMET también se pueden usar como contadores. Esto resulta útil, por ejemplo, para contar las revoluciones del motor o los impulsos del contador de cadena.

#### Configuración del hardware

Normalmente estos sensores se excitan activamente en ambos sentidos, por lo que no hace falta pull-up ni pull-down. Si HALMET se conecta a una salida de baja impedancia, como el borne W del alternador, conviene añadir un fusible en línea para proteger el conductor frente a cortocircuitos por rozadura u otros daños. Por lo demás, el sensor se puede conectar directamente a la entrada digital.

Si la fuente de impulsos tiene mucho ruido y la lectura de revoluciones resulta errática, se puede activar un filtro de paso bajo cerrando el puente de soldadura «LP» de la cara inferior de la placa. El filtro de paso bajo tiene una frecuencia de corte de unos 2,3 kHz, adecuada para aplicaciones como las entradas conectadas al borne W del alternador.

#### Configuración del software

El firmware de ejemplo de HALMET implementa un contador de impulsos que se puede activar en cualquiera de las entradas digitales o en todas ellas. Véase la configuración de ejemplo en `main.cpp` a partir de la línea 214.

### Uso de las entradas analógicas

HALMET tiene cuatro entradas analógicas que se pueden usar para medición pasiva de tensión o para medición activa de resistencia. En esta sección se describe el uso de las entradas en distintos casos de uso habituales.

#### Configuración del hardware

Las entradas analógicas A1–A4 están conectadas a un convertidor analógico-digital ADS1115. El ADS1115 tiene una resolución de 16 bits y una frecuencia de muestreo máxima de 860 muestras por segundo. No obstante, las entradas analógicas de HALMET incorporan un filtro de paso bajo potente con una frecuencia de corte de unos 160 Hz. Aun así, es más que suficiente para medir las salidas de sensores físicos, como los sensores de nivel de tanque o los sensores de presión del motor.

En la figura siguiente, el ejemplo (a) muestra un indicador del panel del motor ya existente conectado a un sensor resistivo. Los indicadores del panel del motor suelen ser de tipo termostático o magnético. En ambos casos, el indicador y el sensor forman un divisor de tensión, y la tensión en el sensor es proporcional a la magnitud medida. Esta tensión se puede medir con las entradas analógicas de HALMET sin interferir en el funcionamiento del indicador original. Debido al divisor de tensión, la tensión puede no guardar una relación lineal con la magnitud medida, pero esto se puede compensar por software.

<figure markdown="span">
![](analog_input.svg){ width="60%" }
<figcaption>Conexión de las entradas analógicas con un indicador existente y sin él. (a) Si ya hay un indicador, utilizar HALMET en modo de medición pasiva de tensión. (b) Si no hay ningún otro dispositivo, utilizar HALMET en modo de medición activa de resistencia.</figcaption>
</figure>


El ejemplo (b) muestra un caso sin indicador. El sensor se conecta directamente a la entrada analógica de HALMET. En ese caso, HALMET debe proporcionar la tensión de excitación al sensor. HALMET realiza la medición de resistencia mediante una fuente de corriente constante de 10 mA. La corriente de 10 mA genera una diferencia de tensión de 1 voltio en una resistencia de 100 ohmios, lo que da una resistencia máxima de unos 300 ohmios. La fuente de corriente constante se activa colocando un puente (jumper) en el par de pines del conector de pines «CCS» (fuente de corriente constante). Véase la figura siguiente.

<figure markdown="span">
![](ccs_jumpers.jpg){ width="60%" }
<figcaption>En la figura, la fuente de corriente constante está activada para las entradas analógicas A2 y A4.</figcaption>
</figure>
