# Religious focuses
# 
# These are kinda like advances, but for religions that have them. They need to be researched like advances, and give modifiers during research as well as once researched.
#
# They are added to religions via the religious_focuses property of religions, e.g.:
# 	religious_focuses = {
#		adopt_ometeotl
#		elevate_patron_god
#		establish_cihuacoatl
#		expand_cuahpipiltin
#		increase_militarism
#		institute_flower_wars
#		legal_reforms
#		raise_sacrifice_rate
#	}
#
# Attributes:
# potential: trigger to see if the focus should be visible in the UI (root = country)
# allow: trigger to see if the focus is available (root = country)
# monthly_progress: script value for how much monthly progress is made to achieving the focus (root = country)
# modifier_while_progressing: modifier applied to the country while a focus is being researched
# modifier_on_completion: modifier applied to the country once research is complete
# effect_on_completion: effect executed once the research is completed (root = country)
