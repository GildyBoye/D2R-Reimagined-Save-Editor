# D2R Hero Editor — Reimagined

Browser-based editor for Diablo II: Resurrected `.d2s` save files using Reimagined mod data.
Reimagined Mod Links: https://www.nexusmods.com/diablo2resurrected/mods/503 or https://github.com/D2R-Reimagined/d2r-reimagined-mod


---

## Overview

This tool loads a character save file, parses its data, and provides an interface to edit stats, skills, inventory, quests, and other character properties. Changes can be exported as a new `.d2s` file.

The editor depends on external Reimagined data files loaded at runtime.

---

## Usage

### 1. Load Base Data
- Open the HTML file in a browser
- The editor will automatically download required data files
- Wait until loading completes

### 2. Load Character
- Drag and drop a `.d2s` file  
  or  
- Click to browse and select a file

### 3. Edit Character
Use the tabbed interface to modify:

- **Stats**: Attributes, health, mana, gold, experience
- **Skills**: Individual skill levels or tree layout
- **Inventory**: Items, equipment, stash
- **Quests**: Completion flags
- **Waypoints**: Activated locations

### 4. Save
- Click **Save .d2s**
- A new file is generated; original is unchanged

---

## Features

- Full character stat editing
- Skill editing (list and grid views)
- Inventory and equipment editor
- Item inspection and insertion
- Quest and waypoint toggles
- New character creation
- Visual character preview and layout

---

## Requirements

- Modern web browser
- Internet connection (for data file loading)
- Valid `.d2s` save file

---

## Behavior

- All edits are performed in memory
- Changes are tracked until saved
- Save operation exports a modified file without overwriting the original
- Critical data load failures prevent editor use
- Non-critical failures may be ignored

---

## Notes

- Tool relies on external Reimagined data sources
- Item names and properties are resolved from loaded data
- Inventory uses grid-based layout matching in-game structure
- Editing invalid or unsupported values may result in broken saves

---

## Controls

- Open file: load `.d2s`
- Save file: export changes
- Status indicator shows loading, ready, modified, or error states

---

## Credits

- Author: GildyBoye
