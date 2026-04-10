# D2R Hero Editor — Reimagined

A browser-based editor for modifying Diablo II: Resurrected character save files (`.d2s`) using data from the Reimagined mod.

This tool allows you to load a character, edit stats, skills, inventory, quests, and more, then export a modified save file.

---

## Requirements

- A Diablo II: Resurrected `.d2s` character file
- Internet connection (required to load Reimagined data files)

---

## Getting Started

### 1. Open the Editor
- Load the HTML file in a browser.
- The editor will automatically begin downloading required data files from the Reimagined repository.

### 2. Wait for Data to Load
- A loading screen will show progress as files are fetched.
- If critical files fail to load, the editor will not function.
- Once complete, the interface will switch to the upload screen.

### 3. Load Your Character
- Drag and drop your `.d2s` file into the upload area  
  **or**
- Click the upload area to browse and select your file

---

## Editing Features

Once a character is loaded, the editor interface becomes available.

### Character Overview
Displays:
- Character name
- Class
- Level
- Difficulty
- Status flags (hardcore, expansion, etc.)

---

### Tabs

The editor is divided into multiple tabs:

#### Character Stats
Modify:
- Strength, Dexterity, Vitality, Energy
- Health, Mana, Stamina
- Gold and experience

#### Skills
- Edit skill levels individually
- Includes both list view and skill tree layout

#### Inventory
- View and modify:
  - Inventory grid
  - Equipped items (paperdoll view)
- Click items to inspect details
- Insert or modify items via modal

#### Items
Supports:
- Item names resolved from game data
- Quality types (normal, magic, rare, unique, etc.)
- Socketed and stacked items

#### Quests
- Toggle quest completion states

#### Waypoints
- Enable/disable discovered waypoints

---

## Saving Changes

- Click **"Save .d2s"** to export your modified character
- The original file is not overwritten
- Always save to a new location as a backup

---

## Important Notes

- The editor depends on external data files hosted online
- If required files fail to load, editing is disabled
- Some non-critical files may fail without breaking functionality
- Changes are applied directly to a working copy of the save data in memory

---

## File Handling

- Input: `.d2s` character save file
- Output: Modified `.d2s` file

---

## Technical Overview

### Data Loading
- Fetches `.txt` data files from the Reimagined repository
- Parses TSV-formatted game data into usable structures
- Loads string tables for item names and UI text

### Parsing
- Reads binary `.d2s` structure
- Extracts:
  - Stats via bit-level decoding
  - Inventory and item data
  - Character metadata

### Editing
- Maintains a working byte array for modifications
- Tracks changes (dirty state)
- Updates UI dynamically based on edits

---

## Error Handling

- Critical file failures block the editor
- Non-critical file failures are logged but ignored
- Timeout protection prevents hanging requests

---

## Controls

- **Open .d2s** — Load a character file
- **Save .d2s** — Export modified file
- Status indicator shows:
  - Loading
  - Ready
  - Modified
  - Error states

---

## Credits

- Created by GildyBoye
