# Auto Modifiers
#
# Modifiers automatically applied to countries based on specified criteria and scale.
#
# ATTRIBUTES
#
# - category: Modifier category for the modifiers. (default: country - if set must be before any modifiers)
# - type: Scope type for potential_trigger. (default: country - if set must be before potential_trigger )
#
# - icon: icon path for the modifier
# - requires_real: (yes/no) does this auto modifier require a real country
# - potential_trigger: trigger for if the auto modifier will be applied
# - scales_with: evaluates a value to multiply the auto modifier effects by
# - limit: trigger checks to see when the auto modifier can be applied
# - hide_effects: (yes/no) is this a hidden modifier
# - alert: (yes/no) should this modifier show in the alerts when it is active?
# Everything else is the modifiers to be applied