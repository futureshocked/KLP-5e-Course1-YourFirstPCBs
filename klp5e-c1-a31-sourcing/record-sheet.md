# A3.1 record sheet

Part number: ______________________  Datasheet version: ________

## 1. The tree

| Question | Your answer | How you know |
|---|---|---|
| Stage 1: in KiCad's standard library? | | What you searched, in which chooser, and what came back. Any near miss, and why it is a different part |
| Stage 2: from a reliable source? | | Which source (SnapMagic, unless you had to move on), the exact part number in the row you picked, and whether it offered a symbol, a footprint and a 3D model |
| Stage 3: author it yourself | Not in this activity | |

**The stage that answered it:** ______

If a download failed a check and you moved to another source, write both here: the source you
rejected, the number that decided it, and the source you used instead.

## 2. The download

| Question | Your answer |
|---|---|
| Where it came from, and the file name of the download | |
| What was in the download? | |
| Which files did you keep? | |
| Library nickname(s) you registered | |
| The footprint named in the symbol's Footprint field | |
| Does that match your nickname and footprint name? If not, what will you do when you place it? | |
| The 3D model path in the footprint, as downloaded | |
| The 3D model path after you fixed it | |

## 3. The footprint against the land pattern

Write the datasheet's number first, then what you measured in KiCad.

| Check | Datasheet | Footprint | Match? |
|---|---|---|---|
| Number of pads, and how they are numbered | | | |
| Pitch between neighbouring pads | | | |
| Pad 1 to the last pad in the same row | | | |
| Distance between the two rows | | | |
| Pad size | | | |
| The pad in the middle: size, and how it is made up | | | |
| Where pin 1 is | | | |
| Module outline, width by length | | | |
| Anything the drawing shows that the footprint does not | | | |

## 4. The symbol against the pin table

| Check | Datasheet | Symbol | Match? |
|---|---|---|---|
| Number of pins | | | |
| Pin 1 name | | | |
| Every ground pin number | | | |
| The pin marked NC | | | |
| Any name that differs (write both) | | | |

## 5. The travel test

| Check | Result |
|---|---|
| Every path in `sym-lib-table` begins `${KIPRJMOD}` | |
| Every path in `fp-lib-table` begins `${KIPRJMOD}` | |
| Copy opened from a new location: footprint loads | |
| Copy opened from a new location: 3D model shows | |

## Verdict

**Pass / Reject:** ______

If you rejected it, which number decided it:
