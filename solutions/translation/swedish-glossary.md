---
title: Swedish translation glossary and style rules (HALMET)
date: 2026-08-05
category: translation
module: documentation
problem_type: reference
component: documentation
severity: medium
applies_when:
  - Translating any page from docs/en/ into Swedish under docs/sv/
  - Reviewing a Swedish translation for consistency
  - Adding a new term that has no established Swedish equivalent
tags:
  - translation
  - i18n
  - swedish
  - terminology
  - mkdocs-static-i18n
---

# Swedish translation glossary and style rules

## Context

The HALMET documentation is written in English under `docs/en/` and translated
into Swedish under `docs/sv/`, using the `mkdocs-static-i18n` folder structure.
Each language directory mirrors the same tree, so a translation keeps its
source's path and filename: `docs/en/hardware/index.md` becomes
`docs/sv/hardware/index.md`. Every page in this repository is an
`<section>/index.md`, so the eight sections are the eight files. Only markdown
lives under `docs/sv/`; images and other assets stay with the English source and
are shared.

**This file began as a copy of the HALPI2 glossary and deliberately keeps its
decisions**, so that two Hat Labs products do not describe the same part with two
different Swedish words. `carrier board` → `bärkort` stands here too, as do the
four typography rules and every row above the HALMET heading. Terms below the
HALMET heading are additions this product needed; everything above it is shared
with HALPI2, and **a change to a shared row must be made in both repositories or
in neither**.

`finnish-glossary.md` is the sibling that was adapted for HALMET first, and the
French and German files carry the same shared core. The general approach is the
same in all of them.

Translations are produced page by page, at different times, potentially by
different people. Without a fixed terminology list the same English term drifts
across pages — *solder jumper* becomes `lödbygel` on one page and `lödbrygga` on
the next — and the result reads as machine output even when each individual
sentence is correct.

This file is the reference that prevents that drift. It is a living document:
extend it when a page introduces a term that is not listed here, rather than
inventing a one-off translation. Like the other glossaries it has no date in its
filename, because it is meant to be edited in place, not superseded.

## Four rules where the siblings are wrong for Swedish

Read this section before anything else. Every one of these is stated the
opposite way in at least one sibling glossary, and carrying the wrong habit
across has already cost two correction rounds on earlier branches.

1. **Address the reader as `du`, not formally.** Swedish technical and consumer
   documentation uses `du`. French uses *vouvoiement* and German uses *Sie* —
   both wrong here. `Anslut strömkabeln.` / `Kontrollera polariteten med
   multimetern innan du slår på spänningen.`

2. **Quotation marks are `”…”`** — the *same* character (U+201D) on both sides.
   Not German's `„…“`, not French's `« … »`, not straight `"…"`.

3. **No space before `; : ! ?`** — as in German, and unlike French, whose rule is
   the exact opposite and demands a no-break space.

4. **Compounding with a proper name takes one hyphen at the junction, not
   throughout.** Swedish writes `NMEA 2000-nätverk`, `Signal K-server`,
   `Raspberry Pi-antenn`. German writes `NMEA-2000-Netzwerk` — hyphens all the
   way through. Copying the German pattern into Swedish is wrong, and it is the
   single most likely way this glossary gets violated.

## Names that are never translated

Identical in principle to the sibling glossaries; only the product list is
HALMET's. Product names, protocol names, hardware standards and software UI
strings stay in English.

- **Products and software:** HALMET, SH-ESP32, SH-RPi, SensESP, Signal K,
  Arduino IDE, ESP-IDF, ESPHome, PlatformIO, Hat Labs
- **Hardware and standards:** ESP32-WROOM-32E, ADS1115, NMEA 2000, CAN bus, I2C,
  1-Wire, GPIO, JTAG, USB, ADC, TVS, PG7, PG9, SP13, M12, Phoenix MC, Schmitt
  trigger
- **Pin and signal names are copied exactly:** `D1`–`D4`, `A1`–`A4`, `SDA`,
  `SCL`, `DQ`, `TXD0`, `RXD0`, `EN`, `IO0`, `CCS`, `LP`, `VP`, `VN`, `3V3`,
  `GND`. These are printed on the board; a translated pin name sends the reader
  looking for a label that does not exist.
- **UI paths, commands, file names:** `main.cpp`, `ConnectAlarmSender()`, and
  every command, hostname and file path

Compounds follow rule 4 above — one hyphen at the junction, none inside the
name: `HALMET-kortet`, `ESP32-modulen`, `1-Wire-givare`, `I2C-buss`,
`NMEA 2000-nätverk`, `Phoenix MC-plint`, `ADS1115-omvandlaren`.

Code fences, command output, URLs and image filenames are never touched.

## Units and numbers

Same handling as the other languages — the English source writes `12V` and
`0.9A`, and both are wrong in Swedish.

| English source | Swedish |
|:---------------|:--------|
| `12V`, `0.9A` | `12 V`, `0,9 A` |
| `5.5 x 2.1 mm` | `5,5 × 2,1 mm` |
| `-20°C to +60°C` | `−20 °C … +60 °C` |
| `120Ω` | `120 Ω` |
| `3-5A` | `3–5 A` (en dash for ranges) |

## Links, images, admonitions, navigation

Same as the sibling glossaries: paths are copied from the English source
unchanged and never carry a language segment; image captions and alt texts are
translated but filenames are not; screenshots stay English because the reader's
own screen is English; standard admonition titles are translated centrally in
`mkdocs.yml`, custom ones in the page.

Navigation titles live in `mkdocs.yml` under the i18n plugin's
`nav_translations`, which is their single source of truth; the list is not
restated here. Three entries are judgement calls worth recording:

- `Errata` → **Kända fel**. The page lists known hardware defects, not
  corrections to be made, and the Latin term is opaque to a general reader.
- `Hardware` → **Hårdvara**, not *maskinvara*. Datatermgruppen prefers
  *maskinvara* for computing in general, but this is a physical board, the trade
  writes `hårdvara`, and `öppen hårdvara` is the established rendering of *open
  hardware*. Use `hårdvara` throughout, including `Hardware Revisions` →
  **Hårdvaruversioner**.
- `Tutorials and Examples` → **Guider och exempel**. *Handledningar* reads
  academic; `guider` is what Swedish technical sites call these.

When a page is added to the nav in English, add its Swedish title in the same
change — an untranslated entry silently falls back to English.

## Glossary

### Enclosure, mounting, and installation

| English | Swedish | Note |
|:--------|:--------|:-----|
| carrier board | bärkort | The accurate term, as in French and German |
| enclosure | kapsling | |
| heat sink | kylfläns | |
| waterproof | vattentät | |
| wall-mount | väggmontage | |
| mounting surface | monteringsyta | |
| pilot hole (to drill) | förborra (verb) | `Förborra hålen` — never `borra förborrade hål` |
| pre-drilled hole (already there) | förborrat hål | The holes the enclosure ships with |
| mounting template | borrmall | |
| bilge water | slagvatten | |
| bulkhead | skott | |
| cable gland | kabelgenomföring | |
| cable routing | kabeldragning | |
| service loop | servicelänga | Slack left at both cable ends |
| cable tie | buntband | |
| blind plug | blindplugg | |
| breather plug | tryckutjämningsplugg | |

**A note on `bärkort`.** Swedish takes the accurate term, like French
(`carte porteuse`) and German (`Trägerplatine`), and unlike Finnish (`emolevy`,
literally *motherboard*, chosen there for reader familiarity). The divergence
between the four is deliberate, decided per language and per audience. Do not
harmonise them.

`bärkort` carries the CM5/board relationship on its own, so passages about
reseating the CM5 or troubleshooting a board that will not boot need no extra
explanation. Only the Finnish glossary needs that warning.

### Electrical

| English | Swedish | Note |
|:--------|:--------|:-----|
| power supply | strömförsörjning | The unit itself: *nätaggregat* |
| input voltage range | inspänningsområde | |
| polarity | polaritet | |
| fuse | säkring | |
| inline fuse | linjesäkring | |
| circuit breaker | automatsäkring | |
| current limiting | strömbegränsning | |
| overcurrent | överström | |
| voltage drop | spänningsfall | |
| grounding | jordning | |
| short circuit | kortslutning | |
| wire gauge | ledararea | Swedish uses mm², not AWG |
| marine-grade wire | sjövattenbeständig ledare | |
| wire strippers | avisoleringstång | |
| crimping | krimpning | |
| crimper | krimptång | |
| heat-shrink tubing | krympslang | |
| heat gun | varmluftspistol | |
| multimeter | multimeter | |
| terminal block | kopplingsplint | |
| strain relief | dragavlastning | |
| super-capacitor | superkondensator | |
| real-time clock | realtidsklocka | |
| backup battery | backupbatteri | |

### Connectors and interfaces

| English | Swedish | Note |
|:--------|:--------|:-----|
| connector | kontakt / anslutning | *anslutning* for a board-mounted socket |
| barrel connector | hålkontakt | |
| header | stiftlist | `40-polig GPIO-stiftlist` |
| pin | stift | |
| backbone | backbone | Established in Swedish NMEA 2000 usage |
| drop cable | stickledning | |
| T-connector | T-koppling | |
| termination (120 Ω) | termineringsmotstånd | |
| front panel | frontpanel | |
| jumper | bygel | |
| male / female | hane / hona | |

### System behaviour and status

| English | Swedish | Note |
|:--------|:--------|:-----|
| boat computer | båtdator | |
| to boot | starta | |
| first boot | första start | |
| shutdown | avstängning | |
| graceful shutdown | kontrollerad avstängning | |
| power loss | spänningsbortfall | |
| blackout | strömavbrott | |
| power management | strömhantering | |
| status LED | status-LED | |
| monitoring | övervakning | |
| passive cooling | passiv kylning | |
| filesystem | filsystem | |
| to unmount | avmontera | |
| watchdog | watchdog | |
| standby | vänteläge | |

### Software and networking

| English | Swedish | Note |
|:--------|:--------|:-----|
| firmware | firmware | Not *fast programvara* — matches the sibling decision to keep the trade term |
| daemon | daemon | |
| to flash | flasha | |
| operating system image | systemavbild | |
| headless | utan skärm | First mention: `utan skärm (headless)` |
| container app | containerapp | |
| container image | containeravbild | |
| dashboard | instrumentpanel | Homarr's *dashboard* view |
| WiFi Access Point | WiFi-accesspunkt | |
| wired / wireless | trådbunden / trådlös | |
| credentials | inloggningsuppgifter | |
| default password | standardlösenord | |
| single sign-on (SSO) | enkel inloggning (SSO) | |
| Certificate Authority (CA) | certifikatutfärdare (CA) | |
| web interface | webbgränssnitt | |
| browser | webbläsare | |

### Applications and use cases

| English | Swedish | Note |
|:--------|:--------|:-----|
| chart plotter | kartplotter | |
| data logging | datalagring | |
| vessel | fartyg | |
| fleet management | flotthantering | |
| predictive maintenance | förebyggande underhåll | |
| remote monitoring | fjärrövervakning | |
| compliance | överensstämmelse | |
| warranty | garanti | |

## HALMET terms

HALMET is a sensor interface board, so it needs vocabulary HALPI2 never used:
input circuits, measurement, and the things printed on a small PCB. Rows above
this heading are shared with HALPI2 and must not be changed here alone.

### Board and inputs

| English | Swedish | Note |
|:--------|:--------|:-----|
| development board | utvecklingskort | HALMET is sold as one; not `bärkort`, which is HALPI2's carrier board |
| digital input | digital ingång | `D1`–`D4` stay as printed |
| analog input | analog ingång | `A1`–`A4` stay as printed |
| input | ingång | The terminal on the board; an incoming signal is `insignal` |
| output | utgång | |
| sender | givare | The marine sender a gauge reads; *sändare* would mean a radio transmitter |
| tank sender | tankgivare | |
| resistive sender | resistiv givare | |
| gauge (engine panel gauge) | mätare | `mätaren i motorpanelen`; the panel as a whole is `motorinstrumenten` |
| counter | räknare | |
| chain counter | kättingräknare | Anchor chain is `ankarkätting`, never *kedja* in this sense |
| alarm signal | larmsignal | |
| engine RPM | motorns varvtal | Not *RPM* in prose; specifications write `varv/min` |
| tachometer | varvräknare | |
| alternator W terminal | generatorns W-uttag | *alternator* is `generator` in Swedish; spelled out, `växelströmsgenerator` |
| fuel flow | bränsleflöde | |

### Measurement and circuits

| English | Swedish | Note |
|:--------|:--------|:-----|
| galvanic isolation | galvanisk isolation | Adjective: `galvaniskt isolerad` |
| isolated (section, area) | isolerad | `isolerad sektion`, `isolerat område` |
| digital isolator | digital isolator | |
| isolation barrier | isolationsbarriär | |
| ground loop | jordslinga | |
| analog-to-digital converter (ADC) | AD-omvandlare | Spelled out: `analog-digital-omvandlare`. The part name `ADS1115` stays |
| resolution (16-bit) | upplösning | `16 bitars upplösning` |
| sampling rate | samplingsfrekvens | `860 sampel per sekund` |
| low-pass filter | lågpassfilter | The `LP` solder jumper keeps its printed label |
| cutoff frequency | gränsfrekvens | *brytfrekvens* also occurs in Swedish; pick `gränsfrekvens` throughout |
| noise (electrical) | brus | Not *buller*, which is sound. Interference coupled in from outside is `störning` |
| noise immunity | störningstålighet | What the Schmitt trigger improves |
| voltage divider | spänningsdelare | |
| constant current source (CCS) | konstantströmkälla | The header label `CCS` stays as printed |
| excitation voltage | matningsspänning | Write `matningsspänning till givaren` so it is not read as the board's own `strömförsörjning`. *excitationsspänning* is correct but rare outside datasheets |
| passive voltage measurement | passiv spänningsmätning | |
| active resistance measurement | aktiv resistansmätning | The quantity is `resistans`; `motstånd` is the component |
| pull-up resistor | pull-up-motstånd | Loan kept — see the note below |
| pull-down resistor | pull-down-motstånd | |
| threshold voltage | tröskelspänning | |
| hysteresis | hysteres | |
| floating (input) | flytande | `ingången blir flytande` |
| normally open / normally closed | slutande / brytande | The established Swedish switch terms: `slutande kontakt` = NO, `brytande kontakt` = NC. Not the literal *normalt öppen / normalt sluten*. Add `(NO)` / `(NC)` on first mention |
| self-resetting fuse | självåterställande säkring | |
| reverse polarity protection | polvändningsskydd | One word; no literal *omvänd polaritet*-construction |
| overvoltage protection | överspänningsskydd | |
| switching power supply | switchat nätaggregat | The shared table renders *power supply* as `strömförsörjning` and the unit itself as `nätaggregat`; this is the unit |
| current consumption | strömförbrukning | |
| short circuit | kortslutning | Already in the shared Electrical table with the same sense — repeated here only because HALMET's chafing warning uses it |
| chafing (of a wire) | skavning | `skador på grund av skavning` |

### Board features and assembly

| English | Swedish | Note |
|:--------|:--------|:-----|
| jumper | bygel | Already in the shared Connectors table, same sense: a removable link on a pin pair. See *solder jumper* for the PCB kind |
| jumper header | bygelstift | The pin pair a `bygel` is placed on; `stiftlist` is the shared word for a header in general |
| solder jumper | lödbygel | Closed permanently with solder, not with a removable `bygel` — the reader needs a soldering iron for one and not the other. Never `lödbrygga`, which is an accidental solder bridge |
| to short (a jumper) | kortsluta | `löd ihop lödbygeln` for the soldered kind, `sätt en bygel över stiften` for the removable kind |
| pad (solder pad) | lödyta | |
| unpopulated | obestyckad | `obestyckade lödytor`; a header not fitted at the factory is `inte monterad` |
| pitch (2.54 mm) | stiftavstånd | `2,54 mm stiftavstånd` |
| pluggable terminal block | löstagbar kopplingsplint | Phoenix MC type; `kopplingsplint` alone is the shared HALPI2 term |
| silkscreen | monteringstryck | The printed text and outlines on the PCB. The errata page's *back side silk screen* → `monteringstrycket på undersidan` |
| to solder | löda | |
| soldering iron | lödkolv | |
| grommet | gummigenomföring | Rubber or silicone; distinct from `kabelgenomföring`, the threaded gland in the shared table |
| step drill bit | stegborr | The one that looks like a metal Christmas tree |
| conical drill bit | koniskt borr | |
| panel connector | panelkontakt | The one mounted in the enclosure wall |
| reset button | reset-knapp | The board's own labels `Reset` and `Boot` stay in English |
| boot button | boot-knapp | |
| bootloader | bootloader | Kept in English, like `firmware` and `daemon` in the shared table |
| download mode | nedladdningsläge | The ESP32 flashing mode; first mention `nedladdningsläge (download mode)` |
| user-programmable LED | användarstyrd LED | |
| open hardware | öppen hårdvara | HALMET's licence statement |

### A note on `pull-up-motstånd`

Swedish electronics keeps the English *pull-up* and *pull-down* and compounds
them with a hyphen: `pull-up-motstånd`, `pull-down-motstånd`, `pull-down-bygeln`.
Translated forms such as *uppdragningsmotstånd* are not established, and they
would also break the link to the schematics and the board labels the reader has
in front of them. Finnish translates these (`ylösvetovastus`) — the divergence is
deliberate and decided per language, exactly as with `bärkort` / `emolevy`. Do
not harmonise them.

### A note on `bygel` and `lödbygel`

These are two different objects and the reader acts differently on each. A
`bygel` is a removable link pushed onto a pin pair — the `CCS` jumper headers,
which are enabled by placing one. A `lödbygel` is a pad pair on the PCB that is
closed permanently with a soldering iron — the `LP`, pull-up, pull-down, CAN
terminator and ADS1115 address jumpers on the bottom side. Confusing them sends
the reader either for a soldering iron they do not need, or trying to pull off
something that is soldered down. When the English says only *jumper*, decide from
the context which one it is; the bottom-side ones are always `lödbyglar`.

### A note on `kontakt`, `stiftlist` and `plint`

HALMET puts *connector* and *header* side by side far more often than HALPI2 does
— *1-Wire header connector*, *I2C header connector*, *analog input connectors*.
The shared split is kept: `kontakt` / `anslutning` for a connector, `stiftlist`
for a pin header. Where the English doubles the words (*header connector*), use
`stiftlist` alone — Swedish does not need both. The pluggable input connectors
are `plintar` (`löstagbar kopplingsplint`), and the one in the enclosure wall is
a `panelkontakt`.

### Numbers on HALMET pages

The shared units table applies unchanged. Three forms occur only in this
repository:

| English source | Swedish |
|:---------------|:--------|
| `320 ohms`, `100 kohm` | `320 Ω`, `100 kΩ` |
| `+/- 30 V`, `-32V and +32V` | `±30 V`, `−32 V och +32 V` |
| `2x10 pin`, `4-pin` | `2×10 stift`, `4-poligt` |

## Verification

A translated page is not done until:

1. `uv run mkdocs build --strict` passes.
2. `uv run check-anchors site` passes.
3. `uv run translation-status` shows the page as current.
4. `uv run check-glossary sv` passes — it catches a prescribed
   term the pages never actually use.
5. `uv run check-typography sv` passes.
6. Structure matches the source — see `.claude/skills/translate-page/SKILL.md`.
7. Every term used on the page that appears in this glossary matches it.
8. **The four rules at the top are tested against the pages, not re-read.** A
   half-applied typography rule looks followed when you read it. Both the French
   and German branches shipped one to review because it was read rather than
   measured.

## Related

- `finnish-glossary.md` — the sibling adapted for HALMET first
- `.claude/skills/translate-page/SKILL.md` — the procedure
- The HALPI2 repository's `solutions/translation/swedish-glossary.md` — the
  source of every row above the HALMET heading; a shared row changes in both
  files or in neither
