# Government bureaucracy! Stuff you implement with good intentions but ends up costing you an arm and a leg.
#
#
# - potential: trigger for whether the action is possible (root = country)
# - allow: trigger for whether the action can start (root = country)
# - years:
# - months:
# - weeks:
# - days: <ints> all used to define how long it takes to become fully implemented. Modifiers will be scaled by how much of this time is completed.
# - on_activate: <effect> fired when the action is chosen (root = country)
# - on_fully_activated: <effect> fired when the action's implementation reaches 100% (instant if there's no time delay): root = country
# - on_deactivate: <effect> fired when the action is removed (root = country)
# - neutral_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for if the modifier applies)> which is applied to whole countries: root = country; scope:maintenance = maintenance; scope:entrenchment = entrenchment.
# - positive_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for if the modifier applies)> which is applied to whole countries: root = country; scope:maintenance = maintenance; scope:entrenchment = entrenchment.
# - negative_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for if the modifier applies)> which is applied to whole countries: root = country; scope:maintenance = maintenance; scope:entrenchment = entrenchment.
# - implementation_price = a scripted standard price, listed in \common\prices\ and referenced by name (like price:<price_id>) or as a result of a script (like scope:target.price)
# - implementation_price_modifier = calculated value, multiplies the price; root is the country
# - removal_price = a scripted standard price, listed in \common\prices\ and referenced by name (like price:<price_id>) or as a result of a script (like scope:target.price)
# - removal_price_modifier = calculated value, multiplies the price; root is the country
# - maintenance_price = a scripted standard price, listed in \common\prices\ and referenced by name (like price:<price_id>) or as a result of a script (like scope:target.price)
# - maintenance_price_modifier = calculated value, multiplies the price; root is the country
# - on_maintenance_changed: <effect> called on the next day after a maintenance setting is changed: root = country; scope:old_maintenance = previous value; scope:new_maintenance = new value