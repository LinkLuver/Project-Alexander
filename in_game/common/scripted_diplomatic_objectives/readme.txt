#<name> = {
#   #How many days to wait before checking for new objectives again
#   ai_tick_frequency = <int/script value>
#   
#   #ROOT = actor
#   actor_trigger = { }
#
#   #scope:recipient = potential country, scope:actor = actor
#   recipient_trigger = { }
#
#   #scope:recipient = potential country, scope:actor = actor
#   #Used when sorting which countries and objectives should be prioritized, is used to compare with other scripted objectives as well
#   recipient_priority = <float/scripted value>
#
#   #Used to narrow down potential countries, if not present all reachable countries will be used
#   recipient_list_builder = { <list builder> }
#
#   #Used to check if an objective should be paused until the next check. Can be used to avoid deleting objectives in cancel_trigger
#   #scope:recipient = potential country, scope:actor = actor
#   pause_trigger = { }
#
#   #Used to check if an objective should be canceled prematurely
#   #scope:recipient = potential country, scope:actor = actor
#   cancel_trigger = { }
#
#   #Should the nations improve relations
#   improve_relation = <yes/no>
#   #To which opinion should the country improve relations, optional, if not present AI will improve up to max
#   improve_relations_limit = <int/scripted value>
#   #Should the actor try to defend the recipient
#   defensive_support = <yes/no>
#   #Should the actor use hostile country interactions/relations against the recipient
#   antagonise = <yes/no>
#   #Should the actor try to destroy recipient
#   destroy = <yes/no>
#
#   #Yes to encourage, No to disable
#   country_interactions = {
#       <country interaction> = <yes/no>
#   }
#   #Yes to encourage, No to disable and cancel if possible
#   country_relations = {
#       <country relation> = <yes/no>
#   }
#   
#   #How much time does the actor have to complete an objective before cancelling, leave empty or 0 for unlimited time
#   #scope:recipient = potential country, scope:actor = actor
#   time_limit = <days/scripted value>
#
#   #How many objectives of the same type can a nation have at once. Leave 0 for unlimited. Default is unlimited.
#   #ROOT = actor
#   max_allowed = <int/scripted value>
#
#}