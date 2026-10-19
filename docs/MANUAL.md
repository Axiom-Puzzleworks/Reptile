# Reptile — player manual

You are a lizard in a maze of earth, rock and stone. Each screen hides a number of diamonds. Dig your way to every one of them without being crushed, caught or running out of time, and the screen is complete. Most screens are puzzles: the order you take things in matters, and a careless move can trap a diamond for good.

This manual covers playing the game. For building your own levels see [EDITOR-GUIDE.md](EDITOR-GUIDE.md).

---

## 1. Starting a game

1. Start **Reptile** from the Start Menu (or run `Reptile.exe`).
2. On the title screen choose **Play**.
3. Choose a pack. Each row shows how many screens you have completed and how many are open. Packs you installed yourself are marked `*`.
4. Choose a screen. A new pack opens at screen A; each screen you complete opens the next. Press **RETURN** to play.

The title screen also has **High scores**, **Settings**, **Credits** and **Quit**.

---

## 2. Controls

### Moving

| | Keyboard | Gamepad |
|---|---|---|
| Move | Arrow keys, or W A S D | D-pad or left stick |
| Move (BBC-style) | Z left, X right, `;` up, `/` down | |

Any of the four control schemes can be switched off in Settings (at least one stays on). If you hold two directions at once, up or down wins. A tap made while the lizard is between cells is remembered and carried out at the next cell, so quick taps are never lost.

### During play

| Action | Keyboard | Gamepad |
|---|---|---|
| Pause and show the status screen | RETURN or ESCAPE | Start |
| Fullscreen on/off (saved) | F11 or Alt+RETURN | |
| Window larger / smaller (saved, windowed only) | `+` / `-` | |
| Authentic / even pace (saved) | F5 | |

### On the status screen

| Action | Keyboard | Gamepad |
|---|---|---|
| Play / resume | SPACE | A or Start |
| Map of the whole screen | M | X |
| Sound on / off | S / Q | |
| Music on / off | D / W | |
| Give up this life (press twice) | ESCAPE | Back |
| Restart the screen from scratch (press twice) | R | |
| End the game (press twice) | BACKSPACE | Y |

Giving up and restarting both cost a life. The map shows the whole screen with the monsters on it and your lizard blinking; press any key to return.

### Menus

Arrow keys, d-pad or stick to move (holding repeats); **RETURN**, **SPACE** or pad **A** to choose; **ESCAPE** or pad **B** to go back.

When typing a password or a name, type normally and use BACKSPACE to delete. On a gamepad, Up and Down cycle the last character through A–Z, 0–9 and space, Right adds a character and Left deletes one. Finish with RETURN or pad A.

---

## 3. The status screen

There is nothing on screen while you play except the maze itself: everything you need to know is on the status screen. It appears at the start of every screen, whenever you pause, and after every death. It shows:

- the pack name and a heading: the screen letter and name at the start, **Paused**, or what killed you;
- **Score** and **Hi-score**;
- **Time**: timer units left (see §5);
- **Lives** left, counting the one you are on;
- **Diamonds** still to collect (it says **Plenty!** while ten or more remain);
- the **Screen** letter, and whether the map is available;
- the sound, music and pace settings with their keys.

Press SPACE to play on.

---

## 4. Objects and their rules

**Earth.** Walk into it to dig it away. Worth 1 point.

**Wall.** Solid. Some walls have rounded corners: a rock that lands on one rolls off it to the left, to the right, or either way, depending on how it is shaped. The edge of the map counts as wall.

**Rock.** Falls whenever the space beneath it is empty, one cell at a time, and a falling rock kills whatever it lands on — you or a monster. A rock resting on top of something rounded (another rock, an egg, a diamond, a skull or a rounded wall) rolls off: to the left if there is room, otherwise to the right.

- You can stand directly beneath a resting rock: it stays put while you are there.
- Stepping sideways out from under it is safe. Stepping *down* out from under it is not: it follows you.
- You can **push** a rock sideways, one rock at a time, if the space beyond it is empty. You cannot push up or down. A rock pushed over a gap drops straight into it.

**Diamond.** Collect them all to complete a screen. Worth 50 points. Rocks roll off diamonds.

**Key and safe.** Safes are solid and count among the diamonds you need. Pick up the key and every safe on the screen turns into a diamond.

**Egg.** Falls, rolls and can be pushed exactly like a rock. If it falls at least one cell, it cracks when it lands. A cracked egg hatches into a monster after a short while — and walking into a hatching egg is fatal. There can be at most four monsters at once; an egg that cracks when all four are about is lost.

**Monster.** Chases you through empty space; it cannot dig. Touching it is fatal. Drop a rock or egg on it to kill it.

**Skull.** Solid and rounded. Walking into a skull kills you.

**Spirit.** Drifts along the walls of empty passages, always keeping a wall on its left. It kills you if it touches you. Lure a spirit into a **cage** and the cage becomes a diamond — which you then also have to collect.

**Transporter.** Walk into it and you are carried to another part of the screen. Each transporter works once and then disappears. It does nothing if its destination is blocked.

**Time capsule.** Refills the timer to the screen's full time.

**Crown.** A prize worth points on some screens. On screens that end with a time bomb you must take the crown before the bomb will work.

**Time bomb.** On a screen with a bomb, collecting every diamond is not enough: take every diamond and the crown, then walk into the bomb. Until then it is just a solid block.

**Fungus.** Solid and deadly to touch. It slowly grows into the empty space around it, and if it grows into you, you die. A monster boxed in by fungus dies.

### Time

Every screen has a timer, shown on the status screen. It runs down whether you move or not, a little faster when you stand still. When it runs out you lose a life.

### Lives and deaths

Each pack gives you three lives. Every death costs one, including giving up (ESCAPE) and restarting (R). In the shipped packs a death puts the screen back exactly as it was when you started it, and your score back to what it was then. When the last life is gone the game is over.

### Scoring

Diamonds are worth 50, each clump of earth 1, and a crown whatever the screen says (250 in Sunken Temple). If your final score makes the pack's top ten you are asked for your name.

---

## 5. Packs and passwords

Reptile comes with four packs, each with its own look, music and set of objects:

| Pack | Screens | What you will meet |
|---|---|---|
| **Caverns** | 12 | Rocks, diamonds, keys and safes, eggs and monsters. The later screens are timed. |
| **Glacier** | 10 | Skulls, transporters, spirits and cages, then the Caverns objects. |
| **Sunken Temple** | 10 | Crowns, time bombs and time capsules on every screen, with tight timers. |
| **Foundry** | 10 | Creeping fungus, then everything else. |

Screens open one at a time: complete a screen and the next one opens. Your progress is saved automatically.

**Passwords.** Every screen has a password. You see it in the screen list once the screen is open, and the next screen's password is shown when you complete one. To jump ahead, open the screen list for a pack and press **P** (pad **Y**), then type the password. Capitals, spaces and punctuation do not matter. A correct password opens that screen and every screen before it. Passwords are the same for everyone, so you can share them with friends.

In the screen list you can also see your best score and time for each completed screen, press **H** (pad **X**) for the pack's high scores, and after completing a screen read its hint.

**More packs.** Packs made by other players come as `.reptilepack` files. To install one, start the Reptile Map Designer, open the pack manager (`Ctrl+Shift+P`) and choose **Install .reptilepack…**; it is copied to `Documents\Reptile\Packs`, and the game lists it with a `*`. You can also unzip a pack folder there by hand: any folder in `Documents\Reptile\Packs` that contains a `pack.json` is a pack.

---

## 6. Settings

Choose **Settings** on the title screen. Left and Right change a value; changes take effect at once and are saved when you leave the screen.

| Setting | Choices | Default |
|---|---|---|
| Window scale | Fit (90 % of the screen) or 1×–8× | Fit |
| Fullscreen | Off / On (borderless) | Off |
| Presentation | **Authentic**: the view jumps a cell at a time, like the original. **Enhanced**: the view glides smoothly. The game itself is identical. | Authentic |
| Scanlines | On / Off (Enhanced only) | On |
| Pace | **Authentic**: the game runs a little faster while you stand still, as the original did. **Even**: always the same speed. | Authentic |
| Sound, Sound volume | On / Off, 0–10 | On, 8 |
| Music, Music volume | On / Off, 0–10 | On, 6 |
| Arrow keys, W A S D, Z X : /, Gamepad | On / Off each | All on |

Your settings, progress, best times and high scores are kept in `%APPDATA%\Reptile\profile.json`. Uninstalling Reptile leaves this file (and your installed packs in `Documents\Reptile\Packs`) in place; delete them by hand to start completely fresh. If the profile is ever damaged, Reptile renames it `profile.json.bad` and starts with defaults.

### Command-line options

Advanced users can start `Reptile.exe` with:

| Option | Effect |
|---|---|
| `--fullscreen` | Start in fullscreen. |
| `--scale <1-8>` | Start at this window scale. |
| `--mute` | Start with sound and music off (not saved). |
| `--enhanced` | Use Enhanced presentation for this run. |
| `--even-pace` | Use even pace for this run. |
| `--profile <file>` | Use a different profile file, e.g. for a second player. |
| `--pack <folder>` | Play the pack in this folder directly. |
| `--level <file.level.json>` | Play a single level file (four lives; a death resumes the level; no progress is saved). |
