# Government actions! Stuff you can get your cabinet to do.
#
# all modifiers are multiplied by 1 + (effective ability + cabinet efficiency)*0.05 (CABINET_ACTION_SKILL_MODIFIER in defines)
#
# ability: monarch ability that this action will use (adm/dip/mil)
# is_finished: trigger for whether the action is completed (root = country, scope:target = province)
# select_trigger = can add multiple of these to allow selection of targets/parameters for the action. They get stored in scope:target, scope:target_1, scope:target_2....etc
#				   format: 
#						looking_for_a = character/location/province/area/region/country/value/boolean etc
#						target_flag = what you want to call this target in the scope (e.g. target, target_1, target_province etc.) Then later you'll use this name to reference what was selected here. If left out it will default to target, target_1, target_2, target_3 etc
#						source = actor/recipient/target/target_1/target_2/target_3/target_4
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
# allow_multiple: flag for whether we can have several of these actions going on at once (yes/no)
# societal_values: amount to change a societal value by
# potential: trigger for whether the action is possible (root = country)
# allow: trigger for whether the action can start (root = country)
# years:
# months:
# weeks:
# days: <ints> all used to define how long it takes to become fully implemented. Modifiers will be scaled by how much of this time is completed.
# progress: <script value> returns the current progress of the action
# on_activate: <effect> fired when the action is chosen (root = cabinet, scope:actor = country, scope:target, scope:target_1 etc)
# on_fully_activated: <effect> fired when the action's implementation reaches 100% (instant if there's no time delay) (root = cabinet, scope:actor = country, scope:target, scope:target_1 etc)
# on_deactivate: <effect> fired when the action is removed (root = cabinet, scope:actor = country, scope:target, scope:target_1 etc)
# country_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for if the modifier applies)> which is applied to whole countries
# province_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for if the modifier applies)> which is applied to provinces
# location_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for if the modifier applies)> which is applied to locations
# ai_will_do = effect script for the AI to use, scope:actor is the country, scope:recipient, scope:target, scope:target_1, scope:target_2....etc
