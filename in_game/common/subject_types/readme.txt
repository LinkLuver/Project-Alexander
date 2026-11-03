# SUBJECT TYPES
#
# visible = <trigger> is this subject type visible at all. root = overlord, target = subject
# enabled = <trigger> is this subject type enabled at all. root = overlord, target = potential subject
# visible_through_diplomacy = <trigger> is this subject type visible through diplomacy in general (additional to visible). root = overlord, target = subject
# enabled_through_diplomacy = <trigger> is this subject type enabled through diplomacy (additional to enabled). root = overlord, target = potential subject
# visible_through_treaty = (optional) <trigger> is this subject type visible to be offered in a peace treaty (additional to visible). root = overlord, target = subject, recipient = peace offer recipient, war = current war
# enabled_through_treaty = (optional) <trigger> is this subject type enabled in a peace treaty (additional to enabled). root = overlord, target = potential subject, recipient = peace offer recipient, war = current war
# creation_visible = <trigger> can this subject type be created in general. root = overlord
# subject_creation_enabled = <trigger> can a new province or building subject be released with this subject type. root = overlord, target_province = potential geography for location- or region- based subject types
# release_country_enabled = <trigger> can the potential overlord create released countries as this subject type. root = overlord, target = potential subject
# can_attack = <trigger> can this subject type offered diplomatically in general. root = subject type, overlord = overlord, subject = subject, attacker = attacker, defender = defender
# can_rival = <trigger> can this subject type offered diplomatically in general. root = subject type, overlord = overlord, subject = subject, actor = country wanting to do the rivalling, recipient = country they want to rival
# can_marry = <trigger> can this subject type offered diplomatically in general. root = subject type, overlord = overlord, subject = subject, actor = country wanting to do the marrying, recipient = country they want to marry into
# minimum_opinion_for_offer = <int> how good the subject's opinion of the overlord must be beforethis subject type can be offered to a potential subject
# type = <location/pop/building/army> type of country that is valid for this subject type
# overlord_modifier = <modifier> modifiers given to the overlord country
# subject_modifier = <modifier> modifiers given to the subject country
# great_power_score_transfer = <float> multiplier for how much of the subject's great power score gets added to the overlord
# government = <government key> government type for the subject on creation
# on_enable = <effect> what happens when the subject type is created. root = subject, future_overlord = overlord
# on_disable = <effect> what happens when the subject type is broken. root = subject, former_overlord = overlord
# on_monthly = <effect> what happens to the subject each month. root = subject
# level = <int> what level this subject type has. Generally, subjects of lower levels have more autonomy than subjects of higher level; rule of thumb: level 3 is subjects for annexation, level 0 subjects are subjects in name
# can_be_annexed = <yes/no> mark if the subject type can be annexed in the first place. default: yes
# annexation_speed = <float script value> how fast annexation progresses per month. root/scope:actor = annexer, scope:target = country to be annexed, default: 1
# annexation_min_years_before = <int> how many years the subject must have had this relation before they can be annexed
# annexation_min_opinion = <int> how good the subject's opinion of the overlord must be before annexation can take place
# annexation_stall_opinion = <int> how good the subject's opinion of the overlord must be before the annexation process is halted
# subject_pays = <price> How much the subject pays to the overlord each month
# join_offensive_wars_always = <trigger> does one country automatically join offensive wars with the other (root = subject type, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# join_offensive_wars_auto_call = <trigger> does one country automatically get a call to arms from the other in offensive wars (root = subject type, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# join_offensive_wars_can_call = <trigger> does one country allow a call to arms from the other in offensive wars (root = subject type, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# join_defensive_wars_always = <trigger> does one country automatically join defensive wars with the other (root = subject type, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# join_defensive_wars_auto_call = <trigger> does one country automatically get a call to arms from a other in defensive wars (root = subject type, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# join_defensive_wars_can_call = <trigger> does one country allow a call to arms from a other in defensive wars (root = subject type, scope:actor = caller, scope:recipient = callee, scope:target (optional) = against who)
# can_attack = <trigger> can one of the countries in the relation attack a particular country (root = subject type, scope:overlord = overlord in the relation, scope:subject = subject in the relation, scope:attacker = country that wants to attack (will be either overlord or subject), scope:defender = country they want to attack)
# has_overlords_ruler = <yes/no> whether or not the subject has the overlord's ruler as their ruler. This will make the subject leave its union and put in a regency if the overlord has not a ruler at the moment the subject gets created
# has_overlords_religion = <yes/no> whether or not the subject has the overlord's religion as their religion.
# has_limited_diplomacy = <yes/no> whether or not the subject's diplomacy options are limited by the overlord
# can_change_rank = <yes/no> whether or not the subject can change their country rank
# can_change_heir_selection = <yes/no> whether or not the subject can change their heir selection method
# diplomatic_capacity_cost_scape = <float> multiplier on formula (not a scriptvalue due to checked so much)
# subject_can_cancel = <yes/no> whether or not the subject can cancel the relationship themselves
# overlord_can_cancel = <yes/no> whether or not the overlord can cancel the relationship themselves
# will_join_independence_wars = <yes/no> whether or not the subject can join independence wars
# fleet_basing_rights = <yes/no> whether or not the subject gives fleet basing rights to the overlord
# food_access = <yes/no> whether or not the subject gives food access to the overlord
# use_overlord_laws = <yes/no> whether or not the subject gives uses the same set of laws and policies as the overlord
# on_overlord_becomes_a_subject = <cancel_subjects/transfer_subjects/nothing> what happens to this subject when its overlord itself becomes a subject of another country. cancel_subjects = release subject as independent; transfer_subjects = move subject to the new top overlord (downgrading to vassal if the subject type conditions fail); nothing = default, subject stays under the old overlord as a sub-subject. default: nothing
# annulled_by_peace_treaty = <yes/no> whether this subject type gets broken / becomes unavailable when treaties get annulled, default: yes
# annullment_favours_required = <integer> number of favours needed to annul this membership diplomatically
# allow_declaring_wars = <trigger> whether or not the subject can declare their own wars. (root = subject type, scope:attacker = subject trying to declare war, scope:defender = country they are trying to declare war on)
# use_overlord_map_color = <yes/no> whether the subject shows in the same color as the overlord on the map
# use_overlord_map_name = <yes/no> whether the subject shows in the same name as the overlord on the map
# only_overlord_culture = <yes/no> whether or not the subject must have as its culture the overlord's culture
# only_overlord_or_kindred_culture = <yes/no> whether or not the subject must have as its culture the overlord's culture or one of its kindred cultures
# only_overlord_court_language = <yes/no> whether or not the subject must have as its court language the overlord's court language
# can_overlord_recruit_regiments = <yes/no> whether or not the overlord can recruit regiments in the subjects territory.
# can_overlord_build_ships = <yes/no> whether or not the overlord can build ships in the subjects ports.
# can_overlord_build_roads = <yes/no> whether or not the overlord can build roads in the subjects land
# can_overlord_build_buildings = <yes/no> whether or not the overlord can build buildings in the subjects locations
# can_overlord_build_rgos = <yes/no> whether or not the overlord can build rgos in the subjects locations
# overlord_share_exploration = <yes/no> whether or not the overlord will share their exploration or not
# overlord_protects_external = <yes/no> whether or not the overlord will protect the subject from external attackers, defaults to yes
# overlord_protects_other_subjects = <yes/no> whether or not the overlord will protect the subject from internal attackers (such as other subjects), defaults to no
# counts_as_external = <yes/no> whether or not that subject type is seen as an external threat if it attacks other subjects of their overlord, in which case the overlord will consider overlord_protects_external against them, defaults to no
# can_be_force_broken_in_peace_treaty = <yes/no> can this subject type be demanded to be broken in a peace treaty
# overlord_can_enforce_peace_on_subject = <yes/no> can the overlord demand that the subject leave any wars they're in
# war_score_cost = <script_value> how much will this subject cost to establish in wars, modifies the base war score cost calculation
# base_antagonism = <script_value how much max antagonism will this subject create when established in wars, will override values calculated by the code unless the value is 0 or less
# monthly_favor_gain = <script_value favors gained by a country in the relationship. root = country we want the favors for, scope:overlord, scope:subject. This is in addition to the favors they gain from the relative strength of the two countries.
# diplo_chance_accept_subject = <list of tag = values> multiplier for various values for the overlord/subject comparison that lead to the overall acceptance of an offer to become this type of subject. E.g. border_distance = -0.1 will give -0.1 points towards acceptance per unit of distance between the countries' borders.
# diplo_chance_accept_overlord = <list of tag = values> multiplier for various values for the overlord/subject comparison that lead to the overall acceptance of an offer to become this type of overlord. E.g. border_distance = -0.1 will give -0.1 points towards acceptance per unit of distance between the countries' borders.
# ai_wants_to_be_overlord = effect script for the AI to use, can use scope:overlord and scope:subject, how much the AI country will want to be an overlord of this type. Used when trying to create a subject, picking subject peace treaties or releasing nations as subjects
# ai_wants_to_be_subject = effect script for the AI to use, can use scope:overlord and scope:subject, how much the AI will want to become a subject of this type. Used when offering to become a subject

# institution_spread_to_overlord = <script_value> how fast do embraced institutions spread from the Subject to the Overlord Capital?
# institution_spread_to_subject = <script_value> how fast do embraced institutions spread from the Overlord to the Subject Capital?

