# <parliament agenda key> = {
# 	type = country/international_organization	#setup for what scope this parliament agenda is intended for, by default country
# 	estate = <estate type>						#for which estate type this agenda applies, ignorable if type != country, can have multiple entries
# 	special_status = <special status key>		#for which special status types this agenda applies, ignorable if type != international_organization, can have multiple entries
# 	potential = {}								#trigger with the scope defined from type (root = country/international_organization; if country then target = estate_type, target = special_status), will only show agendas which fulfill the potential
# 	allow = {}									#trigger with the scope defined from type, for IOs the allow is checked for the actor so only specific members are allowed to pass the agenda, for countries the allow is only checked via is_available_for and is_allowed_for which is used in select_triggers primarily (root = country/international_organization; if country then target = estate_type, target = special_status)
# 	on_accept = {}								#effect with the scope defined from type (root = country/international_organization; if country then target = estate_type, target = special_status)
#   on_bribe = {}                               #effect which are applied to the briber country when using bribe_estate; not used for IO agendas (root = briber, target = estate_type, recipient = bribee)
#   can_bribe = {}                              #trigger which are applied to the briber country when using bribe_estate; not used for IO agendas (root = briber, target = estate_type, recipient = bribee)
# 	chance = {}									#scriptvalue with the scope defined from type (root = country/international_organization; if country then target = estate_type, target = special_status)
#   importance = <script value>					#scriptvalue with the scope defined from type (root = country/international_organization; if country then target = estate_type, target = special_status), the higher the importance, the greater the impact on the parliament issue; will always be set to 1 if not defined
# }