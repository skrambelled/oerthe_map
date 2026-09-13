# OertheMap — a live-updating map plugin for Ancient Anguish

OertheMap is a MUSHclient plugin that shows a scrolling map panel of your
surroundings in Ancient Anguish (anguish.org), centered on your current
position.

## Requirements

- MUSHclient
- A custom Ancient Anguish prompt that includes your coordinates
  (the `|XCOORD|` and `|YCOORD|` prompt elements)
- The [`mush_windows`](../mush_windows) plugin, installed first (or
  alongside this one) — it provides the shared, draggable/resizable
  window chrome the map panel is drawn in. Without it, OertheMap still
  loads and tracks your position, but the map window itself won't
  appear; you'll get a clear note telling you to install it.

## Installation

1. In MUSHclient, open the world you use to connect to Ancient Anguish.
2. Go to **File → Plugins...**
3. Click **Add**, and select `mush_windows.xml` (from the `mush_windows`
   folder) if it isn't already installed for this world.
4. Click **Add** again, and select `OertheMap.xml` from wherever you
   saved this plugin's folder.
5. Click **Close**.

Keep `seed_data.lua` in the same folder as `OertheMap.xml` — the plugin
loads it automatically from its own directory. You don't need to do
anything else with it.

You'll know it loaded correctly if you see a message starting with
`[OertheMap]` in your output the moment the plugin is added.

Plugins are added per-world in MUSHclient. If you connect to Ancient
Anguish through more than one saved world file, repeat the install step
for each one.

## Map data

`seed_data.lua` is generated (never hand-edited) by `map_import_seed
<path>`, from a saved copy of either:

- a [skrambelled/aa-map](https://skrambelled.github.io/aa-map/html/map.html)
  `html/map.html` export — auto-detected, and the only source that
  carries ocean depth data (see the DEPTH button, below)
- the original https://anguish.org/gameplay/mapoerthe.html — the only
  source that carries named-location titles of its own

Re-importing from either preserves existing named-location titles at
any coordinate whose terrain hasn't changed since, so switching sources
(or re-pulling an updated copy of the same one) doesn't wipe titles
that are still accurate.

## Controls

- **Zoom**: +/- buttons, or scroll the mouse wheel over the map
  (`map_zoom_in` / `map_zoom_out` also work without a mouse)
- **Pan**: left-click and drag the map
- **SNAP**: re-centers the map on your current location as you move;
  panning turns it off automatically (`map_snap` also toggles it)
- **DEPTH**: colours "=" (sea) tiles by ocean depth instead of one flat
  colour — only does anything once depth data has been imported (see
  above); off by default