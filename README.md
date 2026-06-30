# Companion Perks Stay - (ESPless with TTW Support)

Keeps companion perks active permanently once you've recruited them, even after dismissal. No plugin (`.esp`/`.esm`) required. Works for both *Fallout: New Vegas* and *Tale of Two Wastelands* (TTW).

## Requirements

* [xNVSE](https://github.com/xNVSE/xNVSE) (v6.1.0 or newer)
* [JIP LN NVSE Plugin](https://www.nexusmods.com/newvegas/mods/58277) (v56.00 or newer)
* [JohnnyGuitar NVSE](https://www.nexusmods.com/newvegas/mods/66970) (v4.00 or newer)

### Optional
* [B42 Notify](https://www.nexusmods.com/newvegas/mods/80868) (for corner message popups)
* [Tale of Two Wastelands](https://taleoftwowastelands.com/) (required for Fallout 3 companion support)

---

## Installation

### Mod Manager (Recommended)
1. Install the ZIP archive using Mod Organizer 2 or Vortex.
2. Enable the mod. (No load order sorting is necessary as there is no plugin file).

### Manual Installation
Extract the contents of the archive directly into your Fallout New Vegas `Data` folder.

---

## INI Settings

You can configure options in `config/CompanionPerksStay.ini`:

```ini
[Settings]
; Show corner notifications when a perk is retained (1 = on, 0 = off)
bShowNotifications = 1

; Check interval in frames (300 frames is roughly 5 seconds at 60 FPS)
iCheckInterval = 300

[Testing]
; Force-hire and teleport all 28 companions to the player on load
bTestMode = 0
```

---

## Compatibility

* Fully compatible with **Tale of Two Wastelands (TTW)** and all official DLCs.
* Compatible with all companion command and overhaul mods (e.g., *JIP Companions Command & Control*).
* Completely safe to install or uninstall mid-playthrough.

---

## Credits

* [xNVSE Team](https://github.com/xNVSE/xNVSE)
* [jazzisparis](https://www.nexusmods.com/newvegas/mods/58277) (JIP LN NVSE)
* [carxt](https://www.nexusmods.com/newvegas/mods/66970) (JohnnyGuitar NVSE)
* [The TTW Team](https://taleoftwowastelands.com/) (Tale of Two Wastelands)
* [Xilandro](https://www.nexusmods.com/newvegas/mods/80868) (B42 Notify template support)
