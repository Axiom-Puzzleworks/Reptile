# Reptile Map Designer — editor guide

The Reptile Map Designer (`Reptile.Editor.exe`, "Reptile Map Designer" in the Start Menu) is the tool the shipped levels were built with. This guide walks through building a level, checking it, playing it, recording a solution, and putting levels together into a pack you can share. Press **F1** in the editor for the built-in help and **Shift+F1** for a keyboard cheat sheet.

For what each object does in play, see [MANUAL.md](MANUAL.md) §4. The file formats are specified in [CONTRACTS.md](CONTRACTS.md) §2.

---

## 1. The window

- **Top:** menus (File, Edit, View, Play, Help) and the toolbar.
- **Left:** the object palette, with statistics underneath (object counts and the maximum score the level allows).
- **Centre:** the map. Below it are three tabs: **Problems**, **Notes**, and **Test-play and solution**.
- **Right:** the Properties panel for the level.
- **Status bar:** the cell under the pointer and what is in it, the zoom, and a problem summary.

**Navigating:** drag with the middle button to pan, scroll with the wheel, Ctrl+wheel to zoom around the pointer, or `Ctrl++` / `Ctrl+-` / `Ctrl+0`. **View ▸ Grid** (`Ctrl+G`) toggles the grid. The yellow-handled rectangle is the 8×8 area the player sees at once; drag it around to judge what is on screen together. The **Theme** box changes which pack's sprites the map is drawn with.

---

## 2. Building a level

### Starting

**File ▸ New** (`Ctrl+N`) creates a 32×32 level: a wall ring filled with earth, with the start in the top-left corner. **File ▸ Open** (`Ctrl+O`) opens a `.level.json`; Open recent keeps the last ten.

### The palette

Left-click an object to make it the **primary** (painted with the left button); right-click to make it the **secondary** (right button). Hotkeys:

| Key | Object | Shift+key | Object |
|---|---|---|---|
| 1 | Blank | Shift+1 | Skull |
| 2 | Earth | Shift+2 | Spirit |
| 3 | Wall | Shift+3 | Cage |
| 4 | Rock | Shift+4 | Transporter |
| 5 | Diamond | Shift+5 | Time capsule |
| 6 | Egg | Shift+6 | Crown |
| 7 | Monster | Shift+7 | Fungus |
| 8 | Key | Shift+8 | Time bomb |
| 9 | Safe | Shift+9 | Cracked egg |
| 0 | Player start | | |

Some objects are limited — one start, one crown, one time bomb, sixteen transporters — and the palette shows how many you have left (in red if you are over).

### Tools

| Tool | Key | Use |
|---|---|---|
| Pencil | B or P | Paint cells. Shift-click draws a straight line from the last point. |
| Line | L | Drag a straight line. |
| Rectangle | R | Drag a rectangle outline. |
| Filled rectangle | Shift+R | Drag a solid rectangle. |
| Fill | G | Flood-fill the connected area of the clicked object. |
| Pick | I | Left-click picks the primary, right-click the secondary. Alt-click does this with any tool. |
| Select | S or M | Drag a selection, then drag inside it to move it (hold Alt or Shift to copy). `Ctrl+C` / `Ctrl+X` / `Ctrl+V` copy as plain map text, so you can paste between levels or into a text file. `Del` clears to blank, `Ctrl+A` selects all, `Esc` drops the selection. |
| Link | T | Click a transporter, then its destination. Right-click a transporter to unlink it. |
| Note | N | Click a cell to add or edit a designer note (an empty note deletes it). Notes are never played. |

Also useful:

- **Mirror:** `H` and `V` flip the selection (or the whole map) horizontally or vertically, carrying links and notes. `Shift+H` copies the left half onto the right, `Shift+V` the top onto the bottom; other directions are in **Edit ▸ Mirror copy**.
- **Scatter** (`Ctrl+Shift+R`): replace a percentage of one object with another across the selection or map, e.g. sprinkle rocks through earth. The same seed always gives the same result.
- **Undo / redo:** `Ctrl+Z`, and `Ctrl+Y` or `Ctrl+Shift+Z`. Every drag, tool action and property change is one step.
- Placing a start removes the old one. Painting over a transporter removes its link.

**Walls** are a single object: the editor (and the game) draws each one joined to its neighbours, so you never pick wall pieces by hand. Turn **Auto-tile walls** off in the View menu to see plain blocks. Rounded walls that rocks roll off (`curvedWalls` in the file) have no editing tool yet; they are kept when you load and save a level, and the validator checks them.

### Level properties (right panel)

| Group | Property | Notes |
|---|---|---|
| Level | Id | Short identifier, e.g. `caverns-03`; must be usable as a file name. |
| | Name, Author | Shown to players. |
| | Password | What players type to jump to this level. Must be unique in the pack. |
| | Hint | One line, shown to the player after the level is completed. |
| | Size | 16–64 each way. Shrinking crops the right and bottom. |
| | Map visible | Whether the player may open the map view. |
| Palette | Colours 0–3 | Four of the eight BBC colours. 0 is the background, 1 the accent (the lizard's trousers). "Theme default" restores the theme's palette. |
| Rules | Completion | **diamonds**; **diamonds+crown+bomb** (take everything, then walk into the bomb); or **everything** (diamonds, crowns, earth, monsters and transporters, then the bomb if any). |
| | Time limit | Timer units; one is lost every tick (6000 is the classic default). |
| | Par time | Optional target, in ticks. |
| | Fungus rate | 0 = fungus does not spread; 1–10 spreads every (11 − rate) × 50 ticks. |
| | Monster speed | 1 = normal, 2 = half speed. |
| | Seed | Drives fungus growth and monster choices; **Random** picks a new one. |
| Scoring | Diamond, Earth, Monster, Crown | Points for each. |
| Rule flags | deathResetsLevel, crackedEggSolid, skullBumpLethal, monsterAxis | Override the pack's setting for this level only; "(pack default)" leaves it to the pack. |

The panel also lists the transporter links and notes, each with a ✕ to remove it.

### Saving

`Ctrl+S` saves (adding `.level.json` if you leave it off); `Ctrl+Shift+S` saves as. The editor autosaves every minute to a separate place, and offers to recover an autosave that is newer than the file you open (**File ▸ Recover autosave…**). `Ctrl+Shift+E` exports a PNG thumbnail of the map.

---

## 3. Validation

The level is checked continuously (a moment after every edit, on open and before every test-play). Problems appear in the **Problems** tab, errors first; double-click one to jump to its cell. Problem cells are outlined on the map in red (error) or orange (warning), and the status bar gives the count.

**Errors** stop a level being playable or shippable, for example:

- no start, or more than one;
- no diamonds; safes but no key;
- a transporter with no link, or a link to a cell that is not empty;
- too many monsters and cracked eggs for the four monster slots;
- a time bomb on a level whose completion rule does not use one, or a bomb rule with no bomb;
- missing id or name, an id that is not a valid file name;
- a recorded solution that no longer completes the level.

**Warnings** point at likely design mistakes, for example: a rock directly above the start, diamonds or other things the player cannot reach, an area sealed off from the start, spirits with no cage, a monster that cannot be killed on an "everything" level, no par time.

---

## 4. Test-play

**Play ▸ Test-play** (`F5`) launches the real game on the level as it is now, saved or not. The editor finds the game beside itself (as installed) or uses the path set in **Edit ▸ Settings…**. If the game is still open from the last test, `F5` reuses it.

When you finish, die or quit, the result appears in the **Test-play and solution** tab: when, how (game or quick play), from where, the outcome and the time in ticks.

**Debug start:** Ctrl+click a cell to start test-plays there instead of at the level's start (a magenta "D"); Ctrl+click it again, or **Play ▸ Clear debug start**, to remove it. It is not saved in the level and runs from it cannot become the solution.

**Quick play** (`Ctrl+F5`) runs the level inside the editor without the game: arrows or WASD to move, `Space` pause, `.` single-step a tick, `R` restart, `Esc` close. Its speed is set in **Edit ▸ Settings…**.

---

## 5. Recording a solution

Every shipped level has a recorded solution, and a pack validator checks that each one still completes its level. That guarantees no level is impossible and catches a level broken by a later edit.

1. Play the level through with Quick play (`Ctrl+F5`), or with test-play (`F5`).
2. When you complete it, the editor offers to save the run as the solution (Quick play asks when there is no solution yet, the old one fails, or the new run is shorter; a completed test-play row has a **Save as solution** button).
3. The run is replayed to make sure it completes, then kept with the level. **Save the level** (`Ctrl+S`) to write it.

The solution is stored beside the level as `<name>.replay.json` (for `03-spoil-heap.level.json` it is `03-spoil-heap.replay.json`). It holds one input per game tick, so the same file replays identically every time. **Play ▸ Verify solution** re-runs it; **Play ▸ Delete solution** removes it. If you edit the level so the solution no longer works, a *SolutionBroken* error appears until you record a new one.

---

## 6. Packs and sharing

A pack is a folder holding `pack.json`, the level files in play order, and optionally each level's solution and a thumbnail. A `.reptilepack` file is that folder zipped up for sharing.

Open the **pack manager** with `Ctrl+Shift+P`. It opens on the current level's pack if there is one.

1. **New pack…** — choose an empty folder and give the pack a name. The theme and music follow the editor's current theme.
2. **Add level…** — adds a level (copying it and its solution into the folder if needed). Reorder with the arrow buttons or `Alt+Up` / `Alt+Down`; **Remove from list** leaves the file on disk. Double-click a level to open it in the editor.
3. Fill in the pack details: name, description, theme, music, lives, unlock (**sequential**: each level opens the next; **all**: everything open), and the pack-wide rule flags.
4. **Validate all** (`F7`) checks every level, every solution, duplicate ids and passwords, and missing or extra files. Fix the errors; warnings are your call.
5. **Save** (`Ctrl+S`) writes `pack.json`.

To play your pack in the game, click **Install to Documents…**: the pack is copied to `Documents\Reptile\Packs\<pack id>`, where the game lists it.

To share it, click **Export .reptilepack…** (tick **Include thumbnails** for previews in the game's pack browser) and send the file. Whoever receives it can:

- use **Install .reptilepack…** in the pack manager to put it straight into `Documents\Reptile\Packs`;
- or use **Import .reptilepack…** to unpack it into a folder of their choice for editing.

Importing never runs anything from the archive: only `pack.json`, the levels, solutions and thumbnails are read, and anything else in the zip is ignored.

---

## 7. reptile-tools (command line)

`reptile-tools.exe` is installed beside the editor for batch work:

| Command | What it does |
|---|---|
| `reptile-tools validate <pack folder> [--require-replays]` | Checks `pack.json` and every level, and plays every solution. Exit code 1 on any failure. |
| `reptile-tools stats <pack folder>` | Per level: object counts, maximum score, par time and the solution's length. |
| `reptile-tools render-map <level.json> <out.png> [--scale n] [--theme name]` | Draws the map view of a level to a PNG. |
| `reptile-tools similarity <pack folder>...` | Flags levels that look too much alike. |
| `reptile-tools play --ascii <level.json> [--replay <file>]` | Plays a level in the console, or checks a replay (exit code 0 = completed). |

---

## 8. Settings and files

**Edit ▸ Settings…** sets the game executable and extra arguments for test-play, the content folder, the theme, the autosave interval and the Quick play speed. They are stored in `%APPDATA%\Reptile\Editor\settings.json`; autosaves live in `%LOCALAPPDATA%\Reptile\Editor\Autosave`.
