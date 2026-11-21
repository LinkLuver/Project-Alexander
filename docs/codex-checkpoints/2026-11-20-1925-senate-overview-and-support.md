# Roman Senate overview and Parliament support

## Goal

Build the Roman Senate inside the international organization panel with Rome's country Parliament handling debates, requests and estate agendas.

## Current work

The Senate Overview shows the chamber, two consuls, faction seats and seat-weighted approval. Favor buttons sit above Parliament Requests. The separate Overview tab and Defy Senate buttons were removed. The country Call Senate control and debate banner are positioned above the chamber.

The IO displays native country Parliament requests and estate agendas. Agenda acceptance is implemented in in_game/common/scripted_guis/pa_senate_estate_agendas.txt. Faction approval calculations are in in_game/common/script_values/pa_senate_approval.txt and initial debate backing is calculated in in_game/common/scripted_effects/pa_senate_country_parliament.txt.

The interface is in in_game/gui/panels/organization/pa_roman_senate.gui, common.gui and parliament.gui. Country Parliament actions are in in_game/common/generic_actions/parliament.txt. English text is in main_menu/localization/english/pa_senate_l_english.yml. Preserve its UTF-8 byte-order mark.

## Reproduce

Use the republic-screen branch. Copy changed files to matching paths under C:/Users/fpicc/Documents/Paradox Interactive/Europa Universalis V/mod/Alexander-Senate and compare file hashes. Restart EU5 after changing localization or script values.

## Checks and outstanding work

Recent GUI edits were checked for balanced braces and copied to the local mod. The localization file was verified to have a UTF-8 byte-order mark. These checks do not establish in-game rendering or behavior.

The user reports Parliament support is 100% every time Parliament is called. The cause is unresolved. Check whether initial backing runs, compare faction vote variables and pa_senate_last_vote with native support, and trace later effects that may change support. Test multiple debates and estate agenda acceptance.

Verify the latest Overview removal and Call Senate placement in game. No commit or push was made.