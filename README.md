# Chu Chu Rocket! VMU Tools

Two browser tools for Chu Chu Rocket! save files on the Dreamcast VMU:

- **Character Editor** – draw your own mouse and cat animation frames and export them as a character-set save.
- **Puzzle Pack Maker** – combine up to 25 puzzle saves into a single puzzle pack.

Each tool is one self-contained HTML file. There is nothing to install and no server: your files are read in your browser and are not uploaded anywhere.

| File | Tool |
| --- | --- |
| `Chu-Chu-Rocket-Character-Editor.html` | Character Editor |
| `Chu-Chu-Rocket-Puzzle-Pack-Maker.html` | Puzzle Pack Maker |

## Getting started

1. Download the HTML file for the tool you want (or clone this repository).
2. Open it in a current desktop browser such as Chrome, Edge, Firefox or Safari. Double-clicking the file is enough.
3. Follow the instructions for that tool below.

The pages load their fonts from Google Fonts when you are online. Offline they fall back to fonts already on your computer and work the same.

To use the tools from a web address instead of a downloaded file, turn on GitHub Pages for this repository (Settings → Pages → deploy from your main branch) and open the HTML files from the Pages URL.

---

## Character Editor

A character-set save holds eight pictures ("frames"), each 32 × 32 pixels: four for the mouse, then four for the cat. The editor lets you change all eight.

### 1. Load something to edit

- **Open .VMS** – open an existing character-set save. You can also drop the file anywhere on the page.
- **New blank set** – start with eight empty frames.
- When the page first opens, a built-in example set (a snail and a storm cloud) is loaded so you can try the tools straight away.

Your work in progress is kept in your browser, so reloading the page picks up where you left off.

### 2. Pick a frame

The strip at the top shows the four **Mouse slot** frames and the four **Cat slot** frames. Click one to edit it. The `,` and `.` keys step to the previous and next frame.

### 3. Draw

| Tool | Key | What it does |
| --- | --- | --- |
| Pencil | `B` | Paints single pixels in the current color. Drag to draw a line. |
| Eraser | `E` | Makes pixels transparent. |
| Fill | `G` | Fills the touching area of same-colored pixels. |
| Pick | `I` | Takes the color of the pixel you click. Alt-click does the same with any tool. |

- **Undo / Redo** – also `Ctrl+Z` and `Ctrl+Shift+Z` (or `Ctrl+Y`). On a Mac use `Cmd`.
- **Grid** – shows or hides the pixel grid.
- **Onion skin** – faintly shows the previous frame of the same character underneath, which helps keep an animation steady.

### 4. Choose colors

Each color has four parts, alpha (A), red (R), green (G) and blue (B), and each part has 16 levels. Alpha 0 is fully transparent and F is fully solid.

- Drag the **A R G B** sliders, or
- type a four-digit code into **Value** (for example `F84C`), or
- use the **Picker**, which is rounded to the nearest color the save can store, or
- click a swatch under **Colors**, which lists the most-used colors in the current set.

### 5. Frame actions

- **Copy frame / Paste** – copy the selected frame, select another, and paste.
- **Clear** – empty the selected frame.
- **Flip ↔ / Flip ↕** – mirror the frame.
- **← ↑ ↓ →** – shift the picture one pixel; it wraps around the edges.

### 6. Import and export pictures

**Import image** accepts PNG, GIF, WebP, JPEG and BMP. What it fills depends on the picture's shape:

| Picture | Fills |
| --- | --- |
| Exactly 128 × 64 | All eight frames (mouse on the top row, cat below) |
| About four times as wide as tall, e.g. 128 × 32 | The four frames of the selected character |
| Anything else | The selected frame, shrunk to fit and centered |

A picture that is already the exact size is copied pixel for pixel. Colors are rounded to the 16 levels per channel the save can store.

**Export frames as PNG** saves all eight frames as one 128 × 64 sheet. You can edit that sheet in any pixel-art program and import it again.

### 7. Preview the animation

The **Animation preview** panel loops the four frames of each character. You can pause it, change the speed, and pick a backdrop. The preview speed belongs to this page; the game uses its own timing.

### 8. Export

1. Type a **File name** of up to 8 characters (letters, digits, `-` and `_`).
2. Press **Export .zip**.

The zip holds two files with that name: the `.VMS` save and its matching `.VMI`. Unzip it and copy the pair to your VMU with the transfer method you already use.

Every export:

- recalculates the save's checksum,
- writes the VMU file name `CHU_CHU_ANI`, and
- writes the creator text `SEGA ENTERPRIZES` into the save header.

### Other VMU saves

If you open a VMU data save that is not a Chu Chu Rocket! character set, the drawing tools are locked, but you can still export it. The export has a corrected checksum and keeps the save's own header text.

---

## Puzzle Pack Maker

A puzzle pack is up to 25 puzzle saves stored one after another in a single file. One puzzle save is 1,536 bytes (3 VMU blocks); a full pack of 25 is 38,400 bytes (75 blocks).

### 1. Add puzzle saves

Press **Choose VMS files**, or drop files anywhere on the page. You can add:

- single puzzle saves (1,536 bytes each), and
- existing packs, which are split back into their individual puzzles.

`.VMI` files are not needed and are skipped. Files that are the wrong size or are not puzzle saves are skipped too, with a message saying which.

When you add several files at once and each has a save number, they go in by that number.

### 2. Put them in order

Each filled slot shows a picture of the puzzle board, its title and the file it came from.

- **← / →** – move the puzzle one slot earlier or later.
- **Drag** the board picture onto another slot to move it there.
- **×** – remove the puzzle from the pack.
- **Sort by save number** – order every puzzle by its original save number.
- **Clear all** – empty the pack.

### 3. Fix a title (optional)

Type in the box under a board to change that puzzle's title. Titles can be up to 20 plain keyboard characters. A title you do not touch is left exactly as it was, including Japanese text.

### 4. Save

1. Set the **Pack file name** (it starts as `PuzzleP.VMS`).
2. Press **Save and Export VMU Files**.

Every slot in the saved pack is given:

- the internal name `CHU_CHU__D01` to `CHU_CHU__D25`, following the order on the page,
- the description `CHUCHU!/DOWNLOAD`,
- the slot tag used by the original pack, and
- a freshly calculated checksum, so saves that arrived with a wrong checksum come out fixed.

The board, arrows and icon of each puzzle are copied through unchanged. A slot marked "wrong checksum, fixed on save" is corrected automatically.

The pack maker saves the `.VMS` only. It does not create a `.VMI`.

---

## Notes

- Both tools read and write `.VMS` files. They do not open `.VMI` or `.DCI` files as saves.
- The Character Editor edits character sets only, and the Puzzle Pack Maker handles puzzle saves only.
- Keep a copy of your original saves before replacing them on a memory card.

## Trademarks

Chu Chu Rocket! and Dreamcast are trademarks of SEGA. This is an unofficial fan project and is not affiliated with or endorsed by SEGA.
