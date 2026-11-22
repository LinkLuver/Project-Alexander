# Roman Senate development handoff

Status: work in progress, 21 November 2026. The latest Senate, election and dictatorship changes have not been validated in a running game. Static checks and successful file copies do not prove that EU5 accepts or executes the scripts.

## Workspace and Git

- Local mod and Git checkout: `C:\Users\fpicc\Documents\Paradox Interactive\Europa Universalis V\mod\Project-Alexander`.
- Additional checkout: `D:\AI-Related Apllications & Modding\Modding\EU5 Modding Stuff\eu5alexander\Project-Alexander`.
- Both checkouts are on `republic-screen`; they are separate directories. Files modified during recent work were copied between them, but future edits need the same care.
- The local checkout has modified and new, uncommitted files. GitHub Desktop must be pointed at that checkout; include new files as well as modified files when committing. Nothing in this handoff asserts that those changes were pushed.
- Preserve existing uncommitted work and the established chamber layout. The existing `README.md` includes older Senate descriptions and is not a reliable source for the current seat layout or rules.

## Intended and scripted behavior

- Rome has three factions: Optimates, Boni and Populares. The normal Senate starts at 300 seats, has an 800-seat cap, and the chamber uses faction icons with each box representing up to five senators. A test button adds up to 500 seats; do not remove it unless requested.
- Faction approval contributes to seat-weighted Senate approval and country Parliament starting support. Favoring a faction increases its approval rather than directly transferring seats. Approval drifts down monthly; tyranny and selected consul actions affect approval. Faction crisis pressure can lead to an ultimatum and civil war.
- The country Parliament remains the native decision system. Senate calculations set its initial backing, and the Roman Senate IO supplies the chamber. Rome's country Parliament sessions have a scripted 100-day resolution fallback and a six-month cooldown. Verify native action behavior before changing the UI or removing any of these links.
- The Roman consular succession is scripted for a one-year term. Candidate forecasts and the election use the same ranked ballot; first place is intended to become the ruler and second place co-consul. Candidates must be male, at least 30, and not subject to the ten-year re-entry restriction. Failed elections are logged and retried; candidate availability and synchronization must be tested.
- Tyranny is stored in `pa_senate_tyranny` and shown in the Senate chamber. At 50, 75 and 90 tyranny, the yearly pulse applies respectively 3, 6 and 10 stability loss. The custom imprison interaction is intended to imprison a selected character for five years and add 5 tyranny. Its world selector and treatment of rulers need testing.
- The custom Roman Constitution law includes a dictatorship policy. Its dedicated country Parliament agenda requires 85 tyranny, or at least 10 war exhaustion after six monthly checks at war. The latter is approximate: a brief peace between monthly checks can be missed, and six checks are not precisely six full months. A successful debate is intended to use the lifetime dictator succession and suppress the co-consul.
- The Senate is scripted to demand the dictator step down around 180 days after the dictatorship begins. Refusal adds 15 tyranny, reduces stability and faction approval, and increases crisis pressure. Accepting attempts to restore the consular law and start a ranked election; reconciliation rewards are delayed until both winners pass the later confirmation check. A restoration agenda also exists. A refusal has a two-year repeat cooldown.
- An overflow repair backs up the original Senate size and faction totals in country variables before correcting over-800 saves. Use a duplicate save when testing migration.

## Key files

- `in_game/gui/panels/organization/pa_roman_senate.gui`: chamber, faction displays, consuls and tyranny meter.
- `in_game/common/on_action/pa_senate_pulses.txt`: initialization, maintenance, faction dynamics, election retries and dictatorship demand scheduling.
- `in_game/common/heir_selections/pa_roman_consular_election.txt`, `in_game/common/scripted_effects/pa_consular_forecast.txt`, `in_game/events/pa_roman_election.txt`: succession, ranking, appointments and diagnostics.
- `in_game/common/generic_actions/parliament.txt`, `in_game/common/scripted_effects/pa_senate_country_parliament.txt`, `in_game/common/parliament_issues/`: native Parliament selection, support and Senate agendas.
- `in_game/common/laws/pa_roman_dictatorship.txt`, `in_game/common/heir_selections/pa_roman_dictatorship.txt`, `in_game/common/scripted_effects/pa_roman_constitution_effects.txt`, `in_game/events/pa_dictatorship.txt`: dictatorship and restoration.
- `in_game/common/character_interactions/pa_imprison_character.txt` and `in_game/common/scripted_effects/pa_senate_integrity.txt`: imprisonment and overflow repair.
- `main_menu/localization/english/pa_senate_l_english.yml` and `pa_senate_dictatorship_l_english.yml`: Senate and dictatorship text.

## Verification and open risks

- `git diff --check`, selected brace counts and hash comparisons for recently copied files passed. These are structural checks, not game tests. Existing logs in `C:\Users\fpicc\Documents\Paradox Interactive\Europa Universalis V\logs` predate the latest changes.
- The biggest engine uncertainty is whether a scripted `add_policy` can enact and restore the permanently locked Roman Constitution law and fire its activation effects. Inspect `error.log` for `PA_DICTATORSHIP_DIAG` and `PA_CONSUL_DIAG`; an individual message does not replace checking the final state.
- Check that the Senate demand event opens once, its choices work, and a queued but undisplayed event does not cause duplicate prompts. The script retries failed dispatch; exact engine event-queue behavior remains unverified.
- Normal diplomatic alliance offers have a mandate check, while scripted alliance creation has an after-creation fallback. The fallback cannot guarantee that every side effect from other scripts is undone.
- Confirm the selector offers both native country agendas and custom proposals, the displayed starting support matches the seat-weighted value, debates resolve within 100 days, and law effects occur only on passage. Some paths are engine-dependent.

## Suggested combined game test

1. Restart the game with this local mod enabled and use a disposable Rome save. Confirm the chamber layout, 300 seats, tyranny meter, both consuls and forecast. Check the log for new script and localization errors.
2. Advance through a year and separately test ruler death. Confirm the forecast winners match both officeholders and both former consuls receive the ten-year restriction. Test an election with too few eligible candidates.
3. Call country Parliament and compare its starting support to the weighted Senate approval. Test an accepted and rejected issue and check the 100-day fallback.
4. Test imprisonment, tyranny gain, approval drift, stability loss, and the 800-seat test button. Test an over-cap save only on a copy.
5. Test dictatorship eligibility at 84 and 85 tyranny and the wartime route before and after six monthly checks with 10 war exhaustion. Pass and fail the agenda; confirm the policy, ruler term and co-consul behavior.
6. Let the Senate demand step-down. Test both refusal and acceptance in separate saves, including the delayed election, rewards, crisis relief and retry behavior. Check the logs and confirm no duplicate demand.

When sharing results, distinguish what was observed in game from static inspection and include the relevant log markers. Do not claim the flow is fully working until the combined test passes.
