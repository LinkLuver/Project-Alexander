#P:A TODO Review imported vanilla file (1.4.7)
#<calling id> = {
#	valid_for_types = { <religious order types> }
#	holding_goods_demand = <goods demand>
#	preferred_societal_values = { <societal values> }
#	location_trigger = { <triggers> }
#	location_modifier = { <location modifiers> }
#	country_modifier = { <country modifiers> }	# per holding, scaled by holdings x zeal
#	low_zeal_country_modifier = { <country modifiers> }	# per holding, scaled by holdings x (100 - zeal)
#	leader_adm = <integer>
#	leader_dip = <integer>
#	leader_mil = <integer>
#	trait_category = <general/admiral/ruler>
#	location_revenue_modifier = <double>
#	graphical_cultures = { <graphical culture ids> }
#	zeal_target_base = <script value>
#	content_priority = <integer>
#	ai_will_select = <script value>	# value evaluating when the AI will pick this calling when creating a religious order / will invite this order with that calling. root/scope:actor = country, scope:location = location (optional)
#}