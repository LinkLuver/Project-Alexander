#<road type id> = {
#	level = <integer>								#Determines what level of road type this is and is important for has_latest_road_to triggers. Generally speaking, higher level = later road type
#	enabled = { <trigger> }							#Can build this road only if the triggers in enabled are true. Root scope is the country which tries to build the road
#	proximity = <integer>							#Reduction of the distance to capital effect for locations
#	movement_cost = <double>						#Modifies how fast units move on a location with this road type
#	build_time_per_unit_distance = <integer>>		#How long does it take to build the roads from one location to another
#	price_per_unit_distance = <price>				#How expensive is it to build the roads from one location to another
#	construction_demand = <goods demand>			#What goods are needed to build this road type
#	color = <named color>							#What color should this road have in the road map mode
#}