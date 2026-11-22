# Senate localization audit — 22 November 2026

## Scope and status

Audited the Roman Senate's English localization and the recent Senate overview and starting-authority changes in the local Project Alexander checkout. This is a static audit informed by the game logs; the fixes have not yet been verified in a new game session.

## Changes made

- Added English names for the Optimates, Boni and Populares rebel groups.
- Replaced two estate-agenda tooltip expressions that the latest `gui.log` reported as failing to parse. The tooltip description now uses the agenda description accessor used by the existing game UI; the unsupported effects expression was removed.
- Corrected the chamber legend to describe faction icons rather than colors, and removed an outdated claim about a prestige-cost compromise from the Senate footer.
- Clarified that vetoing a ten-year Senate bill costs five Senate authority under the existing failed-motion effect.
- Replaced the unexplained abbreviation `RGO` in two measure labels with `rural resource capacity`.
- Confirmed that the Senate GUI's literal `pa_` text keys have corresponding English entries and that the relevant `pa_` localization files have UTF-8 BOMs.
- Confirmed that the game-start, monthly-initialization, missing-variable fallback and scripted-GUI initialization paths use 75 starting Senate authority. Existing saves with an authority value are not reset.

## Files changed

- `in_game/gui/panels/organization/pa_roman_senate.gui`
- `main_menu/localization/english/pa_senate_l_english.yml`
- `main_menu/localization/english/pa_senate_ten_year_measures_l_english.yml`

The changes were copied to both the local mod checkout and the separate D: repository checkout. The local mod is `C:\Users\fpicc\Documents\Paradox Interactive\Europa Universalis V\mod\Project-Alexander`; both checkouts should remain on the `republic-screen` branch, but check Git before committing.

## Remaining checks and limitations

1. Restart EU5 with the local mod enabled. Verify the Senate overview, Senate Laws tab, faction rebel names and veto label render without raw localization keys or clipped text.
2. Open an estate-agenda tooltip and confirm its description appears and no new parsing error is written to `gui.log`. The unsupported effects line was removed, so this audit does not establish that all agenda effects are displayed there.
3. Start a new Rome campaign and check that authority begins at 75. Load an existing save separately and confirm its existing authority is preserved.
4. Test a ten-year bill and veto it; verify the failure callback deducts five authority and no bill modifier is applied. The label reflects the current script, not an observed game result.
5. The latest available `gui.log` also reported layout and text-widget warnings in `pa_roman_senate.gui`. They were not fixed in the localization pass; inspect a fresh log and the actual screen before changing the established chamber layout.
6. The ten-year measures, dictatorship transition, co-consul election, and connection between Senate approval and Parliament starting support still require an in-game combined test. See `SENATE_HANDOFF_2026-11-21.md` for the broader development state, noting that it predates this audit.

Run `git diff --check` after further edits. Static checks and copied files do not establish that the game accepted the UI expressions or gameplay scripts.
