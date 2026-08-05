---
title: Dutch translation glossary and style rules (HALMET)
date: 2026-08-05
category: translation
module: documentation
problem_type: reference
component: documentation
severity: medium
applies_when:
  - Translating any page from docs/en/ into Dutch under docs/nl/
  - Reviewing a Dutch translation for consistency
  - Adding a new term that has no established Dutch equivalent
tags:
  - translation
  - i18n
  - dutch
  - terminology
  - mkdocs-static-i18n
---

# Dutch translation glossary and style rules

## Context

The HALMET documentation is written in English under `docs/en/` and translated
into Dutch under `docs/nl/`, using the `mkdocs-static-i18n` folder structure.
Each language directory mirrors the same tree, so a translation keeps its
source's path and filename: `docs/en/hardware/index.md` becomes
`docs/nl/hardware/index.md`. Only markdown lives under `docs/nl/` — images and
other assets stay with the English source and are shared.

**This file began as a copy of the HALPI2 glossary and deliberately keeps its
decisions**, so that two Hat Labs products do not describe the same part with
two different Dutch words. A reader who has both a HALPI2 and a HALMET on the
bench should not have to learn that a *kabelwartel* on one page is something
else on the other. `carrier board` → `carrierboard` is the HALPI2 call and
stands here too, even though HALMET has no carrier board — the row is kept so
the two repositories stay comparable. Terms below the `## HALMET terms` heading
are additions this product needed; everything above it is shared with HALPI2,
and **a change to a shared row must be made in both repositories or in
neither.**

Translations are produced page by page, at different times, potentially by
different people. Without a fixed terminology list the same English term drifts
across pages — *solder jumper* becomes `soldeerbrug` on one page and
`soldeerjumper` on the next — and the result reads as machine output even when
each individual sentence is correct.

This file is the reference that prevents that drift. It is a living document:
extend it when a page introduces a term that is not listed here, rather than
inventing a one-off translation.

`finnish-glossary.md`, `italian-glossary.md` and `spanish-glossary.md` are the
siblings of this file in this repository; the HALPI2 repository holds the French,
German and Swedish ones. The general approach is the same in all of them.

Unlike the other files under `solutions/`, this one has no date in its filename
because it is meant to be edited in place, not superseded.

## Seven rules where the siblings are wrong for Dutch

Read this section before anything else. Every one of these is stated the
opposite way in at least one sibling glossary. Dutch sits closest to German and
Swedish — solid compounds, no space before punctuation — which is exactly why the
places where it diverges from them get carried across unnoticed.

1. **Address the reader as `u` / `uw`, never `je`, `jij`, `jouw` or `jullie`.**
   Dutch installation, safety and consumer manuals use `u`; Swedish uses `du`,
   and copying that register produces a page that reads as a hobby blog next to
   a warning about 32 V and short circuits.

   The trap is that the Dutch imperative is *identical* for both registers —
   `Sluit de voedingskabel aan.` `Controleer de polariteit met de multimeter
   voordat u de spanning inschakelt.` The register only surfaces in pronouns and
   possessives, so a page can be 90 % correct and still leak `je` in three
   places. That is why this is counted, not read.

   Write `u` and `uw` in lowercase. Capital `U` is an archaic reverential form
   and is wrong here.

2. **Quotation marks are `“…”` — U+201C opening, U+201D closing, two different
   characters.** Not German's `„…“`, not Swedish's `”…”` (the *same* character
   twice), not French's `« … »`, not straight `"…"`. A leaked Swedish habit is
   visible as a `”` count higher than the `“` count.

3. **Dutch does not capitalise common nouns.** German capitalises every noun;
   Dutch capitalises only proper names and the first word of a sentence or
   heading. Write `behuizing`, `voeding`, `carrierboard`, `afsluitweerstand`,
   `soldeerbrug`, `ingang` mid-sentence — never `Behuizing`, `Voeding`,
   `Soldeerbrug`. This is the single most likely German leak.

   The same rule flattens English title case in headings: `Drilling Holes for
   Panel Connectors` becomes `Gaten boren voor paneelconnectoren`, not `Gaten
   Boren voor Paneelconnectoren`.

4. **Compounds are solid, but a compound with a proper name takes exactly one
   hyphen, at the junction.** Dutch writes `NMEA 2000-netwerk`, `Signal
   K-server`, `HALMET-print`, `ESP32-module`, `PG7-kabelwartel`, `M12-connector`,
   `Phoenix MC-klemmenblok`, `ADS1115-omzetter`. German writes
   `NMEA-2000-Netzwerk` — hyphens all the way through — and that pattern is
   wrong in Dutch.

   Ordinary Dutch compounds carry no hyphen and no space: `voedingskabel`,
   `kabelwartel`, `afsluitweerstand`, `soldeerbrug`, `spanningsdeler`,
   `drempelspanning`. English two-word terms adopted whole become one Dutch
   word: `carrier board` → `carrierboard`, `access point` → `accesspoint`,
   `jumper header` → `jumperheader`.

5. **No space before `; : ! ?`** — as in German and Swedish, and unlike French,
   whose rule is the exact opposite and demands a no-break space.

6. **`led` is an ordinary lowercase Dutch word, not an abbreviation.** German
   writes `Status-LED` and Swedish `status-LED`; Dutch writes `status-led`,
   `rgb-led` → `RGB-led`, plural `leds`. Uppercase `LED` belongs only inside
   code, file paths, table cells that quote the GPIO reference, and quoted
   silkscreen labels. Same for `wifi` (lowercase in prose; `WiFi (wlan0)` stays
   as written when it names the on-screen menu item).

7. **HALMET and HALPI2 are `de`-words, the carrierboard is a `het`-word.**
   Grammatical gender drifts between pages faster than terminology does, because
   nothing flags it. Fix it here:

   | Article | Nouns |
   |:--------|:------|
   | `de` | HALMET, HALPI2, behuizing, voeding, zekering, connector, kabelwartel, aardlekbeveiliging, supercondensator, afsluitweerstand, daemon, controller |
   | `het` | carrierboard, frontpaneel, bestandssysteem, schot, klemmenblok, systeemimage, dashboard, energiebeheer |

   The HALMET-specific nouns are listed under `## HALMET terms`.

   English possessives do not survive the crossing: `HALMET's digital inputs`
   becomes `de digitale ingangen van de HALMET`, never `HALMET's digitale
   ingangen`. The apostrophe-`s` in Dutch marks the plural of a vowel-final word
   or an abbreviation (`schema's`, `led's` — but write `leds`, see rule 6),
   nothing else.

## Names that are never translated

Product names, protocol names, hardware standards and software UI strings stay
in English. The board's own labels and its development tools are in English, so
translating one would send the reader looking for something that does not exist.

- **Products and software:** HALMET, SH-ESP32, SH-RPi, SensESP, Signal K,
  Arduino IDE, ESP-IDF, ESPHome, PlatformIO, Hat Labs
- **Hardware and standards:** ESP32-WROOM-32E, ADS1115, NMEA 2000, CAN bus,
  I2C, 1-Wire, GPIO, JTAG, USB, ADC, TVS, PG7, PG9, SP13, M12, Phoenix MC,
  Schmitt trigger, IoT
- **Pin and signal names are copied exactly:** `D1`–`D4`, `A1`–`A4`, `SDA`,
  `SCL`, `DQ`, `TXD0`, `RXD0`, `EN`, `IO0`, `CCS`, `LP`, `VP`, `VN`, `3V3`,
  `GND`, and the GPIO numbers. These are printed on the board; a translated pin
  name sends the reader looking for a label that does not exist. The same
  applies to the button legends `Reset` and `Boot` and to the `DI1`–`DI4` rows
  of the GPIO table.
- **UI strings, commands, hostnames, file paths and identifiers:**
  `main.cpp`, `ConnectAlarmSender()`, `raspi-config`, `passwd`, `shutdown`,
  `halos.local`, `can0`

Code fences and their contents, command output, URLs and image filenames are
never touched.

## Units and numbers

The English source writes `12V` and `0.9A`. Both are wrong in Dutch and need an
active conversion on nearly every technical page.

| English source | Dutch |
|:---------------|:------|
| `12V`, `0.9A` | `12 V`, `0,9 A` |
| `5.5 x 2.1 mm` | `5,5 × 2,1 mm` |
| `-20°C to +60°C` | `−20 °C … +60 °C` |
| `120Ω`, `100 kohm` | `120 Ω`, `100 kΩ` |
| `1.5mm²`, `2m` | `1,5 mm²`, `2 m` |
| `5-32 V`, `3-5A` | `5–32 V`, `3–5 A` (en dash for ranges) |
| `+/- 30 V` | `±30 V` |
| `250 kbps` | `250 kbit/s` |
| `2x10 pin` | `2×10 pins` |

- **Decimal comma**, always: `0,9 A`, `5,5 mm`, `3,3 V-rail`, `2,54 mm`,
  `2,3 kHz`, `1,55 V`.
- **A space between the number and its unit**, preferably a no-break space
  (U+00A0), including before `°C` and `Ω`.
- **Write `ohm` as `Ω`**: the source writes `320 ohms`, `100 kohm`, `120 ohm`;
  Dutch writes `320 Ω`, `100 kΩ`, `120 Ω`.
- **No thousands separator** in technical values: `115200 bps`, not `115.200`.
- **Dimensions given as a single product spec keep the tight form:**
  `200 × 130 × 60 mm`, with `×` (U+00D7), not the letter `x`.
- **Version numbers, part numbers and addresses are identifiers, not numbers**:
  `v1.0.1`, `M.2`, `0x48`, `GPIO21` keep their points and digits exactly as
  written, while `2.54 mm` pitch takes the decimal comma → `2,54 mm`.
- **`16-bit` is attributive in Dutch and takes an `s`**: `een 16-bits
  resolutie`, `een 16-bits AD-omzetter`.

## Links, images, admonitions, navigation

Same as the sibling glossaries: paths are copied from the English source
unchanged and never carry an `en/` or `nl/` segment; image captions and alt
texts are translated but filenames are not; screenshots stay English because the
reader's own screen is English; standard admonition titles are translated
centrally in `mkdocs.yml`, custom ones — `!!! note "Shop Link"` →
`!!! note "Link naar de webshop"` — in the page.

Navigation titles live in `mkdocs.yml` under the i18n plugin's
`nav_translations` and are not restated here. Two entries are judgement calls
worth recording:

- `Errata` → **Bekende hardwarefouten**. The Latin term is opaque to a general
  reader, and in Dutch *errata* additionally suggests corrections still to be
  made rather than defects the reader has to live with. The page lists known
  hardware defects, so plain Dutch is clearer.
- `Hardware Revisions` → **Hardwareversies**. Board versions, not revisions to
  the documentation. `Revisies` alone would read as document revisions.

When a new page is added to the nav in English, add its Dutch title to
`nav_translations` in the same change — an untranslated entry silently falls
back to English and is easy to miss.

## Glossary

### Enclosure, mounting, and installation

| English | Dutch | Note |
|:--------|:------|:-----|
| carrier board | carrierboard | One word, lowercase, `het`-woord — see the note below |
| enclosure | behuizing | |
| lid | deksel | |
| gasket | afdichtingsrubber | Lid gasket |
| heat sink | koellichaam | Not *koelblok*, which is a cooling block on a chip |
| waterproof | waterdicht | |
| rugged | robuust | |
| wall-mount | wandmontage | |
| mounting surface | montageondergrond | What you drill into |
| pilot hole (to drill) | voorboren (verb) | `Boor de bevestigingsgaten voor.` Never `voorgeboorde gaten boren` |
| pre-drilled hole (already there) | voorgeboord gat | The holes the enclosure ships with |
| mounting template | boormal | |
| clearance | vrije ruimte | |
| bilge water | bilgewater | Also seen as *lenswater*; use `bilgewater` on every page |
| bulkhead | schot | `het schot`, plural `schotten` |
| cable gland | kabelwartel | `PG7-kabelwartel` |
| cable routing | kabelroute | The verb is *leggen* / *leiden* |
| service loop | servicelus | Slack left at both cable ends |
| chafing | schuren | |
| cable tie | kabelbinder | |
| blind plug | blindplug | |
| breather plug | ontluchtingsplug | For *pressure equalization* → *drukvereffening* |
| standoff | afstandsbus | |
| threaded insert | draadinzetstuk | |

**A note on `carrierboard`, and why it differs from the siblings.** French,
German and Swedish each coined an accurate native term (`carte porteuse`,
`Trägerplatine`, `bärkort`); Finnish took the familiar-but-inaccurate `emolevy`
(*motherboard*). Dutch takes neither route: the Dutch marine and Raspberry Pi
trade already says *carrier board*, and Dutch spelling turns an adopted English
two-word term into one word — `carrierboard`.

Do not "harmonise" the five. They differ on purpose, decided per language and
per audience.

Two consequences worth stating:

- **Never write `moederbord`.** That is the Finnish trade-off, and it inverts
  the CM5/board relationship: it would make the board the computer and the CM5
  an add-on, which is the reverse of how HALPI2 is built. `carrierboard` carries
  the relationship correctly on its own.
- **Never write `carrier board` with a space,** and never capitalise it
  mid-sentence. Those are the English and German habits respectively, and both
  are countable.

On HALMET the row is inherited, not used: HALMET is not a carrier board and
nothing on it should be called one. See `ontwikkelbord` under
`## HALMET terms`.

### Electrical

| English | Dutch | Note |
|:--------|:------|:-----|
| power supply | voeding | The unit itself: *voedingsadapter* |
| power source | voedingsbron | |
| input voltage range | ingangsspanningsbereik | |
| polarity | polariteit | |
| positive (+) / negative (−) | plus (+) / min (−) | The `+` and `-` markings on the terminal block stay as printed |
| fuse | zekering | |
| inline fuse | kabelzekering | A fuse holder fitted in the positive lead |
| circuit breaker | installatieautomaat | The panel breaker; on a boat panel often just *automaat* |
| current limiting | stroombegrenzing | The switch is the *stroombegrenzer* |
| overcurrent | overstroom | |
| inrush current | inschakelstroom | |
| voltage drop | spanningsval | |
| grounding | aarding | |
| ground loop | aardlus | |
| short circuit | kortsluiting | |
| wire gauge | aderdoorsnede | Dutch uses mm², not AWG |
| marine-grade wire | kabel van maritieme kwaliteit | |
| to strip (a wire) | strippen | |
| wire strippers | striptang | |
| crimping | krimpen | Noun: *krimpverbinding* |
| crimper | krimptang | |
| crimp terminal | kabelschoen | |
| heat-shrink tubing | krimpkous | |
| heat gun | heteluchtpistool | |
| multimeter | multimeter | |
| continuity test | doorbelmeting | |
| terminal block | klemmenblok | The pluggable Phoenix MC connector |
| strain relief | trekontlasting | |
| super-capacitor | supercondensator | One word, lowercase |
| real-time clock | realtimeklok | Abbreviate as RTC after first mention |
| backup battery | backupbatterij | The cell itself is a `CR2032-knoopcel` |

### Connectors and interfaces

| English | Dutch | Note |
|:--------|:------|:-----|
| connector | connector / aansluiting | *aansluiting* for a board-mounted socket |
| barrel connector | DC-plug | Add *(barrel connector)* on first mention |
| header | pinheader | `2×10-pins GPIO-pinheader` |
| pin | pin | |
| pitch | steek | `2,54 mm steek` |
| backbone | backbone | Established in Dutch NMEA 2000 usage |
| drop cable | aftakkabel | |
| T-connector | T-stuk | Also renders *T-adapter* |
| terminator / termination (120 Ω) | afsluitweerstand | The component; the act is *afsluiten* |
| front panel | frontpaneel | |
| jumper | jumper | The removable link; see *soldeerbrug* under `## HALMET terms` |
| male / female | male / female | Trade usage; use *stekker / bus* when the plug-socket pair is meant |
| antenna | antenne | |
| extension cable | verlengkabel | |
| flexible flat cable (FFC) | platte flexkabel (FFC) | Keep the abbreviation after first mention |

### Operation, system behaviour and status

| English | Dutch | Note |
|:--------|:------|:-----|
| boat computer | boordcomputer | |
| to boot | opstarten | |
| first boot | eerste start | |
| shutdown | afsluiten | The noun is *het afsluiten* |
| graceful shutdown | gecontroleerd afsluiten | |
| to power down | uitschakelen | Cutting power, as opposed to *afsluiten* |
| power loss | spanningsuitval | The input goes away |
| blackout | stroomuitval | The boat's supply goes away; the firmware timer stays `blackouttimer` |
| glitch immunity | storingsongevoeligheid | |
| power management | energiebeheer | |
| status LED | status-led | Lowercase *led*, plural *leds* |
| LED bar | ledbalk | |
| monitoring | bewaking | |
| passive cooling | passieve koeling | |
| thermal pad | thermisch pad | |
| filesystem | bestandssysteem | |
| to unmount (a filesystem) | ontkoppelen | `het bestandssysteem wordt veilig ontkoppeld` |
| to unmount (a board or module) | demonteren | The English source uses one word for both — this one is mechanical: `het carrierboard demonteren` |
| to reseat (a module) | opnieuw plaatsen | |
| watchdog | watchdog | |
| standby | standby | `standbymodus`, one word |
| solo mode / co-op mode | solomodus / co-opmodus | Named firmware states; keep them recognisable |

### Software and networking

| English | Dutch | Note |
|:--------|:------|:-----|
| firmware | firmware | Not *bedrijfsprogrammatuur* — the trade term, as in every sibling |
| daemon | daemon | Not *achtergronddienst* |
| to flash | flashen | Past participle *geflasht* |
| system image / operating system image | systeemimage | |
| container image | containerimage | Not *systeemimage* — that is a disk image |
| container app | containerapp | |
| headless | zonder beeldscherm | First mention: `zonder beeldscherm (headless)` |
| deployment | ingebruikname | |
| dashboard | dashboard | `het dashboard` |
| WiFi Access Point | wifi-accesspoint | `wifi` lowercase in prose; `WiFi (wlan0)` stays as written when naming the menu item |
| wired / wireless | bekabeld / draadloos | |
| credentials | inloggegevens | |
| username / password | gebruikersnaam / wachtwoord | |
| default password | standaardwachtwoord | |
| single sign-on (SSO) | single sign-on (SSO) | Kept in English |
| Certificate Authority (CA) | certificaatautoriteit (CA) | |
| to trust (a certificate) | vertrouwen | |
| web interface | webinterface | |
| browser | browser | |
| system administration | systeembeheer | |
| package | pakket | Debian package → `Debian-pakket` |

### Applications and use cases

| English | Dutch | Note |
|:--------|:------|:-----|
| chart plotter | kaartplotter | |
| data logging | dataregistratie | |
| vessel | vaartuig | |
| engine parameters | motorgegevens | |
| fleet management | wagenparkbeheer | For ships it would be *vlootbeheer* |
| process monitoring | procesbewaking | |
| remote monitoring | bewaking op afstand | |
| predictive maintenance | voorspellend onderhoud | |
| electromagnetic interference (EMI/RFI) | elektromagnetische storing (EMI/RFI) | |
| compliance | conformiteit | |
| warranty | garantie | |

## HALMET terms

HALMET is a sensor interface board, so it needs vocabulary HALPI2 never used:
input circuits, measurement, and the things printed on a small PCB. **Rows above
this heading are shared with HALPI2 and must not be changed here alone.**

A handful of rows below repeat a shared row verbatim and are marked
`= shared row above` in the Note column. They are repeated because HALMET puts
them in a context HALPI2 never did — a *jumper* next to a *soldeerbrug*, a
*ground loop* as the reason for galvanic isolation — not because a second
decision was made. If one of those has to change, change it in the shared table
in both repositories.

### Grammatical gender of the new nouns

| Article | Nouns |
|:--------|:------|
| `de` | ingang, uitgang, gever, meter, teller, weerstand, spanningsdeler, drempelspanning, soldeerbrug, jumperheader, trapboor, dynamo, resolutie, ruis, scheiding, hysterese |
| `het` | ontwikkelbord, soldeereiland, laagdoorlaatfilter, alarmsignaal, motortoerental, stroomverbruik, klemmenblok, gescheiden deel |

`het filter` and `de filter` both exist in Dutch; the technical sense is
`het filter`, so write `het laagdoorlaatfilter`.

### Board and inputs

| English | Dutch | Note |
|:--------|:------|:-----|
| development board | ontwikkelbord | HALMET is sold as one. Never *carrierboard*, which is HALPI2's board, and never *moederbord* |
| digital input | digitale ingang | `D1`–`D4` stay as printed; the GPIO table's `DI1`–`DI4` too |
| analog input | analoge ingang | `A1`–`A4` stay as printed |
| input | ingang | Not *invoer*, which is data being typed in |
| output | uitgang | Not *uitvoer* |
| sender | gever | The marine sender a gauge reads. **Never *zender***, which is a radio transmitter; *sensor* is acceptable where the source says *sensor* |
| tank sender | tankgever | Established in the Dutch chandlery trade |
| resistive sender | weerstandsgever | The kind measured with the constant current source |
| tank level sensor | tankniveausensor | The source says *sensor* here, so does the translation |
| gauge (engine panel) | meter | `de meter op het motorpaneel`. Not *meterklok*; *multimeter* keeps its own name |
| counter | teller | |
| pulse counter | pulsteller | The firmware feature on a digital input |
| chain counter | kettingteller | Anchor chain; *ankerkettingteller* on first mention if the context is not obvious |
| alarm signal | alarmsignaal | |
| alarm switch | alarmschakelaar | The contact that produces the signal |
| engine RPM | motortoerental | Not *RPM*; Dutch prose says *toerental*, the unit is `omw/min` |
| engine revolutions | motoromwentelingen | What the pulse counter counts |
| tachometer | toerenteller | The instrument; *toerenteller* also names the signal source in `toerentellersignaal` |
| alternator W terminal | W-klem van de dynamo | Dutch automotive and marine trade says *dynamo* for the alternator; *alternator* is understood but is not what the reader will find on a wiring diagram |
| fuel flow | brandstofdebiet | *Debiet* is flow rate; *brandstofverbruik* is consumption and is a different quantity |
| bilge alarm | bilgealarm | Built on the shared `bilgewater` |
| light bulb (panel lamp) | controlelampje | The existing lamp in the alarm circuit of figure (a); an ordinary bulb is *gloeilamp* |

### Measurement, isolation and input circuits

| English | Dutch | Note |
|:--------|:------|:-----|
| galvanic isolation | galvanische scheiding | The established Dutch term. Not *galvanische isolatie*, which reads as insulating material |
| isolated (section, area) | gescheiden | `het gescheiden deel van de print`, `de gescheiden ingangen`. Not *geïsoleerd*, which means thermally or electrically insulated |
| digital isolator | digitale isolator | The component keeps its trade name even though the property is *scheiding* |
| isolated DC/DC converter | gescheiden DC/DC-omzetter | Powers the isolated section |
| isolation barrier | scheidingsbarrière | The figure caption *HALMET isolation barrier* → `de scheidingsbarrière van de HALMET`. *Isolatiebarrière* also occurs in Dutch datasheets; keep one word across the pages |
| ground loop | aardlus | = shared row above. It is the reason the isolation exists, so it appears on hardware/index.md |
| analog-to-digital converter (ADC) | analoog-digitaalomzetter | `AD-omzetter` after first mention. The part number `ADS1115` and the abbreviation `ADC` stay |
| resolution | resolutie | `een 16-bits resolutie` — attributive `16-bits`, see the units section |
| sampling rate | bemonsteringsfrequentie | Names the property. The value keeps trade usage: `860 samples per seconde`, not *monsters* |
| low-pass filter | laagdoorlaatfilter | `het filter`. The solder jumper is the `LP`-soldeerbrug, label unchanged |
| cutoff frequency | afsnijfrequentie | *Grensfrequentie* also occurs; use *afsnijfrequentie* on every page |
| noise (electrical, in a measurement) | ruis | Never *lawaai* or *geluid*, which are sound. `meetruis`, `een ruisig pulssignaal` |
| noise filtering (on the power input) | storingsfiltering | The two-stage filter on the NMEA 2000 input is EMI suppression, so *storing* — matching the shared `elektromagnetische storing` — not *ruis* |
| noise immunity | ruisongevoeligheid | What the Schmitt trigger buys on the digital inputs. Kept apart from the shared `storingsongevoeligheid`, which renders *glitch immunity* — a power-supply and firmware property, not an input-circuit one |
| voltage divider | spanningsdeler | The gauge and the sender together form one |
| constant current source (CCS) | constantstroombron | Also written *constante stroombron*; use the solid form per rule 4. The header label `CCS` stays as printed |
| excitation voltage | excitatiespanning | The voltage HALMET supplies to a sender that has no gauge. Not *voedingsspanning*, which is the board's own supply |
| passive voltage measurement | passieve spanningsmeting | Mode (a): an existing gauge is present |
| active resistance measurement | actieve weerstandsmeting | Mode (b): HALMET drives the sender itself |
| resistance (the measured quantity) | weerstand | `een weerstand van 320 Ω`. The component is also *weerstand*; let the sentence carry it, as the shared glossary does for `afsluitweerstand` |
| pull-up resistor | pull-upweerstand | English term joined solid to the Dutch noun, keeping the internal hyphen of the English term (rule 4) |
| pull-down resistor | pull-downweerstand | |
| threshold voltage | drempelspanning | `de drempelspanning voor een hoog signaal` |
| hysteresis | hysterese | Dutch drops the `-is`: *hysterese*, not *hysteresis* |
| floating (input) | zwevend | `de ingang blijft zweven en leest willekeurig hoog of laag` |
| normally open (NO) | maakcontact (NO) | Dutch electrical trade term. **Never *normaal open*.** The abbreviation `NO` is kept because it is printed on the switch packaging |
| normally closed (NC) | verbreekcontact (NC) | **Never *normaal gesloten*.** Matches the HALPI2 page, which already writes `drukknop met maakcontact` |
| self-resetting fuse | zelfherstellende zekering | The 500 mA PTC on the NMEA 2000 input |
| reverse polarity protection | ompoolbeveiliging | The trade term; *omgekeerde-polariteitsbeveiliging* is the literal rendering and is not used |
| overvoltage protection | overspanningsbeveiliging | Under-voltage is *onderspanningsbeveiliging* |
| ESD protection | ESD-beveiliging | Junction hyphen after the abbreviation (rule 4) |
| switching power supply | schakelende voeding | Not *schakelvoeding* |
| current consumption | stroomverbruik | `typisch stroomverbruik 90 mA bij 12 V` |
| short circuit | kortsluiting | = shared row above. On usage/index.md it is the fault an inline fuse protects against |
| chafing | schuren | = shared row above. `schuren van de kabel` |
| CAN transceiver | CAN-transceiver | |
| flash memory | flashgeheugen | Never *flitsgeheugen* |

### Board features and assembly

| English | Dutch | Note |
|:--------|:------|:-----|
| jumper | jumper | = shared row above. The **removable** link placed on a pin pair — the CCS jumpers. Repeated here only because HALMET sets it beside *soldeerbrug* |
| jumper header | jumperheader | The pin pair a jumper is placed on. Adopted English term, one word (rule 4); `pinheader` stays the general term |
| solder jumper | soldeerbrug | Closed **permanently with solder**, not with a removable jumper: the LP, pull-up, pull-down, CAN terminator and ADS1115 address jumpers. Getting this wrong sends the reader for a soldering iron they do not need, or has them trying to pull off something that is soldered down |
| to short (a jumper) | doorverbinden | `verbind de jumpercontacten door`. Avoid *kortsluiten*: in Dutch prose that reads as the fault, and `kortsluiting` is already the shared word for it |
| to close a solder jumper | dichtsolderen | The specific act for a `soldeerbrug`: `soldeer de brug dicht` |
| solder pad | soldeereiland | The established Dutch PCB term; *soldeervlak* is the material, *pad* alone is ambiguous next to *thermisch pad* |
| unpopulated | niet-bestukt | `niet-bestukte soldeereilanden voor EN en IO0`. *Bestukking* is the Dutch word for component placement |
| pitch | steek | = shared row above. `2,54 mm steek`, `3,81 mm steek` |
| pluggable terminal block | steekbaar klemmenblok | The shared `klemmenblok` already means the Phoenix MC part; add *steekbaar* only where the source contrasts it with a fixed one |
| silkscreen | opdruk | Inherited from the HALPI2 page vocabulary. `de opdruk op de achterzijde`; a quoted label stays verbatim: `de opdruk “DQ”` |
| to solder | solderen | |
| soldering iron | soldeerbout | |
| grommet | doorvoertule | Inherited from the HALPI2 page vocabulary. Rubber or silicone; distinct from `kabelwartel`, the threaded gland |
| step drill bit | trapboor | The one that looks like a small metal Christmas tree |
| conical drill bit | conische boor | Named alongside the step drill bit |
| panel connector | paneelconnector | The connector mounted through the enclosure wall |
| reset button | resetknop | The legend `Reset` on the board stays English and quoted |
| boot button | bootknop | The legend `Boot` stays English and quoted |
| bootloader | bootloader | Not *opstartlader* |
| download mode | downloadmodus | The ESP32 flashing state. Solid compound, matching `standbymodus` |
| user-programmable LED | door de gebruiker programmeerbare led | Lowercase `led` per rule 6 |
| open hardware | open hardware | Kept in English and lowercase, like `firmware`: `HALMET is open hardware` |

### A note on `connector` and `pinheader`

The shared glossary splits `connector` into *connector* and *aansluiting*, and
renders `header` as *pinheader*. That split is kept. HALMET puts the two side by
side far more often than HALPI2 does — *1-Wire header connector*, *analog input
connectors*, *jumper header contacts* — so let the qualifier carry the
distinction (`1-Wire-pinheader`, `de connectoren van de analoge ingangen`,
`de contacten van de jumperheader`) rather than inventing a second word. Where a
sentence would otherwise be ambiguous, say what the thing is: `pinstrip` for a
bare strip of pins, `kabelconnector` for the plug that goes onto it.

## Verification

A translated page is not done until:

1. `uv run mkdocs build --strict` passes — the same command CI runs.
2. `uv run python scripts/check_anchors.py site` passes.
3. `uv run python scripts/check_typography.py nl` reports `ok`.
4. `uv run python scripts/check_glossary.py nl` passes.
5. `uv run python scripts/translation_status.py` shows the page as current.
6. Lists render as lists — see
   `../best-practices/markdown-lists-need-blank-line-2026-05-16.md`.
7. **The seven rules at the top are counted against the pages, not re-read.**

That last one is the point of this section. A half-applied typography rule looks
followed when you read it, because rereading your own text confirms whatever it
already says. The French and German branches each shipped one to review for
exactly that reason.

`check_typography.py` counts rules 2, 4 and 5 for you. The rest are not covered
by any script, so run this:

```bash
python3 - <<'PY'
import pathlib, re
def prose(p):
    t = re.sub(r'^---\n.*?\n---\n', '', p.read_text(encoding='utf-8'), flags=re.S)
    t = re.sub(r'```.*?```', ' ', t, flags=re.S)   # code fences
    return re.sub(r'`[^`\n]*`', ' ', t)            # inline code
text = '\n'.join(prose(p) for p in sorted(pathlib.Path('docs/nl').rglob('*.md')))
n = lambda pat: len(re.findall(pat, text))
report = [
    ('rule 1  informal address je/jij/jouw/jullie', n(r'\b[Jj](?:e|ij|ouw|ullie)\b')),
    ('rule 1  reverential capital U',               n(r'\bU\b')),
    ('rule 3  spaced "carrier board"',              n(r'(?i)carrier board')),
    ('rule 3  capitalised common nouns',            n(r'(?<![.!?]\s)(?<!^)\b(?:Behuizing|Voeding|Zekering|Ingang|Soldeerbrug|Gever)\b')),
    ('rule 6  uppercase LED outside code',          n(r'\bLED')),
    ('rule 7  wrong article "het HALMET"',          n(r'\bhet HALMET\b')),
    ("rule 7  English possessive HALMET's",         n(r"HALMET['’]s")),
    ('terms   literal normaal open/gesloten',       n(r'(?i)normaal (?:open|gesloten)')),
    ('terms   zender used for a sender',            n(r'(?i)\bzender')),
    ('terms   ohm spelled out instead of Ω',        n(r'(?i)\d\s*k?ohm')),
    ('units   unspaced unit (12V, 0,9A, 120Ω)',     n(r'\d(?:V|A|W|Ω|°C|mm|kg|Hz)\b')),
    ('units   decimal point instead of comma',      n(r'(?<!v)\d\.\d')),
]
for label, count in report:
    print(f'{count:>4}  {label}')
print('\nevery count must be 0; inspect each hit, do not adjust the pattern')
PY
```

Three of these need judgement rather than a blind zero: version numbers such as
`v1.0.1` are identifiers and legitimately contain points, a heading may
legitimately start with a capitalised common noun, and `GPIO21`/`ADS1115` are
identifiers that the unit pattern does not match but a careless variant would.
Read the hits. Everything else is a defect.

Also confirm, as the skill requires, that every number in the English page
appears in the Dutch page. A wrong threshold voltage or a wrong fuse rating in an
installation guide is a safety problem, not a typo.

## Related

- `finnish-glossary.md`, `italian-glossary.md`, `spanish-glossary.md` — the
  siblings in this repository
- `../../../halpi2/solutions/translation/dutch-glossary.md` — the HALPI2
  original this file was copied from; shared rows must stay identical in both
- `solutions/best-practices/markdown-lists-need-blank-line-2026-05-16.md`
- mkdocs-static-i18n documentation: https://ultrabug.github.io/mkdocs-static-i18n/

## Terms added during translation

Reported by the page translators, consolidated here rather than written by each
of them, because several agents share this file. Inherited from HALPI2 unless a
note says otherwise; a row that HALMET has no use for is kept so the two
repositories stay comparable.

| English | Translation | Note |
|:--------|:------------|:-----|
| desktop setup | opstelling op het bureau | The pre-installation bench test. Avoided *desktopopstelling*, which collides with the graphical desktop meaning |
| graphical desktop / desktop interface | grafische werkomgeving | Kept distinct from *opstelling op het bureau* so the two English senses of "desktop" do not merge in Dutch |
| splash screen | opstartscherm | Boot logo screen |
| cable management | kabelbeheer | The wider planning/tidiness sense; *kabelroute* is the physical route |
| cable grommet | doorvoertule | Appears alongside *cable gland* (kabelwartel), so it needs its own word |
| mounting hardware | bevestigingsmateriaal | Corrosion-resistant screws and brackets |
| mounting screws | montageschroeven | |
| transportation damage | transportschade | |
| ambient (temperature) | omgevingstemperatuur | Renders "-20°C to +60°C ambient" as a single Dutch noun |
| cable tester | kabeltester | |
| circuit / dedicated circuit | groep | Dutch electrical-panel usage for a breaker circuit; *circuit* alone would read as an electronic circuit — which on HALMET pages it usually is, so check the sense before applying this row |
| wire (conductor in a multi-core cable) | ader | Cores inside one cable, so *ader*, not *draad* or *kabel* |
| positive / negative terminal | plusklem / minklem | Extends plus (+) / min (−) to the terminal at the power source |
| community forums | communityforums | Hat Labs support channel; solid compound per rule 4 |
| rainbow pattern (LED) | regenboogpatroon | HALPI2 LED fault pattern |
| boot mode switch | bootmodusschakelaar | HALPI2 only; on HALMET the equivalent is the `bootknop` |
| amber LED | amberkleurige led | |
| mass storage device | massaopslagapparaat | |
| command line tool | opdrachtregelgereedschap | "opdrachtregel" is the Dutch term for command line |
| block device | blockdevice | Adopted English two-word term becomes one Dutch word (rule 4) |
| device node | apparaatknooppunt | |
| hardware flow control | hardwarematige flowcontrol | "stromingsregeling" would read as fluid dynamics |
| chip select | chipselect | One word, adopted whole |
| Unix domain socket | Unix-domainsocket | Proper name takes exactly one hyphen at the junction (rule 4) |
| setup wizard | installatiewizard | |
| update manager | updatebeheer | Matches the *beheer* pattern (systeembeheer, energiebeheer) |
| port forwarding | port forwarding | Dutch network documentation uses the English term |
| login console | inlogconsole | |
| silk screen (board legend) | opdruk | Also a HALMET term; see `## HALMET terms` |
| computer mainboard | hoofdprint van de computer | HALPI2 only. *moederbord* is forbidden, so this is the alternative |
| device tree overlay | device tree overlay | Kept in English; the reader meets it verbatim in `config.txt` |
| board-to-board connector | board-to-boardconnector | Adopted English term, one Dutch word, internal hyphens kept |
| expansion board | uitbreidingsprint | Distinct from *carrierboard* and from *ontwikkelbord* |
| spudger | spudger | No Dutch equivalent in trade usage |
| guitar pick | plectrum | |
| to pry / to rock (a connector loose) | wrikken | |
| Label (table column heading) | Aanduiding | *Label* exists in Dutch but reads as a sticker |
| socket (hex tool) | dop / dopsleutel | Kept apart from *aansluiting* |
| surface-mounted component | SMD-component | SMD is the established Dutch trade abbreviation |
| countersunk screw | verzonken schroef | |
| heat spreading area | warmteafvoervlak | |
| Blinkenlights | Blinkenlights | Heading left untranslated — it is a joke term, not a description |
| Load Equivalency Number (LEN) | belastingsgetal (LEN) | NMEA 2000 network loading; the abbreviation is kept |
| voltage bar (LED pattern) | spanningsbalk | HALPI2 LED pattern; *ledbalk* is the physical bar |
| power button | aan/uit-knop | |
| transmit enable (signal/mode) | zendvrijgave | RS-485; one of the few places *zend-* is correct, because it really is a transmitter |
| watchdog timeout | watchdog-time-out | "time-out" is the Dutch spelling |
| grace period | wachttijd | "Respijtperiode" is legal register and wrong here |
| normally-open (NO) momentary switch | drukknop met maakcontact (normally open, NO) | The HALPI2 row that fixes *maakcontact*; HALMET extends it with *verbreekcontact* |
| Battery-Backed RAM (BBR) | batterijgebufferd RAM (BBR) | |
| half-duplex mode | halfduplexmodus | Solid compound, no hyphen |
| multi-talker / single-talker network | multi-talkernetwerk / single-talkertoepassing | Kept in English as trade usage, joined solid to the Dutch noun |
| baud rate / update rate | baudrate / updatesnelheid | |
| progressive fill / solid / dim red (LED states) | oplopende vulling / continu / gedempt rood | HALPI2 LED patterns |
| wake-up event | wekgebeurtenis | |
| Data Browser (Signal K) | Data Browser | A UI string the reader sees in English on their own screen |
| bps / kbps / Mbps (bit rate) | bit/s / kbit/s / Mbit/s | `16.3 kbps` on the 1-Wire section becomes `16,3 kbit/s` |
| Bluetooth | Bluetooth | Capitalised, unlike `wifi`. In compounds it takes exactly one hyphen at the junction (rule 4): `Bluetooth-verbinding` |
| tool / utility | gereedschap | Never *hulpmiddel*, which reads as an aid rather than a program |
| command | opdracht | Never *commando*, which in Dutch reads as a military order |
| section (of this documentation) | onderdeel | Not *gedeelte* and not *sectie* — *sectie* is reserved for a section of a configuration file. A section of the board is `deel` (`het gescheiden deel`) |
| Ethernet port | ethernetaansluiting | Board-mounted socket, so the *aansluiting* branch applies. Other ports stay *poort* (`USB-poort`) |
| USB Boot connector | USB-bootconnector | HALPI2 only. On HALMET the equivalent is the `micro-USB-connector` |
</content>
</invoke>
