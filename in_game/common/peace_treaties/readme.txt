# script your own peace treaties!
#
# potential = trigger, scope:winner = taker, scope:loser = giver, scope:war = war they're in, scope:target = location/country/province specified
# allow = trigger, scope:winner = taker, scope:loser = giver, scope:war = war they're in, scope:target = location/country/province specified
# effect = effect when the treaty is executed, scope:winner = taker, scope:loser = giver, scope:war = war they're in, scope:target = location/country/province specified
# blocks_full_annexation = yes, prevents the target to be fully annexed when this peace treaty is used
# collate_targets = yes/no, can the targets be combined from all givers (i.e. is the treaty giver agnostic)
# are_targets_exclusive = yes, makes location and province targets exclusive so the treaty can't be combined with cede treaties
# category = country/location/province/area, allows you to put the scripted peace treaty in one of the other categories
# custom_tags = { <strings> }	#A list of custom strings to use to identify that peace treaty
# show_tags_in_ui = yes/no #expose the tags in the tooltips and UI
# select_trigger = can add one of these to allow selection of targets/parameters for the treaty. They get stored in scope:target
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
#						name = localisation name of the title for the selection stage
#						allow_null = yes/no to allow the selection of a null object, can be a trigger to check under what circumstances should null be included / excluded instead
#                       allow_self = yes/no to allow the actor to be added to the list (only works for countries)
#                       move_to_next_section_on_click yes/no should the UI move to the next stage when you click on an item. Usually left to the default yes, but set to no if you have some other UI that will perform that action somewhere else
#						top_widget = links to a widget type in the gui files to show at the top of the list. 
#						bottom_widget = links to a widget type in the gui files to show at the bottom of the list. 
#						column = { data = <column_id> width = <int> icon = <path> show_icon_in_cells = yes/no } adds a column to the UI to search with
#                                these can also be defaulted, see \common\attribute_columns
#                       default_sort = key of the sort you want the selection to default to. With nothing it will default to the first sort column. The columns you have are specified in columns = above, the sort keys for the sorts are in \common\attribute_columns\
#                       none_available_msg_key = key of the localisation used when there are no available targets to choose from (optional)
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
# cost = script value for war score cost, scope:winner = taker, scope:loser = giver, scope:war = war they're in, scope:target = location/country/province specified
# base_antagonism = script value for the max amount of antagonism gained, will be adjusted by various factors per country, scope:winner = taker, scope:loser = giver, scope:war = war they're in, scope:target = location/country/province specified
# antagonism_type = key of a bias type for the antagonism that will be added
# ai_desire = script value for how much the winner wants this treaty, scope:winner = taker, scope:loser = giver, scope:war = war they're in, scope:target = location/country/province specified
# ai_force_add = yes/no - Will AI always try to add this treaty to the offer when possible