# GOVERNMENT REFORMS
#
# - age: <age key> optional age the reform can be used from
# - government: <government type key> optional government type that supports the reform
# - major: <yes/no> These are exclusive reforms, you can only implement one major one per country
# - unique: <yes/no> Has additional UI fluff
# - block_for_rebel: <yes/no> Cannot be used by rebels
# - locked: <trigger> to determine if the law is currently locked and cannot be interacted with
# - male_regnal_names: optional list of male names assumed by rulers of the country
# - female_regnal_names: optional list of female names assumed by rulers of the country
# - potential: trigger for whether the action is possible (root = country)
# - allow: trigger for whether the action can start (root = country)
# - years:
# - months:
# - weeks:
# - days: <ints> all used to define how long it takes to become fully implemented. Modifiers will be scaled by how much of this time is completed.
# - on_activate: <effect> fired when the action is chosen (root = country)
# - on_fully_activated: <effect> fired when the action's implementation reaches 100% (instant if there's no time delay)
# - on_deactivate: <effect> fired when the action is removed (root = country)
# - country_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for if the modifier applies)> which is applied to whole countries
# - province_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for if the modifier applies)> which is applied to provinces
# - location_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for if the modifier applies)> which is applied to locations
