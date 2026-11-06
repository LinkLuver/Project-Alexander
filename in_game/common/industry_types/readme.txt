#P:A TODO Review imported vanilla file (1.4.7)
# Industry Types - grantable industry promotions applied to an area (see the Urban Rights / Promote Industry screen).
#
# color = <named_color>
# kept_at_conquest = no   # default no
# potential = {}          # root = country
# allow = {}              # root = country, scope:target = area
#
# goods = { <good> ... }  # the goods this industry promotes (single source of truth)
# output = X              # generated per good -> local_<good>_output_modifier (in-area location modifier)
# pop_demand = X          # generated per good -> global_<good>_pop_demand (country-wide modifier)
#
# The location/country modifiers are GENERATED in C++ at load from the goods list + these two
# magnitudes (CIndustryType::BuildGeneratedModifiers). The same goods list drives the per-area
# building counts in the picker. (Raw country_modifier = {} / location_modifier = {} blocks are still
# honored for bespoke entries, but prefer goods so the system stays a single source of truth.)
#
# Granted/revoked via the CGrantIndustryPromotionCommand / CRevokeIndustryPromotionCommand commands,
# or queried in script with: has_industry_promotion = industry_type:<key>  (country scope).
# Capacity is governed by the possible_industry_promotions country modifier,
# gated by the can_promote_industry boolean modifier.
