#<goods id> = {
#	is_slaves = yes/no									#Defaults to no, mark that good as a slave good
#	block_rgo_upgrade = yes/no							#Defaults to no, blocks the expansion of the rgo for this good
#	inflation = yes/no									#Defaults to no, will cause inflation when produced
#	base_production = <float>							#Defaults to 0
#	color = <color>										#What color the goods should have in the map mode
#	food = <float>										#Defaults to 0, how much food this good provides with
#	transport_cost = <float>							#Defaults to 1, how expensive it is to transport the good
#	default_market_price = <float>						#Defaults to 1, the default price of the good on a market
#	category = raw_material/produced					#Defaults to raw_material, defines if the goods is a raw_material or not
#	method = mining/farming/hunting/gathering/forestry	#Defaults to farming, defines the category of the good
#   ai_rgo_size_importance = <float>                    # ai preference to avoid building a city on this rgo
#   demand_add = {
#		all = <float>
#       <pop types> = <float>
#	}
#	demand_multiply = {
#		upper = <float>
#       <pop types> = <float>
#	}
#   custom_tags = { <strings> }							#A list of custom strings to use to identify that good
#}