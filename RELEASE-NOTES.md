# Release notes

## 1.0.0

First public release.

**Game**
- Four themed packs: Caverns (12 screens), Glacier, Sunken Temple and Foundry (10 each). Every screen has a recorded solution and was blind play-tested twice and retuned.
- Simulation rules reconstructed from the 1985 originals: quarter-cell movement, one-cell-per-tick rock falls, left-first rolling, the shuffle, random-axis monster chase, safes counting as diamonds, resume-after-death as a per-pack option.
- Authentic presentation: four-colour palettes, the eight-by-eight-cell play window with the player centred, status screen with map view, chiptune effects and a music loop per pack. An enhanced mode adds smooth scrolling and optional scanlines.
- Title, pack browser, level select with passwords, settings, high scores per pack, keyboard and gamepad.

**Map Designer**
- Paint tools, wall auto-tiling, transporter linking, properties panel, live validation and statistics, unlimited undo.
- Test-play in the game from any cell, record and verify solutions.
- Pack manager, map thumbnails, `.reptilepack` export and import, installed packs in `Documents\Reptile\Packs`.

**Known limitations**
- Downloads are not code-signed; SmartScreen may prompt on first run.
- Double-clicking a `.reptilepack` opens the designer but does not yet import it; use the pack manager's Install button.
- Installer tested on the development machine only, not yet on a clean Windows installation.
