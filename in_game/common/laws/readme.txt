# Laws and Policies
#
# A law is a container for one or more policies that may be chosen to fulfill that law. Only one policy can be chosen at once.
#
# ATTRIBUTES
#
# Laws:
# - type: the type of entity that this law applies to (usually a country or international_organization)
# - potential: <trigger> determine if the law can be displayed
# - allow: <trigger> determine if the law can be changed
# - locked: <trigger> to determine if the law is currently locked and cannot be interacted with
# - requires_vote: <yes/no> whether or not passing a policy for this law will require a vote (in international organizations)
# - law_religion_group: <catholic/sunni/...> for laws that are unique for some religion/s
# - law_gov_group: <monarchy/republic/theocracy> for laws that are unique for some government type
# - law_country_goup: <country tag> for laws that are unique for some country
# - unique: <yes/no> Default: no
# - custom_tags = { <strings> }	#A list of custom strings to use to identify that law
# -	show_tags_in_ui = yes/no #expose the tags in the tooltips and UI
# anything else is a tag of a policy that can be chosen for this law
#
# Policies:
# - price: <price> what you have to pay to activate the policy
# - potential: trigger for whether the action is possible (root = country)
# - allow: trigger for whether the action can start (root = country)
# - custom_tags = { <strings> }	#A list of custom strings to use to identify that policy
# -	show_tags_in_ui = yes/no #expose the tags in the tooltips and UI
# - years:
# - months:
# - weeks:
# - days: <ints> all used to define how long it takes to become fully implemented. Modifiers will be scaled by how much of this time is completed.
# - on_pay_price: <effect> fired when the price for the policy must be paid (root = country/IO depending on what you're applying the policy to)
# - on_activate: <effect> fired when the action is chosen (root = country/IO depending on what you're applying the policy to)
# - on_fully_activated: <effect> fired when the action's implementation reaches 100% (instant if there's no time delay) (root = country/IO depending on what you're applying the policy to)
# - on_deactivate: <effect> fired when the action is removed (root = country/IO depending on what you're applying the policy to)
# - international_organization_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for if the modifier applies)> which is applied to whole organization
# - country_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for if the modifier applies)> which is applied to whole countries
# - province_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for if the modifier applies)> which is applied to provinces
# - location_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for if the modifier applies)> which is applied to locations
# - wants_this_policy_bias: <scripted maths> Gets a scripted number determining how much a country will want this policy. Scope changes depending on if it's a policy for a government or an international organization. Government: root = country. IO: root = country, scope:actor = other country, scope:recipient = IO, scope:target = potential target, scope:policy = the policy itself
# - wants_propose_policy: <scripted maths> Gets a scripted number determining how much a country wants to propose this policy for vote. root = country, scope:actor = other country (if the IO doesn't exist yet), scope:recipient = IO, scope:target = potential target, scope:policy = the policy itself
# - wants_keep_policy: <scripted math> Gets a scripted number determining how much the country wants to keep this policy in the IO root = country, scope:actor = other country, scope:recipient = IO, scope:target = potential target, scope:policy = the policy itself
# - reasons_to_join: <scripted math> Determines how much of an impact this particular policy has for countries to join the IO root = country, scope:actor = other country, scope:recipient = IO, scope:target = potential target, scope:policy = the policy itself
# - diplomatic_capacity_cost: <scripted maths> [IO only] how much diplomatic capacity is used by this law in an international organization for each member. root = country, scope:recipient = IO
#
# if the policy is for an international organization, you can also specify the following to override anything already existing in the IO. Newer policies will supersede older policies.
# - international_organization_modifier: <scaled and triggered modifier (scale = script for the scale, potential_trigger = trigger for the modifier applies)> which is applied to the whole international organization as an entity
# - modifier: replaces any modifiers we apply to members (scale - root = country, scope:recipient = organization) These replace any modifiers that came before them. For adding extra modifiers, use country_modifier/province_modifier/location_modifier as above
# - leader_modifier: replaces any modifiers we apply to the leader (scale - root = country, scope:recipient = organization) This replaces any previous leader_modifier
# - non_leader_modifier: replaces any modifiers we apply to every member who is not the leader (scale - root = country, scope:recipient = organization) This replaces any previous non_leader_modifier
# - can_join_trigger: can we join this organization type (root = potential joiner, actor = potential leader, recipient = existing organization if it already exists, target = target if available)
# - can_leave_trigger: can we leave this organization type (root = potential leaver, recipient = existing organization)
# - auto_leave_trigger: trigger to auto-leave this organization type (root = country, scope:recipient contains the international organization)
# - auto_disband_trigger: trigger for when the organization will disband itself and cease to exist (root = international organization)
# - join_defensive_wars_always: do we automatically join defensive wars with a fellow member (root = international organization, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# - join_defensive_wars_auto_call: do we automatically get a call to arms from a fellow member in defensive wars (root = international organization, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# - join_defensive_wars_can_call: do we allow a call to arms from a fellow member in defensive wars (root = international organization, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# - join_offensive_wars_always: do we automatically join offensive wars with a fellow member (root = international organization, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# - join_offensive_wars_auto_call: do we automatically get a call to arms from a fellow member in offensive wars (root = international organization, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# - join_offensive_wars_can_call: do we allow a call to arms from a fellow member in offensive wars (root = international organization, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# - can_declare_war: trigger to determine if war can be declared (attacker = attacker, defender = defender, recipient = international organization)
# - has_military_access: trigger to determine if a country has military access in another. (root = int org, actor = country we want to know about, recipient = country we want to know if they have access in, war = boolean if we should include war access or not)
# - <currency type> = yes/no: whether or not this IO has a treasury containing this type of currency
# - min_opinion = float: every member must have at least this opinion of every other member in the IO. If ont, the IO breaks. Use with caution. In large IOs this can be expensive to calculate.
# - min_trust = float: every member must have at least this much trust in every other member in the IO. If ont, the IO breaks. Use with caution. In large IOs this can be expensive to calculate.
# - antagonism_towards_leader_modifier = float: modifier for the accumulation of antagonism by other members towards the leader
# - antagonism_modifier_for_taking_land_from_fellow_member = float: modifier for antagonism gained through actions within the IO's territory
# - no_cb_price_modifier_for_fellow_member = float: price modifier for no cb wars with other members
# - payments_implemented: list of <payment tag>s of payments implemented with this policy
# - payments_repealed: list of <payment tag>s of payments repealed with this policy
# - special_statuses_implemented: list of <special status tag>s of special statuses implemented with this policy
# - special_statuses_repealed: list of <special status tag>s of special statuses repealed with this policy
# - leader_title_key: string providing the key for the title of the leader (default will just be "Leader"). If we have leader_type = character, then _MALE and _FEMALE will be appended accordingly
# - title_is_suffix: (yes/no) whether or not the title goes at the end of the name
# - leader: <script object> gives us the leader of the organization. scope:recipient is the org.
# - leader_type: (none/country/character) is the leader a country or a person? Default is country
# - leader_change_trigger_type: how does this organization choose a new leader? (none/rulerchange/timed)
# - leader_change_method: how does the leadership change? (rotation/vote/lottery/none)
# - leadership_election_resolution: <resolution key> key of the resolution that corresponds to the voting system for the IO
# - months_between_leader_changes: how many months between leader changes? (if timed...if not, this is ignored)
# - has_leader_country: (yes/no) does this type have a leader country
# - has_parliament = yes/no: whether or not this IO has a parliament system (no by default)
# - can_invite_countries: (yes/no) can this IO invite other countries to join it? (defaults to yes)
# - gives_food_access_to_members: (yes/no) does this IO automatically gives food access to its members (defaults to no)
# - has_dynastic_power = yes/no: whether this IO can be subject to influential dynasties within it, used for IOs which work with land ownerships
