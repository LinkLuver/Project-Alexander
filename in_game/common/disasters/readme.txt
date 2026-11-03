# Disasters
#
# custom_description: <string> key for a custom description loc in customizable_localization
# monthly_spawn_chance: script value for how likely the disease is to spawn per month (0..1) (root = country, scope:disaster is the disaster)
# modifier: modifier applied to a country that has this disaster ongoing
# can_start: trigger to see if the disaster can start (root = country, scope:disaster = disaster type)
# can_end: trigger to see if the disaster should end (root = country, scope:disaster = disaster type)
# on_start: effect fired when the disaster starts (root = country, scope:disaster = disaster type)
# on_monthly: effect fired each month that the disaster is ongoing (root = country, scope:disaster = disaster type)
# on_end: effect fired when the disaster ends (root = country, scope:disaster = disaster type)
# map_mode: <map mode tag> optional link to the map mode to show while looking at this disaster
# fire_only_once: yes/no - whether or not the disaster can occur multiple times to the same country

