---
title: Descripción del hardware
translated_from: 66f9306e0980490684ef1cb989b75a230f6600df
---

# Hardware

## Introducción al ESP32

HALMET se basa en el potente módulo microcontrolador ESP32-WROOM-32E. El ESP32 es un microcontrolador de doble núcleo con conectividad WiFi y Bluetooth integrada. El ESP32 es una opción muy extendida en aplicaciones de IoT por su bajo precio, su buen conjunto de periféricos y su facilidad de uso.

## Bloques funcionales de la placa

A continuación se describen los distintos bloques funcionales de la placa.

<figure markdown="span">
![](HALMET-func.jpg){ width="60%" }
<figcaption>Bloques funcionales del HALMET.</figcaption>
</figure>

1.  Entrada y protección de NMEA 2000 y de la alimentación. El conector NMEA 2000
    cuenta con los siguientes elementos de protección:
    - Fusible rearmable de 500 mA
    - Diodo de protección contra inversión de polaridad
    - Diodos TVS de protección contra sobretensión y ESD
    - Filtrado de ruido en dos etapas

2.  Fuente de alimentación. Fuente conmutada con una corriente de salida máxima de 2 A.

3.  Transceptor CAN para NMEA 2000. Incluye LED RX y TX que indican visualmente
    la actividad del bus CAN.

4.  Interfaces I2C y 1-Wire para conectar sensores adicionales.

5.  Interfaz de usuario. Un botón de reinicio, un botón de modo de arranque y uso
    general, un LED rojo de alimentación y un LED azul programable por el usuario.

6.  Interfaz USB 2.0 para programación y depuración.

7.  Módulo ESP32-WROOM-32E con WiFi y Bluetooth integrados. El módulo de la placa
    HALMET incluye 16 MB de memoria flash.

8.  Circuitos de aislamiento galvánico para las entradas digitales y analógicas.

9.  Entradas analógicas. La placa tiene cuatro entradas analógicas con una
    resolución de 16 bits y una tensión de entrada máxima de 33 V. Cada entrada
    cuenta con protección contra subtensión y sobretensión y con filtrado de paso
    bajo con una frecuencia de corte de 160 Hz para reducir el ruido de medición.

    Las entradas analógicas disponen de una fuente de corriente constante opcional
    de 10 mA para la medición activa de resistencia. La fuente de corriente
    constante se activa mediante los conectores de pines para puente CCS.

    En el modo de medición de resistencia, la resistencia máxima que se puede
    medir es de 320 Ω.

10. Entradas digitales. HALMET tiene cuatro entradas digitales con una tensión de
    entrada máxima de ±30 V. Las entradas incorporan un Schmitt trigger para
    mejorar la inmunidad al ruido.


## Aislamiento galvánico

La placa incorpora aislamiento galvánico entre las entradas digitales y
analógicas y el microcontrolador ESP32. El aislamiento se consigue mediante
aisladores digitales para el I2C y para las cuatro entradas digitales,
respectivamente, y un convertidor DC/DC aislado que alimenta la sección aislada.

Gracias a este aislamiento, la placa se puede alimentar desde la red NMEA 2000
sin riesgo de bucles de masa. El aislamiento protege además frente a picos de
tensión y ruido en las entradas.

<figure markdown="span">
![](HALMET-isolation.jpg){ width="60%" }
<figcaption>Barrera de aislamiento del HALMET. Los conectores de entrada están aislados del resto
de la placa, es decir, no comparten masa común con el resto de la placa.</figcaption>
</figure>

## Conectores

<div class="row" markdown>
  <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-top.jpg){ width="100%" }
<figcaption>Conectores del HALMET, cara superior.</figcaption>
</figure>

   </div>
   <div class="col-sm-6" markdown>

<figure markdown="span">
![](HALMET-conx-bottom.jpg){ width="100%" }
<figcaption>Conectores del HALMET, cara inferior.</figcaption>
</figure>

   </div>
</div>

### Conectores de la cara superior

1.  Conector NMEA 2000. Es un bloque de terminales enchufable de 4 pines
    compatible con Phoenix MC 3.81. Sirve para conectar la placa a una red
    NMEA 2000 y para alimentarla.

2.  Conector de pines 1-Wire. Permite conectar sensores 1-Wire a la placa. Es un
    conector de 3 pines con paso de 2,54 mm. No viene montado de fábrica porque
    puede interferir con la colocación de los conectores de panel de la carcasa.

3.  Conector de pines I2C. Permite conectar sensores I2C a la placa. Es un
    conector de 4 pines con paso de 2,54 mm.

4.  Conector Micro USB. Se utiliza para programar y depurar la placa.

5.  Islas de soldadura sin montar para las señales de reinicio (EN) y de arranque
    (IO0).

6.  Conector de pines GPIO. Es un conector de 2×10 pines con paso de 2,54 mm.
    Saca los pines GPIO disponibles del ESP32 y también se puede utilizar como
    conector JTAG.

7.  Conector de pines de alimentación de la zona aislada. Permite alimentar
    dispositivos externos desde las señales «3V3» y «GND» de la sección aislada.

8.  Contactos del conector para puente de la fuente de corriente constante (CCS)
    de las entradas analógicas. La fuente de corriente constante se activa
    puenteando los contactos.

9.  Conectores de entrada analógica. Son bloques de terminales enchufables de
    2 pines compatibles con Phoenix MC 3.81. Sirven para conectar sensores
    analógicos a la placa.

10. Conectores de entrada digital. Son bloques de terminales enchufables de
    2 pines compatibles con Phoenix MC 3.81. Sirven para conectar sensores
    digitales a la placa.

### Conectores de la cara inferior

11.  Puente de soldadura del terminador CAN. Al cerrar el puente de soldadura se
     activa la resistencia de terminación de 120 Ω del bus CAN. No utilizar la
     resistencia de terminación en redes NMEA 2000.

12.  Puente de soldadura del filtro de paso bajo. Al cerrar el puente de soldadura
     se activa un filtro de paso bajo en la entrada analógica correspondiente. El
     filtro tiene una frecuencia de corte de 2,3 kHz. Sirve, por ejemplo, para
     reducir el ruido de una señal de tacómetro.

13.  Puente de soldadura de la resistencia de pull-down. Al cerrar el puente de
     soldadura se activa una resistencia de pull-down (a masa) de 100 kΩ en la
     entrada digital correspondiente. La resistencia de pull-down permite leer un
     interruptor normalmente abierto (NA) que lleva la señal a nivel alto al
     cerrarse.

14.  Puente de soldadura de la resistencia de pull-up. Al cerrar el puente de
     soldadura se activa una resistencia de pull-up (a positivo) de 100 kΩ en la
     entrada digital correspondiente. La resistencia de pull-up permite leer un
     interruptor normalmente cerrado (NC) que lleva la señal a nivel bajo al
     cerrarse.

15.  Puentes de soldadura de selección de la dirección I2C del ADS1115. Al cerrar
     los puentes de soldadura se selecciona la dirección I2C del convertidor
     analógico-digital (ADC) ADS1115. Sirven para evitar conflictos de direcciones
     cuando hay varios convertidores ADS1115 conectados al mismo bus I2C. Las
     islas de soldadura permiten también conectar dispositivos I2C adicionales a
     la zona aislada de la placa.

### Referencia de GPIO

HALMET reserva varios pines GPIO para los periféricos de entrada. Los pines GPIO
disponibles se sacan al conector de pines GPIO de 2×10 pines. La tabla siguiente
enumera los pines GPIO y sus funciones.

|    GPIO | Función           | Notas                                                      |
| ------: | :---------------- | :--------------------------------------------------------- |
|       0 | Botón de arranque | Entra en el gestor de arranque al llevarse a nivel bajo    |
|       1 | TXD0              | Transmisión de datos al USB                                |
|       2 | LED               | LED rojo de la placa                                       |
|       3 | RXD0              | Recepción de datos del USB                                 |
|       4 | 1-Wire DQ         | Línea de datos 1-Wire                                      |
|       5 | -                 | Disponible en el conector de pines GPIO                    |
|      12 | - / TDI           | Disponible en el conector de pines GPIO. Opcional: JTAG TDI |
|      13 | - / TCK           | Disponible en el conector de pines GPIO. Opcional: JTAG TCK |
|      14 | - / TMS           | Disponible en el conector de pines GPIO. Opcional: JTAG TMS |
|      15 | - / TDO           | Disponible en el conector de pines GPIO. Opcional: JTAG TDO |
|      16 | -                 | Disponible en el conector de pines GPIO                    |
|      17 | -                 | Disponible en el conector de pines GPIO                    |
|      18 | CAN RX            | Recepción desde NMEA 2000                                  |
|      19 | CAN TX            | Transmisión a NMEA 2000                                    |
|      21 | I2C SDA           | Línea de datos I2C. Se usa para la entrada analógica       |
|      22 | I2C SCL           | Línea de reloj I2C. Se usa para las entradas analógicas    |
|      23 | DI1               | Entrada digital 1                                          |
|      25 | DI2               | Entrada digital 2                                          |
|      27 | DI3               | Entrada digital 3                                          |
|      26 | DI4               | Entrada digital 4                                          |
|      32 | -                 | Disponible en el conector de pines GPIO                    |
|      33 | -                 | Disponible en el conector de pines GPIO                    |
|      34 | -                 | Disponible en el conector de pines GPIO                    |
|      35 | -                 | Disponible en el conector de pines GPIO                    |
| 36 (VP) | Solo entrada      | Disponible en el conector de pines GPIO                    |
| 39 (VN) | Solo entrada      | Disponible en el conector de pines GPIO                    |


## Alimentación

El rango de tensión de entrada admitido en la placa es de 5–32 V. El consumo de
corriente típico es de 90 mA a 12 V con el módulo WiFi activo (equivale a 1,1 W).

## NMEA 2000

NMEA 2000 es un estándar de comunicaciones omnipresente que se utiliza para conectar sensores y dispositivos de control y visualización en embarcaciones y buques. Se basa en el bus CAN (Controller Area Network), un estándar de bus para vehículos diseñado para que los dispositivos se comuniquen entre sí sin un ordenador anfitrión.

La placa cumple el estándar NMEA 2000 siempre que ninguno de los conectores no
aislados esté conectado a otros dispositivos referidos a masa. Por ejemplo, se
puede utilizar un sensor de temperatura 1-Wire con un cable largo, ya que no
comparte masa común con otros dispositivos. En cambio, conectar un convertidor
analógico-digital I2C al conector I2C no aislado rompería la conformidad con
NMEA 2000.

TODO: asignación de pines GPIO de NMEA 2000

## LED de estado

La placa HALMET tiene dos botones y dos LED. Los botones llevan las etiquetas «Reset» y «Boot». El botón de reinicio «Reset» reinicia la placa llevando a nivel bajo el pin Enable del ESP32. El botón de arranque «Boot» está conectado a GPIO0 y se puede utilizar durante el encendido del dispositivo para forzar el módulo al modo de descarga. El resto del tiempo se puede utilizar como una entrada de botón normal.

Los dos LED no llevan una etiqueta explícita. El LED rojo se enciende siempre que hay alimentación de 3,3 V en la placa. El LED azul está conectado a GPIO2 (el pin que se usa habitualmente para el LED en las placas de desarrollo ESP32). Los programas de usuario pueden controlarlo para indicar el estado del dispositivo.

## 1-Wire

1-Wire es un sistema de bus de comunicación entre dispositivos diseñado por Dallas Semiconductor, empresa adquirida posteriormente por Maxim Integrated Products. Aunque 1-Wire es un protocolo lento, que admite velocidades de solo hasta 16,3 kbps, resulta muy sencillo de implementar y se puede utilizar a largas distancias. Se emplea habitualmente en sensores de temperatura y otros dispositivos de medición sencillos.

La implementación de 1-Wire de HALMET incorpora filtrado de ruido ESD y RF, además de filtrado de paso bajo, para mejorar la fiabilidad de la red.

Conviene tener en cuenta que el pin de datos de 1-Wire (etiquetado «DQ») está asignado físicamente a GPIO4, por lo que en el programa se debe utilizar GPIO4 para todos los datos de 1-Wire.

## I2C

I2C (Inter-Integrated Circuit) es un bus de comunicación serie síncrono muy extendido que se utiliza habitualmente para conectar circuitos integrados de todo tipo. Emplea dos hilos de datos además de la alimentación y la masa.

HALMET utiliza I2C internamente para el convertidor analógico-digital ADS1115. El bus I2C se saca también a un conector de 4 pines para conectar dispositivos I2C adicionales.

El bus I2C está conectado a GPIO21 (SDA) y GPIO22 (SCL) del ESP32. Estos son los pines I2C predeterminados en el entorno Arduino para ESP32, pero difieren de los pines predeterminados del SH-ESP32.
