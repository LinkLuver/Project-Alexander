# Here you can define any kind of scripted trigger which then can be used globally in the script
# my_simple_trigger = {
#     <list of triggers>
# }
#
# Usage in other parts of the script: my_simple_trigger = yes
#
# For more advanced usages, you can use custom arguments by having certain key in $s
# Example:
# my_argument_trigger = {
#     prestige = $value$
# }
# Usage: my_argument_trigger = { value = 12 }
#
# Works with scopes too!
# my_scoped_trigger = {
#     $target$ = {
#         prestige = $value$
#     }
#     is_enemy_of = $target$
# }
# Usage: my_scoped_trigger = { target = scope:my_scope value = 13 }
#
# Arguments are text replacements, which also means you can create triggers à la:
# my_argumented_trigger_hello = { always = no }
# my_argumented_trigger = { my_argumented_trigger_$type$ = yes }
#
# Usage: my_argumented_trigger = { type = hello }
#
# !!Be careful when using this type of triggers though, the error log will complain a lot about missing triggers when the argument is used wrongly!!
#
# Quick note about the usage of custom_description and scripted triggers:
# Due to how the engine works, using the same key for the trigger and the custom description
# will result in custom_description becoming unable to pick up subject/object/value
# As such it is highly advised to have the key of the custom_description a different one than the trigger itself
# So do NOT write
# my_trigger = { custom_description = { text = my_trigger object = <whatever> } }
# But instead write
# my_trigger = { custom_description = { text = my_trigger_text object = <whatever> } }