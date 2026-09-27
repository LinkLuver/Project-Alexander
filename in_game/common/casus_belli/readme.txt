# CASUS BELLIs
#
# Wot you use to wage war, innit
#
#<casus belli ID> = {
#	no_cb = yes/no only for the no cb cb (the best cb)
#	trade = yes/no if it's a trade-related cb
#	create_visible = <trigger> checks to see if we can see this cb (root = country, scope:target = target)
#	create_enabled = <trigger> checks to see if we can create a cb against another country (root = country, scope:target = target)
#	declare_enabled = <trigger> checks to see if we can use this cb to declare war against another country (root = country, scope:target = target)
#	province = <trigger> if this CB has a province as a target, this trigger checks if the province is valid to target (root = province, scope:actor = who wants to use it, scope:recipient = who they're targetting)
#	speed = <float> how much is added to creation progress per month, in per cent (100 = it's created)
#	additional_war_enthusiasm = <script value> gets a value determining how enthusiastic for being in this war said country is. (root = country, scope:war = war, scope:attacker = war leader of the attackers, scope:defender = war leader of the defenders, scope:target = target character (optional), scope:target_province = target province (optional), scope:target_country = target country (optional))
#   additional_war_enthusiasm_attacker = <script value> same as above but only applied to attackers
#   additional_war_enthusiasm_defender = <script value> same as above but only applied to defenders
#	war_goal_type = <war goal ID> when using this CB, what is the war goal
#   allow_separate_peace = yes/no if separate peace deals are allowed (defaults to yes)
#   cut_down_in_size_cb = yes/no only for AI, makes AI choose release treaties more often
#   days/weeks/months/years = <int> override NDiplomacy::CASUS_BELLI_MONTHS with that script value if defined
#   max_warscore_from_battles = <int> to override NDefines::NDiplomacy::WARSCORE_MAX_FROM_BATTLES
#   ai_subjugation_desire = <script value> #root = country; scope:recipient = subject; scope:subject_type = type; scope:war = war;
#   ai_cede_location_desire = <script value> #root = country; scope:location = location; scope:war = war;
#   antagonism_reduction_per_warworth_defender = <script value> #root = country; scope:recipient = recipient; scope:war = war;
#   can_expire = <yes/no>
#   allow_wars_on_own_subjects = <yes/no> #For CBs which are supposed to be usable against your own subject countries
#   allow_ports_for_reach_ai = <yes/no> #For CBs like Crusade where we don't really care if AI will have any control, we want the land to release nations
#   ai_will_do = <script value> #determines when the AI will use this casus belli; overrules the usual calculation done via war goal conquer cost (root = country, scope:target = target)
#   custom_tags = { <strings> }	#A list of custom strings to use to identify that casus belli
#   show_tags_in_ui = yes/no #expose the tags in the tooltips and UI
#   allow_white_peace = yes/no #Determine if a war with that casus belli can have a white peace or not; defaults to yes
#   required_peace_treaties = { <scripted peace treaties> } #A set of peace treaties which need to be enforced by either side to end this war in anything but a white peace
#   required_attacker_peace_treaties = { <scripted peace treaties> } #A set of peace treaties which need to be enforced by the attacker leader to end this war in anything but a white peace
#   required_defender_peace_treaties = { <scripted peace treaties> } #A set of peace treaties which need to be enforced by the defender leader to end this war in anything but a white peace
#   ai_wait_with_sending_peace = <trigger> makes ai wait with sending peace unless the war is stalled out (no battles, sieges or there is ticking call for peace), root = sender, scope:recipient = recipient of the offer, scope:war = war
#}
#
#Localization:
#<casus belli ID>
#<casus belli ID>_PROV
#<casus belli ID>_desc