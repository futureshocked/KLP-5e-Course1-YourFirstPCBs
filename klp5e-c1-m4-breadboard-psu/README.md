# klp5e-c1-m4-breadboard-psu stages

One folder per step of the breadboard power supply, used by Course 1 Modules 4 and 6 and
Activity A4.1. Each stage is the project as it stood at the end of a lecture and the start of the
next one. Open the `.kicad_pro` file inside a stage folder in KiCad.

The project starts from the end of Module 3, so the first stage is `03`. J1 is the USB-C
connector you sourced in Module 3; its symbol and footprint live in each stage's `Libraries/`
folder.

| Stage | State |
|---|---|
| `03-project-ready` | New project with Module 3's libraries copied in and registered |
| `04-symbols-placed` | Every symbol placed and annotated, no wires |
| `05-wired` | Schematic wired, including the no-connect flag on SW1 and the shield to ground |
| `06-values-set` | Resistor and capacitor values set (F1 keeps `Polyfuse` until Module 6) |
| `07-footprints-assigned` | Every symbol has a footprint |
| `08-erc-clean` | Power flags added; the electrical rules check reports 0 errors |
| `09-outline-drawn` | Footprints imported into the board and the outline drawn |
| `10-parts-placed` | Connectors on the edges, the rest placed, outline trimmed and its corners rounded |
| `11-routed` | Power and signal tracks routed at 0.8 mm and 0.4 mm, ground left for the pour |
| `12-ground-poured` | Ground plane poured on the bottom layer |
| `13-drc-clean` | The four shield tracks added; DRC reports 0 errors and 0 unconnected items |
| `14-silkscreen-done` | Designators resized and labels added on the silkscreen; the finished Module 4 board and the start of A4.1 |
| `15-a1-example-solution` | A4.1's worked solution: J3 added to feed the far rail of the breadboard |
| `16-ready-to-order` | The Module 6 result: F1 set to `500mA`, the bill of materials (`klp5e-c1-m4-breadboard-psu.csv`), and in `c1-m4-breadboard-psu/` the seven Gerber layers, the job file, one drill file and the zip you upload to the manufacturer |
