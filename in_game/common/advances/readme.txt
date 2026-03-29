#<advance ID> = {
#	age = <age>												# Determines in which age this advance is available
#	icon = <icon>											# The icon of the advance in particular
#	requires = <advance>									# The advance will be placed directly after the specified advance
#	government = <government_type>							# The advance is only available to you if you have the specified government type
#	country_type = <location/pop/building/army>				# The advance is only available to you if you have the specified coutry type
#	allow = { <triggers> }									# The advance can only be researched if the specified triggers are fulfilled
#	potential = { <triggers> }								# The advance will only appear if the specified triggers are fulfilled. NOTE: advances do not become retroactively visible..
#	for = <adm/dip/mil>										# The advance will only appear for a specified specialization your country can take at the start of an age
#	unlock_unit = <unit>									# Unlocks the specified unit
#	unlock_ability = <ability>								# Unlocks the specified ability
#	unlock_interaction = <interaction>						# Unlocks the specified character interaction
#	unlock_country_interaction = <country_interaction>		# Unlocks the specified country interaction
#	unlock_relation_type = <relation_type>					# Unlocks the specified relation type
#	unlock_building = <building>							# Unlocks the specified building
#	unlock_law = <law>										# Unlocks the specified law
#	unlock_levy = <levy>									# Unlocks the specified levy
#	unlock_government_reform = <government_reform>			# Unlocks the specified government reform
#	unlock_casus_belli = <casus_belli>						# Unlocks the specified casus belli
#	unlock_subject_type = <subject_type>					# Unlocks the specified subject type
#	unlock_production_method = <production_method>			# Unlocks the specified production method
#	allow_children = <yes/no>								# force the advance to be a child note, will produce error log output if this is violated
#	<modifiers>												# The modifiers you can gain once you have researched that advance
#   modifier_while_progressing = { 
#          potential_trigger = <trigger>
#          scale = <maths>
#          <modifiers> }                                    # triggered and scaled modifier applied to the country while an advance is being researched if the conditions are met in the potential_trigger
#}