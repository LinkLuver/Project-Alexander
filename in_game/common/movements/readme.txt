# Movements - model thoughts and ideas travelling through the population through of outbreaks, origins, spreads, resistance
#
# potential: simple trigger. controls whether the movement appears in the UI at all (and is therefore eligible to spawn). Should basically only be used for has_dlc gates. (scope:movement_definition is the movement)
# allow: simple trigger. if it fails the movement won't try monthly spawn chance, but will still appear in the UI. Use this for "is the world ready for this movement to spawn yet" checks. (scope:movement_definition is the movement)
# monthly_spawn_chance: script value for how likely the movement is to spawn per month (0..1) (scope:movement_definition is the movement)
# spawn: effect to spawn the movement somewhere when we've decided it should spawn. Include a spawn_movement effect here (scope:movement_definition is the movement)
# r0: script value to get the R0 number of the movement, or how many people one person will spread the movement to per interval (root is the location, scope:movement_definition is the movement)
# environmental_infection: script value for how much more movement will be added to the location to spread the movement from individual spreaders of the movement (root = location, scope:movement_definition is the movement)
# calc_interval_days: script value for how long between spread calculations. A lower number = possible faster spread, depending on the effect in spread. Nothing in the scope, this will usually just be a number, but could be a random range (scope:movement_definition is the movement)
# location_spread_threshold: script value for the minimum percentage there has to be in a location before it will start spreading to new locations (0..1). (root is the character's location, scope:movement_definition is the movement)
# on_spread_to_country: event sent when the movement spreads to a country (root is the country, scope:movement_definition is the movement)
# on_calc_effect: effect called on a calc day. root = movement
# map_color: map color for the movement (root is the location, scope:movement_definition is the movement)
# secondary_map_color: secondary map color (stripes) for the movement (root is the location, scope:movement_definition is the movement)
# custom_name: scripted link to a custom string key in ../customizable_localization/ . also loc keys in customizable_localization can use script with ROOT = movement

# required_languages: pops need one of these languages to be affected by the movement. ignored if empty.
# required_language_families: pops need one of these language families to be affected by the movement. ignored if empty. works with required_languages - if both are specified, pops only need to match one of the languages OR one of the language families
# required_tags: pops need to belong to one of these countries (has_or_had_tag logic) to be affected by the movement. ignored if empty.
# required_religions: pops need to belong to one of these religions to be affected by the movement. ignored if empty.
# required_religion_groups: pops need to belong to one of these religion groups to be affected by the movement. ignored if empty. works with required_religions - if both are specified, pops only need to match one of the religions OR one of the religion groups
# required_pop_types: pops need to belong to one of these pop types to be affected by the movement. ignored if empty.
# required_cultures: pops need to belong to one of these cultures to be affected by the movement. ignored if empty.

# specific_pop_type_effect: by default, movements do not spread. Set who they spread to here.
#    e.g. specific_pop_type_effect = { pop_type = nobles multiplier = 1 } if you want the movement to affect nobles. Can also use culture = <> religion = <> religion_group = <> language = <> language_family = <>
#    e.g. specific_pop_type_effect = { religion = catholic multiplier = 2 } if you want the movement to affect catholics double.
#    e.g. specific_pop_type_effect = { multiplier = 1 } if you want the movement to affect everyone normally by default.
# location_modifier: modifier applied to locations that have the movement (multiplied by the presence %age)
# religion: optional religion we're spreading. You have to specify this OR culture
# culture: optional culture we're spreading. You have to specify this OR religion

# development = neutral/positive/negative.  Whether development of a location is a positive or negative multiplier on the spread to pops. neutral default 
# literacy = neutral/positive/negative. Whether literacy is a positive or negative multiplier on the spread to pops. neutral default 
# local_control = neutral/positive/negative. Whether local control of a location is a positive or negative multiplier on the spread to pops. neutral default 
# pop_satisfaction = neutral/positive/negative. Whether satisfaction of a pop is a positive or negative multiplier on the spread to pops. neutral default 

# You should also define modifiers:
# local_<tag>_resistance_modifier: which you can use on locations to increase resistance to the movement there.
# national_<tag>_resistance_modifier: which you can use on countries to increase resistance to the movement there.
# global_<tag>_resistance_modifier: which you can use on the movement itself.
# local_<tag>_growth_modifier: which you can use on locations to increase growth of the movement there.
# national_<tag>_growth_modifier: which you can use on countries to increase growth of the movement there.
# global_<tag>_growth_modifier: which you can use on the movement itself.

#spread:
#    no threshold for spreading from a location
#    a movement will not spread to a location if:
#        the destination location is not populated
#        if there's an embargo between the two nations that own the locations
#        if the destination location already has at least 50% presence
#        if the destination location has stagnated
#    movement will spread from a location to (assuming that the above criteria are met):
#        its neighbors (general people movement)
#        its market centre (people going to market)
#        locations it trades with if it's a market centre (merchants going to and from)
#        the location owner's capital (people going to the big city)
