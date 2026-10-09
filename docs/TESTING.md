# In-game testing checklist (0.2.0-beta)

No recompilation or server restart is required to check addon UI changes.

## Before testing

1. Back up the previous version of `Interface/AddOns/NaxxramasClassicBattlegrounds/`.
2. Copy this standalone repository's latest `.lua` and `.toc` into the addon folder.
3. Start WoW 3.3.5a and use `/reload`.
4. Use `/ncbg on` and `/ncbg status`.
5. Allow about 75 seconds for completed progression quest IDs to refresh.

## Vanilla character (before stage 8)

- [ ] PvP tab and Honor statistics remain visible.
- [ ] Battlegrounds tab next to PvP is hidden.
- [ ] Arena points, Arena teams (2v2/3v3/5v5), and Arena toggles are hidden.
- [ ] There is no old overlapping text message.
- [ ] Battlemaster NPC queue interface opens normally.
- [ ] Wintergrasp timer/icon is not visible, including when using a Battlemaster.

## TBC character (stages 8–12)

- [ ] Arena panels and points appear in PvP.
- [ ] Battlegrounds tab stays hidden in the ordinary PvP window.
- [ ] Wintergrasp timer/icon stays hidden.
- [ ] Battlemaster NPC queue interface opens normally.

## WotLK character (stage 13 or higher)

- [ ] Battlegrounds tab appears in the ordinary PvP window.
- [ ] Arena panels remain visible.
- [ ] Wintergrasp timer/icon reappears in the appropriate BG UI.
- [ ] Both Blizzard Join Battle controls are present and function normally.

## Toggle and rollback

- [ ] `/ncbg off` restores the unmodified Blizzard UI.
- [ ] `/ncbg on` reapplies era-specific visuals.
- [ ] Test a login, logout and `/reload` with no Lua errors.
- [ ] Test any known third-party PvP UI addons for conflicts.

**The addon only hides/restores client frames.** The server's remote-queue
security must be tested separately after the next scheduled Naxxramas Core
rebuild; do not treat hidden buttons as proof of server enforcement.

If the UI looks wrong: use `/ncbg off`, or disable this addon at the
character-selection screen; keep your backed-up addon folder for an immediate
rollback.
