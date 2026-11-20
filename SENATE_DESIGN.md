# Senate recreation: implementation notes

The present build is a Rome-only Senate recreation, not a literal copy of Imperator's engine system. It has three Roman factions, persistent approval and seats, an annual concession cooldown, a five-year Senate session cadence, a Rome-only HRE-style international organization, and annually elected consuls. The current motions are deliberately limited: stability, paid holdings, paid public works and civic law. EU5 must load the scripted GUI definitions at startup. Test with Project Alexander and the extension enabled before adding additional systems.

## Imperator references checked locally

- ImperatorRome/game/common/defines/00_defines.txt: SENATE_REQUIRED_APPROVAL = 0.30; SENATE_REQUIRED_APPROVAL_WITHOUT_PENALTIES = 0.51; NEUTRAL_SENATE_APPROVAL = 0.4. Confirm the relevant action-specific rules before copying thresholds.
- ImperatorRome/game/common/party_agendas/senate_objectives_roman.txt: Optimates agendas include war, holdings, laws and offices; Populares agendas include laws, holdings and offices; Boni agendas include buildings, investment, stability and tyranny.
- ImperatorRome/game/common/faction_impact/diplomatic_actions/00_default.txt: faction approval reacts to particular diplomatic actions and their context.
- ImperatorRome/game/common/faction_impact/character_interactions/00_default.txt and changing_laws/00_ROM.txt: faction reactions vary by interaction and law.

## Remaining work

1. Verify initialization, persistence, seat conservation, the annual concession cooldown and all four motion outcomes in a running campaign; fix log errors.
2. Create actual faction agendas with eligibility, progress, expiry, rewards and penalties.
3. Investigate character selection, party membership, faction leaders and character influence; build recovery when a leader dies or leaves.
4. Calculate support separately for each proposal using faction seats and faction-specific approval. Verify the 30% and 51% thresholds against the installed game behavior.
5. Replace the current generic motion outcomes with real EU5 holdings, buildings and laws, and verify ordinary war declarations and laws individually before claiming they are gated.
6. Replace generic concessions with meaningful costs and outcomes. Add AI handling and republic-only eligibility.
7. Integrate families and office expectations once the character foundation works. Provide readable tooltips, cooldown feedback, localization and UI scaling.

The mod overrides government_lateralview.gui in full and can conflict with other mods that modify that file. It is based on the installed game checksum 3fe799f897b20dd02e3ae4caefa85169.
