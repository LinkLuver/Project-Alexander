# Expedition Types
#
# Each file defines one or more expedition types (CExpeditionType). Expeditions are
# country-owned, character-led voyages that follow an ordered path of waypoints and run
# on_start / on_monthly / on_arrive_to_new_location / on_arrive_to_waypoint / on_end /
# on_fail effects.
#
#
# unique (optional)
# -----------------
# Whether only one instance of this expedition type may be active for a country at a time.
#
#   unique = yes
#
# Valid values: yes, no (default no).
#
#
# repeatable (optional)
# ----------------------
# Whether the same country can launch this expedition type again after a previous instance
# has completed successfully.
#
#   repeatable = no
#
# Valid values: yes (default), no.
#
#
# returns_home (optional)
# ------------------------
# Auto-appends a return leg back to the origin after the last waypoint is reached.
#
#   returns_home = yes
#
# Valid values: yes, no (default no).
# With static waypoints, the return leg reverses that waypoints list then appends the
# origin, and on_arrive_to_waypoint fires again at each waypoint on the way back - guard
# one-shot flavor with a has_variable flag. A fully dynamic type (no static waypoints) gets
# a direct engine-pathfound leg straight home instead, with no waypoints on that leg at all;
# use on_arrive_to_new_location for return-leg content in that case.
#
# The engine only appends this leg automatically when should_end_at_last_waypoint = yes
# (the default). With should_end_at_last_waypoint = no, script must start the trip home itself
# with expedition_return_home - see that field below.
#
#
# dynamic_first_waypoint (optional)
# -----------------------------------
# The first waypoint is injected in on_start via add_new_waypoint instead of being
# pre-declared in a static waypoints list.
#
#   dynamic_first_waypoint = yes
#
# Valid values: yes, no (default no).
# Required whenever a type has no static waypoints at all (a fully dynamic route, e.g. a
# player-chosen destination): the path starts empty, and the first add_new_waypoint call in
# on_start becomes the departure location, not a route step. Pick it explicitly in script
# (e.g. the country's best-development owned port) rather than relying on origin, and pair
# it with origin = none.
#
#
# waypoints (optional)
# ---------------------
# Ordered static waypoint list, referencing named location keys.
#
#   waypoints = {
#       cape_of_good_hope
#       calicut
#   }
#
# Omit entirely for a fully dynamic route built at runtime with add_new_waypoint.
#
#
# origin (optional)
# ------------------
# Departure point for the expedition.
#
#   origin = closest_non_rural_port
#
# Valid values: capital, closest_owned, closest_port, closest_non_rural_port, none.
# Resolves against the type's first static waypoint. With no static waypoints declared,
# every mode except none falls back to the country's capital, which may not even be
# reachable under the type's travel_mode. Use origin = none together with
# dynamic_first_waypoint = yes for a fully dynamic path.
#
#
# travel_speed (optional)
# -------------------------
# Scalar multiplier on the base travel time for every leg.
#
#   travel_speed = 0.75
#
# Valid values: any positive number (default 1). Below 1 is slower, above 1 is faster.
#
#
# potential (optional)
# ----------------------
# UI visibility trigger (country scope). Controls whether the expedition type is shown to
# the player at all, separately from whether it can currently be launched.
#
#   potential = {
#       religion.group = religion_group:muslim
#       has_ruler = yes
#   }
#
#
# can_start (optional)
# -----------------------
# Launch gating trigger (country scope), checked when the player tries to start the
# expedition.
#
#   can_start = {
#       at_war = no
#   }
#
#
# leader (optional)
# --------------------
# Which character may lead the expedition (character scope).
#
#   leader = {
#       is_explorer = yes
#   }
#
# Common leader requirements: is_ruler, is_explorer, is_admiral, is_adult, is_heir_of_court_country.
#
#
# fail_if_no_leader (optional)
# ------------------------------
# Whether the expedition automatically fails once it no longer has a living leader (the
# leader died, or was cleared by script).
#
#   fail_if_no_leader = yes
#
# Valid values: yes, no (default no). Checked every expedition tick, whatever the
# expedition is currently doing - traveling, sitting in port, paused, or in deviation.
# Failing runs the type's on_fail and posts the EXPEDITION_FAILED message, and does NOT set
# the completion flag, so a repeatable = no type can be launched again afterwards. Author an
# on_fail block: with none the player is told the expedition was lost but nothing about what
# it cost or salvaged.
#
# Leave it at no (or omit it) and the voyage does NOT stop when its leader dies: the engine
# appoints a replacement - a newly created explorer, abilities rolled just under the dead
# leader's - and fires the on_expedition_leader_replaced on_action so the player is told who
# took over. Set it to yes only when losing the leader should end the attempt outright.
#
# A type may still run its own succession flow off ON_CHARACTER_DEATH (see
# common/on_action/character_death_pulses.txt) and appoint a successor with
# set_expedition_leader. That wins automatically: the engine only steps in when the expedition
# has no usable leader by the time the expedition tick runs, and the character on_action is
# processed earlier in that same tick.
#
#
# should_end_at_last_waypoint (optional)
# ---------------------------------------
# Whether reaching the final path entry completes the expedition.
#
#   should_end_at_last_waypoint = no
#
# Valid values: yes (default), no. With yes the expedition runs on_end and terminates the
# moment it arrives. Use no when the route is discovered as it goes and an event decides where
# to head next.
#
# An expedition ALWAYS either has a next waypoint or is over - there is no idle state. So with
# no, by the time on_arrive_to_waypoint returns the script must have either added a waypoint
# with add_new_waypoint, ended the run with end_expedition, started the trip home with
# expedition_return_home (returns_home types only), or called pause_expedition to buy itself
# time (which is what an event awaiting a player decision does). Anything else is a
# content bug: the engine fails the expedition and ERRORLOGs the type, owner and location.
# When the pause lapses the same check runs again, so a pause is a deadline, not a parking spot.
#
# expedition_return_home = scope:expedition
# For a returns_home type, starts the trip back to the origin instead of ending the run - a
# no-op if the type is not returns_home, or the expedition is already on its way back. Once
# home, on_arrive_to_waypoint fires again there: that handler must itself call end_expedition
# (guard with scope:expedition = { expedition_is_returning = yes }) to actually terminate the
# run and fire on_end - should_end_at_last_waypoint = no means the engine never does this for
# you, at the origin any more than anywhere else.
#
# The trap to avoid is a one-shot latch plus an event that might not fire:
#
#   set_variable = { name = city_revealed value = 1 }   # latched, so arrival cannot retry
#   trigger_event_non_silently = my_events.30           # whose trigger can evaluate false
#
# If that trigger fails, nothing adds a waypoint and the run is over. Make sure every waypoint
# the expedition can reach is handled by some branch - including the LAST one, and including
# any waypoint added dynamically such as a leg home.
#
# Waiting on a player decision, not a known duration: pause_expedition needs a duration up
# front, which means guessing how long a player will take to answer. stall_expedition holds an
# expedition indefinitely instead, with no deadline at all, until script calls resume_expedition
# on it - typically from the immediate of whichever event option lets the voyage continue:
#
#   # on_arrive_to_waypoint
#   stall_expedition = scope:expedition
#   trigger_event_non_silently = my_events.10
#
#   # every option of my_events.10 that should let the voyage continue
#   option = {
#       name = my_events.10.a
#       scope:expedition = { add_new_waypoint = location:chosen_destination }
#       resume_expedition = scope:expedition
#   }
#
# stall_expedition and resume_expedition are callable from any scope, with the target
# expedition passed as the value (scope:expedition), the same way end_expedition and
# fail_expedition already work - not written inside scope:expedition = { ... } like
# pause_expedition. expedition_is_stalled checks the state from script (e.g. an on_monthly
# guard). Because a stall has no built-in deadline, it reopens exactly the failure mode the
# no-idle-state invariant exists to prevent if the deciding event can ever fail to fire or
# resolve without acting: every option of that event must call resume_expedition (paired with
# add_new_waypoint, end_expedition, or fail_expedition) - there is no automatic FailWithExhausted
# Path backstop for a stall the way there is for a lapsed pause_expedition deadline.
#
# triggers_regency (optional)
# ------------------------------
# Whether a leading ruler causes a regency at home for the duration of the expedition.
#
#   triggers_regency = yes
#
# Valid values: yes, no (default no). Only relevant when leader can resolve to the ruler.
#
#
# show_start_message (optional)
# --------------------------------
# Whether launching the expedition through the start_expedition generic action pops up the
# "Expedition launched!" notification.
#
#   show_start_message = no
#
# Valid values: yes (default), no. Set to no when the type's on_start immediately shows its
# own event or notification at the departure waypoint, so the player does not see both at once.
# The confirmation sound still plays either way; only the popup is suppressed. Has no effect on
# types launched through their own dedicated generic action (e.g. pilgrimage_action,
# chinese_treasure_voyages) - those show that action's own message instead.
#
#
# show_end_message (optional)
# ------------------------------
# Whether successfully completing the expedition pops up the generic "Expedition Returns"
# notification.
#
#   show_end_message = no
#
# Valid values: yes (default), no. Set to no when the type's on_end immediately triggers its
# own event, so the player does not see both at once - the generic popup's body already
# previews the on_end effect (including the event trigger itself), so the event's own popup
# right after it is a pure duplicate. Has no effect on the EXPEDITION_FAILED message shown by
# on_fail.
#
#
# utility (optional)
# ---------------------
# Script value that scores this expedition type for the AI's auto-launch decisions. Higher
# values make the AI more likely to launch this expedition type over others. Expedition types with values lower or equal to zero
# won't be picked.
#
#   utility = {
#       value = 5
#       if = {
#           limit = { any_character = { has_trait = zealot } }
#           add = 3
#       }
#   }
#
#
# category (optional)
# -------------------
# Thematic classification used only for presentation (UI grouping, section headers, and
# per-category iconography). It has NO gameplay effect.
#
#   category = commercial
#
# Valid values: exploration (default), commercial, military, religious, diplomatic.
# Each value has a display-name loc "expedition_category_<value>" in
# expedition_types_l_english.yml. The UI reads it via ExpeditionType.GetCategoryKey.
#
#
# travel_mode (optional)
# ----------------------
# Restricts which domains the pathfinder may route the expedition through:
#
#   travel_mode = sea
#
# Valid values: both (default), land, sea.
# - both: land and sea, no restriction.
# - land: overland only (caravans, embassies, surveys).
# - sea:  open water only, EXCEPT the destination of each leg. Because a port behaves as
#         land, the leg endpoint is always reachable, so a sea-only fleet can still dock at
#         its port waypoints; only land transit between ports is forbidden.
#
# A leg whose endpoint cannot be reached within the chosen domain (e.g. an inland waypoint
# under sea) fails pathfinding and ERRORLOGs about a failed expedition path - the signal to
# fix the waypoint list or the mode. Leave it at the default both unless every leg of the
# route stays in one domain.
#
#
# ai_leader_source_list (optional)
# ------------------------------------
# Tells AI countries which characters to check as potential leaders. Improves performance and chances of a successful check.
# If left empty AI will consider only a fraction of available characters but will get through all of them eventually. Scope = country
#
#   ai_leader_source_list = {
#       ruler = {
#           add_to_list = source
#       } 
#   }
#
# leader_utility (optional)
# ------------------------------------
# Script value that scores characters for this expedition type for the AI's auto-launch decisions. Higher
# values make the AI more likely to use this character in this expedition type. Characters with utility lower or equal to zero won't be picked. 
#
#   leader_utility = {
#       value = 5
#       if = {
#           limit = { is_ruler = yes }
#           add = -100
#       }
#   }
#
# ai_chance_to_check (optional)
# ------------------------------------
# Script value that represents chances AI will check this expedition in a given month. Values are capped between 0 and 1.
# Value is optional, when none is given the EXPEDITION_DEFAULT_CHANCE_TO_CHECK define will be used.
#
#   ai_chance_to_check = {
#       value = 0.05
#       if = {
#           limit = { any_character = { has_trait = zealot } }
#           add = 0.1
#       }
#   }
#
# ai (optional)
# ------------------------------------
# Whether AI should consider using this expedition at all. Default is yes, use it only to disable certain
# expeditions for AI countries.
#
#   ai = no
# variables (optional)
# ----------------------
# A set of named saved variables tracked on the expedition and shown as typed rows in the
# expedition tooltip's "Expedition Status" section (name + value, plus a monthly-change breakdown
# when one applies). Each entry:
#
#   variables = {
#       morale = {
#           start = 100                    # initial value, seeded when the expedition launches
#           min = 0                        # display range floor
#           max = 100                      # display range ceiling
#           icon = "gfx/interface/..."     # optional DDS shown beside the value (blank if unset)
#           display = piechart             # optional; piechart = radial gauge, fraction = "X/max" chip, omitted = plain value
#           format = "SOME_FORMAT"         # optional loc key controlling how the value is shown
#           change_format = "SOME_FORMAT"  # optional loc key for the monthly-change display
#           monthly_change = { ... }       # optional scripted value applied and clamped each month
#           hidden = no                    # optional; yes hides the variable from the tooltip
#           monthly_change_hidden = no     # optional; yes hides the monthly-change line
#       }
#   }
#
# The variable name is the same key used by set_variable / change_variable / clamp_variable /
# var: on scope:expedition, so declaring it here is purely additive - existing script that
# reads or writes the variable keeps working, and start replaces an on_start set_variable for
# the initial value. Each declared variable needs a "<name>" and "<name>_desc" localization
# entry (e.g. morale, morale_desc).
#
# start seeds the value when the expedition is created, before on_start runs, so on_start can
# still override it. Omitting start on a value variable leaves it unset until script sets it.
#
# monthly_change is applied and clamped to min/max every month. The change script evaluates in
# the running expedition's own scope, so it can read the expedition's var: values and travel
# state directly - e.g. subtract while expedition_is_traveling = yes, or when var:provisions < 50.
# (This differs from situations/disasters, whose monthly_change runs in TYPE scope.)
#
#
# Lifecycle hooks
# ------------------
# All fire in country scope, with scope:expedition available; arrival hooks also provide
# scope:location.
#
# on_start: at launch - the place to set_variable trackers, inject dynamic waypoints,
#   pause_expedition, schedule kickoff events.
# on_monthly: every month while active - runtime flavor (storms, pirates). Guard with
#   scope:expedition = { expedition_is_traveling = yes } if the flavor should only fire
#   while actually traveling (a paused expedition keeps Traveling status - also add
#   NOT = { scope:expedition = { expedition_is_paused = yes } } if a pause, e.g. a port
#   stay, must suppress it too).
# on_arrive_to_new_location: every entry into a new location, on both the outbound and (for
#   returns_home) the return leg - fires for every step of a fully dynamic path, not just
#   declared waypoints (e.g. discover_location).
# on_arrive_to_waypoint: at every waypoint (static or dynamically added via
#   add_new_waypoint) - branch on scope:location for per-stop content. Does not fire on the
#   engine-built returns_home leg unless the type also has static waypoints.
# on_end: successful completion - rewards, cargo delivery, homecoming events.
# on_fail: fires when script calls fail_expedition = scope:expedition, and - only for types
#   with fail_if_no_leader = yes - when the expedition loses its living leader. Without that
#   field the engine never fails an expedition on its own: a dead leader keeps sailing, still
#   shown as leader, until the type's own script reacts. on_start variables persist if the
#   expedition fails, so clean them up here as well as in on_end.
# on_construction_finished: fires when a start_expedition_wait_construction construction at
#   the expedition's current location completes - the resume point after the wait. Like
#   on_arrive_to_waypoint, script here must add_new_waypoint, end_expedition, fail_expedition,
#   or pause_expedition/start_expedition_wait_construction again; the no-idle-state invariant
#   above applies here too.
#
# Related script pieces: effects add_new_waypoint = location:x, pause_expedition = <days>,
# start_expedition_wait_construction = { duration = <days> goods_demand = <key> } (goods_demand
# optional; creates a construction at the expedition's current location - unlike
# pause_expedition its actual finish date can move with goods stalling/queue position, so it is
# a separate, orthogonal wait mechanism, not a replacement), clear_expedition_waypoints,
# set_expedition_leader (reassigns the leader on an active
# expedition), fail_expedition, end_expedition, expedition_return_home (returns_home types
# only - starts the trip home instead of ending the run); triggers expedition_is_traveling,
# expedition_is_in_port, is_expedition_leader, expedition_is_returning (true once the engine
# has appended the returns_home leg), expedition_is_paused (true for the duration of any
# pause_expedition window, including the initial departure pause), expedition_is_waiting_on_
# construction (true while a start_expedition_wait_construction construction is unresolved);
# data refs expedition_leader, expedition_current_location (scope link to the expedition's
# current location).
#
#
# Hidden waypoints (mystery destinations)
# ----------------------------------------
# add_new_waypoint also accepts a block form with an optional hidden field:
#
#   add_new_waypoint = { location = location:x hidden = yes }
#
# A hidden waypoint behaves exactly like an ordinary dynamic waypoint for every scripted
# purpose - on_arrive_to_waypoint still fires, it still counts toward the no-idle-state
# invariant, it still shapes the pathfound route - but its identity is masked everywhere the
# player would otherwise see it: the lateral view's route list, the expedition tooltip's
# waypoint list, current-location line, and next-waypoint line, and the map marker's hover
# (which reuses the same tooltip). The route bar still shows the stop - as a masked "???"
# entry, not omitted - so the voyage never looks broken or finished early.
#
# Masking is presentation-only. on_arrive_to_waypoint, scope:location, and any event or
# custom_tooltip text the type's own script writes at that stop can still name the location
# explicitly - the engine does not stop content from spoiling its own mystery, so a "sail into
# the unknown" type should keep on_arrive_to_waypoint content generic (no location name in the
# text) until the point where the design wants to reveal it, typically on_end.
#
# The bare scalar form (add_new_waypoint = location:x) is unaffected and always non-hidden.
#
#
# Waypoint messages (notification, not an event)
# ----------------------------------------------
# To show a plain notification when the expedition reaches a defined (static) waypoint,
# add a localization entry following this convention:
#
#   <expedition_type_key>_waypoint_<named_location_key>
#
# Example: a circumnavigation expedition reaching cape_of_good_hope uses the loc key
# circumnavigation_expedition_waypoint_cape_of_good_hope.
# If that key exists, a non-popup EXPEDITION_WAYPOINT message is posted (log + on-map) when
# the fleet arrives there. No script and no event are required; the message exists if and
# only if the loc key exists. Inside the string the EXPEDITION and LOCATION data refs are
# available (e.g. the location name and expedition variables).
#
# Notes:
# - Only static waypoints (the waypoints list) are matched by key; dynamic waypoints added
#   at runtime via add_new_waypoint have no script key and so cannot use this convention.
#   For those, fire a message/event from on_arrive_to_waypoint instead.
# - The message only shows for the human player who owns the expedition.
#
#
# Outcome overview (optional)
# ----------------------------
# A short, hand-written incentive line shown in the Start tooltip, describing in general
# terms what starting the expedition can lead to (its concrete outcome cannot be previewed,
# since it depends on how the expedition ends). Add:
#
#   <expedition_type_key>_outcome_overview: "This expedition can improve your stability and
#   bring in some money, depending on your choices."
#
# The block only appears if this loc key exists; leave it unauthored to omit it.
