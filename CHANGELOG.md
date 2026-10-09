# Changelog

## 1.0.0 — first standalone release (2026-10-09)

- Officially versioned the standalone **N Classic Battlegrounds** addon for WotLK 3.3.5a.
- Includes the confirmed Battlegrounds tab hiding fix for Vanilla/TBC, while keeping the Honor interface and Battlemaster queue controls.
- Includes progression-dependent Arena panel visibility (Vanilla hidden; TBC stage 8+) and Wintergrasp visibility (WotLK stage 13+).
- Includes the final `NClassicBattlegrounds/` folder structure matching the `.toc` file. Retains `/ncbg` commands.
- Installation and baseline behaviour were reported working by the user.
- **Verification note:** expansion transitions and all Battlemaster/Wintergrasp combinations have not been individually verified in-game. Server-side Battlemaster-only queue enforcement is separate, off by default, and still needs a rebuild/test.
- No character/database/DBC/server modification is required to install or update this client addon.


All changes to the **client addon** belong in this repository. Server-only Battlemaster queue enforcement is maintained separately in [Mod-Naxxramas-Core](https://github.com/CosmicCuddle/Mod-Naxxramas-Core).

## Installation packaging correction — invisible addon folder

- Fixed repository layout: the distributable `NClassicBattlegrounds.lua` and `NClassicBattlegrounds.toc` now live inside an install-ready `NClassicBattlegrounds/` folder.
- GitHub repository and ZIP name include the hyphen (`N-ClassicBattlegrounds`), but the WoW addon folder must **not** contain the hyphen, matching its `.toc` file exactly.
- No Lua functionality or progression rules changed during this packaging fix.

## 0.2.1-beta — shorter addon name (not yet tested in game)

- Renamed addon folder, TOC, Lua file, in-game title and internal ADDON_LOADED identifier from `NaxxramasClassicBattlegrounds` to `NClassicBattlegrounds`.
- Shortened chat prefix to `N Classic BG`; existing `/ncbg` commands remain unchanged.
- Per-character settings now use `NClassicBGQueueSettings` (new name defaults to enabled; prior preference does not auto-migrate).
- Kept all stage 8/13 progression visuals identical and left server-side queue enforcement in Mod-Naxxramas-Core.
- Back up then **remove the old addon folder** before installing the new one; never load both copies at once.

## 0.2.0-beta — in-game testing required

- Added progression-aware Vanilla Arena UI: hide Arena points, 2v2/3v3/5v5 team panels and related controls until **TBC entry (stage 8)**.
- Hide the Wintergrasp timer during Vanilla and TBC; restore at **WotLK entry (stage 13)**.
- Continue to hide the **Battlegrounds tab** in the ordinary PvP window until stage 13, while preserving the Battlemaster NPC's separate queue interface.
- Kept the working tab-only hide; no overlapping on-screen messages and no changes to the actual Join Battle controls.
- Added standalone GitHub repository, installation instructions, testing checklist and rollback guidance.
- Marked as beta: Arena and Wintergrasp adjustments still require in-game testing.

## 0.1.0 — initial interface prototype

- Initial expansion-aware client PvP restrictions for Individual Progression.
- Fixed the first implementation to hide the **Battlegrounds tab**, not the Join Battle buttons.
- Corrected the overlapping unlock text.
- Vanilla/TBC tab hiding and the corrected layout were confirmed in game.

## Compatibility

- Client: Wrath of the Lich King 3.3.5a (`Interface: 30300`).
- Progression: modern Individual Progression hidden-quest milestones.
- Real queue enforcement is **not** implemented by this addon.
