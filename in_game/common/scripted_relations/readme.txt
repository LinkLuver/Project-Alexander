# Scripted relations
# These are relations that can be toggled on or off between countries through diplo actions
#
#<name> = {
#	type = <diplomacy/subject/union> defines if the relation type is something you can have with every country, only with subjects or only with your union partners
#	relation_type = <oneway/mutual> determines if the relationship is a giving/receiving kind or if partners are mutual in the relationship
#   uses_diplo_capacity = <none/mutual/giving/receiving> whether this relation uses a diplo relation slot
#   diplomatic_capacity_cost = <scriptvalue>
#	block_when_at_war = <yes/no> whether we can or can't use this relation while at war
#	break_on_war = <yes/no> ends the relationship if either sides ends up in a war against the other side
#   break_on_becoming_subject = <yes/no> ends the relationship if one side becomes a subject of another country
#   break_on_not_spying = <yes/no> ends the relationship if the perpetrator stops building a spy network in the target country, including if their spy is discovered
#	annulled_by_peace_treaty = <yes/no> does this relationship get cancelled when an "annul treaties" peace treaty between the two countries is executed
#   annullment_favours_required = <integer> number of favours needed to annul this membership diplomatically
#	disallow_war = <yes/no> does this forbid declarations of war between the two countries
#	embargo = <yes/no> does this relationship cause an embargo between the two countries
#   military_access = <yes/no> does this relationship give military access between the two countries (if it's mutual, either way; if it's one way, then the receiver gets the rights)
#   fleet_basing_rights = <yes/no> does this relationship give fleet basing rights between the two countries (if it's mutual, either way; if it's one way, then the receiver gets the rights)
#   food_access = <yes/no> does this relationship give food access between the two countries (if it's mutual, either way; if it's one way, then the receiver gets the rights)
#	is_exempt_from_sound_toll = <yes/no> does this relationship give an exemption from sound tolls
#	is_exempt_from_isolation = <yes/no> does this relationship give exemptions from being isolated from the trade network
#	block_building = <yes/no> does this block the receiver (one way)/both parties (mutual) from building foreign buildings in the other's territory
#	skip_diplomat_for_cancel = <yes/no> do we skip diplomat travel time when cancelling/breaking
#   lifts_fog_of_war = <yes/no> does this relation lift the fog of war in their territory
#	called_in_defensively = <none/mutual/giving/receiving> are calls to arms sent when one party gets war declared on them
#	called_in_offensively = <none/mutual/giving/receiving> are calls to arms sent when one party declares war
#   lifts_trade_protection = <yes/no> is market trade protectionism lifted between the countries
#	trade_to_first = <script value> increases the attraction of the first country's markets in locations belonging to the second country
#	trade_to_second = <script value> increases the attraction of the second country's markets in locations belonging to the first country
#	gold_to_first = <script value> amount of gold that the second country gives the first per month
#	gold_to_second = <script value> amount of gold that the first country gives the second per month
#	favors_to_first = <script value> amount of favors that the second country gives the first per month
#	favors_to_second = <script value> amount of favors that the first country gives the second per month
#	institution_spread_to_first = <script value> amount of institution spread that the second country sends to the first country's capital per month
#	institution_spread_to_second = <script value>amount of institution spread that the first country sends to the second country's capital per month
#	diplomatic_cost = <price> cost to create this relation
#	war_declaration_cost = <price> cost to declare war between the two countries
#	buy_price = <price> cost to buy the relation (if not specified, you can't buy it)
#	monthly_ongoing_price_first_country = <price> monthly cost to maintain the relation for the first country (applies to both if mutual)
#	monthly_ongoing_price_second_country = <price> monthly cost to maintain the relation for the second country in a one way relation
#   select_trigger: can add multiple of these to allow selection of targets/parameters for the action. They get stored in scope:target, scope:target_1, scope:target_2....etc
# 				   PerformGenericAction takes the user through selecting these targets
#				   format: 
#						looking_for_a = character/location/province/area/region/country/value/boolean etc
#						target_flag = what you want to call this target in the scope (e.g. target, target_1, target_province etc.) Then later you'll use this name to reference what was selected here. If left out it will default to target, target_1, target_2, target_3 etc
#						source = actor/recipient/target/target_1/target_2/target_3/target_4/world
#						source_ai_override = actor/recipient/target/target_1/target_2/target_3/target_4 (ai only)
#                       source_flags = options to improve game performance by narrowing down the choice (neighbor/possible_colonial_charters/include_dead/include_any_present/possible_exploration_areas/adjacent_locations/vacant_adjacent_locations/adjacent_provinces/border/border_or_recipients_capital_area/provinces_ai_wants_to_give_away/only_actual_locations)
#                       source_flags_ai_override = options to improve game performance by narrowing down the choice for Ai countries (neighbor/possible_colonial_charters/include_dead/include_any_present/possible_exploration_areas/adjacent_locations/vacant_adjacent_locations/adjacent_provinces/border/border_or_recipients_capital_area/provinces_ai_wants_to_give_away/only_actual_locations)
#		                source_global_list = <name of global variable list with the list of candidates in> if you have a pre calculated global list of who you want in the select_trigger, use this
# 						interaction_source_list = <effect> gives us a list of possible candidates to look at. scope:actor is the country, scope:recipient, scope:target, scope:target_1, scope:target_2....etc. Fill the list with add_to_list = source on the scope object
# 						ai_interaction_source_list = { #Same as above but it is only applied to Ai countries
#                       pre_evaluation_sort_value = optional script value, use this to sort the initial list of possible targets that pass the trigger and select the top X to evaluate fully (use in conjunction with pre_evaluation_number_to_evaluate_fully)
#                       pre_evaluation_number_to_evaluate_fully = integer, number of the top sorted pre-evaluated targets to pass on for full evaluation (use in conjunction with pre_evaluation_sort_value) (AI only)
#                       max_targets_for_ui = integer, number of the top sorted pre-evaluated targets to pass on to the UI for the user to choose from
#                       cache_targets = yes/no if the list of targets will always be the same, i.e. doesn't depend on any other selection, then set this to yes to save processing
#                       cache_interaction_source_list = yes/no if the interaction source list will always be the same, i.e. doesn't depend on any other selection, then set this to yes to save processing
#                       cache_order = yes/no if the list of targets will always be in the same order of how good they are at the task, set this to yes to save processing
#						name = localization name of the title for the selection stage
#						allow_null = yes/no to allow the selection of a null object, can be a trigger to check under what circumstances should null be included / excluded instead
#                       allow_self = yes/no to allow the actor to be added to the list (only works for countries)
#                       move_to_next_section_on_click yes/no should the UI move to the next stage when you click on an item. Usually left to the default yes, but set to no if you have some other UI that will perform that action somewhere else
#						top_widget = links to a widget type in the gui files to show at the top of the list. 
#						bottom_widget = links to a widget type in the gui files to show at the bottom of the list. 
#						column = { data = <column_id> width = <int> icon = <path> show_icon_in_cells = yes/no } adds a column to the UI to search with
#                                these can also be defaulted, see \common\attribute_columns
#                       default_sort = key of the sort you want the selection to default to. With nothing it will default to the first sort column. The columns you have are specified in columns = above, the sort keys for the sorts are in \common\attribute_columns\
#                       none_available_msg_key = key of the localization used when there are no available targets to choose from (optional)
#                       show_why_not_visible = yes/no true to show why a target might not be visible if there are no targets
#                       show_why_not_enabled = yes/no true to show why a target might not be enabled if there are no targets
#                       show_if = { <trigger to see if this stage is needed; scope:actor is the country, scope:recipient, scope:target, scope:target_1, scope:target_2....etc}
#						visible = { <some trigger...root is the object being tested, scope:actor is the country, scope:recipient, scope:target, scope:target_1, scope:target_2....etc> }
#						enabled = { <some trigger...root is the object being tested, scope:actor is the country, scope:recipient, scope:target, scope:target_1, scope:target_2....etc> }
#						selected = { <some trigger...root is the object being tested, scope:actor is the country, scope:recipient, scope:target, scope:target_1, scope:target_2....etc> } tests to see if the target is currently selected
#                       min = <script value> minimum value for value types
#                       max = <script value> maximum value for value types
#                       step = <script value> step value for changing value types in the UI
#                       default = <script value> default value for value types
#						map_mode = <map mode tag> map mode the map will switch to while choosing this target (optional)
# 						map_color = <script color> map color for location (root = location, scope:actor/recipient etc)
#                       only_color_selectable = <yes/no> yes to only think about colouring selectable locations; no to be able to colour any location with the script above
# 						secondary_map_color = <script color> striped map color for location (root = location, scope:actor/recipient etc)
#
#	sound = "<sound gfx>" sound that should play once this relationship is established
#	mutual_color = <color definition> for the diplomacy map mode
#	giving_color = <color definition> for the diplomacy map mode
#	receiving_color = <color definition> for the diplomacy map mode
#
#	visible = <trigger> should the relationship to be visible in the first place
#   offer_visible = <trigger> is offering this relationship available
#   request_visible = <trigger> is requesting this relationship available
#   cancel_visible = <trigger> is cancelling this relationship available
#   break_visible = <trigger> is breaking this relationship available
#	offer_enabled = <triggers> can we offer to establish this relationship (i.e. offer to give the one way relationship) (mutual counts here)
#	request_enabled = <triggers> can we request the relationship (i.e. request to receive the one way relationship)
#	cancel_enabled = <triggers> can we cancel a relationship that is either mutual or is one way that we are giving
#	break_enabled = <triggers> can we break a one way relationship we are receiving
#	will_expire_trigger = <triggers> criteria for this relationship auto-expiring
#   should_ai_offer_trigger = <triggers> if false ai will not consider sending this relation
#
#	wants_to_give = <ai evaluation> - use this one for both mutual and one way relations. Calculation when a request is being evaluated.
#	wants_to_receive = <ai evaluation> - one way relations only. Calculation when an offer is being evaluated.
#	wants_to_give_diplo_chance = <diplo evaluation> - only use this one for mutual and one way relations. Calculation when a request is being evaluated.
#	wants_to_receive_diplo_chance = <diplo evaluation> - one way relations only. Calculation when an offer is being evaluated.
#   wants_to_keep = <ai evaluation> - use this for both mutual and one way relations. If evaluation results in values below or equal 0 ai will try to cancel/break relation
#   wants_to_keep_diplo_chance = <diplo evaluation> - use this for both mutual and one way relations.
#   show_break_alert = <yes/no> - whether the relation should be shown in alert when AI is about to break it
#
#	giving_modifier_scale = <script math> - this is the scale the modifier is applied for the giver, scope:first is the giving country, scope:second is the receiving country
#	receiving_modifier_scale = <script math> - this is the scale the modifier is applied for the receiver, scope:first is the giving country, scope:second is the receiving country
#	mutual_modifier_scale = <script math> - this is the scale the modifier is applied for both sides, scope:first is the giving country, scope:second is the receiving country
#
#	offer_effect = <effects> what happens when an offer is accepted
#	request_effect = <effects> what happens when a request is accepted
#	cancel_effect = <effects> what happens when a relation is cancelled
#	break_effect = <effects> what happens when a relation is broken
#	offer_declined_effect = <effects> what happens when an offer for a relation is declined
#	request_declined_effect = <effects> what happens when an request for a relation is declined
#   expire_effect = <effects> what happens when a relation expires
#
#Ongoing actions - this meta data is used for when you want the relation to show in the ongoing actions area of the diplomacy panel
#Also add a string with _ongoing_tooltip suffix to show when it's hovered over
#   is_ongoing = <yes/no> makes it show up in the ongoing diplomacy area
#   texture_file = <string> texture to use for the icon in the ongoing diplomacy area
#   concept - <string> concept to use in the tooltip (like "annex" or "country")
#	progress = <script value> returns a number between 0 and 100 for how far through the process the ongoing action is (scope:first and scope:second are the countries in the relation)
#}
#
# Modifiers automatically apply for countries that have a scripted relation. These can be specified as follows:
# <key>: modifier added when having a mutual relation
# giving_<key>: modifier added when giving the one-way relation
# receiving_<key>: modifier added when receiving the one-way relation
#
# You can have biases auto-apply for when the relation is operational between two countries.
# opinion_<key>: opinion of a country added when having a mutual relation with them
# opinion_giving_<key>: opinion of a country added when giving the one-way relation to them
# opinion_receiving_<key>: opinion of a country added when receiving the one-way relation from them
# opinion_decline_<key>: opinion of a country added when the relation was declined
# trust_<key>: trust of a country added when having a mutual relation with them
# trust_giving_<key>: trust of a country added when giving the one-way relation to them
# trust_receiving_<key>: trust of a country added when receiving the one-way relation from them
# trust_decline_<key>: trust of a country added when the relation was declined

#################################
# Values used for diplo chances #
#################################
# at_war
# recipient_at_war
# actor_at_war
# recipient_civil_war
# actor_civil_war
# multiple_offensive_wars
# actor_is_rival
# recipient_is_rival
# same_religion
# different_religion
# same_culture
# same_court_language
# same_common_language
# different_culture
# diplomatic_reputation
# culture_war
# opinion
# warscore
# peaceoffer
# peaceoffer_most_of_wanted
# months_at_war
# planning_demise
# conflicting_interests
# max_relations
# actor_max_relations
# capital_distance
# yesman
# defeat
# victory
# has_border
# same_international_organization
# giving_defensive_support
# receiving_defensive_support
# base
# giving_them_access
# in_debt
# cost
# claim
# current_strength
# potential_strength
# relative_strength
# capital
# location_value
# interesting
# vital
# avoided
# stability
# positive_stability
# negative_stability
# war_exhaustion
# low_manpower
# disloyal_subject
# no_action
# separate_peace
# junior_to
# price
# desperation
# war_balance
# war_goal
# making_gains
# on_retreat
# tutorial
# target_opinion
# lacks_border
# another_war
# fighting_together
# border_distance
# province_distance
# revolter
# rank
# rank_difference
# common_threat
# competing_power
# recipient_at_peace
# actor_at_peace
# best_possible_offer
# substantial_land_lost
# last_major_battle
# few_relations
# no_access
# positive_opinion
# negative_opinion
# allied_to_enemy
# enforced_demand
# ai_setting
# has_truce
# has_truce_with_target
# overlord
# my_proposal
# heir
# interest_rate_too_high
# good_interest_rate
# existing_loans_from_country
# too_many_loans
# need_loan
# loan_is_insignificant
# loan_ends_too_soon
# loan_ends_too_late
# using_favors
# unbalanced_favors
# trust_in_actor
# trust_in_recipient
# positive_trust_in_actor
# negative_trust_in_actor
# same_government_type
# different_government_type
# estates_like
# estates_dislike
# culture_view
# religion_view
# royal_ties
# call_for_peace
# war_enthusiam
# want_more
# too_much_antagonism number of countries that will go over the antagonism limit the country is willing to take
# want_something_else
# tax_base
# promised_land
# demands_made
# belongs_to_international_organization
# different_religion_group
# conquer_desire
# produced_goods
# price_percentage_of_treasury_funds
# antagonism
# common_rivals_and_enemies
# common_rivals