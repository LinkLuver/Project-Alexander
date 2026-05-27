# Unit Type scripts
# 
# age: determines in which age this unis is enabled
# build_time:
# light = yes/no is it a light or heavy unit
# upgrades_to = <another unit type> preferred upgrade path if available (optional)
# buildable = yes / no
# levy = yes / no (can be used for levy)
# default:
# construction_demand:
# maintenance_demand:
# use_ship_names = yes / no
# assault = yes/no                                      # Allows the unit to assualt a fort
# bombard = yes/no                                      # Allows the unit to bombard a fort
# auxiliary = yes/no                                    # The unit gets treated as an auxiliary unit
# category = <unit_category>                            # Defines what kind of unit this specific unit is
# location_trigger = { <location_triggers> }            # Allows the unit to recruit in the location if the location triggers are fulfilled
# location_potential = { <location_triggers> }          # Shows the unit to recruit in the location if the location triggers are fulfilled
# country_potential = { <country_triggers> }            # Shows the unit to recruit if the triggers are fulfilled
# mercenaries_per_location = { pop_type = <pop type> multiply = <proportion> }
# limit = { <value calculations> } / <default_value>    # Determines how many units of this type you can have
# combat = { <topography> / <vegetation> / <climate> }    # Modifies the damage the unit deals when fighting in certain terrain
# impact = { <topography> / <vegetation> / <climate> }    # Modifies the movement speed of the unit when in certain terrain.
# copy_from = <unit_type>                               # The unit type will copy all its value from the specified unit template. All traits can be then further modified later
# gfx_tags = {}
# color = color 										# override primary color in visuals
# modifiers:
#   General Modifiers:
#       morale_damage_taken
#       strength_damage_taken
#       morale_damage_done
#       strength_damage_done
#       supply_weight
#       attrition_loss
#       food_storage_per_strength
#       food_consumption_per_strength
#       movement_speed
#
#   Land Modifiers:
#       max_strength
#       combat_speed
#       initiative
#       frontage
#       combat_power
#       flanking_ability
#       secure_flanks_defense
#
#   Naval Modifiers:
#       transport_capacity
#       maritime_presence
#       crew_size
#       blockade_capacity
#       cannons
#       hull_size
#       anti_piracy_warfare