# Drydock (beta)

A free, browser-based ship editor for **Cosmoteer: Starship Architect & Commander**. Open a ship `.png`, inspect it, rebuild it, or start a brand-new hull from any picture, then save it straight back into a file the game can load. Use the online link or save the .html and use offline!

**[Open Drydock →](https://viperg.github.io/Drydock/)**

Nothing to install, and nothing is uploaded: Drydock runs entirely in your browser, and your ship files never leave your computer.

![Editing a ship in Drydock: mirrored placement, thruster exhaust zones, overclocked reactors and live stats](screenshot-editor.png)

## What it does

**View any ship**
- Open a ship `.png` by dragging it in or using **Open ship…**
- Interior and exterior views, with color-coded modules, doors, heat-pipe networks and slanted armor drawn at their real angles
- Hover any module or door for details
- Stats: part count, cost, crew needed and capacity, footprint, mass and overclocked modules
- A collapsible **Ship info** card over the view: cost, mass, recommended crew vs. beds, estimated max speed, DPS, and heat made vs. cooled
- A **Recent blocks** panel with block previews for quick reuse, docked on the right or along the bottom

**Edit it**
- Searchable module list; click a module, then click to place it
- Move, rotate and delete modules; copy and paste them
- Multi-select: Shift+drag a box or Shift+click parts, then move, delete or copy/paste the whole group (Ctrl+A selects everything)
- Add and remove doors, limited to the spots each module allows
- A ship check that warns about a missing control room, disconnected pieces, blocked thrusters or weapons, invalid doors, and overclocked ships that make more heat than their radiators remove
- Placing a module on corridor, structure or armor replaces it; modules you remove leave corridor behind
- Mirror mode: left ↔ right, top ↔ bottom, or either diagonal
- Red no-build zones for thruster exhaust, weapon firing lanes and radiators, enforced as you build
- Shield arcs: see each shield's coverage and range, including overclocked Expanded and Hardened modes
- Weapon arcs: see which directions each turret can aim, short or out to its full range
- Set a module's overclock on or off, and a small shield's overclock mode (Expanded or Hardened)
- Ion prisms: placed only on structure (deleting one leaves structure), drawn pointing at their target, and aimable at another prism (to build chains) or at any spot on the ship; ion emitters can be aimed at a prism too
- Set the ship's front, including the four diagonal directions
- Undo and redo
- Build-area border for vanilla (120 × 120), Larger Ships (200 × 200) or Huge Ships (1000 × 1000)

**Build a hull from a picture**

- **New from image…** turns any favorite sci-fi ship silhouette into a hull: an armor shell of the thickness you choose, filled with corridor
- Scale it to any length up to your build-area limit
- Rotate in 90° or 45° steps (45° for diagonal ships)
- Works best with a transparent PNG, or a dark ship on a light background (tick **Invert** for light-on-dark)

## Import and export

- **Import ▾** (next to Open ship): a ship `.png` file, a link to a `.ship.png` or `.json` file, a JSON file, or pasted JSON.
- **Save .json** and **Copy JSON** (next to Save as .ship.png) export the ship as JSON.
- The JSON uses the same decoded layout as other Cosmoteer tools (`Parts` with `ID`, `Location`, `Rotation`, `FlipX`, plus `Doors`, `Name`, `FlightDirection` and the rest), so it works with them. Drydock adds a packed `_drydock` copy so a JSON round trip loses nothing; other tools can ignore it.
- You can edit `Parts`, `Doors`, `Name` and `FlightDirection` by hand and import the result.
- Importing from a link only works if the site allows other pages to download from it (GitHub raw links do).

## Getting your ship into the game

1. Click **Save as .ship.png**. Drydock always saves a new file and never changes the one you opened.
2. Put the file in your Saved Ships folder:
   `%userprofile%\Saved Games\Cosmoteer\<your Steam ID>\Saved Ships`
3. Keep the `.ship.png` ending. The image holds the ship data, so don't resize, crop or re-save it in an image editor.

Keep a backup of any ship before replacing it.

## Use it offline

Drydock is a single `index.html` file written in plain HTML, CSS and JavaScript, with no frameworks, libraries or build step. That means you can keep your own copy:

1. Download `index.html` from this repository (or save the page from your browser).
2. Double-click it to open it in any modern browser.

That's a complete offline ship editor. It works without an internet connection; the only thing it fetches online is its two fonts, and it falls back to your system fonts when they aren't available. Everything else, including the part data and the ship-file reader and writer, is built into the file.

## Keyboard shortcuts

| Key | Action |
| --- | --- |
| **R** | Rotate the module you're placing or the selected one |
| **Delete** / **Backspace** | Remove the selected module or door |
| **O** | Toggle overclock on the selected module |
| **Shift**+drag / **Shift**+click | Select several parts |
| **Ctrl+A** | Select every part |
| **Ctrl+C** / **Ctrl+V** | Copy the selected module or group / place copies of it |
| **?** | Show all shortcuts |
| **Esc** | Stop placing, or deselect |
| **Ctrl+Z** / **Ctrl+Y** | Undo / redo |
| Scroll / drag | Zoom / pan (pinch with two fingers on touch screens) |

On touchscreens, the **Rotate** and **Delete** buttons in the Edit panel do the same job.

## Known limits (beta)

- The thermal canister missile factory's price (18,000) is worked out from its materials; other factories cost a few percent more in game, so it may be slightly low.
- Recommended crew uses the game's own formula (required crew plus crew to carry power and ammo) for most parts; a few (deck cannon, large laser, missiles, railguns, factories, pumps, boost thruster, tractor beam) fall back to their minimum crew. Crew roles and priorities on loaded ships are kept but can't be edited.
- Heat counts overclocked parts at full load against radiators (1,100/s each); lasers, chainguns, railguns, factories and power storage aren't counted yet, and heat-pipe connections aren't checked.
- Max speed is an estimate from forward thrust (including engine rooms and overclocked thrusters), mass and the game's drag.
- DPS (without overclock) counts lasers, cannons, disruptors, ion beams (with prism networks and their per-beam falloff, so 2:1 is most efficient), chainguns at full spin, flak and railgun launchers (without accelerators); missiles and the resonance lance aren't counted yet.
- The thermal safety setting is kept as saved but can't be changed yet.
- Very large hulls (hundreds of thousands of parts) can be slow.

Found a bug, or a ship that doesn't load the way it should? Please [open an issue](../../issues) and attach the `.ship.png` if you can.

## Credits

Drydock builds on the work of others in the Cosmoteer community:

- **Save-format research:** GameDungeon's `cosmoteer_save_tools`, as used in [lunastrod/cosmoteer-com](https://github.com/lunastrod/cosmoteer-com) and [Helicophel/cosmoteer-ship-to-wikitext](https://github.com/Helicophel/cosmoteer-ship-to-wikitext)
- **Part sizes, costs and outlines:** the part table from [Helicophel/cosmoteer-ship-to-wikitext](https://github.com/Helicophel/cosmoteer-ship-to-wikitext) (MIT License, © franklin050187)
- **Speed model hints, engine-room thrust and some weapon DPS values:** [ContestMath/cosmo-shipbuilder](https://github.com/ContestMath/cosmo-shipbuilder) (MIT License)
- **Heat-era part geometry:** the vanilla part export from [0neye/Voidwright](https://github.com/0neye/Voidwright) (Apache License 2.0)
- **No-build zones, shield and weapon arcs, and overclock data** are derived from Cosmoteer's own part rules files, via the [Rojamahorse/CosmoteerUpdates](https://github.com/Rojamahorse/CosmoteerUpdates) mirror

Drydock is an unofficial fan project and is not affiliated with or endorsed by Walternate Realities. Cosmoteer is © Walternate Realities.
