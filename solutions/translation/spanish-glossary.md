---
title: Spanish translation glossary and style rules (HALMET)
date: 2026-08-05
category: translation
module: documentation
problem_type: reference
component: documentation
severity: medium
applies_when:
  - Translating any page from docs/en/ into Spanish under docs/es/
  - Reviewing a Spanish translation for consistency
  - Adding a new term that has no established Spanish equivalent
tags:
  - translation
  - i18n
  - spanish
  - terminology
  - mkdocs-static-i18n
---

# Spanish translation glossary and style rules

## Context

The HALMET documentation is written in English under `docs/en/` and translated
into Spanish under `docs/es/`, using the `mkdocs-static-i18n` folder structure.
Each language directory mirrors the same tree, so a translation keeps its
source's path and filename: `docs/en/hardware/index.md` becomes
`docs/es/hardware/index.md`. Only markdown lives under `docs/es/`; images and
other assets stay with the English source and are shared.

**This file began as a copy of the HALPI2 glossary and deliberately keeps its
decisions**, so that two Hat Labs products do not describe the same part with
two different Spanish words. `carrier board` → `placa portadora` was decided
there and stands here too, as does every typography rule below. Terms under the
`## HALMET terms` heading are additions this product needed; everything above it
is shared with HALPI2, and **a change to a shared row must be made in both
repositories or in neither.**

Translations are produced page by page, at different times, potentially by
different people. Without a fixed terminology list the same English term drifts
across pages — *solder jumper* becomes `puente de soldadura` on one page and
`puente soldado` on the next — and the result reads as machine output even when
each individual sentence is correct. This file is the reference that prevents
that drift, and it is a living document: extend it when a page introduces a term
that is not listed, rather than inventing a one-off translation.

`finnish-glossary.md` is the sibling of this file in this repository, and it was
adapted from HALPI2 the same way. The general approach is the same in both.

The locale is a single generic `es`. There is no `es-ES` and no `es-419` build,
so every regional choice below is made once, for both audiences, and recorded
here.

## Six rules where the siblings are wrong for Spanish

Read this section before anything else. Every one of these is stated the
opposite way in at least one sibling glossary — the Finnish, French, German and
Swedish files, which live beside this one in the HALPI2 repository and, for
Finnish, in this one too. Each rule is written so it can be counted in the
finished page rather than nodded at.

1. **The reader is never addressed.** French uses *vouvoiement*, German uses
   *Sie*, Finnish and Swedish use the second person singular. All four are wrong
   here. Spanish technical documentation is impersonal:

   > La unidad se apaga automáticamente cuando se interrumpe la alimentación.

   Procedure steps take the **infinitive**, not an imperative:

   > Conectar el cable de alimentación. Comprobar la polaridad con el multímetro
   > antes de aplicar tensión.

   This is also the only register that survives a generic `es` build: `usted`
   sounds commercial in Spain, `tú` sounds wrong in an installation manual
   anywhere, and `vosotros` does not exist in Latin America. The impersonal has
   no regional split at all.

   *Count:* `usted`, `ustedes`, `tú`, `ti`, `vosotros`, `vosotras` appear **zero**
   times. Every numbered and bulleted procedure step begins with an infinitive —
   count the steps, count the infinitives, the two numbers are equal.

2. **Inverted opening marks are mandatory.** `¿` and `¡` do not exist in the
   English source, so a missing one is never a copy error — it is always an
   omission, and it is the defect a Spanish reader sees first. Headings that are
   questions carry both marks: `## ¿Qué es HALMET?`

   *Count:* the number of `¿` equals the number of `?` outside code. Exclamations
   in prose are rare here; when one is used it opens with `¡`. Do not count the
   `!` in `!!! warning` or in `![image]` — those are markdown syntax.

3. **Quotation marks are `«…»`** — angular marks, the RAE first level. Not
   German's `„…"`, not Swedish's `”…”`, not straight `"…"`. Use them for quoted
   hardware labels and UI strings that stay in English: `el botón «Reset»`,
   `el botón «Boot»`, `el puente «CCS»`.

   **Unlike French, there is no space inside the marks.** `«Abnormal»`, never
   `« Abnormal »`. A French translator's muscle memory puts a no-break space
   there and it is invisible in review.

   *Count:* `«` and `»` occur the same number of times. `"`, `”`, `„` and `“`
   occur zero times outside code. The sequences `« ` and ` »` occur zero times,
   including with U+00A0.

4. **No space before `; : ! ?`** — as in German and Swedish, and the exact
   opposite of French, whose rule demands a no-break space there.

   *Count:* zero occurrences of a space (U+0020 **or** U+00A0) immediately before
   `;`, `:`, `!` or `?` outside code. Check U+00A0 explicitly: it is invisible,
   and it is what arrives when a French sentence pattern is carried across.

5. **A proper name never takes a hyphen in a compound.** German writes
   `NMEA-2000-Netzwerk`, Swedish `NMEA 2000-nätverk`, Finnish `NMEA 2000 -verkko`.
   Spanish uses a plain noun phrase or a preposition:

   - `red NMEA 2000`, `bus NMEA 2000`, `servidor Signal K`, `módulo ESP32`
   - `carcasa del HALMET`, `conector M12`, `entradas del ADS1115`, `bus I2C`

   *Count:* `NMEA-2000`, `Signal-K`, `HALMET-`, `SH-ESP32-`, `ESP32-` (as a
   compound with a Spanish noun, not the module name `ESP32-WROOM-32E`) and
   `ADS1115-` occur zero times outside code and outside repository names such as
   `HALMET-example-firmware`.

6. **One Spanish, no mixing.** No sibling language has a regional split, so no
   sibling glossary warns about this. Three decisions, made once:

   | Use | Never | Why |
   |:----|:------|:----|
   | ordenador | computadora, computador | One form must win; `ordenador` is chosen for the whole site |
   | supercondensador | supercapacitor | `capacitor` is an Americanism; `condensador` is the general term |
   | supervisión | monitoreo, monitorización | Both alternatives are regionally marked; `supervisión` is not |

   *Count:* each banned word appears zero times.

## Names that are never translated

Product names, protocol names, hardware standards and software UI strings stay
in English — the device's own interface is in English, so translating a menu
name sends the reader looking for something that is not on the screen.

- **Products and software:** HALMET, SH-ESP32, SH-RPi, SensESP, Signal K,
  Arduino IDE, ESP-IDF, ESPHome, PlatformIO, Hat Labs
- **Hardware and standards:** ESP32-WROOM-32E, ADS1115, NMEA 2000, CAN bus, I2C,
  1-Wire, GPIO, JTAG, USB, ADC, TVS, PG7, PG9, SP13, M12, Phoenix MC, Schmitt
  trigger
- **Pin and signal names are copied exactly:** `D1`–`D4`, `A1`–`A4`, `SDA`,
  `SCL`, `DQ`, `TXD0`, `RXD0`, `EN`, `IO0`, `CCS`, `LP`, `VP`, `VN`, `3V3`,
  `GND`. These are printed on the board; a translated pin name sends the reader
  looking for a label that does not exist. The same holds for `DI1`–`DI4`,
  `GPIO0`, `GPIO2`, `GPIO4`, `TDI`, `TCK`, `TMS`, `TDO`, `CAN RX` and `CAN TX`
  in the GPIO table.
- **Repository, file and command names:** `HALMET-example-firmware`, `main.cpp`,
  `halmet-hardware`
- **UI strings and silkscreen labels the reader will see in English:**
  `«Reset»`, `«Boot»`, `«CCS»`, `«LP»`, `«3V3»`, `«GND»`

`bus CAN` is the one exception worth stating: `CAN bus` is a compound of a
standard's name with a common noun, so Spanish word order applies — `el bus CAN`,
never `el CAN bus`. The name `CAN` itself is untouched.

Code fences, command output, URLs and image filenames are never touched.

## Units and numbers

The English source writes `12V` and `0.9A`. Both are wrong in Spanish: SI
spacing and a decimal comma are required, and this needs an active conversion on
nearly every technical page.

| English source | Spanish |
|:---------------|:--------|
| `12V`, `0.9A` | `12 V`, `0,9 A` |
| `5.5 x 2.1 mm` | `5,5 × 2,1 mm` |
| `-20°C to +60°C` | `−20 °C … +60 °C` |
| `120Ω` | `120 Ω` |
| `3-5A` | `3–5 A` (en dash for ranges) |
| `1.5mm²`, `2m` | `1,5 mm²`, `2 m` |

Dimensions written as a single product spec keep the tight form:
`200×130×60 mm`.

**No thousands separator anywhere on this site.** Spanish forbids the English
comma (`115,200` reads as a decimal), and the alternatives — a period or a thin
space — buy nothing at the magnitudes used here. Baud rates, port numbers and
firmware versions are identifiers, not measurements: `115200 bps`, `9600`,
`puerto 2947`, `3.1.0` are copied unchanged.

## Links, images, admonitions, navigation

Same as the sibling glossaries: paths are copied from the English source
unchanged and never carry an `en/`, `es/` or other language segment; image
captions and alt texts are translated but filenames are not; screenshots stay
English because the reader's own screen is English; standard admonition titles
are translated centrally in `mkdocs.yml`, custom ones in the page.

Translated headings change their anchors, and `¿` and the accents are stripped
by the slugifier — `## ¿Qué es HALMET?` does **not** become `#¿que-es-halmet`.
Do not guess: build the site and read the real ids out of the generated HTML.
This matters on HALMET's `usage/index.md`, which links to
`../hardware/index.md#gpio-reference`: that anchor changes as soon as the
heading is translated, and `check_anchors.py` is what catches it.

Section and page titles in the navigation are not part of any markdown file —
they live in `mkdocs.yml` under the i18n plugin's `nav_translations`, which is
the single source of truth. Two entries are judgement calls worth recording:

- `Errata` → **Defectos conocidos**. The page lists known hardware defects;
  Spanish `erratas` means printing errors or corrections, which is the wrong
  thing entirely.
- `Hardware Revisions` → **Versiones del hardware**. Board versions, not
  document revisions, so not `revisiones`.

## Glossary

### Enclosure and mounting

| English | Spanish | Note |
|:--------|:--------|:-----|
| carrier board | placa portadora | The accurate term, as in French, German and Swedish |
| enclosure | carcasa | |
| heat sink | disipador térmico | The enclosure doubles as one |
| waterproof | estanco | `carcasa estanca (IP65)` |
| rugged | robusto | |
| wall-mount | montaje en pared | |
| mounting surface | superficie de montaje | |
| pilot hole (to be drilled) | agujero guía | `Taladrar los agujeros guía para los tornillos` |
| pre-drilled hole (already there) | orificio pretaladrado | The holes the enclosure ships with |
| mounting template | plantilla de taladrado | |
| clearance | espacio libre | |
| bilge water | agua de sentina | The compartment alone: *sentina* |
| bulkhead | mamparo | |
| cable gland | prensaestopas | `prensaestopas PG7` |
| cable routing | tendido de cables | |
| service loop | bucle de servicio | Slack left at both cable ends |
| cable tie | brida | |
| blind plug | tapón ciego | |
| breather plug | tapón compensador de presión | Must never be removed |

**Two rows, not one, for the holes.** `pilot hole` is a hole that does not exist
yet and has to be drilled; `pre-drilled hole` is one the enclosure arrives with.
The English source uses both, three sections apart. Collapsing them produced a
nonsense instruction in Swedish — *drill the pre-drilled holes* — so never write
`taladrar los orificios pretaladrados`.

**A note on `placa portadora`.** Spanish takes the accurate term, like French
(`carte porteuse`), German (`Trägerplatine`) and Swedish (`bärkort`), and unlike
Finnish (`emolevy`, literally *motherboard*, chosen there for reader
familiarity). The divergence between the five is deliberate, decided per
language and per audience. Do not harmonise them.

`placa portadora` carries the CM5/board relationship on its own, so passages
about reseating the CM5 or troubleshooting a board that will not boot need no
extra explanation. Only the Finnish glossary needs that warning.

### Power and electrical

| English | Spanish | Note |
|:--------|:--------|:-----|
| power supply | alimentación | The unit itself: *fuente de alimentación* |
| power source | fuente de alimentación | |
| input voltage range | rango de tensión de entrada | |
| polarity | polaridad | |
| positive (+) / negative (−) | positivo (+) / negativo (−) | |
| fuse | fusible | |
| inline fuse | fusible en línea | |
| circuit breaker | interruptor automático | Neutral; not *magnetotérmico* or *disyuntor* |
| electrical panel | cuadro eléctrico | |
| current limiting | limitación de corriente | |
| current limiter | limitador de corriente | The circuit |
| current limit | límite de corriente | The `0,9 A` / `2,5 A` setting |
| overcurrent | sobrecorriente | |
| voltage drop | caída de tensión | |
| grounding | puesta a tierra | |
| short circuit | cortocircuito | |
| wire gauge | sección del conductor | Spanish uses mm², not AWG |
| marine-grade wire | cable de calidad náutica | |
| to strip (a wire) | pelar | |
| wire strippers | pelacables | |
| crimping | crimpado | Verb: *crimpar*. Established trade usage, like `firmware` |
| crimper | tenaza de crimpar | |
| heat-shrink tubing | tubo termorretráctil | Two r's |
| heat gun | pistola de aire caliente | |
| multimeter | multímetro | Not *polímetro* |
| continuity test | prueba de continuidad | |
| terminal | terminal | |
| terminal block | bloque de terminales | Not *bornera* or *regleta* |
| strain relief | descarga de tracción | Its absence is why the screw-terminal barrel plug is temporary only |
| super-capacitor | supercondensador | |
| real-time clock | reloj de tiempo real | |
| backup battery | pila de respaldo | The CR2032 for the RTC |

### Connectors and interfaces

| English | Spanish | Note |
|:--------|:--------|:-----|
| connector | conector | |
| barrel connector | conector cilíndrico | Add *(barrel)* on first mention |
| header | conector de pines | `conector GPIO de 40 pines` |
| pin | pin | |
| jumper | puente | Add *(jumper)* on first mention |
| backbone | cable troncal | The NMEA 2000 trunk; the network as a whole: *red troncal* |
| drop cable | cable de derivación | |
| T-connector | conector en T | Also for the source's *T-adapter* |
| terminator | terminador | The bus terminator enabled by the jumper |
| termination resistor | resistencia de terminación | The 120 Ω component |
| termination | terminación | The act, and the network property |
| front panel | panel frontal | |
| antenna | antena | |
| extension cable | cable alargador | |
| male / female | macho / hembra | |

### Operation and system behaviour

| English | Spanish | Note |
|:--------|:--------|:-----|
| boat computer | ordenador de a bordo | See rule 6 on `ordenador` |
| to boot | arrancar | Noun: *arranque* |
| first boot | primer arranque | |
| shutdown | apagado | |
| graceful shutdown | apagado controlado | |
| power loss | pérdida de alimentación | |
| blackout | corte de corriente | `temporizador de corte de corriente` |
| glitch immunity | inmunidad a microcortes | |
| power management | gestión de la alimentación | |
| status LED | LED de estado | |
| LED bar | barra de LED | |
| monitoring | supervisión | Never *monitoreo* or *monitorización* |
| passive cooling | refrigeración pasiva | |
| watchdog | watchdog | Gloss once as *(temporizador de vigilancia)*, then keep the term |
| standby | modo de reposo | The planned state where the CM5 is off and the controller waits |
| filesystem | sistema de archivos | |
| to unmount (a filesystem) | desmontar | `el sistema de archivos se desmonta de forma segura` |
| to unmount (a board or module) | retirar | The source says *unmount* for the carrier board and the CM5 too; `desmontar` there reads as *dismantle* |
| to reseat (a module) | volver a asentar | |

### Software and networking

| English | Spanish | Note |
|:--------|:--------|:-----|
| firmware | firmware | Not *microprogramación* — matches the sibling decision to keep the trade term |
| daemon | demonio | Established in Spanish Linux usage, as in French |
| to flash (firmware or an image) | grabar | Noun: *grabación*. Never *flashear* |
| to flash (an LED) | parpadear | A machine translator renders both English senses the same way; these are different words in Spanish |
| system image | imagen del sistema | |
| operating system image | imagen del sistema operativo | |
| headless | sin pantalla | First mention: `sin pantalla (headless)` |
| deployment | puesta en marcha | |
| container app | aplicación en contenedor | |
| container image | imagen de contenedor | Not *imagen del sistema* |
| dashboard | panel de control | Homarr's *dashboard* view |
| WiFi Access Point | punto de acceso WiFi | |
| wired / wireless | por cable / inalámbrico | |
| credentials | credenciales | |
| username / password | nombre de usuario / contraseña | |
| default password | contraseña predeterminada | |
| single sign-on (SSO) | inicio de sesión único (SSO) | |
| Certificate Authority (CA) | autoridad de certificación (CA) | |
| to trust (a certificate) | confiar en | |
| web interface | interfaz web | Feminine: *la interfaz* |
| browser | navegador | |
| system administration | administración del sistema | |

### Applications and use cases

| English | Spanish | Note |
|:--------|:--------|:-----|
| chart plotter | plóter cartográfico | |
| data logging | registro de datos | |
| vessel | embarcación | Not *buque*, which implies a ship |
| engine parameters | parámetros del motor | |
| fleet management | gestión de flotas | |
| predictive maintenance | mantenimiento predictivo | |
| process monitoring | supervisión de procesos | |
| remote monitoring | supervisión remota | |
| electromagnetic interference (EMI/RFI) | interferencias electromagnéticas (EMI/RFI) | |
| compliance | conformidad | |
| warranty | garantía | |

## HALMET terms

HALMET is a sensor interface board, so it needs vocabulary HALPI2 never used:
input circuits, measurement, and the things printed on a small PCB. **Rows above
this heading are shared with HALPI2 and must not be changed here alone.** Rows
below it are HALMET's own.

### Board and inputs

| English | Spanish | Note |
|:--------|:--------|:-----|
| development board | placa de desarrollo | What HALMET is sold as. Never `placa portadora` — that is HALPI2's carrier board and implies a module plugged into it |
| board (the HALMET board itself) | placa | `la placa`, `la cara inferior de la placa`. Not *tarjeta*, which is a plug-in card |
| microcontroller | microcontrolador | |
| flash memory | memoria flash | `16 MB de memoria flash`; the unit spacing rule applies |
| digital input | entrada digital | `D1`–`D4` stay as printed |
| analog input | entrada analógica | `A1`–`A4` stay as printed |
| input | entrada | |
| output | salida | |
| sender | sensor | The sending unit a gauge reads. Not *emisor* or *transmisor*, which suggest a radio transmitter. Spanish does not keep the English *sender*/*sensor* distinction; where a sentence pairs them, let the role carry it: `el indicador y el sensor forman un divisor de tensión` |
| tank sender | sensor de tanque | |
| tank | tanque | Regional decision per rule 6: `depósito` is Spain-marked, `tanque` is the neutral marine word |
| resistive sender | sensor resistivo | |
| gauge (engine panel gauge) | indicador | `indicador del panel del motor`. Never *calibre* — that is a machine translation of the other English *gauge*, the one the shared glossary renders as `sección del conductor` |
| counter | contador | |
| chain counter | contador de cadena | The anchor-chain counter. `cuentacadenas` is the trade name for the finished instrument; the function is `contador de cadena` |
| pulse | impulso | `contador de impulsos`, `impulsos del contador de cadena` |
| alarm signal | señal de alarma | |
| on/off signal | señal de todo o nada | The source's *on/off type signals*. A literal `señal de encendido/apagado` describes a power state, not a contact |
| engine RPM | revoluciones del motor | Spelled out in prose; `rpm` only as a unit after a number, lowercase and spaced: `3000 rpm` |
| tachometer | tacómetro | Regional decision per rule 6: `cuentarrevoluciones` is Spain-marked |
| alternator W terminal | borne W del alternador | A stud on the alternator, so `borne`. The shared glossary's `terminal` → `terminal` is unchanged and still applies to wiring terminals |
| fuel flow | caudal de combustible | Not *flujo*, which is the phenomenon rather than the measured rate |
| low-impedance output | salida de baja impedancia | |

### Measurement and circuits

| English | Spanish | Note |
|:--------|:--------|:-----|
| galvanic isolation | aislamiento galvánico | |
| isolated (section, area) | aislado | `sección aislada`, `zona aislada` |
| digital isolator | aislador digital | |
| isolation barrier | barrera de aislamiento | |
| ground loop | bucle de masa | `masa`, not `tierra`: this is the shared signal reference, not the protective earth the shared glossary calls `puesta a tierra`. A board with no common ground has `sin masa común` |
| analog-to-digital converter (ADC) | convertidor analógico-digital (ADC) | The acronym and the part number `ADS1115` stay English |
| resolution | resolución | `resolución de 16 bits` — Spanish spells the bit count out, no hyphen |
| sampling rate | frecuencia de muestreo | `860 muestras por segundo` |
| low-pass filter | filtro de paso bajo | One form for the whole site per rule 6: `pasa bajos`, `pasabajo` and `paso bajo` all circulate regionally. The solder-jumper label `LP` stays as printed |
| cutoff frequency | frecuencia de corte | |
| noise (electrical) | ruido | Electrical interference, not sound. Distinct from the shared `interferencias electromagnéticas (EMI/RFI)`, which is the radiated kind |
| noise immunity | inmunidad al ruido | Distinct from the shared `glitch immunity` → `inmunidad a microcortes`, which is about supply interruptions |
| voltage spike | pico de tensión | |
| voltage divider | divisor de tensión | `tensión`, never `voltaje`, throughout — the shared glossary already fixes this in `caída de tensión` and `rango de tensión de entrada` |
| constant current source (CCS) | fuente de corriente constante | A current source, not the shared `power source` → `fuente de alimentación`. The header label `CCS` stays as printed |
| excitation voltage | tensión de excitación | The voltage HALMET supplies to a sender that has no gauge |
| passive voltage measurement | medición pasiva de tensión | `medición`, not `medida`, for the act, consistently |
| active resistance measurement | medición activa de resistencia | |
| pull-up resistor | resistencia de pull-up | Trade term kept in English inside a Spanish noun phrase, like the shared `firmware` and `watchdog`. Gloss once on first mention: `resistencia de pull-up (a positivo)`. Not *resistencia de polarización*, which is a different circuit |
| pull-down resistor | resistencia de pull-down | Gloss once as `(a masa)` |
| to pull high / to pull low | llevar a nivel alto / llevar a nivel bajo | `el interruptor lleva la señal a nivel alto al cerrarse` |
| threshold voltage | tensión de umbral | |
| hysteresis | histéresis | |
| floating (input) | flotante | `la entrada queda flotante` |
| normally open (NO) / normally closed (NC) | normalmente abierto (NA) / normalmente cerrado (NC) | Established Spanish electrical terms; the abbreviation NO becomes **NA**. See the note below |
| self-resetting fuse | fusible rearmable | The 500 mA PTC. Not *autorreiniciable* |
| reverse polarity protection | protección contra inversión de polaridad | |
| overvoltage protection | protección contra sobretensión | Under-voltage: `subtensión`. Built on the shared `overcurrent` → `sobrecorriente` |
| switching power supply | fuente de alimentación conmutada | |
| current consumption | consumo de corriente | |
| short circuit | cortocircuito | Unchanged from the shared row above; repeated only because it is the reason HALMET asks for an in-line fuse on an alternator W terminal |
| chafing | rozadura | `cortocircuitos por rozadura`. New here: HALPI2's Spanish glossary has no row for it |

### Board features and assembly

| English | Spanish | Note |
|:--------|:--------|:-----|
| jumper | puente | Shared row, unchanged. The removable link placed on a pin pair — the CCS one. Add *(jumper)* on first mention |
| jumper header | conector de pines para puente | The pin pair a jumper is placed on. Built on the shared `header` → `conector de pines`; `contactos del conector` for the source's *jumper header contacts* |
| solder jumper | puente de soldadura | Same Spanish term as HALPI2 but the **opposite action** — see the note below |
| to short (a jumper) | puentear | `puentear los contactos`, `puentear el puente de soldadura para activar la resistencia`. Covers both kinds |
| solder pad | isla de soldadura | KiCad's Spanish term, consistent with the shared glossary's `footprint` → `huella`. Not *almohadilla*, which the shared list assigns to `thermal pad` |
| unpopulated | sin montar | `islas sin montar`. Of a header absent from the board as delivered, the verbal form reads better: `no viene montado de fábrica` |
| pitch | paso | Already fixed for HALPI2 (`paso de 3,81 mm`, `paso de 2,54 mm`); repeated because it occurs on nearly every HALMET connector |
| pluggable terminal block | bloque de terminales enchufable | Phoenix MC 3.81 type. Built on the shared `terminal block` → `bloque de terminales`; still never *bornera* or *regleta* |
| silkscreen | serigrafía | Already fixed for HALPI2. `la serigrafía de la cara inferior` |
| to solder | soldar | The tool: `soldador`. The material: `estaño` |
| grommet | pasacables | Rubber or silicone. Distinct from the shared `cable gland` → `prensaestopas`, the threaded one, exactly as in the HALPI2 list |
| step drill bit | broca escalonada | The one that looks like a small metal Christmas tree |
| conical drill bit | broca cónica | |
| panel connector | conector de panel | The connectors mounted through the enclosure wall; `tuercas del conector` for the nuts that hold them |
| reset button | botón de reinicio | The silkscreen label stays English: `el botón de reinicio «Reset»`. Not *reseteo* |
| boot button | botón de arranque | Label stays English: `el botón de arranque «Boot»`. It selects the boot mode; it does not switch the board on, so say what it does on first mention |
| bootloader | gestor de arranque | |
| download mode | modo de descarga | The ESP32's own flashing mode. Not *modo de grabación*: the shared glossary assigns `grabar` to the act of flashing, and reusing it here would blur the two |
| user-programmable LED | LED programable por el usuario | |
| open hardware | hardware abierto | The licence statement in `index.md`. `hardware` stays English, as in the shared `herrajes de montaje` note |

### A note on `puente` and `puente de soldadura`

Two different things, one word apart, and confusing them makes the reader do the
wrong physical action.

- **`puente` (jumper)** is a removable link that is *placed on* a pin pair. On
  HALMET this is the `CCS` header: `colocar el puente en el par de pines CCS`.
  It comes off again with fingers.
- **`puente de soldadura` (solder jumper)** is a pair of pads on the PCB that is
  *closed with solder*: `cerrar el puente de soldadura`. It needs a soldering
  iron, and a reader who expects to pull it off will look for something that is
  not there.

The verb has to carry the difference, because the nouns are so close. Use
`colocar`/`retirar` for the jumper and `cerrar`/`soldar` for the solder jumper.

**The HALPI2 sense is the opposite one.** There, `puente de soldadura` is a
factory-closed trace that has to be *cut* to open it, and the note in the
inherited term list says so. On HALMET the solder jumpers ship open and are
closed by the user. The Spanish term is the same in both products and stays the
same; only the verb changes. Never write `cortar el puente de soldadura` on a
HALMET page.

### A note on `normalmente abierto` / `normalmente cerrado`

Spanish has established terms for these and they must be used rather than a
literal rendering of the English words. A switch is `normalmente abierto (NA)` or
`normalmente cerrado (NC)`. The abbreviation changes: English `NO` becomes `NA`,
while `NC` happens to be the same in both languages. This matches the decision
already recorded for HALPI2 (`pulsador momentáneo normalmente abierto (NA)`).

The pull-up/pull-down instructions in `usage/index.md` depend on getting this
right: with a normally closed switch the treatment is reversed, and a reader who
reads `abierto` where the source says *closed* enables the wrong resistor.

### A note on `conector`

The shared glossary renders both `connector` and `header` as connectors —
`conector` and `conector de pines` — and that is kept. HALMET puts the two side
by side more often than HALPI2 does (*1-Wire header connector*, *analog input
connectors*), so let the qualifier carry the distinction: `conector de pines
1-Wire`, `conectores de entrada analógica`. Where a sentence would still be
ambiguous, say what the thing is: `regleta de pines` for a bare pin strip,
`conector enchufable` for the plug that comes off.

## Verification

A translated page is not done until:

1. `uv run mkdocs build --strict` passes.
2. `uv run python scripts/check_anchors.py site` passes.
3. `uv run python scripts/translation_status.py` shows the page as current.
4. `uv run python scripts/check_glossary.py es` passes.
5. `uv run python scripts/check_typography.py es` passes — it knows this
   language's quotation marks and its space-before-punctuation rule.
6. Structure matches the source — see `.claude/skills/translate-page/SKILL.md`.
7. Every term used on the page that appears in this glossary matches it.
8. **The six rules at the top are measured against the pages, not re-read.** A
   half-applied typography rule looks followed when you read it, because
   rereading your own text confirms whatever it already says. The French and
   German branches each shipped one to review for exactly this reason. Every
   rule above carries a *Count:* line; run the counts.

The four that catch the most on a Spanish page, as one command from the repo
root:

```bash
python3 - <<'PY'
import re, pathlib
text = "\n".join(
    re.sub(r"`[^`\n]*`", " ", re.sub(r"```.*?```", " ", p.read_text(encoding="utf-8"), flags=re.S))
    for p in sorted(pathlib.Path("docs/es").rglob("*.md"))
)
print("¿ vs ?          ", text.count("¿"), text.count("?"))
print("« vs »          ", text.count("«"), text.count("»"))
print("stray quotes    ", sum(text.count(c) for c in '"”„“'))
print("space before ;:!?", len(re.findall(r"[  ][;:!?]", text)))
print("reader addressed", len(re.findall(r"\b(usted|ustedes|tú|ti|vosotr[oa]s)\b", text, re.I)))
print("regional mixing ", len(re.findall(r"\b(computador[a]?|supercapacitor|monitoreo|monitorizaci[óo]n)\b", text, re.I)))
PY
```

Every number on the right must be zero except the first two pairs, which must be
equal within each pair.

## Related

- `finnish-glossary.md` — the sibling in this repository, adapted from HALPI2
  the same way
- `../../../halpi2/solutions/translation/spanish-glossary.md` — the original.
  Read-only from here: a shared row changes in both repositories or in neither
- `.claude/skills/translate-page/SKILL.md` — the procedure
- mkdocs-static-i18n documentation: https://ultrabug.github.io/mkdocs-static-i18n/

## Terms added during translation

Inherited from the HALPI2 pages, where these were reported by the page
translators and consolidated into one list. They are kept because the Spanish
decisions in them are binding for HALMET too — `paso`, `serigrafía`, `puente de
soldadura`, `pasacables`, `normalmente abierto (NA)` and `V CC` are all reused
above. Rows naming HALPI2-only parts (CM5, HaLOS, the E7T connector) simply
never come up on a HALMET page; `check_glossary.py` only tests a term whose
English appears in the source, so they cost nothing.

Extend this list the same way when a HALMET page introduces a term that is not
in the glossary tables.

| English | Translation | Note |
|:--------|:------------|:-----|
| Getting Started (page/section title) | Primeros pasos | Page H1 and the HaLOS guide link text. Standard Spanish docs heading; avoids turning a noun phrase into a question that would need ¿…? |
| desktop setup (on a desk/bench, as opposed to permanent installation) | configuración de sobremesa | Recurs six times on this page as the counterpart of `instalación permanente`. Not the GUI desktop — `escritorio` would be wrong here. |
| wall wart (power supply) | «wall wart» (transformador de enchufe) | Quoted colloquial English in the source. Kept in guillemets per rule 3 with a short gloss on first and only mention; there is no established Spanish t |
| splash screen | pantalla de inicio | Raspberry Pi OS boot screen; needed a fixed rendering so it does not drift to `pantalla de bienvenida` on other pages. |
| cable grommet | pasacables | Appears alongside `cable gland` (prensaestopas) in the same sentence; the two must stay distinct, as with the pilot-hole / pre-drilled-hole pair. |
| mounting hardware (screws, brackets) | herrajes de montaje | "Corrosion-resistant mounting hardware" — `hardware` alone would read as electronics in a hardware manual. |
| cable tie / mounting clip | brida / clip de sujeción | `brida` is already in the glossary; `mounting clip` is not and is paired with it in the materials list. |
| rainbow pattern (LED fault indication) | patrón de arcoíris | Diagnostic LED pattern for an unseated CM5; a fixed wording matters because it is the symptom a reader searches for. |
| cable tester | comprobador de cables | Troubleshooting tool, distinct from `multímetro` which the glossary already fixes. |
| over-torque (verb) | excederse en el par (de apriete) | Mounting-screw instruction; `sobrepar` is not idiomatic Spanish. |
| Container Apps store (Cockpit) | tienda de aplicaciones en contenedor | Built on the glossary's `aplicación en contenedor`. Cockpit's own label is English, but the source uses it descriptively rather than as a quoted butto |
| known-good device | dispositivo que se sepa que funciona | Troubleshooting idiom with no compact Spanish equivalent; a literal `dispositivo bueno conocido` is meaningless. |
| device tree overlay | overlay | interfaces.md, 3 occurrences. Kept as the trade term, consistent with the glossary's decision to keep `firmware`. `superposicion de arbol de dispositi |
| chip-select | chip-select | interfaces.md table, `CAN FD chip-select`. A signal name on the board, not prose; `seleccion de chip` would not match anything the reader can look up. |
| transceiver | transceptor | interfaces.md, `an RS-485 transceiver's enable line`. Standard Spanish electronics term. |
| hardware flow control | control de flujo por hardware | interfaces.md, introduces the `ctsrts` parameter. |
| mass storage device | dispositivo de almacenamiento masivo | software.md, USB-boot procedure, 3 occurrences. The state the HALPI2 presents itself in during `rpiboot` flashing. |
| block device | dispositivo de bloques | software.md step 6, `any other tool that can write to a block device`. |
| boot mode switch | interruptor de modo de arranque | software.md, 3 occurrences in the USB-boot steps. Built on the glossary's `arranque`; the associated silkscreen labels stay English as `«Normal»` / `« |
| power cycle (noun) / to power-cycle | ciclo de alimentacion / realizar un ciclo de alimentacion | software.md, 3 occurrences including the admonition title. Distinct from `apagado` and from `reinicio`, and the firmware-update section depends on the |
| marine apps | aplicaciones náuticas | software.md image-variant table and Homarr description, 4 occurrences. The glossary has `vessel -> embarcacion` but no adjective for the application c |
| firewall | cortafuegos | software.md, VNC and Raspberry Pi Connect sections. |
| port forwarding | redireccion de puertos | software.md VNC section, alongside VPN. |
| taskbar | barra de tareas | software.md, Graphical Updates section. |
| update manager | gestor de actualizaciones | software.md, Graphical Updates section. |
| hostname | nombre de host | software.md, Raspberry Pi Imager customisations. Kept close to the English because the Imager field itself reads `hostname`. |
| to roll back (firmware) | volver a la version anterior | software.md Firmware Safety Features. Verbal phrase rather than a noun, so it composes with the impersonal register required by rule 1. |
| login console | consola de inicio de sesion | interfaces.md, the dedicated debug UART. Reuses the glossary's `inicio de sesion` from `single sign-on`. |
| power rail (3.3V rail, 5V rail) | línea (línea de 3,3 V, línea de 5 V) | Not in the glossary and it occurs eight times across both pages. Chose «línea» over the calque «raíl»/«riel» because it is regionally neutral (rule 6) |
| flange (wide flange required on inside) | reborde | The obvious equivalent «brida» is already assigned to *cable tie* in the glossary, so using it here would collide. «Reborde» names the wide collar of  |
| standoff | separador | HAT mounting hardware; appears five times in the HAT installation section and had no glossary entry. |
| spudger | espátula (spudger) | No Spanish equivalent in common trade use; glossed on first mention and the English kept in parentheses, following the glossary's `sin pantalla (headl |
| solder jumper | puente de soldadura | Distinct from the removable `jumper` already in the glossary (`puente`); this one is a PCB trace that has to be cut. |
| Solo Mode / Co-op Mode | modo solo / modo cooperativo (co-op) | Firmware operating modes, not UI strings the reader sees on screen, so translated. «co-op» kept in parentheses on first mention because `halpi status` |
| VDC (11-32 VDC, 100 VDC) | V CC (11–32 V CC, 100 V CC) | SI/Spanish convention for direct-current voltage; the glossary sets unit spacing but does not cover the DC suffix. |
| chip select | selección de chip (chip select) | SPI signal name; translated with the English glossed once because the table row abbreviates it as `SPI CS`. |
| watchdog timeout | tiempo de espera del watchdog agotado | The glossary fixes `watchdog` itself but not `timeout`; «tiempo de espera» is used consistently for all four timeout occurrences across both pages. |
| blinkenlights | Blinkenlights | Left untranslated. It is a jargon in-joke, not a technical term, and any Spanish rendering loses the joke while gaining nothing; flagged here so a rev |
| rail (power rail: 5V rail, 3.3V rail) | línea (línea de 5 V, línea de 3,3 V) | Not in the glossary but already used in docs/es/user-guide/operation.md:121 ("La línea de 5 V se desactiva") and hardware.md:92. Adopted for consisten |
| pitch (connector pitch) | paso | Appears constantly in hardware.md (3.81 mm, 2.54 mm, 0.5 mm). Already established in docs/es/user-guide/hardware.md ("tipo Phoenix MC, paso de 3,81 mm |
| hub (USB hub) | concentrador | Already established in docs/es/user-guide/hardware.md:114-116 and appendices/design-files.md ("concentrador USB3"). |
| pinout | asignación de pines | Heading term in both pages. Already established in docs/es/user-guide/hardware.md:185,247. Chosen over "patillaje", which is Spain-marked. |
| VDC | V CC | Unit form, not a protocol name, so it is translated. Already established in docs/es/index.md:30, operation.md:43 and troubleshooting.md:11. |
| Load Equivalency Number (LEN) | número de equivalencia de carga (LEN) | NMEA 2000 term. Acronym kept in English because it is what the reader sees on cabling datasheets; the expansion is glossed once on first mention. |
| multi-talker / single-talker / single-talker-multiple-listener | multiemisor / de un solo emisor / de un emisor y varios receptores | RS-485 and NMEA 0183 topology terms used three times in interfaces.md. "Talker" has no established Spanish loan here; "emisor"/"receptor" is the stand |
| normally-open (NO) momentary switch | pulsador momentáneo normalmente abierto (NA) | Switch specification, not a UI string, so the abbreviation is translated (NO → NA) per Spanish electrical convention. |
| thermal pad | almohadilla térmica | Thermal management table in hardware.md. Distinct from "disipador térmico" (heat sink), which the glossary already covers. |
| half-duplex | semidúplex | RAE-accepted form; used once in the RS-485 section. |
| flexible flat cable (FFC) | cable plano flexible (FFC) | Used for the HDMI and MIPI connectors; the acronym stays English because it is the part-ordering term. |
| buck converter | convertidor reductor | Power supply table. "Convertidor buck" is also common but the Spanish form is unambiguous and needs no gloss. |
| receptacle (USB receptacle) / socket (M.2 Socket M) | conector hembra / zócalo | Two different English words for connector openings in hardware.md; kept distinct because the M.2 one is a card slot and the USB one is a cable port. |
| pigtail (panel connector) | latiguillo | Product name in the shop link in the RS-485 wiring section. |
| threaded insert / countersunk / gasket | inserto roscado / avellanado / junta | Mechanical specifications table; none appear in the glossary's enclosure section. |
| VDC (unit suffix, e.g. 32 VDC) | V CC | The glossary's units table covers V, A, Ω, °C, mm² but not the DC suffix. Spanish writes corriente continua, so the SI-spaced form is `32 V CC`. Appea |
| mounting ledge | resalte de montaje | errata.md, twice. Distinct from `punto de montaje` (mounting point, design-files.md) and from `superficie de montaje` (mounting surface, already in th |
| flash (casting defect, in quotes in the source) | rebaba | errata.md. The source quotes it as "flashes" and glosses it as leftover aluminium from casting. Standard Spanish foundry term. Written «rebabas» per r |
| inrush current | corriente de irrupción | errata.md. The glossary has `overcurrent` → sobrecorriente and `current limiting` → limitación de corriente, but not the power-up surge. `corriente de |
| copper pour / copper fill | vertido de cobre | design-files.md and errata.md. PCB-layout term; `relleno de cobre` used for the errata heading where the source says "Copper Fill", `vertidos de cobre |
| power plane / rail | plano de alimentación / línea | errata.md (`3.3V power plane` → plano de alimentación de 3,3 V) and design-files.md (`3.3V rail` → la línea de 3,3 V). Kept distinct because the sourc |
| solder nut | tuerca soldable | design-files.md, twice. |
| footprint (PCB component) | huella | design-files.md. Established KiCad terminology in Spanish. |
| opamp (operational amplifier) | amplificador operacional | design-files.md. |
| test point | punto de prueba | design-files.md. |
| silkscreen | serigrafía | design-files.md. The glossary already refers to "the board's own silkscreen labels" in the what-stays-English section but does not give the Spanish no |
| PCB layout | trazado del PCB | design-files.md. Verb form for `to re-route`: volver a trazar. |
| signal integrity | integridad de señal | design-files.md, twice. |
| cable plug (the loose connector supplied for custom wiring) | clavija de cable | index.md (`E7T cable plug` → Clavija de cable E7T). Distinct from `conector` (the mating connector on the enclosure) and from `conector cilíndrico (ba |
| cutout (in the enclosure, for an extra connector) | troquel | index.md (`cutouts for 2 extra SMA connectors`). Not the same as `orificio pretaladrado`, which the glossary reserves for holes the enclosure already  |
| thermal throttling | limitación térmica | troubleshooting.md. |
| runaway process | proceso desbocado | troubleshooting.md. |
| stray voltage | tensión parásita | troubleshooting.md, twice. The source says "stray voltages" injected by a connected device. |
| bus contention | contención en el bus | troubleshooting.md. |
| baud rate / bit rate (prose) | velocidad de transmisión | troubleshooting.md (`incorrect baud rate`). The glossary's number rules cover how to write `115200 bps` but not the prose noun. |
| differential signaling | señalización diferencial | troubleshooting.md (RS-485 A/B lines). |
| differential pair | par diferencial | design-files.md (`USB3 hub RX differential pairs`). |
| USB hub | concentrador | design-files.md. |
| clock oscillator | oscilador de reloj | design-files.md. |
| balancing circuit (super-capacitor) | circuito de equilibrado | design-files.md, twice. Verb/noun: equilibrado, not balanceo. |
| 3rd party | de terceros | ubuntu-installation.md (3rd party operating systems) and resources.md (third-party software compatibility). Used consistently across both. |
| user space | espacio de usuario | ubuntu-installation.md (`the user space halpid daemon`). |
| prebuilt package | paquete precompilado | ubuntu-installation.md. |
| command line tool | herramienta de línea de comandos | ubuntu-installation.md. The glossary keeps command names in English but does not give the phrase. |
| cross-compilation | compilación cruzada | integration.md. |
| custom image building | creación de imágenes personalizadas | integration.md. Built on the glossary's `imagen del sistema`. |
| security hardening | refuerzo de la seguridad | advanced-config.md. |
| backup and recovery (data, not power) | copia de seguridad y recuperación | advanced-config.md. Deliberately not `respaldo`, which the glossary assigns to the super-capacitor and RTC battery senses (`pila de respaldo`, `respal |
| performance tuning | ajuste del rendimiento | advanced-config.md. |
| power-on/off sequencing | secuenciación de encendido y apagado | power-supply.md. |
| brownout | caída de tensión | power-supply.md. Reuses the glossary's `voltage drop` → caída de tensión; kept distinct from `corte de corriente` (blackout), which the glossary alrea |
| load management | gestión de la carga | power-supply.md. |
| status reporting | notificación del estado | controller.md. Paired with the glossary's `monitoring` → supervisión in the same bullet. |
| CE marking | marcado CE | compliance.md. Official EU term. |
| environmental rating | clasificación ambiental | compliance.md. |
| chart plotter (plural) | plóteres cartográficos | index.md. Confirms the plural of the glossary's `plóter cartográfico`; plóteres, not plóters. |
| single-board computer | ordenador de placa única | index.md. Follows rule 6 on ordenador. |
| in-vehicle infotainment | infoentretenimiento a bordo | index.md. |
| telematics | telemática | index.md. |
| environmental sensing | detección ambiental | index.md. |
| quick start guide | guía de inicio rápido | index.md. Note this is the printed leaflet in the box, distinct from the nav section `Getting Started` → `Primeros pasos`, which mkdocs.yml already fi |
| goodie bag | bolsa de accesorios | index.md, image alt text only. |
| clean shutdown | apagado controlado | troubleshooting.md. The source varies its wording (`clean shutdown` here, `graceful shutdown` elsewhere) for one concept; Spanish keeps the single rendering the glossary already assigns to `graceful shutdown`. Not `apagado limpio`. |
| power connector / power socket | conector de alimentación | The English source alternates the two words for the same E7T port; Spanish uses one. `toma` is reserved for nothing here — see `receptacle / socket` above for the connector-opening senses. |
