# A3.1 worked solution: ESP32-C6-WROOM-1-N8

Finish your own record sheet before you read this.

Worked on 2026-09-23 with KiCad 10.0.6 and its standard libraries (10.0.6), the Espressif KiCad
library release 3.2.1, and the datasheet "ESP32-C6-WROOM-1 & WROOM-1U Datasheet" version 1.4.

## 1. The tree

| Question | Answer | How we know |
|---|---|---|
| Stage 1: in KiCad's standard library? | **No** | Symbol chooser, `esp32-c6`: one hit, `RF_Module:ESP32-C6-MINI-1`. Footprint chooser, `c6-wroom`: nothing. |
| Stage 2: from a reliable source? | **Yes** | SnapMagic lists `ESP32-C6-WROOM-1-N8` by Espressif Systems with a symbol, a footprint and a 3D model. Espressif, the manufacturer, also publishes its own KiCad library on GitHub, free and with no login, and its README says every footprint follows the datasheet's Recommended PCB Land Pattern. |
| Stage 3: author it yourself | Not in this activity | Stage 2 answered it, and this activity never goes to stage 3. |

**The stage that answered it: stage 2.**

The trap at stage 1 is the MINI-1. It is the same chip in a different module, 13.2 by 16.6 mm
with a different pad layout, so it is a different part. A near miss in the chooser is a no.

The trap at stage 2 is `ESP32-C6-WROOM-1U-N8`, which sits right beside it in SnapMagic's results.
The U version has an antenna connector instead of an antenna on the module. It is a different part.

SnapMagic is the source the task sends you to, and the first stop on lecture 3.1's list. The files
in this worked solution come from the next source on that list, Espressif's own library, because
Espressif's licence lets us pass its files on to you. Both are reliable sources, and both answer
the tree at stage 2.

This answer belongs to KiCad 10.0.6. The standard library grows between releases, so if a later
release adds the WROOM-1, stage 1 answers it instead. Ask the question every time.

## 2. The download

This section describes Espressif's download, the one this worked solution is built from. If you
used SnapMagic, as the task says, your file names, your nickname and your 3D model path as
downloaded will all be different, and that is fine. Compare the pattern instead: what came in the
download and what you kept, whether the symbol's Footprint field names a nickname you registered,
and whether the downloaded 3D model path points anywhere inside your project.

The library comes from <https://github.com/espressif/kicad-libraries/releases/latest>, as
`espressif-kicad-addon.zip`. That is 55 MB, and it unpacks to about 260 MB for the whole Espressif
range. The README's own route is to install it through the Plugin and Content Manager. That
installs it for every project on the machine, which is exactly what this task avoids, so we
unzipped it instead.

| Question | Answer |
|---|---|
| What was in the download? | `symbols/Espressif.kicad_sym` (49 symbols), `footprints/Espressif.pretty/` (54 footprints), `3dmodels/espressif.3dshapes/` (STEP models), plus `metadata.json` and an icon for the Plugin and Content Manager |
| Which files did we keep? | `Espressif.kicad_sym`, the whole file, because one library file is not split without editing it; `ESP32-C6-WROOM-1.kicad_mod` only, in a new `Espressif.pretty` folder; `ESP32-C6-WROOM-1.STEP` only |
| Library nicknames registered | `Espressif`, in both Project Specific tables |
| The symbol's Footprint field | `PCM_Espressif:ESP32-C6-WROOM-1` |
| Does it match? | **No.** `PCM_Espressif` is the nickname the Plugin and Content Manager would have created. Our nickname is `Espressif`. When the module is placed, assign `Espressif:ESP32-C6-WROOM-1` in the footprint assignment step (lecture 1.6). |
| 3D model path, as downloaded | `${KICAD8_3RD_PARTY}/3dmodels/com_github_espressif_kicad-libraries/espressif.3dshapes/ESP32-C6-WROOM-1.STEP` |
| 3D model path, fixed | `${KIPRJMOD}/Libraries/3D-models/ESP32-C6-WROOM-1.STEP` |

The downloaded model path points into the Plugin and Content Manager's folder, where this file never
went. Left alone, the footprint shows bare pads in the 3D viewer. Fixing it is lecture 3.6's move.

The zip carries no licence file. The licence is in the GitHub repository: CC-BY-SA 4.0, with an
exception that leaves your own designs free. It is kept here as `Libraries/LICENSE-Espressif.md`
because this worked solution passes the library on to you, and the licence requires that.

## 3. The footprint against the land pattern

Datasheet Figure 11-1, "ESP32-C6-WROOM-1 Recommended PCB Land Pattern", page 44. All values in
millimetres. The footprint values are pad centres read from Pad Properties and distances measured
with the Measurement tool.

The Datasheet column is the same for any download. The Footprint column is what we measured in
Espressif's file. A footprint from SnapMagic may be built differently, for example with the middle
pad drawn another way, so measure your own and judge it against the Datasheet column, not against
ours.

| Check | Datasheet | Footprint | Match? |
|---|---|---|---|
| Number of pads, and numbering | 28 edge pads, 1 to 14 down the left, 15 to 28 up the right, plus pin 29, the thermal pad | 28 edge pads, same numbering; nine small pads all numbered 29 | Yes |
| Pitch between neighbours | 1.27 | 1.27 | Yes |
| Pad 1 to pad 14 | 16.51 | 16.51 | Yes |
| Between the two rows, centre to centre | 17.5 | 17.5 (pads at x = ±8.75) | Yes |
| Pad size | 1.5 by 0.9 ("28x1.5", "28x0.9") | 1.5 by 0.9 | Yes |
| The thermal pad | 3.3 square, nine 0.8 squares with 0.45 gaps | nine 0.8 squares, 1.25 apart centre to centre (0.8 + 0.45), 3.3 overall | Yes |
| Where pin 1 is | Top of the left row, just below the antenna area, 7.49 below the module's top edge | Pad 1 at the top of the left row, 7.49 below the outline's top edge | Yes |
| Module outline | 18 by 25.5 | 18 by 25.5, on the silkscreen | Yes |
| Pads beyond the module edge | 0.5 | 0.5 (pad outer edge at 9.5, outline at 9.0) | Yes |
| Thermal pad position | 7.495 from the module's left edge, 12.29 from its bottom edge | 7.495 and 12.29 | Yes |
| Antenna area | 18 by 6 at the top, nothing on any copper layer | A keep-out zone, 18 by 6, on all copper layers: no tracks, vias, pads or pours | Yes |
| What the drawing shows and the footprint does not | Vias in the thermal pad ("Via for thermal pad") | No vias | See below |

The thermal-pad vias are a board decision, not a footprint defect. You add them when you lay out the
board. Note it on your record sheet and move on.

## 4. The symbol against the pin table

Datasheet Table 3-1, "Pin Definitions", page 11.

| Check | Datasheet | Symbol | Match? |
|---|---|---|---|
| Number of pins | 29 | 29 | Yes |
| Pin 1 | GND | GND | Yes |
| Ground pins | 1, 28, and 29 (EPAD) | 1, 28, 29 | Yes |
| NC | 22 | 22, NC | Yes |
| Names that differ | The table uses short names: `IO4`, `EN`, `RXD0`, `TXD0` | The symbol spells out functions: `MTMS/GPIO4/ADC1_CH4`, `EN/CHIP_PU`, `U0RXD/GPIO17`, `U0TXD/GPIO16` | Yes: same pin numbers, same functions |

We checked all 29 pins, not only the ones in the table above. The Symbol column shows Espressif's
names; a symbol from SnapMagic may use the table's short names instead. Either is a match when the
pin number and the function agree.

## 5. The travel test

| Check | Result |
|---|---|
| `sym-lib-table` | One row, `${KIPRJMOD}/Libraries/Espressif.kicad_sym` |
| `fp-lib-table` | One row, `${KIPRJMOD}/Libraries/Espressif.pretty` |
| Copy opened from a new location: footprint loads | Yes |
| Copy opened from a new location: 3D model shows | Yes, with the fixed path. With the downloaded path, the same copy shows bare pads. |

We ran the test on a copy in a different folder, with a KiCad configuration that had no libraries
registered at all, so nothing on the original machine could fill a gap.

## Verdict

**Pass.** Every number on Figure 11-1 matches, and so does every pin in Table 3-1. Before this
project was self-contained, two things had to be put right: the 3D model path, and the footprint
nickname in the symbol, which you deal with when you place the module. Neither is a reason to reject
the part. They are the reason you look inside every download.

## What is in this folder

```
esp32-c6-sourcing/
├── esp32-c6-sourcing.kicad_pro   an empty project; nothing is placed
├── esp32-c6-sourcing.kicad_sch
├── esp32-c6-sourcing.kicad_pcb
├── sym-lib-table                 Espressif -> ${KIPRJMOD}/Libraries/Espressif.kicad_sym
├── fp-lib-table                  Espressif -> ${KIPRJMOD}/Libraries/Espressif.pretty
├── SOLUTION.md                   this file
└── Libraries/
    ├── Espressif.kicad_sym       unchanged from release 3.2.1
    ├── Espressif.pretty/
    │   └── ESP32-C6-WROOM-1.kicad_mod   release 3.2.1, 3D model path changed
    ├── 3D-models/
    │   └── ESP32-C6-WROOM-1.STEP        unchanged from release 3.2.1
    └── LICENSE-Espressif.md
```

To see it for yourself, open the project and open the Footprint Editor. Pick
`Espressif` → `ESP32-C6-WROOM-1`, then open Footprint Properties and its 3D Models tab.
