# N Classic Battlegrounds

**WoW 3.3.5a addon** that makes the PvP interface reflect a character's era in [Individual Progression](https://github.com/ZhengPeiRu21/mod-individual-progression).

The addon changes **what is shown in the client only**. For actual server-enforced Battlemaster-only Battleground queues, the optional companion feature lives in [Mod-Naxxramas-Core](https://github.com/CosmicCuddle/Mod-Naxxramas-Core).

## Features

| Character progression | PvP / Honor | Arena section | Remote Battlegrounds tab | Wintergrasp |
| --- | --- | --- | --- | --- |
| Vanilla (stages 0–7) | Visible | Hidden | Hidden | Hidden |
| The Burning Crusade (stages 8–12) | Visible | Visible | Hidden | Hidden |
| Wrath of the Lich King (stage 13+) | Visible | Visible | Visible | Visible |

- Hides the **Battlegrounds tab beside PvP**, not the Join Battle buttons.
- Preserves the normal Battlemaster NPC queue window.
- Hides Arena points and the Arena-team panels during Vanilla only.
- Hides the Wintergrasp timer during Vanilla and TBC.
- Leaves the Honor statistics and original PvP display available.
- Does not draw over the interface or change the Blizzard Join Battle APIs.
- Uses individual character's rewarded hidden progression quests (`66008` for TBC, `66013` for WotLK and subsequent milestones).
- No database edits, DBC edits, MPQ, AzerothCore build or server restart required for the addon.

## Installation

1. **Back up** your existing `NaxxramasClassicBattlegrounds` folder (and any previous `NClassicBattlegrounds` folder), then **remove the old `NaxxramasClassicBattlegrounds` folder from `Interface/AddOns`** so the two versions do not load simultaneously.
2. On this repository, select **Code → Download ZIP** and extract it.
3. Inside `World of Warcraft/Interface/AddOns/`, create a folder named **`NClassicBattlegrounds`**.
4. Copy the `NClassicBattlegrounds.lua` and `NClassicBattlegrounds.toc` files from the extracted ZIP into that folder. The GitHub repository ZIP may still be called `NaxxramasClassicBattlegrounds-main` until the repository itself is renamed.
5. Check that your two addon files are immediately inside that folder:

   ```text
   Interface/
   └── AddOns/
       └── NClassicBattlegrounds/
           ├── NClassicBattlegrounds.toc
           └── NClassicBattlegrounds.lua
   ```

6. Enable the addon at character selection, enter the game and type `/reload` if needed.

**Important:** Only the new `NClassicBattlegrounds` folder should be active. Do not install both names together. Your addon folder must directly contain its matching `.toc` and `.lua` files. This file rename does **not** rename the GitHub repository itself.

The addon can be used to test the **interface alone** while the Naxxramas Core server feature is still disabled. Hiding a tab is **not** a security or matchmaking restriction.

## Name change

**New addon name:** `NClassicBattlegrounds`. **Former addon name:** `NaxxramasClassicBattlegrounds`.

The **GitHub repository URL may still display the old name** until its owner renames it in GitHub Settings. That does not affect the client addon folder, which must use the new name.

## Commands

| Command | What it does |
| --- | --- |
| `/ncbg status` | Shows the last detected era and whether visual changes are enabled |
| `/ncbg refresh` | Requests completed quest data; the client may throttle requests |
| `/ncbg off` | Restores the Blizzard PvP interface for this character |
| `/ncbg on` | Enables expansion-specific UI changes again |

The WoW 3.3.5a completed-quest API limits how often new data may be queried; allow approximately **75 seconds** for a new progression milestone to be reflected in the UI.

## Optional server-side Battlemaster rule

The independent [Naxxramas Core server module](https://github.com/CosmicCuddle/Mod-Naxxramas-Core) has an **opt-in** Battlemaster-only queue system (currently disabled by default and awaiting compilation and gameplay testing). When enabled, Vanilla/TBC characters must visit an interactable Battlemaster; remote queueing unlocks at WotLK entry, stage 13.

- This addon **does not** prevent players from queueing with macros or a modified client.
- Installing this addon **does not** enable that server system.
- Disabling this addon **does not** bypass an enabled server-side restriction.
- The visual UI changes and the server queue rule can be used independently.
- No changes are required to the original Individual Progression or Playerbots modules.

## Testing status

**Version: 0.2.1-beta — not a verified stable release.**

- **Confirmed in game:** the Vanilla/TBC remote Battlegrounds tab hides correctly, the PvP panel remains, and the earlier overlapping message has been removed.
- **Still needs testing:** Vanilla Arena frames, pre-WotLK Wintergrasp information, TBC stage-8 restoration of Arena frames, WotLK stage-13 restoration of the Battlegrounds tab and Wintergrasp, Battlemaster NPC presentation, and other addon compatibility.
- **Not yet tested:** companion server-side Battlemaster restriction (requires a future Naxxramas Core rebuild).

Follow the [addon test checklist](docs/TESTING.md) before publishing a stable release.

## Development and rollback

This repository is the **canonical home of the addon**; new Lua and TOC updates should be made here first. The earlier copy kept inside Mod-Naxxramas-Core is an **unchanged backup** during this migration and should not be treated as the update target.

To undo all client changes, use `/ncbg off` or disable/remove the `NClassicBattlegrounds` folder. No character or server data is modified.

**Name migration:** the new addon saves its per-character on/off preference as `NClassicBGQueueSettings`. The old `NaxxramasClassicBGQueueSettings` value is not automatically carried over from the renamed addon; the new name defaults to **enabled**. You can use `/ncbg off` again if needed. Keep your old addon folder backed up for rollback.

For history of changes, see [CHANGELOG.md](CHANGELOG.md).
