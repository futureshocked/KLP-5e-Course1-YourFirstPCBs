# klp5e-c1-m5-solar-psu stages

One folder per step of the tiny solar power supply, used by Course 1 Module 5 and Activities
A5.1 and A5.2. Each stage is the project as it stood at the end of a lecture and the start of the
next one. Open the `.kicad_pro` file inside a stage folder in KiCad.

| Stage | State |
|---|---|
| `00-libraries-waiting` | New project, the three part libraries not yet registered |
| `01-libraries-registered` | Symbol and footprint libraries registered |
| `02-annotated` | Symbols placed and annotated |
| `03-values-set` | Sixteen parts named and valued, no wires (the start of A5.1) |
| `04-schematic-complete` | Schematic fully wired |
| `04b-erc-clean` | Schematic wired and the electrical rules check clean |
| `05-parts-placed` | Footprints imported and placed on the board, no outline tightened yet |
| `06-outline-tightened` | Board outline shrunk to fit and its corners rounded |
| `07-routed` | Every connection except ground routed on the top layer |
| `08-drc-clean` | Ground pour and stitching via added; DRC reports 0 errors and 0 unconnected items |
| `09-silkscreen-done` | Reference designators resized and moved, text added on the silkscreen |
| `10-3d-models` | 3D models attached; the finished board (the worked solution for A5.2) |
