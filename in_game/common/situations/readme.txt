# Situations
#
#
#
# monthly_spawn_chance: script value for how likely the disease is to spawn per month (0..1) (scope:situation is the situation)
# international_organization_type = <international_organization_type_tag> IO type associated with the situation
# resolution = <resolution_tag> a specific resolution that the situation references
# voters = <global_list_tag> list of people eligible to vote in the resolution above
# can_start = <trigger> can the situation start now (root = situation)
# can_end = <trigger> can the situation end (root = situation)
# visible = <trigger> can the player country see the situation and participate in it (root = country, scope:target = situation)
# on_start = <effect> effect when the situation starts, used for general set up (root = situation)
# on_monthly = <effect> effect every month (root = situation)
# on_ending = <effect> effect when the situation ends, just before its status changes (root = situation)
# on_ended = <effect> effect when the situation ends, just after its status changes (root = situation)
# tooltip = <effect> used to generate a tooltip for the map, not actually executed (root = location, scope:target = situation)
# map_color = <script color> map color for location (root = location, scope:target = situation)
# secondary_map_color = <script color> striped map color for location (root = location, scope:target = situation)
