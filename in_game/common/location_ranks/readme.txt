#P:A TODO Review imported vanilla file (1.4.7)
#Note:  logic assumes that anything below a rank in the list is worse
#<location rank id> = {
#   color = <named color>                           # What color should this location rank have in the location rank mapmode
#   rank_modifier = <modifier>                      # Modifier applied to the location
#   country_modifier = <modifier>                   # Modifier applied to the country
#   capital_country_modifier = <modifier>           # Modifier applied to the country if the location is the capital of that country        
#   is_established_city = <yes/no>                  # Does the location have a city status. Locations with a city status are treated as non rural.
#   build_time = <int>                              # Build time in days
#   frame_tier = <int>                              # Which frame to use for the map markers
#   tier = <int>                                    # Used for diplomatic acceptance and picking new capital, higher = better
#   construction_demand = <goods demand>            # What goods are needed to build this location rank
#   allow = <trigger>                               # Can the location rank be upgraded to or downgraded to (root = location)
#   max_rank = <yes/no>                             # Is the location rank the best possible rank
#   show_in_label = <yes/no>                        # Should the name of the rank be shown next to the location, example "City of <name>"
#   institution_spawn_chance_factor = <float>       # How much more likely institutions are to spawn in locations with this rank, default = 1
#   ai_construct_weight = <scripted float>          # Influences AI utility of the location rank when constructing (root = location, scope:builder = country doing the construction)
#}