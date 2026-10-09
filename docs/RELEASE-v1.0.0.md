# N Classic Battlegrounds — v1.0.0

First public release of **N Classic Battlegrounds**, a client-only WoW 3.3.5a addon designed for Individual Progression.

## What's included

- **Vanilla (stages 0–7):** Hide Arena points/team panels, Wintergrasp information and the remote Battlegrounds tab beside PvP.
- **TBC (stages 8–12):** Restore Arena points/team panels. Keep Wintergrasp information and the remote Battlegrounds tab hidden.
- **WotLK (stage 13+):** Restore the ordinary WotLK Arena, Wintergrasp and remote Battlegrounds tab interface.
- Preserve Honor statistics, PvP information and the normal Battlemaster NPC queue interface.
- Commands: `/ncbg on`, `/ncbg off`, `/ncbg status` and `/ncbg refresh`.
- Install-ready `NClassicBattlegrounds/` folder with matching `.toc` and `.lua` filenames. WoW Interface version: `30300`.
- No DBC, SQL, MPQ or server recompilation required for the client addon.

## Download and installation

**Preferred download:** `dist/NClassicBattlegrounds-v1.0.0.zip` in this repository.

1. Back up your existing `Interface/AddOns/NClassicBattlegrounds/` folder.
2. Remove old addon folders such as `NaxxramasClassicBattlegrounds` or `N-ClassicBattlegrounds`; never install two copies.
3. Extract the release ZIP **directly into** `World of Warcraft/Interface/AddOns/`. The ZIP must unpack as `NClassicBattlegrounds/NClassicBattlegrounds.toc` and `NClassicBattlegrounds/NClassicBattlegrounds.lua`.
4. Enable **N Classic Battlegrounds** at the character-selection AddOns menu.
5. Log in and enter `/ncbg status`.

## Scope and verification

The renamed and repackaged addon is **reported working in game** by the server owner, including the original Battleground tab behaviour. Not all Vanilla→TBC and TBC→WotLK milestone transitions, Wintergrasp timer combinations, or other addon combinations have been separately tested. Please report any issues.

**Important:** This is an **interface-only addon**. Actual Battlemaster-only queue enforcement requires the separate opt-in system from [Mod-Naxxramas-Core](https://github.com/CosmicCuddle/Mod-Naxxramas-Core). That server-side feature is disabled by default and still requires compilation and testing; `/ncbg off` only turns off visual restrictions.

## Rollback

Use `/ncbg off` to restore original interface presentation, or disable/remove `NClassicBattlegrounds/` from AddOns after backing it up. No character or server data migration is performed by the addon.

## Publishing this release on GitHub

This document is also the suggested **GitHub Release description**.

1. Open the [repository Releases page](https://github.com/CosmicCuddle/N-ClassicBattlegrounds/releases).
2. Choose **Draft a new release**.
3. Choose **Create new tag**, type `v1.0.0` and target the current `main` branch.
4. Set release title to **N Classic Battlegrounds v1.0.0** and use this file's contents for the release description.
5. Attach `NClassicBattlegrounds-v1.0.0.zip` from the repository's `dist/` directory, or point users to its direct download location. Verify it extracts correctly.
6. Keep **Set as a pre-release** unchecked, then choose **Publish release**.

The GitHub Release object and tag must be created through GitHub's Release interface; updating a `.toc` version is not the same as publishing a GitHub Release.
