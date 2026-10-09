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

1. **Back up** your existing `NaxxramasClassicBattlegrounds`, `N-ClassicBattlegrounds` or `NClassicBattlegrounds` folders in `Interface/AddOns`. Remove these existing versions after backing them up to avoid duplicate addons.
2. Select **Code → Download ZIP** on this repository and extract it.
3. Open the extracted **`N-ClassicBattlegrounds-main`** repository folder. **Inside it**, find the install-ready **`NClassicBattlegrounds`** folder.
4. **Copy only that inner `NClassicBattlegrounds` folder** to `World of Warcraft/Interface/AddOns/`. Do not copy the outer repository folder.
5. Check the final layout:

   ```text
   Interface/
   └── AddOns/
       └── NClassicBattlegrounds/
           ├── NClassicBattlegrounds.toc
           └── NClassicBattlegrounds.lua
   ```

6. Launch WoW 3.3.5a. Check the **AddOns** button at character selection for **N Classic Battlegrounds**, then use `/ncbg status` in game.

**Common mistake:** The GitHub repository is named `N-ClassicBattlegrounds` (with a hyphen), but the **installed addon folder MUST be named `NClassicBattlegrounds`** (without a hyphen), matching the `.toc` filename. Installing the outer ZIP/repository folder directly prevents the addon from appearing.

**Important:** Only the new `NClassicBattlegrounds` folder should be active. Do not install both names together. Your addon folder must directly contain its matching `.toc` and `.lua` files. The repository now ships an install-ready inner `NClassicBattlegrounds/` folder; the outer `N-ClassicBattlegrounds-main` folder is **not** the WoW addon.

The addon can be used to test the **interface alone** while the Naxxramas Core server feature is still disabled. Hiding a tab is **not** a security or matchmaking restriction.

## Name change

**New addon name:** `NClassicBattlegrounds`. **Former addon name:** `NaxxramasClassicBattlegrounds`.

**Current repository:** [CosmicCuddle/N-ClassicBattlegrounds](https://github.com/CosmicCuddle/N-ClassicBattlegrounds). The shorter GitHub repository name and the no-hyphen WoW addon folder are intentionally different.

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

**Version: 1.0.0 — first public release.**

- **Reported working in game:** after correcting the addon directory, the addon loads and the user confirmed it works; the original remote Battlegrounds tab hide was separately confirmed. The PvP panel remains and the earlier overlapping message was removed.
- **Further verification recommended:** actual progression transitions (Vanilla to TBC stage 8, TBC to WotLK stage 13), Wintergrasp display in each era, Battlemaster NPC presentation, and third-party addon compatibility. These are not being claimed as fully tested.
- **Not yet tested:** companion server-side Battlemaster restriction (requires a future Naxxramas Core rebuild).

See the [addon test checklist](docs/TESTING.md) for recommended post-release regression checks and [v1.0.0 release notes](docs/RELEASE-v1.0.0.md) for details.

## Development and rollback

This repository is the **canonical home of the addon**; new Lua and TOC updates should be made here first. The earlier copy kept inside Mod-Naxxramas-Core is an **unchanged backup** during this migration and should not be treated as the update target.

To undo all client changes, use `/ncbg off` or disable/remove the `NClassicBattlegrounds` folder. No character or server data is modified.

**Name migration:** the new addon saves its per-character on/off preference as `NClassicBGQueueSettings`. The old `NaxxramasClassicBGQueueSettings` value is not automatically carried over from the renamed addon; the new name defaults to **enabled**. You can use `/ncbg off` again if needed. Keep your old addon folder backed up for rollback.

For history of changes, see [CHANGELOG.md](CHANGELOG.md).
