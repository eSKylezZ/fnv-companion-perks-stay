# Changelog

## Version 1.1

Perk ID audit pass — all form IDs verified by directly scanning the relevant ESM/ESP files.

**Bug fixes:**
- Fixed Dead Money: Dog/God and Christine companion perks were swapped. Dog/God now correctly retains `NVDLC01InMyFootsteps` (0x13B26) and Christine retains `NVDLC01SignalInterference` (0x8A2E).
- Fixed Butch: the original "Butch" callback tracked `TTWFollowerPerkButch` (0x7E9D), a perk applied to Butch's own actor rather than the player. Removed incorrect callback and consolidated to the single correct player perk `TTWFollowerPerkButchFollower` (0x9089).

**New callbacks (5 added, total now 32):**
- Added Cass - Calm Heart (`CalmHeartPerk`) — earned by completing Heartache by the Number via NCR evidence route.
- Added Cass - Hand of Vengeance (`HandOfVengeance`) — earned by completing Heartache by the Number via killing the merchants.
- Added Veronica - Bonds of Steel (`BondsOfSteel`) — earned by completing I Could Make You Care with Veronica staying with the BoS.
- Added Veronica - Causeless Rebel (`CauselessRebel`) — earned by completing I Could Make You Care with Veronica leaving the BoS.
- Added ED-E (Lonesome Road) - Enhanced Sensors (`NVDLC04EnhancedSensors`, 0xDF65) — the initial companion join perk separate from the ranked Camarader-E upgrades.

**Testing script overhaul:**
- Rewrote `gl_CompanionPerksStay_Test.txt` as a tick-based three-state machine, replacing the previous `ScriptWait`-based hire/fire approach which did not function correctly in a global script context.
- State 0: arms all 30 CPS AuxVars to `1` and strips every companion perk via `RemovePerk`, simulating a full companion dismissal across all supported companions simultaneously.
- State 1: waits per-tick until Boone's Spotter perk is restored by CPS, confirming the retention callbacks have fired.
- State 2: checks and prints `PASS`/`FAIL` for all 30 tracked perks (base FNV, Dead Money, Honest Hearts, Lonesome Road, TTW).
- Added `iTestWait` INI key (now unused by the state machine but retained for future use).

**Notes:**
- Rex's post-quest perks (Faithful Protector, Blood of the Legion, Unshakeable Tracker) are applied to Rex's actor directly, not to the player, so no callbacks are needed for them.
- Branching perks (Cass/Veronica quest completions) use `&&` locking logic rather than `||` to prevent granting a perk the player never earned.

## Version 1

First release of the completely plugin-free (ESPless) companion perk retention script.

- Implemented independent, per-companion loop callbacks to bypass GECK's 512-character inline preprocessor compilation limit.
- Utilized direct GetFormFromMod resolution inside callbacks to prevent companion reference nullification when cells unload.
- Added full Tale of Two Wastelands (TTW) support, covering all 8 Fallout 3 companions.
- Added full DLC support (Dead Money, Honest Hearts, Lonesome Road).
- Added configurable INI settings for check interval timing and message notification toggles.
- Implemented dynamic notification logic (native B42 Notify integration, gracefully falling back to standard MessageEx corner messages if not installed).
- Included a built-in Testing script (gl_CompanionPerksStay_Test.txt) to easily force-hire and teleport all 23 companions for verification.
