# D2R Hero Editor — Reimagined

Browser-based editor for Diablo II: Resurrected `.d2s` save files using Reimagined mod data.

Maintained by Gildyboye, not the Reimagined team. 
Unofficial.

Reimagined Mod Links: https://www.nexusmods.com/diablo2resurrected/mods/503 or https://github.com/D2R-Reimagined/d2r-reimagined-mod

---

## Overview

This tool loads a `.d2s` save file, parses its binary structure, and exposes editable fields through a tabbed interface.  
All edits are applied to an in-memory copy and can be written back to disk as a new file.

The editor relies on external data from the D2R Reimagined repository (item data, strings, templates, etc.), with automatic fallback to bundled local data if remote fetch fails.

---

## Features

### Character Editing
- Name, class, level, and core stats
- Difficulty and progression flags
- Hardcore / Expansion / death flags
- Direct stat input with validation

### Skills
- Full skill tree layout per class
- Editable skill levels with limits enforced
- Unspent skill points control
- Reads and writes directly to save data

### Inventory & Equipment
- Grid-based inventory and stash system
- Paperdoll equipment slots
- Item rarity coloring and metadata display
- Tooltip inspection with modifiers and flags
- Item insertion via categorized modal (weapons, armor, misc, uniques, sets, runewords)

### Stash & Shared Stash
- Multi-tab stash support
- Specialty tab splitting (gems, runes, materials)
- Item search across tabs
- Grid rendering consistent with in-game layout

### Vault System
- Load and save `.d2i` vault files
- Search items across all pages
- Move items between sources and vault
- Multi-page and quad-view layouts

### Grail Tracking
- Visual item completion grid
- Displays found vs missing items
- Page-based navigation

### Quests
- Per-act quest tracking
- Complete / clear all controls
- Difficulty-specific state editing
- Reward handling tied to completion flags

### Waypoints
- Toggle waypoint unlocks per difficulty
- Organized by act

### Mercenary
- View and edit mercenary data
- Equipment and stats where applicable

---

## Authentication

This tool uses Supabase for authentication, with Discord as the OAuth provider.

### How it works
- Users sign in via Discord OAuth
- Supabase manages authentication, sessions, and tokens
- A valid session may be required for features that rely on remote data or persistence

### Notes
- No standalone account system is implemented
- Discord is used only as an identity provider
- Authentication is handled entirely through Supabase

---

## File Handling

### Input
- Accepts `.d2s` character save files
- Drag-and-drop or file picker supported

### Output
- Writes modified data to a new file
- Original file is not overwritten by default

### Additional Files
- `.d2i` vault files (optional)
- Shared stash and grail data handled separately

---

## Data Loading

On startup, the editor performs:

1. Fetch base game data (items, stats, templates)
2. Fetch string tables for localization
3. Load editor-specific JSON data
4. Fallback to local copies if remote fetch fails

Failure to load required data prevents the editor from initializing.

---

## Localization

- Supports multiple languages via string tables
- Dynamically updates UI labels and item names
- Cleans raw strings (removes formatting and color codes)

---

## UI Structure

### Views
- Loading View – Fetches required data
- Error View – Displays critical load failures
- Upload View – File selection interface
- Editor View – Main editing interface

### Tabs
- Character
- Skills
- Inventory
- Stash
- Shared Stash
- Quests
- Waypoints
- Mercenary
- Grail
- Vault

Some tabs (inventory-related) require confirmation due to potential data corruption risks.

---

## Editing Model

- Save file is parsed into structured data (`parsedChar`)
- Changes are applied to a working byte array
- Dirty state tracks unsaved changes
- Undo snapshot supports single-level rollback

---

## Auto-Save

- Optional auto-save using the File System Access API
- Writes are debounced (~2.5 seconds after changes)
- Tracks file modification timestamps
- Detects external file changes
- Disables after repeated write failures

---

## Item Editing

### Capabilities
- Insert new items via selection modal
- Adjust item level (ilvl) within valid bounds
- Handle special item types (runes, misc, runewords)
- Supports multi-slot item placement

### Limitations
- Some item operations are unstable
- Inventory editing may produce invalid states if misused
- Warnings are shown before enabling editing

---

## Search

- Search across inventory, stash, and vault
- Supports:
  - Item name
  - Type code
- Results highlight and navigate to item location

---

## Visual Systems

- Canvas-based item rendering
- Grid-based layout for inventory and stash
- Background visual effects (pixel-based animation)

---

## Dependencies

### Remote Data Sources
- D2R Reimagined repository (GitHub)
- Localization string files
- Editor-specific JSON datasets

### Browser Requirements
- Modern Chromium-based browser recommended
- File System Access API required for auto-save

---

## Safety Notes

- Always back up original save files before editing
- Inventory modifications can corrupt saves if used incorrectly
- Not all item structures are fully validated

---

## Credits

- Developed by GildyBoye
- Uses data from the D2R Reimagined project

---
