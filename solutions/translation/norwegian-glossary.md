---
title: Norwegian Bokmål translation glossary and style rules (HALMET)
date: 2026-08-05
category: translation
module: documentation
problem_type: reference
component: documentation
severity: medium
applies_when:
  - Translating any page from docs/en/ into Norwegian Bokmål under docs/nb/
  - Reviewing a Norwegian Bokmål translation for consistency
  - Adding a new term that has no established Norwegian Bokmål equivalent
tags:
  - translation
  - i18n
  - norwegian
  - bokmal
  - terminology
  - mkdocs-static-i18n
---

# Norwegian Bokmål translation glossary and style rules

## Context

The HALMET documentation is written in English under `docs/en/` and translated
into Norwegian Bokmål under `docs/nb/`, using the `mkdocs-static-i18n` folder
structure. Each language directory mirrors the same tree, so a translation keeps
its source's path and filename: `docs/en/hardware/index.md` becomes
`docs/nb/hardware/index.md`. Only markdown lives under `docs/nb/`; images and
other assets stay with the English source and are shared.

**This file began as a copy of the HALPI2 glossary and deliberately keeps its
decisions**, so that two Hat Labs products do not describe the same part with two
different Norwegian Bokmål words. `carrier board` → `bærekort` is the HALPI2 call
and stands here too, even though HALMET is not a carrier board and the term will
mostly appear in comparisons. Terms below the `## HALMET terms` heading are
additions this product needed; everything above it is shared with HALPI2, and a
change to a shared row must be made in both repositories or in neither.

`finnish-glossary.md`, `french-glossary.md`, `german-glossary.md`,
`swedish-glossary.md`, `spanish-glossary.md` and `italian-glossary.md` are the
siblings of this file in this repository; `check_glossary.py` also reserves
`da` and `nl`, so a Danish and a Dutch sibling may appear. The general approach
is the same in all of them, and Danish is the one to watch — see the next
section.

Translations are produced page by page, at different times, potentially by
different people. Without a fixed terminology list the same English term drifts
across pages — *solder jumper* becomes `loddebro` on one page and `loddejumper`
on the next — and the result reads as machine output even when each individual
sentence is correct. This file is the reference that prevents that drift. It is
a living document: extend it when a page introduces a term that is not listed
here, rather than inventing a one-off translation.

Unlike the other files under `solutions/`, this one has no date in its filename
because it is meant to be edited in place, not superseded.

## Six rules where the siblings are wrong for Norwegian Bokmål

Read this section before anything else. Every one of these is stated the
opposite way in at least one sibling glossary. Danish is the dangerous
neighbour: it is close enough to read as correct and is being written against
the same English source, so a Danish habit that slips in will not look wrong to
anyone who is not counting.

1. **Quotation marks are `«…»`, pointing inward.** Norwegian opens with `«` and
   closes with `»`. **Danish is the exact opposite** — Danish opens with `»` and
   closes with `«`. Not Swedish's `”…”`, not German's `„…“`, not straight
   `"…"`. And unlike French, **no space inside the guillemets**: write
   `«Abnormal»`, never `« Abnormal »`.

2. **Address the reader as `du`.** Norwegian technical and consumer
   documentation uses `du`. French uses *vouvoiement* and German uses *Sie* —
   both wrong here. `Koble til strømkabelen.` / `Kontroller polariteten med
   multimeteret før du slår på spenningen.` The formal `De`/`Dem`/`Deres` must
   not appear at all.

3. **No space before `; : ! ?`** — as in German and Swedish, and unlike French,
   whose rule is the exact opposite and demands a no-break space.

4. **Compounds are written solid, as one word.** `strømforsyning`,
   `kabelgjennomføring`, `bærekort`, `spenningsfall`, `nedstenging`. Splitting a
   compound in two (*særskriving*, `strøm forsyning`) is the single most visible
   error in written Norwegian and is what English word order invites. English
   `power supply` is two words; Norwegian is one.

5. **Compounding with a proper name takes one hyphen at the junction, not
   throughout.** Norwegian writes `NMEA 2000-nettverk`, `Signal K-server`,
   `HALMET-kabinett`, `ESP32-modulen`. German writes
   `NMEA-2000-Netzwerk` — hyphens all the way through. Copying the German
   pattern is wrong, and copying English spacing (`NMEA 2000 nettverk`) is also
   wrong.

6. **Norwegian spelling, not Danish.** The pairs below are the ones this corpus
   actually produces. Left is Norwegian and required; right is Danish and must
   not appear.

   | Norwegian Bokmål | Danish — never write this |
   |:-----------------|:--------------------------|
   | konfigurasjon, installasjon, informasjon, funksjon, terminering | konfiguration, installation, information, funktion |
   | å koble til (infinitive marker `å`) | at tilslutte (infinitive marker `at`) |
   | bare | kun |
   | nå | nu |
   | noen | nogen |
   | mye | meget |
   | enn | end |
   | etter | efter |
   | sette, hjelp, endre | sætte, hjælp, ændre |
   | sjekk | tjek |
   | forbindelsene, kablene (definite plural `-ene`) | forbindelserne, kablerne (`-erne`) |
   | bærekort | bæreprint |

   `kun` is not ungrammatical in Bokmål, but it is the Danish default. Banning
   it here costs nothing and makes a leak from the Danish branch visible in one
   `grep`.

## Names that are never translated

Product names, protocol names, hardware standards and software UI strings stay
in English — the device's own interface is in English, so translating a menu
name would send the reader looking for something that does not exist on screen.

- **Products and software:** HALMET, SH-ESP32, SH-RPi, SensESP, Signal K,
  Arduino IDE, ESP-IDF, ESPHome, PlatformIO, Hat Labs. HALPI2 and HaLOS keep
  their names too, on the pages that mention them.
- **Hardware and standards:** ESP32-WROOM-32E, ADS1115, NMEA 2000, CAN bus,
  I2C, 1-Wire, GPIO, JTAG, USB, ADC, TVS, PG7, PG9, SP13, M12, Phoenix MC,
  Schmitt trigger.
- **Pin and signal names are copied exactly:** `D1`–`D4`, `A1`–`A4`, `SDA`,
  `SCL`, `DQ`, `TXD0`, `RXD0`, `EN`, `IO0`, `CCS`, `LP`, `VP`, `VN`, `3V3`,
  `GND`. These are printed on the board; a translated pin name sends the reader
  looking for a label that does not exist. The same holds for `DI1`–`DI4`,
  `GPIO4`, `GPIO21`, `Reset` and `Boot` as printed labels — the buttons are
  `Reset`-knappen and `Boot`-knappen when the label itself is meant.

**Commands, file paths, configuration keys and code stay in English**, verbatim:
`main.cpp`, `ConnectAlarmSender()`, `can0`, `halos.local`,
`HALMET-example-firmware`. Code fences, command output, URLs and image
filenames are never touched.

`CAN bus` is a name here, but Norwegian compounds it like any other: the bus
itself is `CAN-bussen`, and `NMEA 2000-nettverket` follows rule 5.

## Units and numbers

Same handling as the other languages — the English source writes `12V` and
`0.9A`, and both are wrong in Norwegian.

| English source | Norwegian Bokmål |
|:---------------|:-----------------|
| `12V`, `0.9A` | `12 V`, `0,9 A` |
| `5.5 x 2.1 mm` | `5,5 × 2,1 mm` |
| `-20°C to +60°C` | `−20 °C … +60 °C` |
| `120Ω` | `120 Ω` |
| `3-5A` | `3–5 A` (en dash for ranges) |
| `200×130×60 mm` | `200 × 130 × 60 mm` |
| `2m`, `45mm`, `2kg` | `2 m`, `45 mm`, `2 kg` |

**Do not insert a thousands separator.** `115200 bps` and `9600` stay exactly as
in the source. Norwegian typography would allow a no-break space, but the
verification step compares every number in the English text against the
translation, and `115 200` no longer matches `115200`. Digits are copied, not
reformatted — only the decimal separator and the unit spacing change.

Decimal comma everywhere in prose, decimal point never — except inside inline
code and version numbers, which are copied verbatim (`v0.5.0`, `M4x10`, `PH2`).

## Links, images, admonitions, navigation

Same as the sibling glossaries: paths are copied from the English source
unchanged and never carry an `en/`, `nb/` or other language segment; image
captions and alt texts are translated but filenames are not; screenshots stay
English because the reader's own screen is English; standard admonition titles
are translated centrally in `mkdocs.yml`, custom ones in the page.

Admonition titles used centrally: `note` → Merk, `warning` → Advarsel, `tip` →
Tips, `info` → Informasjon, `danger` → Fare, `example` → Eksempel.

Navigation titles live in `mkdocs.yml` under the i18n plugin's
`nav_translations`, which is their single source of truth; the list is not
restated here. Two entries are judgement calls worth recording:

- `Errata` → **Kjente feil**, carried unchanged from HALPI2. The Latin word is
  opaque to a general reader, and the page lists known hardware defects, not
  corrections to be made.
- `Hardware Revisions` → **Maskinvareversjoner**, not *revisjoner*. Norwegian
  *revisjon* reads as an audit; the page is about board versions.

When a page is added to the nav in English, add its Norwegian title in the same
change — an untranslated entry falls back to English silently.

## Glossary

### Enclosure, mounting, and installation

| English | Norwegian Bokmål | Note |
|:--------|:-----------------|:-----|
| carrier board | bærekort | The accurate term, as in Swedish, French and German — see the note below |
| enclosure | kabinett | Not *hus*; *kabinett* is what an electronics box is called |
| lid | lokk | |
| gasket | pakning | |
| heat sink | kjøleribbe | |
| waterproof | vanntett | |
| wall-mount | veggmontering | |
| mounting surface | monteringsflate | |
| pilot hole (to drill) | forbore (verb) | `Forbor hullene for monteringsskruene` — an action the reader performs |
| pre-drilled hole (already there) | ferdigboret hull | The holes the enclosure ships with. Never write `forbor de ferdigborede hullene` — that is the nonsense the Swedish branch shipped |
| mounting template | boremal | |
| bilge water | lensevann | As in *lensepumpe*; not *bunnvann* |
| bulkhead | skott | |
| cable gland | kabelgjennomføring | The PG7 parts specifically may be called `kabelnippel` when the physical part is meant |
| cable routing | kabelføring | |
| service loop | servicesløyfe | Slack left at both cable ends |
| cable tie | kabelstrips | |
| blind plug | blindplugg | |
| breather plug | trykkutjevningsplugg | |
| standoff | avstandsbolt | |
| threaded insert | gjengeinnsats | |
| thermal pad | varmeledende pute | |
| spudger | plastspade | Non-conductive prying tool |

**A note on `bærekort`.** Norwegian takes the accurate term, like Swedish
(`bärkort`), French (`carte porteuse`) and German (`Trägerplatine`), and unlike
Finnish (`emolevy`, literally *motherboard*, chosen there for reader
familiarity). The divergence between the languages is deliberate, decided per
language and per audience. Do not harmonise them.

`bærekort` carries the CM5/board relationship on its own, so passages about
reseating the CM5 or troubleshooting a board that will not boot need no extra
explanation. Only the Finnish glossary needs that warning.

Danish would form this as `bæreprint` (Danish uses *print* for a circuit board).
Norwegian does not: the Norwegian word for a circuit board is `kretskort`, so
the compound is `bærekort`.

### Power and electrical

| English | Norwegian Bokmål | Note |
|:--------|:-----------------|:-----|
| power supply | strømforsyning | The external unit itself: *strømadapter* |
| input voltage range | inngangsspenningsområde | |
| polarity | polaritet | |
| fuse | sikring | |
| inline fuse | linjesikring | |
| circuit breaker | automatsikring | The panel breaker on the boat's electrical panel |
| current limiting | strømbegrensning | `strømbegrensningsbryter` for the switch |
| overcurrent | overstrøm | |
| voltage drop | spenningsfall | |
| grounding | jording | |
| short circuit | kortslutning | |
| wire gauge | ledertverrsnitt | Norwegian uses mm², not AWG |
| marine-grade wire | kabel av marin kvalitet | |
| wire strippers | avisoleringstang | |
| crimping | krimping | See the note below — *not* `krymping` |
| crimper | krimptang | |
| heat-shrink tubing | krympestrømpe | |
| heat gun | varmepistol | |
| multimeter | multimeter | |
| terminal block | koblingsklemme | In this documentation always the pluggable screw terminal on the carrier board, not a DIN-rail *rekkeklemme* |
| strain relief | strekkavlastning | |
| super-capacitor | superkondensator | |
| real-time clock | sanntidsklokke | |
| backup battery | reservebatteri | The CR2032 for the RTC |
| backup power | reservestrøm | What the super-capacitors deliver |
| voltage rail | spenningsskinne | `3,3 V-skinnen`, `5 V-skinnen` |

**A note on `krimping` versus `krymping`.** Norwegian trade usage says both, and
that is exactly the problem: `krympe` also means *to shrink*, and this
documentation talks about heat-shrink tubing (`krympestrømpe`) two lines from
where it talks about crimping terminals. `krimping`/`krimptang` for the crimp
and `krymping`/`krympestrømpe` for the heat-shrink keeps the two apart on the
page. Do not "correct" one into the other.

### Connectors and interfaces

| English | Norwegian Bokmål | Note |
|:--------|:-----------------|:-----|
| connector | kontakt / tilkobling | *kontakt* for the physical part, *tilkobling* for the act of connecting |
| barrel connector | DC-plugg | First mention: `DC-plugg (barrel)` |
| header | pinneliste | `40-pinners GPIO-pinneliste` |
| pin | pinne | |
| pitch | senteravstand | `3,81 mm senteravstand` |
| backbone | backbone | Established in Norwegian NMEA 2000 usage |
| drop cable | stikkledning | Dealer catalogues also say *dropkabel*; this documentation uses *stikkledning* throughout |
| T-connector | T-kobling | The source also writes *T-adapter*; translate both as `T-kobling` |
| terminator (the component) | termineringsmotstand | The 120 Ω resistor and its jumper |
| termination (the state) | terminering | `Kontroller at nettverket er riktig terminert` |
| front panel | frontpanel | |
| jumper | jumper | The physical shunt; `loddebro` for a solder jumper |
| male / female | hann / hun | `hannkontakt`, `hunkontakt` |
| flexible flat cable (FFC) | flatkabel | Keep `(FFC)` on first mention |
| silk screen | silketrykk | |

### Operation and system behaviour

| English | Norwegian Bokmål | Note |
|:--------|:-----------------|:-----|
| boat computer | båtdatamaskin | |
| to boot | starte opp | |
| first boot | første oppstart | |
| shutdown | nedstenging | |
| graceful shutdown | kontrollert nedstenging | |
| to shut down | slå av / stenge ned | |
| power loss | strømbortfall | The event: input power disappears |
| blackout | strømbrudd | The interval the blackout timer measures: `strømbruddstimer` |
| power management | strømstyring | |
| status LED | status-LED | |
| monitoring | overvåking | Not the Swedish *övervakning* |
| passive cooling | passiv kjøling | |
| filesystem | filsystem | |
| to unmount (a filesystem) | avmontere | `filsystemene avmonteres trygt` |
| to unmount (hardware, remove a module) | demontere | Removing the CM5 or the carrier board is *demontering*, never *avmontering* |
| watchdog | watchdog | `watchdog-tidsavbrudd` |
| standby | ventemodus | The CM5 is off while the controller stays awake — not *hvilemodus*, which is sleep |
| power button | strømknapp | |
| reset button | resetknapp | |
| solo mode / co-op mode | solomodus / samspillsmodus | Keep the English in parentheses on first mention |

### Software and networking

| English | Norwegian Bokmål | Note |
|:--------|:-----------------|:-----|
| firmware | firmware | Not *fastvare* — matches the sibling decision to keep the trade term, and the package is named `halpi2-firmware` |
| daemon | daemon | `HALPI-daemonen`; not *tjeneste*, which is a systemd service |
| to flash | flashe | `flashe systembildet til SSD-en` |
| system image | systembilde | Also for *operating system image* |
| container image | containerbilde | |
| container app | containerapp | |
| headless | uten skjerm | First mention: `uten skjerm (headless)` |
| dashboard | dashbord | Homarr's dashboard view. The UI itself says *Dashboard* in English — keep that when naming the on-screen label |
| WiFi Access Point | WiFi-aksesspunkt | |
| wired / wireless | kablet / trådløs | |
| credentials | påloggingsinformasjon | |
| default password | standardpassord | |
| single sign-on (SSO) | enkel pålogging (SSO) | |
| Certificate Authority (CA) | sertifikatutsteder (CA) | |
| web interface | webgrensesnitt | |
| browser | nettleser | |
| to log in | logge på | |
| update | oppdatering | |
| device tree overlay | device tree-overlay | Keep the English term; it names a file the reader edits |

### Applications and use cases

| English | Norwegian Bokmål | Note |
|:--------|:-----------------|:-----|
| chart plotter | kartplotter | |
| data logging | datalogging | |
| vessel | fartøy | |
| fleet management | flåtestyring | |
| predictive maintenance | prediktivt vedlikehold | |
| remote monitoring | fjernovervåking | |
| compliance | samsvar | As in *samsvarserklæring* |
| warranty | garanti | |

## HALMET terms

HALMET is a sensor interface board, so it needs vocabulary HALPI2 never used:
input circuits, measurement, and the things printed on a small PCB. Rows above
this heading are shared with HALPI2 and must not be changed here alone.

### Board and inputs

| English | Norwegian Bokmål | Note |
|:--------|:-----------------|:-----|
| development board | utviklingskort | HALMET is sold as one; not `bærekort`, which is HALPI2's carrier board |
| digital input | digital inngang | `D1`–`D4` stay as printed |
| analog input | analog inngang | `A1`–`A4` stay as printed |
| input | inngang | The terminal on the board; the signal arriving there is `inngangssignal`. Never *innmating* |
| output | utgang | |
| sender | giver | The marine sender a gauge reads: `nivågiver`, `temperaturgiver`. *sender* means a radio transmitter and is wrong here |
| tank sender | tankgiver | |
| resistive sender | resistiv giver | What it varies is `motstand` — see *active resistance measurement* |
| gauge (engine panel gauge) | måler | `måleren i motorpanelet`; the panel as a whole is `motorinstrumentene` |
| counter | teller | |
| chain counter | kjettingteller | Anchor chain is `ankerkjetting`, never *kjede* in this sense |
| alarm signal | alarmsignal | |
| engine RPM | motorens turtall | Not *RPM* in prose; the unit is `o/min` (omdreininger per minutt) |
| tachometer | turteller | The instrument. `turtall` is the quantity it shows |
| alternator W terminal | generatorens W-uttak | The alternator is `generatoren`, in full `vekselstrømsgeneratoren`. *dynamo* is widespread in Norwegian trade usage for the same part but names a DC machine — do not use it |
| fuel flow | drivstoffstrøm | `drivstoff`, never the Danish *brændstof* |
| engine panel | motorpanel | |
| bilge alarm | lensealarm | Formed on the shared `lensevann`, not *bunnvannsalarm* |
| microcontroller | mikrokontroller | The ESP32-WROOM-32E is a `modul`; the chip inside it is the `mikrokontrolleren` |

### Measurement and circuits

| English | Norwegian Bokmål | Note |
|:--------|:-----------------|:-----|
| galvanic isolation | galvanisk isolasjon | Not *galvanisk skille* — see the note below. Adjective: `galvanisk isolert` |
| isolated (section, area) | isolert | `isolert seksjon`, `isolert område`, `den isolerte siden` |
| digital isolator | digital isolator | The component that carries I2C and the four digital inputs across the barrier |
| isolation barrier | isolasjonsbarriere | Names the figure in `hardware/index.md` |
| ground loop | jordsløyfe | `uten fare for jordsløyfer` |
| analog-to-digital converter (ADC) | AD-omformer | Spelled out: `analog-digital-omformer`. The part name `ADS1115` stays. *konverter* is not used |
| resolution (16-bit) | oppløsning | `16 bits oppløsning` |
| sampling rate | samplingsfrekvens | `860 samplinger per sekund` |
| low-pass filter | lavpassfilter | The `LP` solder jumper keeps its printed label |
| cutoff frequency | grensefrekvens | *knekkfrekvens* also occurs in Norwegian; use `grensefrekvens` throughout |
| noise (electrical) | støy | `elektrisk støy` on first mention, because `støy` alone is also the ordinary word for sound. Interference coupled in from outside is `forstyrrelser` |
| noise immunity | støyimmunitet | What the Schmitt trigger improves. *støytoleranse* also occurs; pick one and keep it |
| voltage divider | spenningsdeler | The gauge and the sender together form one |
| constant current source (CCS) | konstantstrømkilde | One word. The header label `CCS` stays as printed |
| excitation voltage | matespenning | Write `matespenning til giveren`, so it is not read as the board's own `strømforsyning`. *eksitasjonsspenning* belongs to machines with field windings |
| passive voltage measurement | passiv spenningsmåling | |
| active resistance measurement | aktiv motstandsmåling | The measured quantity is `motstand` (`320 Ω`); `resistans` only where a sentence would otherwise confuse the quantity with the component |
| pull-up resistor | pull-up-motstand | The loan is kept and compounded — see the note below. Already fixed in the HALPI2 glossary's added-terms list; unchanged here |
| pull-down resistor | pull-down-motstand | |
| threshold voltage | terskelspenning | `terskelspenningen er om lag 1,55 V` |
| hysteresis | hysterese | Norwegian drops the `-is`: `en hysterese på omtrent 0,7 V` |
| floating (input) | flytende | `inngangen blir flytende` |
| normally open (NO) / normally closed (NC) | normalt åpen (NO) / normalt lukket (NC) | The established Norwegian pair — see the note below. Carried from the HALPI2 added-terms list, which already fixed `normalt åpen (NO)` |
| self-resetting fuse | selvtilbakestillende sikring | The 500 mA PTC on the NMEA 2000 input. Not *selvresettende* |
| reverse polarity protection | polvendingsvern | *polvendingsbeskyttelse* also occurs; `-vern` is chosen so it reads as a pair with `overspenningsvern` |
| overvoltage protection | overspenningsvern | |
| ESD protection | ESD-vern | Same `-vern` pattern; `ESD` is never translated |
| switching power supply | switchet strømforsyning | Trade spelling. Bokmål permits `svitsjet`, but no Norwegian datasheet writes it |
| current consumption | strømforbruk | Not *strømtrekk*, which is a momentary draw |
| short circuit | kortslutning | Already in the shared Power table with the same sense — repeated here only because HALMET's chafing warning turns on it |
| chafing (of a wire) | gnaging | `skade på grunn av gnaging`. *skuring* is about hulls, not cables |

### Board features and assembly

| English | Norwegian Bokmål | Note |
|:--------|:-----------------|:-----|
| jumper | jumper | Already in the shared Connectors table, same sense: the removable shunt pushed onto a pin pair. See *solder jumper* for the PCB kind |
| jumper header | jumperpinner | The pin pair a jumper is pushed onto. `pinneliste` is the shared word for a header in general; a single pair may be called `pinneparet` |
| solder jumper | loddebro | Inherited from the shared Connectors row. Closed permanently with a soldering iron — see the note below |
| to short (a jumper) | kortslutte | But prefer the verb that says which kind: `lodd sammen loddebroen` for the soldered ones, `sett en jumper over pinnene` for the removable ones |
| solder pad | loddeflate | The bare copper. `loddepunkt` is the finished joint and is not the same thing |
| unpopulated | ubestykket | `ubestykkede loddeflater`. A header the factory left off is `ikke montert` |
| pitch (2.54 mm) | senteravstand | Already in the shared Connectors table, same sense; repeated because nearly every HALMET connector is specified by it: `2,54 mm senteravstand`, `Phoenix MC 3,81` |
| pluggable terminal block | pluggbar koblingsklemme | Phoenix MC type; `koblingsklemme` alone is the shared HALPI2 term |
| silkscreen | silketrykk | Already in the shared Connectors table. The errata page's *back side silk screen* → `silketrykket på undersiden` |
| to solder | lodde | |
| soldering iron | loddebolt | The Norwegian tool word. Danish *loddekolbe* must not appear |
| grommet | gummigjennomføring | Carried from the HALPI2 added-terms list (*cable grommet*). Rubber or silicone; distinct from `kabelgjennomføring`, the threaded gland in the shared table |
| step drill bit | trinnbor | The one that looks like a small metal Christmas tree |
| conical drill bit | konisk bor | |
| panel connector | panelkontakt | The one mounted through the enclosure wall |
| reset button | resetknapp | Already in the shared Operation table. The printed label `Reset` stays English |
| boot button | boot-knapp | Hyphenated while `resetknapp` is solid — see the note below; do not "fix" either into the other |
| bootloader | bootloader | Kept in English, like `firmware`, `daemon` and `watchdog` in the shared tables. *oppstartslaster* is not established |
| download mode | nedlastingsmodus | The ESP32 flashing mode; first mention `nedlastingsmodus (download mode)`. Distinct from the HALPI2 added-terms `oppstartsmodus` (*boot mode*), which is about which medium the machine boots from |
| user-programmable LED | brukerprogrammerbar LED | The blue one on `GPIO2` |
| flash memory | flashminne | `16 MB flashminne`. The verb is `flashe`, already in the shared Software table |
| open hardware | åpen maskinvare | HALMET's licence statement. Source code is `åpen kildekode`; the two are not interchangeable |

### A note on `galvanisk isolasjon`, and why not `galvanisk skille`

`galvanisk skille` is the more frequent phrase in general Norwegian electrical
writing, and it is the wrong choice in a marine document: to a Norwegian boat
owner, *et galvanisk skille* is a specific product — the galvanic isolator
fitted in the shore-power earth conductor to stop stray-current corrosion.
HALMET has no such device, and the isolation being described is a property of
the board. `galvanisk isolasjon` for the property, `galvanisk isolert` for the
adjective, and `isolert seksjon` / `isolert område` for the parts on the far
side of the barrier. This is the same kind of near-collision the shared table
solves for `krimping` versus `krymping`.

### A note on `normalt åpen` and `normalt lukket`

Norwegian relay catalogues also say `sluttekontakt` (NO) and `brytekontakt`
(NC), and those are good words — but they name contacts, not switches, and the
HALPI2 glossary already fixed `normalt åpen (NO)` when it described the external
Power/Reset buttons. That decision is kept and `normalt lukket (NC)` completes
the pair. `normalt åpen`/`normalt lukket` is standard Norwegian technical usage
and not a literal calque; keep the English abbreviation in parentheses on first
mention, because the reader will meet `NO`/`NC` in the sender's own datasheet.

Swedish diverges here (`slutande` / `brytande`). The divergence is deliberate,
decided per language, exactly as with `bærekort` / `emolevy`. Do not harmonise.

Getting this pair wrong inverts the instructions: a normally open switch needs
the pull-down resistor, a normally closed one needs the pull-up, and the
`usage/index.md` passage says so in a single sentence.

### A note on `jumper` and `loddebro`

These are two different objects and the reader acts differently on each.

A **`jumper`** is a removable shunt pushed onto a pin pair. On HALMET that is
only the `CCS` constant-current-source headers, which are enabled by placing
one and disabled by pulling it off.

A **`loddebro`** is a pad pair on the PCB closed permanently with a soldering
iron: the `LP` low-pass filters, the pull-up and pull-down resistors, the CAN
terminator and the `ADS1115` address selection, all on the bottom side.
Confusing the two sends the reader either for a `loddebolt` they do not need or
trying to pull off something that is soldered down. Where the English says only
*jumper*, decide from the context which one it is — everything on the bottom
side is a `loddebro`.

`loddebro` is the inherited term and is kept, but it is also what Norwegian
calls an accidental solder bridge. When the accidental kind is meant — the
errata page's short-circuit description is the place this will come up — write
`utilsiktet loddebro` and never leave it bare.

### A note on `pull-up-motstand`

Norwegian electronics keeps the English *pull-up* and *pull-down* and compounds
them with a hyphen: `pull-up-motstand`, `pull-down-motstanden`,
`pull-down-loddebroen`. Translated forms such as *oppdragningsmotstand* are not
established and would break the link to the schematic and to the board labels
the reader has in front of them. This is the same treatment the shared table
gives `device tree-overlay`. Finnish translates these (`ylösvetovastus`); that
divergence is deliberate and per language.

### A note on `boot-knapp` next to `resetknapp`

`reset` has been naturalised in Norwegian and compounds solid, which is why the
shared table already has `resetknapp`. `boot` has not, and `bootknapp` reads as
a typo, so it takes a junction hyphen — the same treatment the shared table
gives `status-LED`. The asymmetry is intentional. When the printed label itself
is meant rather than the button's function, write `Reset`-knappen and
`Boot`-knappen with the label in code style.

### A note on `kontakt`, `pinneliste` and `klemme`

HALMET puts *connector* and *header* side by side far more often than HALPI2
does — *1-Wire header connector*, *I2C header connector*, *analog input
connectors*. The shared split is kept: `kontakt` for a connector as a physical
part, `tilkobling` for the act of connecting, `pinneliste` for a pin header.
Where the English doubles the words (*header connector*), use `pinneliste`
alone — Norwegian does not need both. The pluggable input connectors are
`koblingsklemmer` (`pluggbare koblingsklemmer`), and the one mounted through the
enclosure wall is a `panelkontakt`.

### Numbers on HALMET pages

The shared units table applies unchanged. Four forms occur only in this
repository:

| English source | Norwegian Bokmål |
|:---------------|:-----------------|
| `320 ohms`, `100 kohm`, `120 ohm` | `320 Ω`, `100 kΩ`, `120 Ω` |
| `+/- 30 V`, `-32V and +32V` | `±30 V`, `−32 V og +32 V` |
| `2x10 pin`, `4-pin`, `3-pin` | `2×10 pinner`, `4-pinners`, `3-pinners` |
| `5-32 V`, `2-3 panel connectors` | `5–32 V`, `2–3 panelkontakter` (en dash) |

Drill sizes keep the inch fraction as the source writes it: `12,5 mm eller
1/2"`, `16 mm eller 5/8"`. The fraction is a bit designation, not a measurement
to convert, and rewriting it would trip the numeric-drift check.

## Verification

A translated page is not done until:

1. `uv run mkdocs build --strict` passes — the same command CI runs.
2. `uv run python scripts/check_anchors.py site` passes.
3. `uv run python scripts/translation_status.py` shows the page as current.
4. `uv run python scripts/check_glossary.py nb` passes.
5. `uv run python scripts/check_typography.py nb` passes.
6. Lists render as lists — see
   `../best-practices/markdown-lists-need-blank-line-2026-05-16.md`. The rule
   applies identically to Norwegian pages.
7. Every term used on the page that appears in this glossary matches it.

`scripts/check_glossary.py` already carries `"nb": "norwegian-glossary.md"` in
its `GLOSSARIES` dict, and `check_typography.py` already knows that Norwegian
quotes are `«…»` and Danish `»…«`, so steps 4 and 5 run as they stand.

One gap to know about: `check_typography.py` measures the junction hyphen only
for the names it lists, and `HALMET` is not among them. `HALMET-kabinett` and
`HALMET-kortet` are therefore not machine-checked — use the grep in the table
below.

### The six rules are measured, not reread

**A rule that was read looks followed.** Rereading your own page confirms
whatever it already says. Both the French and German branches shipped a
half-applied typography rule to review for exactly this reason, and Danish is
close enough to Norwegian that a leak from the parallel branch will read as
fine. Run these against `docs/nb/` and act on any non-zero count. Strip code
fences first — every count below is about prose, and inline code is exempt.

| Rule | Command | Expected |
|:-----|:--------|:---------|
| Guillemets pair and point inward | `grep -o '«' -r docs/nb \| wc -l` and the same for `»` | equal counts |
| No Danish outward quotes | `grep -rnE '»[^«»]*«' docs/nb` | no output |
| No space inside guillemets | `grep -rnE '« \| »' docs/nb` | no output |
| Reader is `du` | `grep -rowiE '\b(du\|deg\|din\|ditt\|dine)\b' docs/nb \| wc -l` | well above zero |
| No formal address | `grep -rnE '\b(De\|Dem\|Deres)\b' docs/nb` | no output outside sentence-initial `De` |
| No space before `;:!?` | `grep -rnE ' [;:!?]' docs/nb` | no output |
| No `-tion` (Danish/English) | `grep -rniE '[a-zæøå]{3,}tion(en\|er\|ene\|s)?\b' docs/nb` | no output |
| Infinitive marker is `å` | `grep -rnE '\bat [a-zæøå]+e\b' docs/nb` | no output |
| No Danish function words | `grep -rniwE '(kun\|nu\|nogen\|meget\|end\|efter\|sætte\|hjælp\|ændre\|tjek)' docs/nb` | no output |
| No `-erne` plurals | `grep -rniE '[a-zæøå]{3,}erne\b' docs/nb` | no output |
| No split compounds | `grep -rniE '(strøm forsyning\|kabel gjennomføring\|lodde bro\|lavpass filter\|spennings deler\|konstant strømkilde\|status LED-\|spennings fall)' docs/nb` | no output |
| German hyphen chain | `grep -rn 'NMEA-2000\|Signal-K\|Raspberry-Pi' docs/nb` | no output |
| Junction hyphen present | `grep -rn 'NMEA 2000-\|Signal K-\|HALMET-' docs/nb` | matches wherever the name is compounded |
| Pin labels not translated | `grep -rniE '\b(inngang ?[1-4]\|utgang ?[1-4])\b' docs/nb` | no output — `D1`–`D4` and `A1`–`A4` are copied |
| Sender is `giver`, not `sender` | `grep -rniwE '(senderen\|sendere\|senderne)' docs/nb` | no output |
| Unit spacing | `grep -rnE '[0-9](V\|A\|W\|Ω\|mm\|kg\|m)\b' docs/nb` | no output |
| Decimal comma | `grep -rnE '[0-9]\.[0-9]' docs/nb` | no output outside version numbers |
| En dash in ranges | `grep -rnE '[0-9]-[0-9] ?(V\|A)' docs/nb` | no output |
| Numbers did not drift | every number in the English page appears in the Norwegian page | all present |

A wrong voltage or current in an installation guide is a safety problem, not a
typo. The last row is not optional.

## Related

- `finnish-glossary.md`, `french-glossary.md`, `german-glossary.md`,
  `swedish-glossary.md`, `spanish-glossary.md`, `italian-glossary.md`,
  `danish-glossary.md` — siblings
- `.claude/skills/translate-page/SKILL.md` — the procedure
- `../best-practices/` — the markdown traps that survive `--strict`
- mkdocs-static-i18n documentation:
  <https://ultrabug.github.io/mkdocs-static-i18n/>

## Terms added during translation

Reported by the page translators, consolidated here rather than written by each
of them, because several agents share this file.

**The rows below were added while translating the HALPI2 pages.** They are kept
because they are Norwegian terminology decisions, not HALPI2 facts: where the
same English term occurs in a HALMET page — *transceiver*, *pull-up*, *boot
mode*, *cable grommet*, *normally-open* — the rendering here is binding, and the
HALMET tables above cite them where they overlap. The notes still describe the
HALPI2 page each term came from; that context is history, not scope. New terms
found while translating HALMET pages are appended to the same table.

| English | Translation | Note |
|:--------|:------------|:-----|
| guitar pick | gitarplekter | Named as an alternative non-conductive prying tool next to the spudger in the CM5 removal procedure. The glossary lists spudger -> plastspade but not  |
| board-to-board connector | kort-til-kort-kontakt | The two high-density connectors joining the CM5 to the carrier board. Central to the CM5 replacement section and its warranty warning, so it needs one |
| amber (LED colour) | ravgul | LED colour column in the status-LED table. Norwegian trade usage also says gul, which would collide with the yellow Ethernet-speed LED two rows above; |
| voltage bar (LED pattern) | spenningssøyle | The LED pattern name in the operation.md quick-reference table, where the five LEDs form a bar-graph charge indicator. |
| hex socket / socket size (tool) | pipe / pipestørrelse | The connector-removal step lists 26 mm, 10 mm, 8 mm and 17 mm sockets. pipe (pipenøkkel) is the Norwegian tool word; nøkkel alone would read as a span |
| countersunk screw | senkeskrue | The four M4x10 lid screws. Appears in the very first procedure on the page. |
| boot mode | oppstartsmodus | USB boot mode / Abnormal boot mode, in the connector table, the LED table and the SSD section. The glossary has to boot -> starte opp but not this com |
| single-sided / double-sided (SSD) | ensidig / tosidig | The M.2 2230-2280 compatibility rule turns on this distinction, so it is load-bearing rather than decorative. |
| chip select | chip select | Kept in English in the GPIO conflict table and prose, like the other SPI signal names (MISO, MOSI, SCK) which are already never-translate. |
| transceiver | transceiver | RS-485 transceiver, in the interface-disabling section. The Norwegian trade term is the English one, consistent with the glossary keeping firmware and |
| grace period | venteperiode | The 5-second window before HALPI2 restarts itself after a manual shutdown. naadeperiode is a legal term and wrong here. |
| feeding the watchdog | mating av watchdogen | The source sets it in quotes as jargon; kept as jargon inside Norwegian guillemets so it still reads as a quoted idiom. |
| heat spreading area | varmespredende flate | The areas on the enclosure bottom the CM5 thermal pads must meet, in the CM5 final-assembly step. |
| solid (LED state) | lyser fast | Opposed to blinker (flashing) throughout the operation.md LED table; needed one fixed rendering to keep the table columns parallel. |
| pressure equalization | trykkutjevning | The stated purpose of the breather plug. The glossary gives the part (trykkutjevningsplugg) but not the function, which the panel-connector list state |
| terminals (crimp-on cable terminals) | kabelsko | Appears twice in the permanent-installation materials list and in "Install terminals using proper crimping technique". The glossary covers terminal bl |
| cable grommet | gummigjennomføring | "Install cable glands or cable grommets if routing through bulkheads" lists it alongside cable gland (kabelgjennomføring). Needed a distinct word so t |
| "wall wart" (power supply type) | «wall wart» (kept English in guillemets) | Jargon in the optional-items list. No idiomatic Norwegian equivalent; kept as a quoted English idiom inside «…», the same treatment the glossary gives |
| mounting clips | monteringsklips | Last item of the materials list, next to cable ties (kabelstrips). Recording it so the next page that mentions clips does not invent klemmer or festek |
| known-good device | en enhet du vet fungerer | NMEA 2000 troubleshooting bullet. Rendered as a relative clause rather than a compound; noting it so the phrase stays the same if it recurs. |
| Load Equivalency Number (LEN) | Load Equivalency Number (LEN) | NMEA 2000 standard term for how much bus power a device draws. Norwegian marine dealers and the standard itself use the English name and the LEN abbre |
| multi-talker / single-talker-multiple-listener | multi-talker / single-talker-multiple-listener | NMEA 0183 / RS-485 topology terms. Kept English but glossed once on first use: 'nettverk med flere sendere (multi-talker)' and 'nettverk med én sender |
| half-duplex | halv dupleks | The RS-485 mode that lets one wire pair both transmit and receive. Two words in Norwegian (halv dupleks) rather than a solid compound, matching establ |
| normally-open (NO) momentary switch | normalt åpen (NO) momentbryter | The switch type required for the external Power/Reset/User buttons. Load-bearing: the wrong switch type makes the button behave inverted. 'momentbryte |
| Battery-Backed RAM (BBR) | batteribackup-RAM (BBR) | Where the u-blox GNSS receiver stores its settings. Explains why the configuration is re-run on every boot, so it needs a stable rendering. Abbreviati |
| PLC (programmable logic controller) | PLS | Industrial RS-485 device listed under common applications. PLS is the standard Norwegian abbreviation (programmerbar logisk styring); writing PLC woul |
| buck converter | buck-omformer | Names the SiC463ED regulating the 10 V intermediate rail in the power-supply table. Norwegian trade usage keeps 'buck' and compounds it with a junctio |
| ferrite bead | ferrittperle | USB 3.0 port filtering in technical-reference/hardware.md. Standard Norwegian component name. |
| pull-up (resistor) | pull-up-motstand | The 2,2 kΩ pull-ups on the controller I2C bus. Norwegian keeps the English 'pull-up' and compounds it, as with the glossary's device tree-overlay. |
| ingress protection | inntrengningsbeskyttelse | The IP65 row in the specifications summary. The separate 'IP rating' row in the enclosure table is rendered 'IP-klasse' — the two English phrasings ar |
| solder nut | loddemutter | The 4× M2.5 fasteners holding the CM5, in the mounting list. Distinct from the glossary's gjengeinnsats (threaded insert), which is the HAT mounting m |
| current limit (the value) | strømgrense | Column header in the USB 3.0 port table, where each cell is a number (0,93 A). The glossary has current limiting -> strømbegrensning for the function  |
| depth sounder / wind instrument | ekkolodd / vindmåler | NMEA 0183 instrument types listed under common applications for RS-485. Both are the ordinary Norwegian boating words. |
| recessive state | resessiv tilstand | The bus state an RS-485 multi-talker interface must hold when not transmitting. Direct loan, as in the CAN literature. |
| power-on / power-off threshold | innkoblingsterskel / utkoblingsterskel | The 8,0 V and 5,5 V supercapacitor thresholds. Chosen as a matched pair so the two table rows read parallel; UVLO is kept as the English abbreviation  |
| user space | brukerrommet (user space) | ubuntu-installation.md describes halpid as a user space daemon that talks to the power-management hardware over I2C. The glossary fixes daemon -> daem |
| thermal throttling | termisk struping | troubleshooting.md, the 'System runs slowly or freezes' step about CPU temperature above 80 °C. The glossary covers passiv kjøling but not the throttl |
| rollback (of a firmware update) | tilbakerulling / rulle tilbake | The whole 'Firmware Update Failed or Rolled Back' section turns on this word, and the LED/firmware sections of software.md already describe the same 3 |
| login prompt | påloggingsledetekst | troubleshooting.md tells the reader to attach HDMI and look for boot errors or a login prompt. The glossary has to log in -> logge på but not the on-s |
| bus contention | konflikt på bussen | The CAN error-counter step in troubleshooting.md lists it alongside wiring problems and wrong baud rate. No single-word Norwegian equivalent is in use |
| 3rd party (operating systems) | tredjeparter | The warning admonition at the top of ubuntu-installation.md. Spelled out as a word rather than kept as a digit, so the numeric-drift check will report |
| errata / known hardware issues | kjente feil | Page title of appendices/errata.md. Taken from the nb nav_translations block in mkdocs.yml ("Errata": "Kjente feil") so the H1 and the sidebar agree,  |
| mounting ledge | monteringsknast | The cast aluminium ledges inside the enclosure that the PCB rests on. Central to the second errata item (heading plus three prose mentions); knast is  |
| solder mask | loddemaske | The PCB coating a casting flash can penetrate, in the errata short-circuit description. |
| copper pour / power plane | kobberflate / spenningsplan | Both appear: copper pours in the v0.5.0 changelog and a 3,3 V power plane in errata. Kept apart because the errata text names the plane as a net, not  |
| inrush current / initial current spike | startstrom | The errata compliance item turns on this quantity (1,1 A against the NMEA 2000 limit of 1 A), so it needed one fixed rendering rather than an ad-hoc p |
| through-hole (THT) | gjennomhullsmontering (THT) | The v0.5.0 jumper-header changelog entry. Abbreviation kept in parentheses as the source has it. |
| footprint (component) | komponentfotavtrykk | Last v0.6.0 changelog entry. Fotavtrykk alone would read as a carbon/disk footprint in a marine document. |
| signal integrity | signalintegritet | Appears twice in design-files (v0.6.1 summary and the v0.6.0 re-routing entry). |
| security hardening | sikkerhetsherding | Bullet in software-development/advanced-config.md. Sikring would collide with the glossary entry fuse -> sikring, which is the reason for choosing her |
| cross-compilation | krysskompilering | Bullet in software-development/integration.md. |
| kernel module | kjernemodul | Bullet in software-development/integration.md; kernel is otherwise never translated in the glossary, but the compound reads badly in English here. |
| goodie bag | tilbehørspose | The bag of extras shipped in the box. Appears only as the index.md image alt text, so nothing else in the corpus pins it down; recorded here so the next page that mentions it does not invent godtepose or tilbehørspakke. |
| layout | oppsett / oppbygning / plassering / kretskortlayout | Four senses the English word covers and Norwegian splits; they are not rivals and must not be harmonised. A set of items chosen from options is oppsett (standardoppsettet, tastaturoppsett, standardoppsettet med 40 pinner). How something is built up internally is oppbygning (the Intern oppbygning heading, and the carrier-board alt text Bærekortets oppbygning, oversiden). Where parts sit on a face is plassering (Kontaktplassering på HALPI2, the index.md alt text). PCB design files are kretskortlayout, the trade loan. |
