# Building Types
#
# ATTRIBUTES
# - build_time: <integer> building time in days
# - employment_size: <float> how many people can be employed there. 1 = 1000 people
# - output: <float> how much of the produced good can be output per building level
# - is_foreign: <yes/no> is the building type able to be built in foreign lands
# - in_empty: <empty/owned/any> empty = can build in non-owned locations only; owned = can build in owned locations only; any = can build anywhere
# - stronger_power_projection: <yes/no> if yes, and you're building it in a foreign-owned location, you need stronger power projection than the location's owner to build it
# - need_good_relation: <yes/no> if yes, and you're building it in a foreign-owned location, you need good relations with the location's owner to build it
# - conversion_religion: <religion> religion that pops are converted to by this building
# - pop_type: <pop type> the pop type employed in this building
# - category: <building category> building category tag
# - construction_demand: what goods are required during construction
# - possible_production_methods = { <procuction_methods>}: production methods for each slot. (add as many lists as you desire)
# - unique_production_methods = { x = { } } , defining unique production methods scripted directly into the building
# - obsolete: <building type> what building type this one makes obsolete
# - price: <price> cost of creating the building
# - destroy_price: <price> price to destroy the building
# - estate: <estate type> what estate can build the building
# - max_levels: <scripted integer> maximum levels the building can be upgraded to (root = location, scope:owner = building owner, scope:builder = who's paying)
# - international_organization_link: international organization type, determines in which international organization type this building should be available to. That also means that this building will always be owned by the IO leader if one exists, gets destroyed if the IO gets destroyed, and the IO pays for the building if it can afford it. Note that the IO must be allowed to have buildings linked to it
# - allow: <trigger> can the building be built in the location (root = location, scope:actor = country building it) (think of this as an "enabled" check)
# - location_potential: <trigger> can the building be built in the location (root = location) (think of this as a "visible" check)
# - country_potential: <trigger> can the building be built by the country (root = country) (think of this as a "visible" check)
# - international_organization_potential: <trigger> can the building be built by the international organization (root = international organization, scope:actor = country) (think of this as a ")
# - can_destroy: <trigger> can the building be destroyed in the location (root = location, actor = destroyer, building = building)
# - is_indestructible: <yes/no> if set to yes, the building can neither be destroyed via button press nor via the effect for it. remove_if can still delete the building tho
# - remove_if: <trigger> will the building be auto-destroyed in the location (root = building)
# - capital_modifier: <modifier> modifier applied to the location if built in the capital (multiplied by building level and goods access)
# - capital_country_modifier: <modifier> modifier applied to the country if built in the capital (multiplied by building level and goods access)
# - capital_to_overlord_modifier: <modifier> modifier applied to the overlord of the country whose capital contains the building (multiplied by building level and goods access). Only applies when the building owner is a subject; useful for foreign buildings transferred to a subject country via change_building_owner.
# - foreign_country_modifier: <modifier> modifier applied to the country that currently owns the building (multiplied by building level and goods access). Only relevant for is_foreign = yes buildings; applies to whoever owns the building at any given time, so changes when change_building_owner is used.
# - modifier: <modifier> modifier applied to the location (multiplied by building level and goods access)
# - raw_modifier: <modifier> modifier applied to the location (not scaled)
# - market_center_modifier: <modifier> modifier applied to the location if built in a market center (multiplied by building level and goods access)
# - pop_size_created: <float> creates a pop of this size for the new building, taking it from your capital (for foreign buildings only)
# - increase_per_level_cost: <per cent> each new level added increases the cost by this percentage. So 0.5 = 50% more expensive per extra level
# - <location rank>: <yes/no> location ranks that the building can be built in
# - on_built = { <effects> }
# - on_destroyed = { <effects> }
# - always_add_demands = <yes/no> when set to yes building will need full demand even if doesn't employ all workers
# - custom_tags = { <strings> } #A list of custom strings to use to identify that building type
# - AI_ignore_available_worker_flag = <yes/no> AI will build this building even if it is lacking the required pop type
# - important_for_AI = <yes/no> When set it makes the AI use more performance trying to find a suitable place to build this
# - important_for_UI = <yes/no> When set the building type can appear in important UI elements (e.g. high-priority alerts)
# - audio_category: <string> overrides the audio_category inherited from the building_category. Used to pick the Wwise event when this building is built or upgraded — final event name is "construction_building_<audio_category>_<audio_tier>". If unset, falls back to the building_category's audio_category, then to NCityAudio::CONSTRUCTION_DEFAULT_AUDIO_CATEGORY. Categories used by audio: generic, industry, military, culture, religion, economy.
# - audio_tier: <int 1..6> impact-driven loudness tier for the construction sound. 1 = age-1 / basic, 2 = age-2 default or age-1 with strong modifier, 3 = anchor / chain-mid / capital upgrade with strong local effect, 4 = palace-class capital with country-wide modifier, 5 = top-impact rare strategic / wonder-adjacent, 6 = age-6 endgame cool stuff (apex of a chain, late-age factories, advanced government, monuments). Clamped to [NCityAudio::CONSTRUCTION_AUDIO_MIN_TIER, NCityAudio::CONSTRUCTION_AUDIO_MAX_TIER] at use-time. Out-of-range values ERRORLOG during PostReadInit. Default: 1.
