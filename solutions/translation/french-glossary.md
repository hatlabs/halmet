---
title: French translation glossary and style rules (HALMET)
date: 2026-08-05
category: translation
module: documentation
problem_type: reference
component: documentation
severity: medium
applies_when:
  - Translating any page from docs/en/ into French under docs/fr/
  - Reviewing a French translation for consistency
  - Adding a new term that has no established French equivalent
tags:
  - translation
  - i18n
  - french
  - terminology
  - mkdocs-static-i18n
---

# French translation glossary and style rules

## Context

The HALMET documentation is written in English under `docs/en/` and translated
into French under `docs/fr/`, using the `mkdocs-static-i18n` folder structure.
Each language directory mirrors the same tree, so a translation keeps its
source's path and filename: `docs/en/hardware/index.md` becomes
`docs/fr/hardware/index.md`. Only markdown lives under `docs/fr/` — images and
other assets stay with the English source and are shared.

**This file began as a copy of the HALPI2 glossary and deliberately keeps its
decisions**, so that two Hat Labs products do not describe the same part with
two different French words. `carrier board` → `carte porteuse` is the HALPI2
call and stands here too, including its deliberate divergence from the Finnish
`emolevy`. Terms below the HALMET heading are additions this product needed;
everything above it is shared with HALPI2, and a change to a shared row should
be made in both repositories or in neither.

Translations are produced page by page, at different times, potentially by
different people. Without a fixed terminology list the same English term drifts
across pages — *drop cable* becomes `câble de dérivation` on one page and
`câble de descente` on the next — and the result reads as machine output even
when each individual sentence is correct.

This file is the reference that prevents that drift. It is a living document:
extend it when a page introduces a term that is not listed here, rather than
inventing a one-off translation.

The Finnish glossary (`finnish-glossary.md`) is the sibling of this file and the
place to look for the general approach. The rules below cover what is specific
to French.

Unlike the other files under `solutions/`, this one has no date in its filename
because it is meant to be edited in place, not superseded.

## Names that are never translated

Product names, protocol names, hardware standards, and software UI strings stay
in English — the device's own interface is in English, so translating a menu
name would send the reader looking for something that does not exist on screen.

- **Products and software:** HALMET, SH-ESP32, SH-RPi, SensESP, Signal K,
  Arduino IDE, ESP-IDF, ESPHome, PlatformIO, Hat Labs
- **Hardware and standards:** ESP32-WROOM-32E, ADS1115, NMEA 2000, CAN bus,
  I2C, 1-Wire, GPIO, JTAG, USB, ADC, TVS, PG7, PG9, SP13, M12, Phoenix MC,
  Schmitt trigger, IoT
- **Pin and signal names are copied exactly:** `D1`–`D4`, `A1`–`A4`, `SDA`,
  `SCL`, `DQ`, `TXD0`, `RXD0`, `EN`, `IO0`, `GPIO2`, `CCS`, `LP`, `VP`, `VN`,
  `3V3`, `GND`. These are printed on the board; a translated pin name sends the
  reader looking for a label that does not exist.
- **UI paths, commands, hostnames, file paths:** `main.cpp`,
  `ConnectAlarmSender()`, and every command, hostname and path in the same
  position.

Code fences, command output, URLs and image filenames are never touched.

## Style rules

### Address form

Instructions use **the second person plural imperative** (*vouvoiement*):

> Branchez le câble d'alimentation. Vérifiez la polarité au multimètre avant de
> mettre sous tension.

Not the infinitive (*Brancher le câble*), which reads as a parts list rather
than guidance, and not *tu*.

Descriptive passages use a plain statement or the passive:

> L'appareil s'éteint automatiquement lorsque l'alimentation est coupée.

### Typography

French typography is stricter than English and this is the most common source of
sloppy-looking translated pages. The space before `; : ! ?` is not decoration:
an ordinary space lets the line break in front of the punctuation, which is the
first thing a French reader notices.

U+00A0 rather than U+202F (narrow no-break): U+202F is the typographically
precise character but renders inconsistently across fonts, while U+00A0 is
universally supported and is what French technical documentation uses in
practice.

- **No-break space (U+00A0) before** `;` `:` `!` `?` and inside `« »`
- **Guillemets** `« … »` for quotations, not `"…"`
- **Decimal comma**, as in Finnish: `0,9 A`, `5,5 × 2,1 mm`
- **Space before the unit**: `12 V`, `250 kbit/s`, `−20 °C`
- **En dash for ranges**: `3–5 A`

`scripts/check_typography.py fr` enforces the quotation pairing and the
no-break space; it is the one check that is different for French than for every
sibling language, so do not assume a clean run in another language says
anything about this one.

### Units and numbers

Identical handling to Finnish — the English source writes `12V` and `0.9A`, and
both are wrong in French. Convert every one.

| English source | French |
|:---------------|:-------|
| `12V`, `0.9A` | `12 V`, `0,9 A` |
| `5.5 x 2.1 mm` | `5,5 × 2,1 mm` |
| `-20°C to +60°C` | `−20 °C … +60 °C` |
| `120Ω` | `120 Ω` |
| `5-32 V` | `5–32 V` (en dash for ranges) |
| `100 kohm` | `100 kΩ` |

`+/- 30 V` in the source is written `±30 V`.

### Links, images, admonitions, navigation

Same rules as the Finnish glossary: paths are copied from the English source
unchanged and never carry an `en/` or `fr/` segment; image captions and alt
texts are translated but filenames are not; screenshots stay English because the
reader's own screen is English; standard admonition titles are translated
centrally in `mkdocs.yml`, custom ones in the page.

Two navigation entries are judgement calls worth recording:

- `Errata` → **Problèmes connus**. The page lists known hardware defects, not
  corrections to be applied; *errata* in French reads as a printer's correction
  list.
- `Hardware Revisions` → **Versions de la carte**. The page is about board
  versions, and *révisions* alone would suggest servicing.

## Glossary

### Enclosure, mounting, and installation

| English | French | Note |
|:--------|:-------|:-----|
| carrier board | carte porteuse | Deliberately *not* the Finnish approach — see the note below |
| enclosure | boîtier | |
| heat sink | dissipateur thermique | |
| waterproof | étanche | |
| wall-mount | fixation murale | |
| mounting surface | surface de fixation | |
| pilot hole | avant-trou | |
| mounting template | gabarit de perçage | |
| bilge | cale | |
| bulkhead | cloison | |
| cable gland | presse-étoupe | |
| cable routing | cheminement des câbles | |
| service loop | boucle de service | |
| cable tie | collier de serrage | |
| blind plug | bouchon obturateur | |
| breather plug | bouchon d'équilibrage de pression | |

**A note on `carte porteuse`, and why it differs from Finnish.** Finnish
translates `carrier board` as `emolevy` — literally *motherboard* — chosen for
reader familiarity over accuracy. French deliberately does **not** follow that:
`carte porteuse` says what the board actually is.

Do not "harmonise" the two. They differ on purpose, decided per language and per
audience, and the divergence is the decision rather than an oversight in either
one.

The practical consequence is that French needs *less* care than Finnish here.
`emolevy` inverts the CM5/board relationship and the Finnish glossary tells
translators to write the roles out explicitly in passages where that matters.
`carte porteuse` carries the relationship on its own, so the surrounding sentence
does not have to.

### Electrical

| English | French | Note |
|:--------|:-------|:-----|
| power supply | alimentation | |
| input voltage range | plage de tension d'entrée | |
| polarity | polarité | |
| fuse | fusible | |
| inline fuse | fusible en ligne | |
| circuit breaker | disjoncteur | |
| current limiting | limitation de courant | |
| overcurrent | surintensité | |
| voltage drop | chute de tension | |
| grounding | mise à la terre | |
| short circuit | court-circuit | |
| wire gauge | section du conducteur | French uses mm², not AWG |
| marine-grade wire | conducteur de qualité marine | |
| wire strippers | pince à dénuder | |
| crimping | sertissage | |
| crimper | pince à sertir | |
| heat-shrink tubing | gaine thermorétractable | |
| heat gun | pistolet à air chaud | |
| multimeter | multimètre | |
| terminal block | bornier | |
| strain relief | serre-câble | |
| super-capacitor | supercondensateur | |
| real-time clock | horloge temps réel | |
| backup battery | pile de sauvegarde | |

### Connectors and interfaces

| English | French | Note |
|:--------|:-------|:-----|
| connector | connecteur | |
| barrel connector | connecteur cylindrique | Add *(barrel)* on first mention |
| header | connecteur | `connecteur GPIO 40 broches` |
| pin | broche | |
| backbone | dorsale | NMEA 2000 backbone |
| drop cable | câble de dérivation | |
| T-connector | connecteur en T | |
| termination (120 Ω) | résistance de terminaison | |
| front panel | panneau avant | |
| jumper | cavalier | |
| male / female | mâle / femelle | |

### System behaviour and status

| English | French | Note |
|:--------|:-------|:-----|
| boat computer | ordinateur de bord | |
| to boot | démarrer | |
| first boot | premier démarrage | |
| shutdown | arrêt | |
| graceful shutdown | arrêt propre | |
| power loss | perte d'alimentation | |
| blackout | coupure de courant | |
| power management | gestion de l'alimentation | |
| status LED | LED d'état | |
| monitoring | surveillance | |
| passive cooling | refroidissement passif | |
| filesystem | système de fichiers | |
| to unmount | démonter | |
| watchdog | chien de garde (watchdog) | Keep the English in parentheses once |
| standby | veille | |

### Software and networking

| English | French | Note |
|:--------|:-------|:-----|
| firmware | firmware | Not *micrologiciel* — matches the Finnish decision to keep the term the trade uses |
| daemon | démon | Established in French Linux usage, unlike Finnish |
| to flash | flasher | |
| operating system image | image système | |
| headless | sans écran | First mention: `sans écran (headless)` |
| container app | application conteneurisée | |
| container image | image de conteneur | |
| dashboard | tableau de bord | |
| WiFi Access Point | point d'accès WiFi | |
| wired / wireless | filaire / sans fil | |
| credentials | identifiants | |
| default password | mot de passe par défaut | |
| single sign-on (SSO) | authentification unique (SSO) | |
| Certificate Authority (CA) | autorité de certification (CA) | |
| web interface | interface web | |
| browser | navigateur | |

### Applications and use cases

| English | French | Note |
|:--------|:-------|:-----|
| chart plotter | traceur de cartes | |
| data logging | enregistrement de données | |
| vessel | navire | |
| fleet management | gestion de flotte | |
| predictive maintenance | maintenance prédictive | |
| remote monitoring | surveillance à distance | |
| compliance | conformité | |
| warranty | garantie | |

## HALMET terms

HALMET is a sensor interface board, so it needs vocabulary HALPI2 never used:
input circuits, measurement, and the things printed on a small PCB. Rows above
this heading are shared with HALPI2 and should not be changed here alone.

### Board and inputs

| English | French | Note |
|:--------|:-------|:-----|
| development board | carte de développement | HALMET is sold as one; not `carte porteuse`, which is HALPI2's carrier board and names a different relationship |
| digital input | entrée numérique | `D1`–`D4` stay as printed |
| analog input | entrée analogique | `A1`–`A4` stay as printed |
| input | entrée | |
| output | sortie | |
| sender | capteur | The marine sender a gauge reads; not *transmetteur*, which reads as a telemetry transmitter |
| tank sender | capteur de niveau de réservoir | `capteur de niveau` alone after first mention |
| resistive sender | capteur résistif | |
| gauge (engine panel gauge) | indicateur | `indicateur du tableau moteur`; not *jauge*, which names the level itself or the dipstick |
| counter | compteur | |
| chain counter | compteur de chaîne | Windlass chain counter |
| alarm signal | signal d'alarme | |
| engine RPM | régime moteur | Not *RPM*; the unit is written `tr/min` |
| tachometer | compte-tours | |
| alternator W terminal | borne W de l'alternateur | `W` is printed on the alternator and stays |
| fuel flow | débit de carburant | |

### Measurement and circuits

| English | French | Note |
|:--------|:-------|:-----|
| galvanic isolation | isolation galvanique | Not *isolement*, which names the property rather than the arrangement; one word throughout |
| isolated (section, area) | isolé | `partie isolée`, `zone isolée` |
| digital isolator | isolateur numérique | |
| isolation barrier | barrière d'isolation | |
| ground loop | boucle de masse | Not *boucle de terre*: the shared conductor in a boat's DC system is the masse. `grounding` stays `mise à la terre` in the shared table — the two are different senses, not a contradiction |
| analog-to-digital converter | convertisseur analogique-numérique | **Never abbreviate to `CAN`** — see the note below. `ADC` and `ADS1115` stay as printed |
| resolution (16-bit) | résolution | `résolution de 16 bits` |
| sampling rate | fréquence d'échantillonnage | |
| low-pass filter | filtre passe-bas | The solder jumper is labelled `LP` and stays |
| cutoff frequency | fréquence de coupure | |
| noise (electrical) | bruit | `bruit électrique` where a reader could hear sound; unlike Finnish, French uses one word for both |
| noise immunity | immunité au bruit | |
| voltage divider | diviseur de tension | |
| constant current source | source de courant constant | The header label `CCS` stays as printed; write `source de courant constant (CCS)` on first mention |
| excitation voltage | tension d'excitation | |
| passive voltage measurement | mesure passive de tension | |
| active resistance measurement | mesure active de résistance | |
| pull-up resistor | résistance de tirage vers le haut | Add `(pull-up)` on first mention on a page — datasheets print the English |
| pull-down resistor | résistance de tirage vers le bas | Add `(pull-down)` on first mention |
| threshold voltage | tension de seuil | |
| hysteresis | hystérésis | |
| floating (input) | flottant | `l'entrée reste flottante` |
| normally open / normally closed | normalement ouvert / normalement fermé | The established switch terms, abbreviated `NO` / `NF`. Not a literal rendering |
| self-resetting fuse | fusible réarmable | The PTC kind; *auto-réarmable* is the same thing, pick one |
| reverse polarity protection | protection contre l'inversion de polarité | |
| overvoltage protection | protection contre les surtensions | |
| switching power supply | alimentation à découpage | |
| current consumption | consommation de courant | |
| short circuit | court-circuit | Already in the shared Electrical table with the same sense; repeated here only because HALMET's wiring advice turns on it. Change it there, not here |
| chafing (of a wire) | ragage | The nautical term for wear by rubbing; `usure par frottement` if the passage is not addressed to boaters |

**A note on `CAN`, and why the ADC is never abbreviated.** The standard French
abbreviation for *convertisseur analogique-numérique* is `CAN` — the same three
letters as the CAN bus, which appears on nearly every HALMET page. A sentence
about the CAN transceiver and one about the CAN of the ADS1115 would be
indistinguishable. Write the converter out in full, keep `CAN` for the bus, and
keep `ADC` where the English source uses it as a label.

### Board features and assembly

| English | French | Note |
|:--------|:-------|:-----|
| jumper | cavalier | The shared term, kept: a removable link placed on a pin pair. See *solder jumper* for the PCB kind |
| jumper header | connecteur à cavalier | The pin pair a cavalier is placed on; `header` is `connecteur` in the shared table and that is kept |
| solder jumper | pont à souder | Closed permanently with a soldering iron. **Never `cavalier`** — the distinction decides whether the reader reaches for a soldering iron or tries to pull off something soldered down. Avoid *pont de soudure*, which also names an accidental bridge, i.e. a defect |
| to short (a jumper) | court-circuiter | `court-circuitez les deux broches` |
| pad (solder pad) | pastille | `pastilles de soudure` where the sentence needs it spelled out |
| unpopulated | non implanté | `pastilles non implantées`, `connecteur non implanté` — the component was never fitted |
| pitch (2.54 mm) | pas | `pas de 2,54 mm` |
| pluggable terminal block | bornier débrochable | Phoenix MC type; `bornier` alone is the shared HALPI2 term |
| silkscreen | sérigraphie | |
| to solder | souder | |
| soldering iron | fer à souder | |
| grommet | passe-fil | Rubber or silicone; distinct from `presse-étoupe`, the threaded gland |
| step drill bit | foret étagé | The one that looks like a small metal Christmas tree |
| conical drill bit | foret conique | |
| panel connector | connecteur de panneau | Mounted through the enclosure wall |
| reset button | bouton Reset | The board's own labels `Reset` and `Boot` stay in English; `bouton Reset (réinitialisation)` on first mention |
| boot button | bouton Boot | |
| bootloader | bootloader | Kept English, like `firmware`; *chargeur d'amorçage* is correct but not what the ESP32 tooling or the trade says |
| download mode | mode de téléchargement | The ESP32 flashing mode entered with the Boot button |
| user-programmable LED | LED programmable par l'utilisateur | |
| open hardware | matériel libre | Parallel to *logiciel libre*; add `(open hardware)` on first mention |

### A note on `connecteur`

The shared glossary renders both `connector` and `header` as `connecteur`, and
that is kept. HALMET puts the two side by side more often than HALPI2 does —
*1-Wire header connector*, *analog input connectors* — so let the qualifier
carry the distinction (`connecteur 1-Wire`, `connecteurs des entrées
analogiques`) rather than inventing a second word. Where a sentence would
otherwise be ambiguous, say what the thing is: `barrette de broches` for a bare
pin strip, `connecteur de câble` for the plug.

## Verification

A translated page is not done until:

1. `uv run mkdocs build --strict` passes — the same command CI runs.
2. `uv run python scripts/check_anchors.py site` passes.
3. `uv run python scripts/translation_status.py` shows the page as current.
4. `uv run python scripts/check_glossary.py fr` reports every prescribed term in
   use.
5. `uv run python scripts/check_typography.py fr` passes — the French rules are
   the ones no sibling language shares.
6. Structure matches the source — see `.claude/skills/translate-page/SKILL.md`.
7. Every term used on the page that appears in this glossary matches it.

## Related

- `finnish-glossary.md` — the sibling glossary and the general approach
- `.claude/skills/translate-page/SKILL.md` — the procedure
- mkdocs-static-i18n documentation: https://ultrabug.github.io/mkdocs-static-i18n/
