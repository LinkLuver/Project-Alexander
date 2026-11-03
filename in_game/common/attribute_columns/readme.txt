# Attribute columns for different object types. This allows you to specify how columns will work for when you're using a select_trigger in generic actions or country/character interactions.
#
# This is the action script. In addition to adding an action here, you'll need strings for the name (tag is the <action_tag>) and description (tag is <action_tag>_desc)
#
# <column_tag> = {} choose a unique column tag
#   format: 
#       widget = links to a widget type in the gui files. This widget will be given an InteractionTarget to get data from, which is the object you're selecting, so you can use InteractionTarget.GetCountry if it's a country, InteractionTarget.GetCharacter etc
#       width = the default column width
#       fixed_height = the height of the widget if it's fixed. allow for performance optimization when displaying a lot of items.
#       is_constant_width = yes/no by default yes, but setting to no allows this column to soak up any remaining column width
#       contains_select_target_button = yes/no set this if your widget includes the select_target_button so we don't create a dupliacte
#       single_widget_for_row = yes/no set this if you're using one widget for the entire row so we can get errors if more columns are accidentally specified
#       sort = {} you can add 0..n sort headers for each column. Format is:
#           sort_key = a unique key for the sort column
#           sort_text = scripted text for getting the text to sort the column by. Text has access to all the scope variables that the rest of the script has, so root is the object being selected, then others like scope:actor, scope:recipient, scope:target etc are available
#           sort_value = scripted value for getting the value to sort the column by. Script has access to all the scope variables that the rest of the script has, so root is the object being selected, then others like scope:actor, scope:recipient, scope:target etc are available
#           * You'll need EITHER sort_text for text columns OR sort_value for numeric columns
#           sort_by_tooltip_key = the text to show in the tooltip for the sort headers
