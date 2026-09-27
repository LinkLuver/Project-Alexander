## Artist Types
#
#Defines the disciplines an artist character can belong to. Each type controls:
#- Which countries can have artists of this discipline (potential)
#- A passive country modifier applied while the artist is at court (modifier)
#- Which works-of-art types the artist can commission (encoded via allow = { artist_type = X }
#  on each work-of-art type definition in common/artist_work/)
#
### Format
#
#<artist_type_id> = {
#	potential = {
#		# Country-scoped triggers. If omitted the type is available to all countries.
#		# Used to gate culture/religion/advance-specific disciplines.
#	}
#
#	modifier = {
#		# Country modifier applied while this artist is employed at court.
#		# Applied as a character modifier on the artist character; removed on death/dismissal.
#		# Supports all standard country modifier fields.
#	}
#}
#
#
### Localization
#
#Names and descriptions are looked up in localization as:
#  ARTIST_TYPE_NAME_<id>   — display name
#  ARTIST_TYPE_DESC_<id>   — tooltip description
#
### Notes
#
#- A country can employ multiple artists of different types simultaneously.
#- The passive modifier from the type stacks across all artists of that type at court.
#- Works-of-art affinity (which WoA types an artist prefers) is defined on the WoA side
#  via allow = { artist_type = <id> } in common/artist_work/, not here.
#- The dismiss_artist character interaction removes an artist from court at a prestige
#  recruitment.
#