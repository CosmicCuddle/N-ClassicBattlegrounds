# Changelog

All changes to the **client addon** belong in this repository. Server-only Battlemaster queue enforcement is maintained separately in [Mod-Naxxramas-Core](https://github.com/CosmicCuddle/Mod-Naxxramas-Core).

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
