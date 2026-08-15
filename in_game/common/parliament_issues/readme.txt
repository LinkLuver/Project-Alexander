#<parliament_issue> = {
#	type = country/international_organization					#by default country
#	estate = <estate type>										#only used when type = country
#	special_status = <special status>							#only used when type = international_organization
#	modifier_when_in_debate = { <modifiers> }					#country or international organization modifier
#	allow = { <triggers> }										#root = country / international_organization
#	potential = { <triggers> }									#root = country / international_organization
#   selectable_for = { <triggers> }                             #root = country who tries to select this, scope:recipient = international_organization
#	chance = { <chance parameters> }							#root = country / international_organization
#	on_debate_passed = { <effects> }							#root = country / international_organization
#	on_debate_failed = { <effects> }							#root = country / international_organization
#	on_debate_start = { <effects> } 							#root = country / international_organization
#   wants_this_parliament_issue_bias = { <scripted maths> }		#Gets a scripted number determining how much a country will want this parliament issue. Scope changes depending on if it's a policy for a government or an international organization. Government: root = country. IO: root = country, scope:actor = other country (if the IO doesn't exist yet), scope:recipient = IO, scope:target = potential target
#}