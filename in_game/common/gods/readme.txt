# Gods! Deities that may or may not affect gameplay.
#
# - religion: 
# - group: these two both allow specification of multiple religions and religion groups that the god applies to. Format:
#        religion/group = {
#            religion/group = <religion or group key>
#            name_key = string key of the name of the god in that religion or group
#        }
#   OR:
#        religion/group = <religion or group key> use this if the name is just the same as the id tag of the god
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
#
# Use the following to add gods to a country
# add_god = <god id>
# remove_god = <god id>