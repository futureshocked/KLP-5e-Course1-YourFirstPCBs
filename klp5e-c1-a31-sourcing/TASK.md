# A3.1: Source a part you have never used

You have a manufacturer part number and its datasheet, and nothing else. Your job is to get the
part into a KiCad project the way Module 3 showed you, and to prove it is right before you trust it.

Allow 30 to 45 minutes.

## The part

**`ESP32-C6-WROOM-1-N8`**, a Wi-Fi 6, Bluetooth LE and Thread module made by Espressif.

Datasheet (free, no login):
<https://documentation.espressif.com/esp32-c6-wroom-1_wroom-1u_datasheet_en.pdf>

You need two parts of it:

1. **Figure 11-1, "ESP32-C6-WROOM-1 Recommended PCB Land Pattern"**, on page 44. This is the
   page you check the footprint against.
2. **Table 3-1, "Pin Definitions"**, on page 11. This is the table you check the symbol against.

Page numbers are for datasheet version 1.4. If Espressif has published a newer version, find the
figure and the table by their names.

Would you rather source a part of your own? Do that instead, as long as it is one no lecture has
used. The steps and the record sheet are the same. The worked solution then shows you what a
finished answer looks like, even though it is for a different part.

## What to do

1. **Make a new, empty KiCad project** for this, for example `a31-sourcing`. Keep it away from
   the Module 4 project.
2. **Work the tree in order** (lecture 3.1). Search the standard library first, both choosers
   (lecture 3.2). Stop at the first yes. Write down which stage answered it, and why the stage
   before it did not.
3. **Get the files** for the part: symbol, footprint and 3D model (lecture 3.4). Whatever the
   source, look inside the download before you use it. Take only what this part needs.
4. **Put them inside the project and register them** in the Project Specific tables, on
   `${KIPRJMOD}` paths (lecture 3.5).
5. **Check the footprint against Figure 11-1** (lecture 3.3): pad count, pitch, pad size, pin 1
   and the outline. Measure. Don't trust a number you have not measured.
6. **Check the symbol against Table 3-1**: every pin number and every name. This check is new,
   but it is the same idea as step 5.
7. **Make the project travel** (lecture 3.6). Give the 3D model a `${KIPRJMOD}` path, then copy
   the project folder somewhere new, open the copy, and confirm nothing is missing.
8. **Fill in `record-sheet.md`** as you go, not at the end.

## You are done when

1. The project folder holds the symbol library, the footprint library and the 3D model, and both
   library tables contain nothing but `${KIPRJMOD}` paths.
2. A copy of the folder, opened somewhere else, shows the footprint and its 3D model.
3. Every line of the record sheet is filled in, with a pass or a reject at the bottom.

## The worked solution

It is in `worked-solution/`. Open it last, after your record sheet is finished. Compare your
record sheet with its `SOLUTION.md`. Where you disagree, measure again before deciding who is
right.
