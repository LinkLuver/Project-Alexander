# Diseases - model possibility of outbreaks, origins, spreads, resistance, pop deaths, and ends.
#
# potential: simple trigger. if it fails it won't try monthly spawn chance. (scope:disease is the disease)
# monthly_spawn_chance: script value for how likely the disease is to spawn per month (0..1) (scope:disease is the disease)
# spawn: effect to spawn the disease somewhere when we've decided it should spawn. Include a spawn_disease effect here (scope:disease is the disease)
# r0: script value to get the R0 number of the disease, or how many people one person will spread the disease to per interval (root is the location, scope:disease is the disease)
# environmental_infection: script value for how much more disease percentage will be added to the location to spread the disease from the environment (root = location, scope:disease is the disease, scope:disease_outbreak is the specific outbreak, scope:current_presence is the current disease presence)
# calc_interval_days: script value for how long between spread calculations. A lower number = possible faster spread, depending on the effect in spread. Nothing in the scope, this will usually just be a number, but could be a random range (scope:disease is the disease)
# location_stagnation_chance: script value for how much chance there is of the disease stagnating in a location, slowing its advance greatly. (0..1) (root is the location, scope:disease is the disease, scope:disease_outbreak is the specific outbreak, scope:current_presence is the current disease presence in the location)
# sub_unit_stagnation_chance: script value for how much chance there is of the disease stagnating in a sub unit, slowing its advance greatly. (0..1) (root is the sub unit, scope:disease is the disease, scope:disease_outbreak is the specific outbreak, scope:current_presence is the current disease presence in the location)
# percentage_to_meet_their_fate_on_calc: script value for how many of the affected should have their fate decided (live and become resistant, or die) per calc interval (0..1) (scope:disease is the disease, scope:disease_outbreak is the specific outbreak, scope:current_presence is the current disease presence in the location)
# location_modifier: modifier applied to locations that have the disease (multiplied by the presence %age)
# mortality_rate: script value for mortality rate of the disease (0..1) (scope:disease is the disease)
# character_mortality_chance: script value for how likely it is that a character will die per calc interval (0..1) (root is the location, scope:disease is the disease, scope:disease_outbreak is the specific outbreak, scope:current_presence is the current disease presence in the location)
# monthly_resistance_reduction: script value for how much resistance will leak away per month. Default is 0
# location_spread_threshold: script value for the minimum percentage there has to be in a location before it will start spreading to new locations (0..1). (root is the character's location, scope:disease is the disease, scope:disease_outbreak is the specific outbreak, scope:current_presence is the current disease presence in the location)
# on_spread_to_country: event sent when the disease spreads to a country (root is the country, scope:disease is the disease)
# map_color: map color for the disease (root is the location, scope:disease is the disease)
# secondary_map_color: secondary map color (stripes) for the disease (root is the location, scope:disease is the disease)
# specific_pop_type_effect: by default, diseases spread to all pop types equally. This can be adjusted here.
#    e.g. specific_pop_type_effect = { pop_type = nobles multiplier = 0 } if you want the disease to leave all nobles alone. Can also use culture = <> religion = <> religion_group = <> language = <> language_family = <>
#    e.g. specific_pop_type_effect = { religion = catholic multiplier = 2 } if you want the disease to affect catholics double.
#    e.g. specific_pop_type_effect = { multiplier = 0 } if you want the disease not to affect anyone by default, then poke holes in it with allowances as above.
#
# You should also define modifiers:
# local_<disease_tag>_impact_modifier, which you can use on locations to lessen or augment the impact the disease has there. E.g. a hospital might carry local_my_disease_imapct_modifier = -0.9.
# local_<tag>_resistance_modifier: which you can use on locations to increase resistance to the disease there.
# national_<tag>_resistance_modifier: which you can use on countries to increase resistance to the disease there.
# local_<tag>_growth_modifier: which you can use on locations to increase growth of the disease there.
# national_<tag>_growth_modifier: which you can use on countries to increase growth of the disease there.

#spread:
#    no threshold for spreading from a location
#    a disease will not spread to a location if:
#        the destination location is not populated
#        if there's an embargo between the two nations that own the locations
#        if the destination location already has at least 50% presence
#        if the destination location has stagnated
#    disease will spread from a location to (assuming that the above criteria are met):
#        its neighbors (general people movement)
#        its market centre (people going to market)
#        locations it trades with if it's a market centre (merchants going to and from)
#        the location owner's capital (people going to the big city)
