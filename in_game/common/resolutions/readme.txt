# International Organization Resolution system - create a resolution entirely in script and place a GUI button for it entirely in script - no need for coders!
#
# This is the resolution script. In addition to adding a resolution here, you'll need strings for the name (tag is the <action_tag>) and description (tag is <action_tag>_desc)
#
# - loc <string>: [optional] base loc key for everything to do with this resolution (if not specified, it will be the resolution key)
# - potential <trigger>: can this be shown. scope:actor is the country attempting to perform the action
# - allow <trigger>: is this enabled. scope:proposer is the country attempting to initiate the action; scope:recipient is the international organization
# - can_vote <trigger>: can actor vote. scope:actor is the country testing if it can vote or not; scope:recipient is the international organization
# - is_live <trigger>: is this resolution active. Used for elections mainly. If a resolution is live, then it will be tested to see if it can be finalized.
# - proposal_price <scriptedprice>: listed in \common\prices\ and referenced by name (like price:<price_id>) or as a result of a script (like scope:target.price)
# - proposal_price_modifier <script value>: multiplies the price; scope:actor is the country, scope:recipient, scope:target, scope:target_1, scope:target_2....etc
# - proposal_payer <scripted country>: script to determine who is paying the price. By default, the proposer
# - proposal_payee <scripted country>: script to determine who gets paid. By default, nobody, the price disappears into the ether
# - price <scriptedprice>: listed in \common\prices\ and referenced by name (like price:<price_id>) or as a result of a script (like scope:target.price)
# - price_modifier <script value>: multiplies the price; scope:actor is the country, scope:recipient, scope:target, scope:target_1, scope:target_2....etc
# - payer <scripted country>: script to determine who is paying the price. By default, the proposer
# - payee <scripted country>: script to determine who gets paid. By default, nobody, the price disappears into the ether
# - requires_vote <trigger>: returns yes if this resolution must be voted on, no if it can be actioned unilaterally
# - requires_explicit_votes <yes/no>: does this require all votes to be explicitly set or do we just take the current opinion (basically, we use this for elections as they happen all of a sudden and we don't need to go through waiting for all countries to cast votes explicitly)
# - votes <scripted value>: value script to get the number of votes each country has. scope:actor is the country we're calculating a score for; scope:proposer is the proposer country; scope:recipient, scope:target, scope:target_1, scope:target_2....etc
# - total_votes_needed <scripted value>: [optional] value script to get the voting threshold for winning the vote. scope:actor is the country we're calculating a score for; scope:proposer is the proposer country; scope:recipient, scope:target, scope:target_1, scope:target_2....etc
# - should_finalize_vote <trigger>: determines if the vote should be finalized right now. Before this trigger is run, any deadline is checked, deadlines take precedence over this trigger. Additional parameters are available here - scope:total_votes_needed is the total votes needed to win (if that is specified), scope:total_votes_available is the total number of votes that can be cast, and highest_vote is the total of whoever has the current highest vote. These can be used to implement voting thresholds.
# - select_trigger: can add multiple of these to allow selection of targets/parameters for the action. They get stored in scope:target, scope:target_1, scope:target_2....etc
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
# NOTE: The last select_trigger is what countries will vote on.
# - show_message = no, optional, to prevent messages showing
# - ai_will_select <scripted value>: script for the AI to use for how much it wants to propose a vote for whatever, scope:actor is the country we're calculating a score for; scope:recipient is either the situation or international organization this resolution applies to - depending on the looking_for_a definition, scope:target, scope:target_1, scope:target_2....etc
# - ai_will_do <scripted value>: script for the AI to use for how much it wants to vote for whatever, scope:actor is the country we're calculating a score for; scope:proposer is the proposer country; scope:recipient is either the situation or international organization this resolution applies to - depending on the looking_for_a definition, scope:target, scope:target_1, scope:target_2....etc
# - ai_proposer_risk <scripted value>: script for the AI to use for how much it doesn't want a resolution to be rejected, scope:actor is the country we're calculating a score for; scope:proposer is the proposer country; scope:recipient, scope:target, scope:target_1, scope:target_2....etc
# - ai_tick_frequency <scripted value>: script to determine how often this action should be checked for each country. scope:actor is the country. This is just a per-country check.
# - years:
# - months:
# - weeks:
# - days: <ints> all used to define how long until a resolution must be finalized. When the expiry date is reached, all AI countries will automatically vote.
# - vote_ongoing_modifier <modifier>: modifiers applied to the member countries while a vote is ongoing
# - propose_effect <effect>: what happens when the resolution is proposed; scope:proposer is the proposer country, scope:recipient, scope:target, scope:target_1, scope:target_2....etc
# - effect <effect>: what happens when the resolution is passed, scope:proposer is the proposer country, scope:recipient, scope:target, scope:target_1, scope:target_2....etc plus scope:price/scope:price_modifier/scope:payer/scope:payee returns the price details
# - reject_effect <effect>: what happens when a resolution is rejected, scope:proposer is the proposer country, scope:recipient, scope:target, scope:target_1, scope:target_2....etc
# - vote_effect <effect>: what happens when a country votes in the resolution; scope:actor = the voter country, scope:proposer is the proposer country, scope:active_resolution is the resolution, scope:vote is the vote, scope:recipient, scope:target, scope:target_1, scope:target_2... etc
# - abstain_effect <effect>: what happens when a country removes its vote in the resolution; scope:actor = the voter country, scope:proposer is the proposer country, scope:active_resolution is the resolution, scope:recipient, scope:target, scope:target_1, scope:target_2... etc
# - cooldown = { type = <any tag> days/weeks/months/years = <integer> } adds a cooldown for the action during which time it cannot be performed again
# - show_target_in_tooltip = <yes/no>. Set to <yes> to display target of the resolution in UI elements that support it. By default, <no>
#
# To use the action in GUI script, use this sort of thing:
#
#action_button_default = {
#	title = "<optional title for action tooltip>"
#	description = "<optional description for action tooltip. By default, uses the generic action description>"
#	effects = "<optional description of the effects for action tooltip. By default, uses the generic action effects but you can override>"
#	conditions = "<optional description of the conditions for action tooltip. By default, uses the generic action trigger but you can override>"
#	root = "[GUI script to get the country that is contemplating the action]"
#	actor = "[GUI script to get the country that is proposing/voting on the action]"
#   proposer = "[GUI script to get the country that proposed the action]"
#	recipient = "[<GUI script to get the recipient of the action>]"
#	target = "[<GUI script to get the target of the action>]"
#   target = ... (you can add as many targets as you want in case the action has several)
#	left_action = "<id of the action to perform with a click of the left button>"
#	left_click_and_hold_action = "<id of the action to perform with a click and hold of the left button>"
#	right_action = "<id of the action to perform with a click of the right button>"
#	right_click_and_hold_action = "<id of the action to perform with a click and hold of the right button>"
#}
#
# Useful triggers/effects:
# - resolution:<key> - scopes to the resolution
# - any_active_resolution - list for international organization scope, a list of all resolutions currently being voted on
# - set_vote = { 
#       resolution = <resolution>
#       voter = <country>
#       vote = <whatever they want to vote for from the last select_trigger>
#   } - sets a vote for a country
#
# As for message types that get sent to the player, the format is as follows. At the very least, the generic version should be provided. If the more specific ones are available, they will be used.
# Generic catch-all message: PERFORM_ + Key + _ACTION e.g. PERFORM_do_some_stuff_ACTION
#
# These are added as message types in gui/messagetypes.txt.
#
# The text for them needs to be added as localizations. There are plenty of examples, all the localizations use the stem of the action type as the basis for the localization key.
#
# When the player does the action: WE_PERFORM_ + Key + _ACTION e.g. WE_PERFORM_throw_tomatoes_ACTION
# When another country does it: OTHER_PERFORMS_ + Key + _ACTION e.g. OTHER_PERFORMS_rain_dance_ACTION
# When another country does it to us: ACTION_ + Key + _PERFORMED_ON_US e.g. ACTION_declare_war_PERFORMED_ON_US
#
# In the strings for these messages, in addition to being able to use the scope variables in the strings, you can use the following presets:
# $ACTION$ - the name of the action
# $EFFECT$ - the effect of the action
# $DESC$ - the action description (<action_tag>_desc)