# A3.1: Source a part you have never used

You have a manufacturer part number and its datasheet. Your job is to find a ready-made symbol,
footprint and 3D model for it, import them into a new KiCad project, and prove they are right
before you trust them. It is the process from lectures 3.1 to 3.6, on a part no lecture has shown
you.

Allow 30 to 45 minutes.

## Find the part; do not draw it

The sourcing tree from lecture 3.1 has three stages. This activity uses the first two:

1. **Stage 1:** look for the part in KiCad's standard library.
2. **Stage 2:** download it from a reliable source and import it. For this part, the source to use
   is SnapMagic, at <https://www.snapeda.com>.

**Stage 3, drawing the symbol and footprint yourself, is not part of this activity.** Every file
you need already exists, made by someone else. You will open the Symbol Editor and the Footprint
Editor to look at and measure what you downloaded, and to set the 3D model's path, but you never
draw, move or resize a pin or a pad. Authoring a part is Volume 2 and Course 2. If the download
fails a check, go to [If you get stuck](#if-you-get-stuck); don't fix it by hand.

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

## Before you start

1. KiCad 10, installed and working.
2. A free SnapMagic account. SnapMagic used to be called SnapEDA, and its address is still
   snapeda.com. Browsing is open to everyone, but downloading needs you to be signed in.
3. The datasheet, open at Figure 11-1.
4. `record-sheet.md`, open beside KiCad. Fill it in as you go, not at the end. It asks for
   numbers, not ticks.

## Step 1: Make a new project

In the KiCad project manager, choose File → New Project… and call it `a31-sourcing`. Save it
somewhere of its own, away from the Module 4 project. Leave the schematic and the board empty;
nothing gets placed in this activity.

## Step 2: Look in KiCad's standard library (stage 1, lecture 3.2)

1. Open the schematic editor, press **A** and click the sheet to open the symbol chooser. Search
   `esp32-c6` and read the full name of every result.
2. Press Esc. Open the PCB editor, press **A** and click the board to open the footprint chooser.
   Search `c6-wroom`, then `wroom`.
3. The answer is yes only if you find `ESP32-C6-WROOM-1` itself. A module with the same chip but a
   different name, such as a MINI instead of a WROOM, is a different part with a different size and
   pad layout. A near miss is a no.
4. Fill in section 1 of the record sheet: what you searched, in which chooser, and what came back.

If the answer is no, carry on to step 3. If a later KiCad release has added the module and the
answer is yes, record that, and carry on to step 3 anyway: this activity is about importing, the
same way lecture 3.4 imported a connector the library already had.

Close both editors without saving.

## Step 3: Download it from SnapMagic (stage 2, lecture 3.4)

1. Go to <https://www.snapeda.com> and sign in.
2. Search the full part number, `ESP32-C6-WROOM-1-N8`. Search the part number, never a
   description: a description matches dozens of lookalikes.
3. In the results table, find the row whose Part column reads `ESP32-C6-WROOM-1-N8` exactly, made
   by Espressif Systems. Skip the boxed advert above the table and the cards below it; they are
   other parts.
4. Watch for the near miss. `ESP32-C6-WROOM-1U-N8` has a **U** in it: it is the version with an
   antenna connector instead of an antenna on the module, and it is a different part.
5. Check the icons at the right of the row. You want a symbol, a footprint and a 3D model, all
   three.
6. Open the part page and take a first look at the previews: a row of pads down each long side and
   a group of pads in the middle. This is a first look, not the check; the check is step 5.
7. Click "Download Symbol and Footprint", choose **KiCad**, then **V6 & Later**. V6 and later
   covers every modern KiCad, including 10.
8. Unzip the download into a scratch folder, not the project yet. Find the three files you need:
   the symbol ends `.kicad_sym`, the footprint ends `.kicad_mod`, and the 3D model ends `.step`.
   If the zip has no `.step`, download the 3D model from the same part page, in STEP format.
9. Fill in the first two lines of section 2 of the record sheet: everything that came in the
   download, and the three files you keep. The rest stays behind.

## Step 4: Bring the files into the project (lecture 3.5)

Give the library a nickname. These steps use `ESP32_C6_Local`, the same pattern as lecture 3.5's
`USB_C_Local`.

1. In your file manager, open the project folder and make a folder called `Libraries`. Inside it,
   make two more folders: `ESP32_C6_Local.pretty` and `3D_models`.
2. Move the `.kicad_mod` into `ESP32_C6_Local.pretty`. Move the `.kicad_sym` into `Libraries` and
   rename it `ESP32_C6_Local.kicad_sym`. Move the `.step` into `3D_models`.
3. Symbols first. In the schematic editor, choose Preferences → Manage Symbol Libraries… and open
   the **Project Specific Libraries** tab. Click the folder button at the bottom left and pick
   `Libraries/ESP32_C6_Local.kicad_sym`.
4. Read the row it made. The nickname should be `ESP32_C6_Local` and the path
   `${KIPRJMOD}/Libraries/ESP32_C6_Local.kicad_sym`. If the path starts with your home folder or a
   drive letter instead, edit it so it begins `${KIPRJMOD}`. Click OK.
5. Footprints, the same way. In the PCB editor, choose Preferences → Manage Footprint Libraries…,
   open the **Project Specific Libraries** tab, click the folder button and pick the
   `ESP32_C6_Local.pretty` folder. The path should be
   `${KIPRJMOD}/Libraries/ESP32_C6_Local.pretty`. Click OK.
6. Fill in the next lines of section 2: the nickname you registered, and the footprint named in
   the symbol's Footprint field. To read the field, open the symbol in the Symbol Editor and open
   Symbol Properties, then close it with Cancel. It probably names a nickname you did not choose. Write down both, and note that
   when you place this part on a real board, you pick `ESP32_C6_Local:<footprint name>` in the
   footprint assignment step (lecture 1.6).

## Step 5: Check the footprint against Figure 11-1 (lecture 3.3)

Open the Footprint Editor, pick the `ESP32_C6_Local` library, and open the footprint. Measure
everything; don't eyeball it.

- To read a pad's size and position, double-click it to open Pad Properties. Close with Cancel.
- To measure a distance, use the Measurement tool (Ctrl+Shift+M): click the start point, then the
  end point.

Work down section 3 of the record sheet. For each line, write the datasheet's number first, then
the number you measured:

1. The number of pads, and how they are numbered.
2. The pitch between neighbouring pads.
3. Pad 1 to the last pad in the same row.
4. The distance between the two rows, centre to centre.
5. The pad size.
6. The pad in the middle: its overall size, and how it is made up.
7. Where pin 1 is.
8. The module outline, width by length.
9. Anything the drawing shows that the footprint does not.

One number that does not match is a reject. Close the Footprint Editor without saving.

## Step 6: Check the symbol against Table 3-1

Open the Symbol Editor, pick the `ESP32_C6_Local` library and open the symbol. Look; don't change
anything.

Compare every pin with Table 3-1: every number and every name. The symbol may spell a name out in
full where the table uses a short name, for example `MTMS/GPIO4/ADC1_CH4` for the table's `IO4`.
That is a match if the pin number and the function are the same. A pin with the wrong number, or
a missing pin, is a reject. Fill in section 4 of the record sheet, then close the Symbol Editor
without saving.

## Step 7: Give the 3D model a `${KIPRJMOD}` path (lecture 3.6)

1. In the Footprint Editor, open the footprint again, then open Footprint Properties and its
   **3D Models** tab.
2. Write down what is there on the record sheet, as downloaded: nothing, or a path. A downloaded
   footprint often names no model, or names one in a folder your project doesn't have.
3. If there is a row with a path outside the project, delete that row.
4. Add a model with the folder button and pick the `.step` file in `Libraries/3D_models`. Leave
   "Embed File" unticked.
5. The path should read `${KIPRJMOD}/Libraries/3D_models/<file>.step`. If it starts with your home
   folder or a drive letter, edit it so it begins `${KIPRJMOD}`. Write the fixed path on the record
   sheet.
6. Check that the module appears in the dialogue's 3D preview. Click OK, then press Ctrl+S to save
   the footprint into the project's library.

This is the one change you make to a downloaded file, and it changes where the model is found, not
the footprint itself.

## Step 8: The travel test (lecture 3.6)

1. Open `sym-lib-table` and `fp-lib-table` in the project folder with a text editor. Every path in
   both must begin `${KIPRJMOD}`.
2. Close KiCad. Copy the whole project folder somewhere new, then rename the original so nothing
   can reach it.
3. Open the copy. In the Footprint Editor, check that `ESP32_C6_Local` is listed, that the
   footprint opens, and that the 3D preview shows the model.
4. Close KiCad, delete the copy, and rename the original back.
5. Fill in section 5 of the record sheet, then the verdict at the bottom.

## You are done when

1. The project folder holds the symbol library, the footprint library and the 3D model, and both
   library tables contain nothing but `${KIPRJMOD}` paths.
2. A copy of the folder, opened somewhere else, shows the footprint and its 3D model.
3. Every line of the record sheet is filled in, with a pass or a reject at the bottom.

## If you get stuck

1. **SnapMagic has no 3D model, or the download fails a check in step 5 or 6.** Don't edit the
   pads or pins to make it pass. Try the next reliable source on lecture 3.1's list, the maker's
   own library: Espressif publishes one at <https://github.com/espressif/kicad-libraries>. Record
   the rejected download and the reason, then run the same checks on the new one.
2. **The folder button gave you a full path, not `${KIPRJMOD}`.** Edit the path by hand in the
   table. The part of the path after the project folder stays the same.
3. **The footprint opens but the 3D preview is empty.** The model path is wrong or the file is not
   where the path says. Check the spelling of `3D_models` and the `.step` file name, letter by
   letter.

## Your own part instead

You may source a part of your own instead, if all of these are true:

1. No lecture has used it.
2. It is not in KiCad's standard library.
3. SnapMagic has a symbol, a footprint and a 3D model for it. Check this before you start.
4. Its datasheet has a recommended land pattern and a pin table.

The steps and the record sheet are the same. The worked solution then shows you what a finished
answer looks like, even though it is for a different part.

## The worked solution

It is in `worked-solution/`. Open it last, after your record sheet is finished, and compare your
record sheet with its `SOLUTION.md`. Where you disagree, measure again before deciding who is
right.

The worked solution's files come from Espressif's own library, not SnapMagic, because its licence
lets us pass the files on to you. Your answers in section 2 (file names, nickname, and the 3D
model path as downloaded) will differ from it. The datasheet numbers in sections 3 and 4 are the
same whichever source you used.
