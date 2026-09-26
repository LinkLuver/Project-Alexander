#<tag> = {
#	priority = int; which special status is more important for gui lists; higher is better; default 1; 0 makes it equal to regular membership
#	can_bestow_trigger = trigger to test if a country can have this status (root = country, scope:recipient = organization, scope:source = special status)
#	auto_bestowal_trigger = trigger to test if a country should automatically gain this status (root = country, scope:recipient = organization, scope:source = special status)
#	auto_dismissal_trigger = trigger to test if a country should automatically lose this status (root = country, scope:recipient = organization, scope:source = special status)
#	max_countries = <script value> maximum number of countries that can have this status, (root = international organization, scope:source = special status)
#	on_bestowed_effect = effect when the status is set on a country (root = country, scope:recipient = organization, scope:source = special status)
#	on_rescinded_effect = effect when the status is removed from a country (root = country, scope:recipient = organization, scope:source = special status)
#	modifier = modifier applied to countries with this status
#	leader_modifier = modifier applied to the leader, multiplied by the number of countries with this status
#	map_color = scripted color on the map (root = country, scope:recipient = organization)
#   special_status_power = <script value> the political power this group of special status countries have, relevant for io parliament issues (root = country, scope:recipient = organization, scope:source = special status)
#}