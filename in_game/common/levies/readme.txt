#<levy_id> = {
#	unit = <unit_type>
#	size = <scriptvalue>
#   country_allow = { <triggers> } #Scope: country
#	allow = { <triggers> }	#Scope: pops
#	allow_as_crew = {
#		<triggers>	#Scope: pops
#	}
#   allowed_pop_type = <pop type> #which pop types can use this levy, can have multiple, none given means all pop types are eligible
#   allowed_culture = <culture_definition> #which culture can use this levy, can have multiple, none given means all cultures are eligible
#}

#IMPORTANT: if you add new levy unit types make sure that the super specialized units with many conditions are at the very top and the more general units are at the bottom of the file.
#Otherwise, the game will just fill all the available levy picks with the first levy it finds and move on.