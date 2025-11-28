# CASUS BELLIs
#
# Wot you use to wage war, innit
#
#<casus belli ID> = {
#	no_cb = yes/no only for the no cb cb (the best cb)
#	trade = yes/no if it's a trade-related cb
#	visible = <trigger> checks to see if we can see this cb (root = country, scope:target = target)
#	allow_creation = <trigger> checks to see if we can create a cb against another country (root = country, scope:target = target)
#	allow_declaration = <trigger> checks to see if we can use this cb to declare war against another country (root = country, scope:target = target)
#	province = <trigger> if this CB has a province as a target, this trigger checks if the province is valid to target (root = province, scope:actor = who wants to use it, scope:recipient = who they're targetting)
#	speed = <float> how much is added to creation progress per month, in per cent (100 = it's created)
#	additional_war_enthusiasm = <script value> gets a value determining how enthusiastic for being in this war said country is. (root = country, scope:war = war)
#   additional_war_enthusiasm_attacker = <script value> same as above but only applied to attackers
#   additional_war_enthusiasm_defender = <script value> same as above but only applied to defenders
#   ai_selection_desire = <script value> How more likely Ai is to select this CB, 0 doesn't mean never
#	war_goal_type = <war goal ID> when using this CB, what is the war goal
#   allow_separate_peace = yes/no if separate peace deals are allowed (defaults to yes)
#   cut_down_in_size_cb = yes/no only for AI, makes AI choose release treaties more often
#   days/weeks/months/years = <int> override NDiplomacy::CASUS_BELLI_MONTHS with that script value if defined
#   max_warscore_from_battles = <int> to override NDefines::NDiplomacy::WARSCORE_MAX_FROM_BATTLES
#   ai_subjugation_desire = <script value> #root = country; scope:recipient = subject; scope:subject_type = type; scope:war = war;
#   ai_cede_location_desire = <script value> #root = country; scope:location = location; scope:war = war;
#   antagonism_reduction_per_warworth_defender = <script value> #root = country; scope:recipient = recipient; scope:war = war;
#   can_expire = <yes/no>
#   allow_ports_for_reach_ai = <yes/no> #For CBs like Crusade where we don't really care if AI will have any control, we want the land to release nations
#}
#
#Localization:
#<casus belli ID>
#<casus belli ID>_PROV
#<casus belli ID>_desc