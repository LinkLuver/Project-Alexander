# SUBJECT TYPES IMPORTED FROM IMPERATOR (pa_*.txt in this folder, 2026-09-29)
#
# Source: Imperator: Invictus common/subject_types/00_default.txt. Terra Indomita has the same types
# (minus temple_state and march) and only differs where each file says so; Invictus wins on conflicts.
# fiefdom and march already exist in EU5: the Imperator values are merged into those files.
# tributary also exists in both games; it was merged too, then reverted to the EU5 version (2026-09-29).
#
# Field mapping, Imperator -> EU5
#   subject_pays                        -> subject_pays (prices in prices/pa_imperator_subject_prices.txt)
#   joins_overlord_in_war = yes         -> join_offensive_wars_always + join_defensive_wars_always
#                                          (the subject joins when its overlord calls)
#   protected_when_attacked = yes       -> overlord_protects_external = yes, and the overlord joins
#                                          the subject's defensive wars (join_defensive_wars_always)
#   allowed_to_declare_war_against_others = yes -> allow_declaring_wars = { always = yes }
#   has_overlords_ruler                 -> has_overlords_ruler
#   can_be_integrated                   -> can_be_annexed
#   costs_diplomatic_slot = yes / no    -> diplomatic_capacity_cost_scale = 1 / 0
#   subject_can_cancel                  -> subject_can_cancel
#   has_limited_diplomacy               -> has_limited_diplomacy
#   overlord_modifier / subject_modifier -> same, per modifier (only where EU5 has the same modifier)
#   allow (root = subject, scope:future_overlord = overlord)
#                                       -> enabled_through_diplomacy (root = overlord, scope:target = subject)
#                                          (not enabled: EU5 checks enabled for subjects set up at game start too)
#   allow = { always = no } (script only) -> visible_through_diplomacy / visible_through_treaty = { always = no }
#   on_enable / on_disable              -> same (same scopes in both games)
#   can_build, only_trade_with_overlord, diplo_chance -> no EU5 equivalent, kept as comments
#
# Markers
#   #P:A TODO Placeholder from <type>   EU5-only field; value copied from that EU5 subject type
#   #P:A TODO No EU5 equivalent         Imperator content kept as a comment
