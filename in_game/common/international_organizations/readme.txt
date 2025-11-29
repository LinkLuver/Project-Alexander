# International Organization
#
# A group of countries that have joined together for some reason, with an optional target country of the organization.
#
# In addition to the following attributes, automatic opinion and trust of fellow members is applied.
# - io_opinion_<key>: opinion of other members automatically applied
# - io_trust_<key>: trust towards other members automatically applied
#
# ATTRIBUTES
#
# - should_show_ruler_history: <yes/no> to show the ruler/leader history button in the IO view
# - background_texture: <path to texture> picture to show in the background on the IO panel. Defaults to DEFAULT_IO_BACKGROUND_PATH
# - show_strength_comparison_with_target: (yes/no) to show the strength comparison between IO and target in the UI
# - declare_war_on_target_casus_belli: <casus belli tag> CB used to declare war on the target from the IO page
# - has_target: (yes/no) does this type have a target country
# - has_leader_country: (yes/no) does this type have a leader country (defaults to no)
# - potential_target_trigger: are we close to becoming a target of this organization type (root = potential enemy)(used for alerts in the ui)
# - create_visible_trigger: can we see a diplo action to create these? (root = potential creator) (defaults to yes)
# - create_enabled_trigger: is the option to create these enabled? (root = potential creator) (defaults to yes)
# - invite_visible_trigger: can we see a diplo action to invite people to join? (root = potential inviter, scope:recipient = IO, scope:target = target if applicable) (defaults to yes)
# - invite_enabled_trigger: is the diplo action to invite people to join enabled? (root = potential inviter, scope:recipient = IO, scope:target = target if applicable) (defaults to yes)
# - join_visible_trigger: can we see a diplo action to join the IO? (root = potential inviter, scope:recipient = IO, scope:target = target if applicable) (defaults to yes)
# - join_enabled_trigger: is the diplo action to join enabled? (root = potential inviter, scope:recipient = IO, scope:target = target if applicable) (defaults to yes)
# - can_target_trigger: can we become a target of this organization type (root = potential enemy)
# - has_enemies: (yes/no) does this type allow enemies to target it
# - can_be_enemy_trigger: can we become an enemy of this organization type (root = potential enemy, recipient = existing organization)
# - unique: (yes/no) is there only one of these organizations in existence
# - expel_members_who_are_targets_of_other_members: (yes/no) come on.
# - expel_members_who_target_the_leader: (yes/no)
# - expel_members_who_are_attackers_at_war_with_other_members: (yes/no)
# - expel_members_who_are_defenders_at_war_with_other_members: (yes/no)
# - override_ruler_title: (yes/no) yes if this title should be more important than any country titles a ruler has; no if it should be displayed after country titles (for character leaders).
# - leader_title_key: string providing the key for the title of the leader (default will just be "Leader"). If we have leader_type = character, then _MALE and _FEMALE will be appended accordingly
# - title_is_suffix: (yes/no) whether or not the title goes at the end of the name
# - leader: <effect> gives us the leader(s) of the organization. This is primarily "who is displayed at the top of the Union UI" and leader countries will normally exist under the hood, unless explicitly not set through has_leader_country = no (which is default). root is the org. Fill the list with add_to_list = leaders on the scope object
# - leader_type: (none/country/character) is the leader a country or a person? Default is country
# - use_regnal_number: <yes/no> if it's a character, do we use regnal numbers?
# - leader_change_trigger_type: how does this organization choose a new leader? (none/rulerchange/timed)
# - leader_change_method: how does the leadership change? (rotation/vote/lottery/score/none)
# - leadership_election_resolution: <resolution key> key of the resolution that corresponds to the voting system for the IO
# - months_between_leader_changes: how many months between leader changes? (if timed...if not, this is ignored)
# - can_lead_trigger: can we lead this organization type (root = potential leader)
# - leader_score: a dynamic script value which determines who should lead the IO in case leader_change_method = score (root = potential leader, recipient = existing organization)
# - disband_if_no_leader: (yes/no) disband the IO if no leader can be found either in the vote or because nobody is eligible (defaults to yes)
# - max_active_resolutions <integer>: max number of resolutions that can be active at once
# - custom_name: scripted link to a custom string key in ../customizable_localization/ . also loc keys in customizable_localization can use script with ROOT = IO, location = Seat of IO
# - land_ownership_rule: optional land ownership rules for the organization (in folder international_organization_land_ownership_rules)
# - show_on_diplomatic_map: yes/no, should we show this organization on the diplomatic map
# - show_as_overlord_on_map_trigger: <optional> trigger. if your game settings allow it, this IO will show its own color and name as an overlord on the regular political map. root = member country; scope:recipient = IO 
# - show_leave_message: <yes/no> show a message when a country leaves the IO (default to yes)
# - use_laws_as_join_reason: <yes/no> ai countries will consider the laws and policies the IO has enacted as reasons to join (default to yes)
# - disband_message_trigger: <optional> trigger which allows the disband message to only appear when the triggers are fulfilled. root = IO, actor = instigator (optional)
# - map_color_override: <optional> returns a color that will override any of the color options below like leader_color, member_color etc if you want to overlay anything. root = location, scope:recipient = IO
# - secondary_map_color_override: <optional> returns a color that will override any of the striped color options like owned_location_color, member_color etc if you want to overlay anything. root = location, scope:recipient = IO
# - tooltip: <optional> returns a loc key that will show the tooltip for the location. root = location, scope:recipient = IO
# - leader_color: <optional> color of the leader on the diplomatic map
# - member_color: <optional> color of members on the diplomatic map
# - target_color: <optional> color of target on the diplomatic map
# - diplomatic_capacity_cost: (script value) how much diplomatic capacity is used by this IO. root = country, scope:recipient = IO
# - subject_limited: (yes/no) is creation and maintenance of these IOs limited when it's a subject with limited diplomacy? (defaults to yes)
# - can_invite_countries: (yes/no) can this IO invite other countries to join it? (defaults to yes)
# - gives_food_access_to_members: (yes/no) does this IO automatically gives food access to its members (defaults to no)
# - on_creation: effect when the organization gets created (root = international organization, actor = creator (optional), target = target (optional))
# - on_disband: effect when the organization gets disbanded (root = international organization)
# - on_joined: effect when a country has joined (root = country, scope:recipient = existing organization, scope:target contains target if allowed)
# - on_left: effect when a country has left (root = country, scope:recipient = existing organization, scope:target contains target if allowed)
# - monthly_effect: effect performed every monthly tick (root = international organization)
# - variables: list of variables attached to this organization. 
#       <var name> = {
#           format = <string> how you want this variable to be displayed
#           change_format = <string> how you want monthly changes to this variable to be displayed
#           monthly_change = <scripted value> how this variable changes per month
#           start = <script> initial value when the organization is created
#           min = <float> min value if it's a number
#           max = <float> max value if it's a number
#		    hidden = <yes/no> if we want to display this var to the world
#		    monthly_change_hidden = <yes/no> if we want to display any monthly change of this var to the world
#       }
# - special_statuses_implemented: list of <special status tags>s of special statuses implemented initailly when setting up the international organization. Special statuses are from the international_organization_special_statuses folder. Tehy can also be added or repealed using laws and policies.
# - payments_implemented: list of <payment tag>s of payments implemented initially when setting up the international organization. Payments are from the international_organization_payments folder. They can also be added or repealed using laws and policies.
# - ai_desire_to_join: how much the AI wants to join the org (root = potential joiner, actor = potential leader, recipient = existing organization if it already exists, target = target if available)
# - ai_desire_to_allow_new_member: how much the AI wants to accept a new member (root = international organization, actor = potential new member, target = target if available)
# - modifier: modifiers we apply to members (scale - root = country, scope:recipient = organization)
# - leader_modifier: modifiers we apply to the leader (scale - root = country, scope:recipient = organization)
# - non_leader_modifier: modifiers we apply to every member who is not the leader (scale - root = country, scope:recipient = organization)
# - international_organization_modifier: modifiers which are applied on the international organization as a base (root = organization)
# - can_join_trigger: can we join this organization type (root = potential joiner, actor = potential leader, recipient = existing organization if it already exists, target = target if available)
# - can_leave_trigger: can we leave this organization type (root = potential leaver, recipient = existing organization)
# - auto_leave_trigger: trigger to auto-leave this organization type (root = country, scope:recipient contains the international organization)
# - auto_disband_trigger: trigger for when the organization will disband itself and cease to exist (root = international organization, scope:target (optional) = against who)
# - join_defensive_wars_always: do we automatically join defensive wars with a fellow member (root = international organization, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# - join_defensive_wars_auto_call: do we automatically get a call to arms from a fellow member in defensive wars (root = international organization, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# - join_defensive_wars_can_call: do we allow a call to arms from a fellow member in defensive wars (root = international organization, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# - join_offensive_wars_always: do we automatically join offensive wars with a fellow member (root = international organization, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# - join_offensive_wars_auto_call: do we automatically get a call to arms from a fellow member in offensive wars (root = international organization, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# - join_offensive_wars_can_call: do we allow a call to arms from a fellow member in offensive wars (root = international organization, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# - only_leader_country_joins_defensive_wars = yes/no: Default: no, when calling to war defensively do we consider all members or just the leader, improves performance of big IOs
# - only_leader_country_joins_offensive_wars = yes/no: Default: no, when calling to war offensively do we consider all members or just the leader, improves performance of big IOs
# - can_declare_war: trigger to determine if war can be declared (attacker = attacker, defender = defender, recipient = international organization)
# - has_military_access: trigger to determine if a country has military access in another. (root = int org, actor = country we want to know about, recipient = country we want to know if they have access in, war = boolean if we should include war access or not)
# - gives_military_access_to_all_when_at_war = yes/no: optimized has_military_access, if any war member is part of the IO, everyone in the war gets access to the IO, use this for higher performance
# - fleet_basing_rights: trigger to determine if a country has fleet basing rights in another. (root = int org, actor = country we want to know about, recipient = country we want to know if they have access in, war = boolean if we should include war access or not)
# - can_recruit_regiments_in_members = yes/no: whether members can recruit regiments in locations owned by other members
# - can_build_ships_in_members = yes/no: whether members can build ships in locations owned by other members
# - can_build_roads_in_members = yes/no: whether members can build roads in locations owned by other members
# - can_build_buildings_in_members = yes/no: whether members can build buildings in locations owned by other members
# - can_build_rgos_in_members = yes/no: whether members can build rgos in locations owned by other members
# - opinion_bonus = float: additional opinion bonus applied to all members
# - opinion_trust = float: additional trust bonus applied to all members
# - can_initiate_policy_votes: trigger to determine if a country can initiate votes on policies in the IO. (root = country, recipient = IO)
# - <currency type> = yes/no: whether or not this IO has a treasury containing this type of currency
# - min_opinion = float: every member must have at least this opinion of every other member in the IO. If ont, the IO breaks. Use with caution. In large IOs this can be expensive to calculate.
# - min_trust = float: every member must have at least this much trust in every other member in the IO. If ont, the IO breaks. Use with caution. In large IOs this can be expensive to calculate.
# - antagonism_towards_leader_modifier = float: modifier for the accumulation of antagonism by other members towards the leader
# - antagonism_modifier_for_taking_land_from_fellow_member = float: modifier for antagonism gained through actions within the IO's territory when both you and the country you're antagonising are in the IO
# - antagonism_modifier_for_taking_land_from_member_as_outsider = float: modifier for antagonism gained through actions within the IO's territory when you're not a member but the country you're antagonising is
# - no_cb_price_modifier_for_fellow_member = float: price modifier for no cb wars with other members
# - has_parliament = yes/no: whether or not this IO has a parliament system (no by default)
# - parliament_type = <parliament_type>: defines the parliament type this IO uses by default, no effect if has_parliament = no, only utilizes parliament_type which are defined for IOs
# - resolution_widget = <key of widget to toggle>: define what widget should be toggled if the player clicks on the resolutions to vote alert
# - has_dynastic_power = yes/no: whether this IO can be subject to influential dynasties within it, used for IOs which work with land ownerships
# - allow_member_annexation = yes/no: whether this IO allows members to diplomatically annex each other regardless of being subjects or not
# - annexation_min_years_before = <integer script value>: the amount of years a member needs to be in the IO before they can be annexed. root = annexer, scope:target = country to be annexed, scope:recipient = IO
# - can_annex_members: what conditions must be fulfilled before a member can start diplomatically annex another one. root = annexer, scope:target = country to be annexed, scope:recipient = IO
# - annexation_speed: defines how long it takes for organization members to annex each other
# - ai_issue_voting_bias = <script value>: script value used as extra reasoning in resolutions, used in conjunction with the ai_issue_voting_bias trigger
#
# available scripts for the scope of international organization: 
# TRIGGERS
# - total_members: number of members
# - total_enemies: number of enemies
# - any_international_organization_member: goes through all members of the organization. Can use "count = <x>" as the first line to count how many pass the following trigger or "percent = <x>" to test the percentage of members that pass the following trigger
# - any_international_organization_enemy: goes through all enemies of the organization. Can use "count = <x>" as the first line to count how many pass the following trigger or "percent = <x>" to test the percentage of members that pass the following trigger
# - any_international_organization_owned_location: lists all locations owned by the organization. Can use "count = <x>" as the first line to count how many pass the following trigger or "percent = <x>" to test the percentage of locations that pass the following trigger
# - is_international_organization_unique: checks if the organization is unique
# - location_can_be_added_to_international_organization: tests if the supplied location can be added to the organization
# - location_can_be_removed_from_international_organization: tests if the supplied location can be removed from the organization
# - law_visible_to_international_organization: tests if the supplied law can be seen by the organization
# - law_enabled_to_international_organization: tests if the supplied law can be enacted by the organization
# - policy_visible_to_international_organization: tests if the supplied policy can be seen by the organization
# - policy_enabled_to_international_organization: tests if the supplied policy can be enacted by the organization
# - international_organization_can_own_land: returns true if the organization can own land
# - international_organization_type: checks if the organization is of the supplied type
# - has_international_organization_modifier: checks if the scoped international organization has a given modifier
# - has_elections: checks if the organization has elections
# - has_special_status_available: checks if the organization has a particular special status available for countries
# - country_has_special_status { type = special_status:<> country = <> }: checks if the supplied country has a particular special status in the scope organization
# - leader_type: checks if the organization uses either character, country or none as leader type
# - leader_change_method: checks if the organization uses either rotation/vote/lottery/score/none as method
# - leader_change_trigger_type: checks if the organization uses either none/rulerchange/timed as trigger
# - months_between_leader_changes: checks if the time between elections for the organization is the integer. Can use all the normal operators
# EFFECTS
# - international_organization_member (every/random/ordered): lists all members of the organization
# - international_organization_owned_location (every/random/ordered): lists all locations owned by the organization
# - add_country_to_international_organization: adds a country to the organization
# - remove_country_from_international_organization: removes a country from the organization
# - add_enemy_to_international_organization: adds an enemy to the organization
# - remove_enemy_from_international_organization: removes an enemy from the organization
# - add_location_to_international_organization: adds a location to an organization
# - remove_location_from_international_organization: removes a location from an organization
# - add_policy_to_international_organization: enacts a policy in an organization
# - remove_policy_from_international_organization: removes a policy from an organization
# - international_organization_chooses_new_leader: organization chooses a new leader according to its own process
# - international_organization_add_special_status { type = special_status:<> country = <> }: bestows a special status on a country in the organization
# - international_organization_remove_special_status { type = special_status:<> country = <> }: removes a special status from a country in the organization
# - add_international_organization_modifier: add a modifier to an international organization { name = name days/months/years=x mode = add/extend/replace/add_and_extend <size = x> }
# - remove_international_organization_modifier: remove the named modifier from an international organization
# LINKS
# - target: links to the target of the organization
# - leader: links to the leader of the organization
# - leadership_election_resolution: links to the resolution used to elect the leader of the organization
# - international_organization:<type_tag>: sets the scope to the international organization of the supplied unique type (doesn't work for non-unique types as there could be more than one of them)
#
# available scripts for country scope:
# TRIGGERS
# - international_organizations_member_of (all/any): lists all organizations a country is a member of
# - international_organizations_target_of (any/all): lists all organizations a country is a target of
# - is_member_of_international_organization_of_type: checks to see if a country is a member of an organization of the supplied type
# - is_member_of_international_organization: checks to see if a country is a member of an organization
# - is_enemy_of_international_organization: checks to see if a country is an enemy of an organization
# - has_special_status_in_international_organization { type = special_status:<> international_organization = <> }: checks to see if a country has a type of special status in an organization
# - can_lead_international_organization: checks to see if a country can lead the organization
# - country_can_join_international_organization: checks to see if the scope country can join the supplied organization
# EFFECTS
# - international_organizations_member_of (every/random): lists all organizations a country is a member of
# - international_organizations_target_of (every/random): lists all organizations a country is a target of
# - create_international_organization: creates a new organization and scope into it
#
# available scripts for location scope:
# TRIGGERS
# - is_owned_by_international_organization: checks to see if the location is owned by the supplied organization