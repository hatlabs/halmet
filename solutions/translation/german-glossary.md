---
title: German translation glossary and style rules (HALMET)
date: 2026-08-05
category: translation
module: documentation
problem_type: reference
component: documentation
severity: medium
applies_when:
  - Translating any page from docs/en/ into German under docs/de/
  - Reviewing a German translation for consistency
  - Adding a new term that has no established German equivalent
tags:
  - translation
  - i18n
  - german
  - terminology
  - mkdocs-static-i18n
---

# German translation glossary and style rules

## Context

The HALMET documentation is written in English under `docs/en/` and translated
into German under `docs/de/`, using the `mkdocs-static-i18n` folder structure.
Each language directory mirrors the same tree, so a translation keeps its
source's path and filename: `docs/en/hardware/index.md` becomes
`docs/de/hardware/index.md`. Only markdown lives under `docs/de/` — images and
other assets stay with the English source and are shared.

**This file began as a copy of the HALPI2 glossary and deliberately keeps its
decisions**, so that two Hat Labs products do not describe the same part with
two different German words. `carrier board` → `Trägerplatine` is the HALPI2
call and stands here too, as does every typography rule below. Terms below the
`## HALMET terms` heading are additions this product needed; everything above it
is shared with HALPI2, and a change to a shared row should be made in both
repositories or in neither.

Translations are produced page by page, at different times, potentially by
different people. Without a fixed terminology list the same English term drifts
across pages — *solder jumper* becomes `Lötbrücke` on one page and
`Lötjumper` on the next — and the result reads as machine output even when each
individual sentence is correct.

This file is the reference that prevents that drift. It is a living document:
extend it when a page introduces a term that is not listed here, rather than
inventing a one-off translation.

`finnish-glossary.md` was adapted from HALPI2 first and is the model this file
followed; the other glossaries in this directory are its siblings. The general
approach is the same in all of them; the rules below cover what is specific to
German.

Unlike the other files under `solutions/`, this one has no date in its filename
because it is meant to be edited in place, not superseded.

## Names that are never translated

Product names, protocol names, hardware standards, and software UI strings stay
in English. The device's own interface and toolchain are in English, so
translating a menu name or a build target would send the reader looking for
something that does not exist on screen.

- **Products and software:** HALMET, SH-ESP32, SH-RPi, SensESP, Signal K,
  Arduino IDE, ESP-IDF, ESPHome, PlatformIO, Hat Labs
- **Hardware and standards:** ESP32-WROOM-32E, ADS1115, NMEA 2000, CAN bus,
  I2C, 1-Wire, GPIO, JTAG, USB, ADC, TVS, PG7, PG9, SP13, M12, Phoenix MC,
  Schmitt trigger
- **Pin and signal names are copied exactly:** `D1`–`D4`, `A1`–`A4`, `SDA`,
  `SCL`, `DQ`, `TXD0`, `RXD0`, `EN`, `IO0`, `CCS`, `LP`, `VP`, `VN`, `3V3`,
  `GND`. These are printed on the board; a translated pin name sends the reader
  looking for a label that does not exist.
- **UI paths, commands, hostnames, file paths:** `main.cpp`, `ConnectAlarmSender()`,
  `can0`, and every command line quoted from the source.

Code fences, command output, URLs and image filenames are never touched.

**`CAN bus` in German prose.** The standard stays as written where it names the
standard (`CAN bus`), but German compounds it as `CAN-Bus` when it becomes part
of a sentence: `der CAN-Bus`, `CAN-Bus-Aktivität`. Both are correct; do not
write `CAN Bus` without the hyphen.

## Style rules

### No space before punctuation

**German does not put a space before `;` `:` `!` `?`** — write `Symptome:`, not
`Symptome :`.

This is stated explicitly because the French glossary requires the opposite, and
that rule cost a 334-site correction on its own branch. Do not carry the French
habit across. German's non-breaking spaces belong elsewhere: between a number
and its unit, and inside abbreviations like `z. B.`.

### Quotation marks

German uses `„…“` — low opening, high closing. Not `"…"`, and not the French
`« … »`.

### Address form

Instructions use the **Sie form imperative**, the standard register for German
consumer and installation manuals:

> Schließen Sie das Stromkabel an. Prüfen Sie die Polarität mit dem Multimeter,
> bevor Sie die Spannung einschalten.

Not the infinitive (*Kabel anschließen*), which reads as a parts list, and not
*du*.

Descriptive passages use a plain statement or the passive:

> Das Gerät schaltet sich automatisch ab, wenn die Stromversorgung getrennt wird.

### Compound nouns

German compounds a multi-word proper name with hyphens throughout, which the
English source does not:

- `NMEA-2000-Netzwerk`, `NMEA-2000-Bus`, `Signal-K-Server`,
  `Raspberry-Pi-Antenne`, `Compute-Module-5-Anschluss`
- `HALPI2-Gehäuse`, `E7T-Stecker`, `HaLOS-Image`, `USB-Tastatur`

On HALMET pages the same rule produces `HALMET-Platine`, `ESP32-WROOM-32E-Modul`,
`Phoenix-MC-Klemmenblock`, `1-Wire-Stiftleiste`, `I2C-Adresse`,
`Schmitt-Trigger-Eingang`, `CCS-Stiftleiste`.

A missing hyphen inside such a compound is the most visible marker of a
machine-translated German page.

### Units and numbers

Same handling as the other languages — the English source writes `12V` and
`0.9A`, and both are wrong in German.

| English source | German |
|:---------------|:-------|
| `12V`, `0.9A` | `12 V`, `0,9 A` |
| `5.5 x 2.1 mm` | `5,5 × 2,1 mm` |
| `-20°C to +60°C` | `−20 °C … +60 °C` |
| `120Ω` | `120 Ω` |
| `3-5A` | `3–5 A` (en dash for ranges) |

HALMET's pages add three recurring forms: `320 ohms` → `320 Ω`,
`2.54 mm pitch` → `2,54 mm Rastermaß`, and `+/- 30 V` → `±30 V`.

### Links, images, admonitions, navigation

Same as the sibling glossaries: paths are copied from the English source
unchanged and never carry an `en/`, `de/` or other language segment; image
captions and alt texts are translated but filenames are not; screenshots stay
English because the reader's own screen is English; standard admonition titles
are translated centrally in `mkdocs.yml`, custom ones in the page.

Two navigation entries are judgement calls worth recording:

- `Errata` → **Bekannte Fehler**. The Latin term is opaque to a general reader,
  and the page lists hardware defects that exist, not corrections to be applied.
- `Hardware Revisions` → **Hardware-Revisionen**. Board versions, not document
  revisions.

## Glossary

### Enclosure, mounting, and installation

| English | German | Note |
|:--------|:-------|:-----|
| carrier board | Trägerplatine | The accurate term, as in French — see the note below |
| enclosure | Gehäuse | |
| heat sink | Kühlkörper | |
| waterproof | wasserdicht | |
| wall-mount | Wandmontage | |
| mounting surface | Montagefläche | |
| pilot hole | Vorbohrung | |
| mounting template | Bohrschablone | |
| bilge | Bilge | |
| bulkhead | Schott | |
| cable gland | Kabelverschraubung | `PG7-Kabelverschraubung` |
| cable routing | Kabelführung | |
| service loop | Serviceschlaufe | |
| cable tie | Kabelbinder | |
| blind plug | Blindstopfen | |
| breather plug | Druckausgleichsstopfen | |

**A note on `Trägerplatine`.** German takes the accurate term, like French
(`carte porteuse`) and unlike Finnish (`emolevy`, literally *motherboard*, chosen
there for reader familiarity). The divergence between the three is deliberate,
decided per language and per audience. Do not harmonise them.

The practical consequence matches French: `Trägerplatine` carries the CM5/board
relationship on its own, so passages about reseating the CM5 or troubleshooting
a board that will not boot need no extra explanation. The Finnish glossary does
need that warning.

On HALMET the term does not apply at all — HALMET carries no module and is a
`Entwicklungsboard`, see the HALMET section. The row stays because it is shared,
not because these pages use it.

### Electrical

| English | German | Note |
|:--------|:-------|:-----|
| power supply | Stromversorgung | The unit itself: *Netzteil* |
| input voltage range | Eingangsspannungsbereich | |
| polarity | Polarität | |
| fuse | Sicherung | |
| inline fuse | Leitungssicherung | |
| circuit breaker | Leitungsschutzschalter | |
| current limiting | Strombegrenzung | |
| overcurrent | Überstrom | |
| voltage drop | Spannungsabfall | |
| grounding | Erdung | |
| short circuit | Kurzschluss | |
| wire gauge | Leiterquerschnitt | German uses mm², not AWG |
| marine-grade wire | seewasserfeste Leitung | |
| wire strippers | Abisolierzange | |
| crimping | Crimpen | |
| crimper | Crimpzange | |
| heat-shrink tubing | Schrumpfschlauch | |
| heat gun | Heißluftpistole | |
| multimeter | Multimeter | |
| terminal block | Klemmenblock | |
| strain relief | Zugentlastung | |
| super-capacitor | Superkondensator | |
| real-time clock | Echtzeituhr | |
| backup battery | Pufferbatterie | |

### Connectors and interfaces

| English | German | Note |
|:--------|:-------|:-----|
| connector | Stecker / Anschluss | *Anschluss* for a board-mounted socket |
| barrel connector | Hohlstecker | |
| header | Stiftleiste | `40-polige GPIO-Stiftleiste` |
| pin | Pin | |
| backbone | Backbone | Established in German NMEA 2000 usage |
| drop cable | Stichleitung | |
| T-connector | T-Stück | |
| termination (120 Ω) | Abschlusswiderstand | |
| front panel | Frontplatte | |
| jumper | Jumper | The removable link; see *solder jumper* in the HALMET section for the soldered kind |
| male / female | Stecker / Buchse | |

### System behaviour and status

| English | German | Note |
|:--------|:-------|:-----|
| boat computer | Bordcomputer | |
| to boot | starten | |
| first boot | erster Start | |
| shutdown | Herunterfahren | |
| graceful shutdown | geordnetes Herunterfahren | |
| power loss | Spannungsausfall | |
| blackout | Stromausfall | |
| power management | Energieverwaltung | |
| status LED | Status-LED | |
| monitoring | Überwachung | |
| passive cooling | passive Kühlung | |
| filesystem | Dateisystem | |
| to unmount | aushängen | |
| watchdog | Watchdog | |
| standby | Standby | |

### Software and networking

| English | German | Note |
|:--------|:-------|:-----|
| firmware | Firmware | |
| daemon | Daemon | |
| to flash | flashen | |
| operating system image | Systemabbild | |
| headless | ohne Bildschirm | First mention: `ohne Bildschirm (headless)` |
| container app | Container-Anwendung | |
| container image | Container-Image | |
| dashboard | Dashboard | |
| WiFi Access Point | WLAN-Access-Point | German prose says *WLAN*; keep *WiFi* only where it names a UI string or a physical label |
| wired / wireless | kabelgebunden / drahtlos | |
| credentials | Zugangsdaten | |
| default password | Standardpasswort | |
| single sign-on (SSO) | Single Sign-on (SSO) | |
| Certificate Authority (CA) | Zertifizierungsstelle (CA) | |
| web interface | Weboberfläche | |
| browser | Browser | |

### Applications and use cases

| English | German | Note |
|:--------|:-------|:-----|
| chart plotter | Kartenplotter | |
| data logging | Datenaufzeichnung | |
| vessel | Schiff | |
| fleet management | Flottenmanagement | |
| predictive maintenance | vorausschauende Wartung | |
| remote monitoring | Fernüberwachung | |
| compliance | Konformität | |
| warranty | Garantie | |

## HALMET terms

HALMET is a sensor interface board, so it needs vocabulary HALPI2 never used:
input circuits, measurement, and the things printed on a small PCB. Rows above
this heading are shared with HALPI2 and should not be changed here alone.

### Board and inputs

| English | German | Note |
|:--------|:-------|:-----|
| development board | Entwicklungsboard | HALMET is sold as one; not *Trägerplatine*, which is HALPI2's carrier board |
| digital input | Digitaleingang | `D1`–`D4` stay as printed |
| analog input | Analogeingang | `A1`–`A4` stay as printed |
| input | Eingang | |
| output | Ausgang | |
| sender | Geber | The marine sender a gauge reads. Never *Sender*, which in German means a radio transmitter or broadcast station |
| tank sender | Tankgeber | |
| resistive sender | Widerstandsgeber | |
| gauge (engine panel gauge) | Anzeigeinstrument | `Motorinstrument` where the engine panel is meant; never *Messgerät*, which is a test instrument |
| counter | Zähler | |
| chain counter | Kettenzähler | |
| alarm signal | Alarmsignal | |
| engine RPM | Motordrehzahl | Not *RPM*; German prose uses `1/min` or `U/min` for the unit |
| tachometer | Drehzahlmesser | |
| alternator W terminal | W-Klemme der Lichtmaschine | `W-Klemme` alone after first mention |
| fuel flow | Kraftstoffdurchfluss | |
| bilge alarm | Bilgenalarm | |
| pulse | Impuls | `Impulszähler` for the firmware's pulse counter |

### Measurement and circuits

| English | German | Note |
|:--------|:-------|:-----|
| galvanic isolation | galvanische Trennung | Not *Isolierung*, which is insulating material |
| isolated (section, area) | galvanisch getrennt | `galvanisch getrennter Bereich`; shortened to `getrennter Bereich` after first mention |
| digital isolator | Digitalisolator | |
| isolation barrier | Trennstelle | `galvanische Trennstelle` on first mention |
| ground loop | Masseschleife | Boat DC grounds; not *Erdschleife*, which belongs to mains earthing |
| analog-to-digital converter (ADC) | Analog-Digital-Wandler (ADC) | The part number `ADS1115` stays |
| resolution (16-bit) | Auflösung | `16-Bit-Auflösung` |
| sampling rate | Abtastrate | |
| low-pass filter | Tiefpassfilter | |
| cutoff frequency | Grenzfrequenz | |
| noise (electrical) | Störungen | Not *Rauschen*, which is broadband noise specifically, and never *Lärm* or *Geräusch*, which are sound |
| noise immunity | Störfestigkeit | |
| voltage divider | Spannungsteiler | |
| constant current source (CCS) | Konstantstromquelle | The header label `CCS` stays as printed |
| excitation voltage | Speisespannung | *Erregerspannung* is the literal bridge-measurement term; `Speisespannung` is what a boat electrician reads |
| passive voltage measurement | passive Spannungsmessung | |
| active resistance measurement | aktive Widerstandsmessung | |
| pull-up resistor | Pull-up-Widerstand | Hyphenated both sides; not *Pullup-Widerstand* |
| pull-down resistor | Pull-down-Widerstand | |
| threshold voltage | Schwellenspannung | |
| hysteresis | Hysterese | |
| floating (input) | undefiniertes Potenzial | `der Eingang liegt auf undefiniertem Potenzial`. **Never *potentialfrei*** — see the note below |
| normally open / normally closed | Schließer / Öffner | The established German switch terms; see the note below |
| self-resetting fuse | selbstrückstellende Sicherung | The PTC type; *rückstellbare Sicherung* is also read |
| reverse polarity protection | Verpolungsschutz | |
| overvoltage protection | Überspannungsschutz | |
| switching power supply | Schaltnetzteil | |
| current consumption | Stromaufnahme | Not *Stromverbrauch*, which is energy over time |
| short circuit | Kurzschluss | Inherited row; the sense is the same here |
| chafing (of a wire) | Scheuern | `Scheuerstellen` for the damaged spots |
| voltage spike | Spannungsspitze | |

**A note on `normally open` / `normally closed`.** German has established
single-word terms: a normally open contact is a **Schließer** (it closes on
actuation), a normally closed contact an **Öffner** (it opens on actuation).
Use them. A literal *normalerweise offen / normalerweise geschlossen* is
readable but marks the page as translated, and worse, it inverts easily under
editing — `Schließer` and `Öffner` cannot be got backwards by accident because
each names what the switch *does*. Write `Schließer (normally open)` on first
mention if the reader is likely to be matching against an English datasheet.

**A note on `floating`.** German `potentialfrei` is a false friend here. It
means galvanically isolated — a volt-free contact, a *good* property, and the
one HALMET's isolation barrier actually provides. The English source's
*floating* means the opposite kind of thing: an input left undriven, sitting at
an undefined level and reading high or low at random. Rendering that as
`potentialfrei` tells the reader the circuit is fine when the page is telling
them to enable a pull-down resistor. Write `undefiniertes Potenzial` or
`unbeschalteter Eingang`.

### Board features and assembly

| English | German | Note |
|:--------|:-------|:-----|
| jumper | Jumper | Inherited row. The removable link placed on a pin pair — see the note below |
| jumper header | Jumper-Stiftleiste | The pin pair a jumper is placed on; `CCS-Stiftleiste` |
| solder jumper | Lötbrücke | Closed permanently with solder, not with a removable jumper — see the note below |
| to short (a jumper) | schließen | `die Lötbrücke schließen`, `die Kontakte brücken` |
| solder pad | Lötpad | *Lötfläche* is equally correct; pick one per page |
| unpopulated | unbestückt | `unbestückte Lötpads` |
| pitch (2.54 mm) | Rastermaß | `2,54 mm Rastermaß` |
| pluggable terminal block | steckbarer Klemmenblock | Phoenix MC type; `Klemmenblock` alone is the shared HALPI2 term |
| silkscreen | Bestückungsdruck | Not *Siebdruck*, which names the printing process, not the layer |
| to solder | löten | |
| soldering iron | Lötkolben | |
| grommet | Kabeltülle | Rubber or silicone; distinct from `Kabelverschraubung`, the threaded gland |
| step drill bit | Stufenbohrer | The one that looks like a metal Christmas tree |
| conical drill bit | Kegelbohrer | |
| panel connector | Einbausteckverbinder | `Einbaustecker` / `Einbaubuchse` when the gender matters |
| reset button | Reset-Taster | The board's own labels `Reset` and `Boot` stay in English |
| boot button | Boot-Taster | |
| bootloader | Bootloader | |
| download mode | Download-Modus | The ESP32 flashing mode |
| user-programmable LED | benutzerprogrammierbare LED | |
| open hardware | Open Hardware | The movement and licence family; add `offene Hardware` in parentheses on first mention |

**A note on `Lötbrücke` and `Jumper`.** These are two different things and the
page tells the reader to do two different things with them:

- A **Lötbrücke** (solder jumper) is a pair of pads on the PCB, closed
  permanently with a soldering iron. HALMET's CAN terminator, low-pass filter,
  pull-up, pull-down and ADS1115 address selections are all Lötbrücken, all on
  the underside of the board.
- A **Jumper** is a removable plastic link pushed onto a pin pair. HALMET's
  constant-current source is enabled this way, with a Jumper on the `CCS`
  header.

Rendering both as *Jumper*, or both as *Brücke*, sends the reader either
reaching for a soldering iron they do not need or trying to pull off something
that is soldered down. Keep `Lötbrücke` for the pads and `Jumper` for the link,
and never write *Lötjumper* or *Jumperbrücke*.

### A note on `Stecker`, `Anschluss` and `Stiftleiste`

The shared glossary splits `connector` into `Stecker` (the plug) and `Anschluss`
(the board-mounted socket), and renders `header` as `Stiftleiste`. That split is
kept, and HALMET needs it more than HALPI2 did, because the source puts the two
words side by side — *1-Wire header connector*, *analog input connectors*,
*panel connector*. Resolve each by what the thing is rather than by the English
wording: `1-Wire-Stiftleiste` (a pin strip on the board),
`Analogeingangs-Anschlüsse` (sockets on the board),
`Einbausteckverbinder` (the connector through the enclosure wall). Do not
translate *header connector* as two words.

## Verification

A translated page is not done until:

1. `uv run mkdocs build --strict` passes — the same command CI runs.
2. `uv run python scripts/check_typography.py de` reports no faults — this is
   what catches a French space before a colon or a `"…"` pair that should be
   `„…“`.
3. `uv run python scripts/check_glossary.py de` reports no unused prescribed
   term.
4. `uv run python scripts/translation_status.py` shows the page as current.
5. `uv run mkdocs serve` shows the page rendering correctly in the browser, with
   lists as lists (see
   `../best-practices/markdown-lists-need-blank-line-2026-05-16.md` — the
   blank-line rule applies identically to German pages).
6. Every term used on the page that appears in this glossary matches it.

## Related

- `finnish-glossary.md` and the other glossaries in this directory — the siblings
- `/Users/helmi/projects/halpi2/solutions/translation/german-glossary.md` — the
  source this file was copied from; shared rows must change in both or neither
- `solutions/best-practices/markdown-lists-need-blank-line-2026-05-16.md`
- mkdocs-static-i18n documentation: https://ultrabug.github.io/mkdocs-static-i18n/
