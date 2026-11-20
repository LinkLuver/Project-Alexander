# Alexander Senate: development state

Rome-only Senate extension for Project Alexander. The Senate button replaces the body of the government view; **Back to Government** returns to vanilla. A Rome-only international organization provides the HRE-style institutional shell, while the internal faction-seat system decides all Senate outcomes. Foreign countries cannot join or receive seats.

Implemented: three Senate factions with approval, seats, family leaders, independent senators, social coalitions, office influence, elections, crises and civil-war ultimatums; a 100–160 member chamber; four faction-weighted motions; and patronage actions that alter both approval and the actual seat distribution. The view uses Imperator's Senate debate art, faction icons, approval icon, Senate frame and Senate-seat icon. Rome also uses one-year consular elections: the primary consul is EU5's ruler and the second consul is represented by a co-consul character variable. When the ruler belongs to a faction family, the co-consul is selected from its strongest rival faction.

Important: scripted GUI and on-action changes require the game to load the updated definitions. Do not rely on GUI hot reload to load new script databases. The running game has not yet been used to verify this build. Load a disposable test campaign, inspect errors, advance at least one month and one year, and verify values, leader selection, save/reload and cooldowns before considering the feature playable. Do not test on the sole copy of an important save.

The mod completely overrides in_game/gui/government_lateralview.gui, based on local checksum 3fe799f897b20dd02e3ae4caefa85169. Other mods changing the same file can conflict; update the copy when the game changes. Disable the extension to remove it from a playset. Scripted country and character variables may persist in saves made with the extension; rollback behavior has not been verified.

## Current Senate rules

- Rome begins with 100 senators. **Expand Senate** costs 100 gold, adds 5 seats to the highest-approval faction, is available once every five years, and caps at 160 senators.
- Voting thresholds scale with Senate size: 51% is a clean pass; 30% is a compromise pass with a prestige cost.
- Every faction has a leader family, a count of adult members, and individually assigned independent senators. Independents reduce their faction's vote contribution.
- Senate elections run every five years. Consular elections run annually through Rome's dedicated election selection. Faction crises build only while a large bloc is deeply dissatisfied; an ultimatum can end in a faction-led civil war.
- Agendas have distinct coalitions: Optimates back holdings, Boni back stability/public works, and Populares back civic law.

Still required: game-campaign verification of persistence and outcomes; actual EU5 holdings, buildings and laws instead of generic rewards; office expectations and character influence; AI behavior; action gating/override penalties; and final UI scaling against multiple resolutions.
