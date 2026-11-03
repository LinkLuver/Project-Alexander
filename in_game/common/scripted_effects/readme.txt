# Here you can define any kind of scripted effect which then can be used globally in the script
# my_simple_effect = {
#     <list of effects>
# }
#
# Usage in other parts of the script: my_simple_effect = yes
#
# For more advanced usages, you can use custom arguments by having certain key in $s
# Example:
# my_argument_effect = {
#     add_prestige = $value$
# }
# Usage: my_argument_effect = { value = 12 }
#
# Works with scopes too!
# my_scoped_effect = {
#     $target$ = {
#         add_prestige = $value$
#     }
#     take_over_all_wars = $target$
# }
# Usage: my_scoped_effect = { target = scope:my_scope value = 13 }
#
# Arguments are text replacements, which also means you can create effects à la:
# my_argumented_effect_hello = { add_stability = 5 }
# my_argumented_effect = { my_argumented_effect_$type$ = yes }
#
# Usage: my_argumented_effect = { type = hello }
#
# !!Be careful when using this type of effects though, the error log will complain a lot about missing effects when the argument is used wrongly!!
#
# Quick note about the usage of custom_description and scripted effects:
# Due to how the engine works, using the same key for the effect and the custom description
# will result in custom_description becoming unable to pick up subject/object/value
# As such it is highly advised to have the key of the custom_description a different one than the effect itself
# So do NOT write
# my_effect = { custom_description = { text = my_effect object = <whatever> } }
# But instead write
# my_effect = { custom_description = { text = my_effect_text object = <whatever> } }