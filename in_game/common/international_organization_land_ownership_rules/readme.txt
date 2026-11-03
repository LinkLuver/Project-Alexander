# International Organization Land Ownership Rules
#
# If your international organization can own land too, then we enter the rules here. The land will still be owned by countries, but extra stuff will apply.
#
# ATTRIBUTES
#
# - modifier: applied to locations that are owned by the international organization
# - can_add_trigger: can we add locations to the organization in general (root = international organization)
# - can_remove_trigger: can we remove locations from an organization in general (root = international organization)
# - can_add_location_trigger: can we add a location to the organization (root = location, recipient = international organization)
# - can_remove_location_trigger: can we remove a location from an organization (root = location, recipient = international organization)
# - on_added: effect when a location is added to the orgnaisation (root = location, recipient = international organization)
# - on_removed: effect when a location is removed from the orgnaisation (root = location, recipient = international organization)
# - ai_desire_to_add: how much the actual country owner of the land wants to add it to the organization (root = location, recipient = international organization)
# - owned_location_color: <optional> color of owned locations on the diplomatic map (will be stripes)
# - removed_by_peace_treaty: <yes/no> makes that land can only be removed via peace treaties from the IO, defaults to no
# - remove_war_score_modifier: <double> modify the war score cost for removing provinces from the IO, has no effect if removed_by_peace_treaty is not used