#<parliament type key> = {
#	type = country/international_organization
#	potential = { <triggers> }						#scope depends on type (root = country if type = country, root = io if type = international_organization), determines if that type is even visible or not
#	allow = { <triggers> }							#scope depends on type (root = country if type = country, root = io if type = international_organization)
#   locked = { <triggers> }							#scope depends on type (root = country if type = country, root = io if type = international_organization)
#	modifier = { <country modifiers> }
#}