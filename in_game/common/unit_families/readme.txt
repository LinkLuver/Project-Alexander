#P:A TODO Review imported vanilla file (1.4.7)
# Unit Family scripts
#
# A unit family lets several unit types share a single recruitment limit, so that upgrading
# a unit from one member of the family to another does not free up a slot for a new one.
#
# A unit type joins a family with family = <family_key> in common/unit_types/.
#
# limit = { <value calculations> } / <default_value>   # Shared maximum across every member of the family
#
# A unit type that sets its own limit does not use its family's limit. Setting both is an error
# and is reported at load time.
#
# The family name shown in tooltips comes from a localization key matching the family key.
