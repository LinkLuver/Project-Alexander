# WAR GOAL TYPES:
#	- take_province
#	- superiority					#If conquer cost in superiority wars is less than 0, AI will always try and select.
#	- naval_superiority
#   - defend_capital
#	- enforce_military_access
#	- independence
#	- take_capital
#	- take_border
#	- take_country
#
#<war_goal_id> = {
#	type = <type>
#	war_name = "<war_name_loc_key>"
#	war_name_is_country_order_agnostic = <yes/no> if we should treat two countries declaring on each other either way the same as one declaring on the other (default is no, so Eng v Fra would yield a different number to Fra v Eng; setting yes here will treat Eng v Fra and Fra v Eng the same)
#	allow = {
#		<triggers>
#	}
#	attacker = {
#		call_in_overlord = <yes/no> does the overlord get called in
#		call_in_subjects = <yes/no> do subjects get called in
#		conquer_cost = <float> # factor applied to warscore cost of taking land in peace deal
#		subjugate_cost = <float> # factor applied to warscore cost when making the target a subject
#       antagonism = <float> # factor applied to whole peace deal
#		allowed_locations = { <triggers> } # checks what locations the attacker is allowed to take with this war goal; scope:loser = giver, scope:winner = taker, scope:war = war, scope:location = location
#		allowed_subjugation = { <triggers> } # allow the attacker to subjugate the defender if the triggers are true; scope:loser = giver, scope:winner = taker, scope:war = war
#	}
#	defender = {
#		call_in_overlord = <yes/no> does the overlord get called in
#		call_in_subjects = <yes/no> do subjects get called in
#		conquer_cost = <float> #cost of taking provinces
#		subjugate_cost = <float> # factor applied to warscore cost when making the target a subject
#       antagonism = <float> # factor applied to whole peace deal
#		allowed_locations = { <triggers> } # checks what locations the defender is allowed to take with this war goal; scope:loser = giver, scope:winner = taker, scope:war = war, scope:location = location
#		allowed_subjugation = { <triggers> } # allow the defender to subjugate the attacker if the triggers are true; scope:loser = giver, scope:winner = taker, scope:war = war
#	}
#	ticking_war_score = <float> #Defaut 1
#}