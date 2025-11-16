#Make sure that for the event file you first define the namespace for all the events in the file!
# namespace = <event id name>

#The id number must be between 1 and 9999. Also, the event id as a whole must be unique
#<event id name>.<id number> = {
#	type = country_event/location_event/unit_event/exploration_event/age_event			# Defines for what scope this event fires, must be one of the options there!
#	title = <event id name>.<id number>.title											# The title of the event. Can use scopes from immediate for the localization
#	title = {																			# Alternative way for event titles which shows the first title which fulfils the trigger. Use that if you rely on saved event targets from immediate
#		first_valid = {
#			triggered_desc = {
#				trigger = { <triggers> }												# root = defined scope from type
#				desc = <event id name>.<id number>.title.a
#			}
#			triggered_desc = {
#				desc = <event id name>.<id number>.title.b
#			}
#		}
#		#Alternatively:
#		#random_valid = {}		
#	}
#	desc = <event id name>.<id number>.desc												# The description of the event. Can use scopes from immediate for the localization
#	desc = {																			# Alternative way for event descriptions which shows the first title which fulfils the trigger. Use that if you rely on saved event targets from immediate
#		first_valid = {
#			triggered_desc = {
#				trigger = { <triggers> }												# root = defined scope from type
#				desc = <event id name>.<id number>.desc.a
#			}
#			triggered_desc = {
#				desc = <event id name>.<id number>.desc.b
#			}
#		}
#	}
#	historical_info = <event id name>.<id number>.historical_info						# The extra text of the event describing the historical background of the event
#	historical_info = {																	# Alternative way for event historical info which shows the first title which fulfils the trigger. Use that if you rely on saved event targets from immediate
#		first_valid = {
#			triggered_desc = {
#				trigger = { <triggers> }												# root = defined scope from type
#				desc = <event id name>.<id number>.historical_info.a
#			}
#			triggered_desc = {
#				desc = <event id name>.<id number>.historical_info.b
#			}
#		}
#	}
#	trigger = {																			# The triggers needed by the event to fire in the first place. root = defined scope from type
#		<triggers>
#	}
#	major = yes																			# The event will create a notification for other countries if set to yes. Default: no
#	major_trigger = {																	# Defines who can see the notification of this event. root = country who should see this event, scope:from = the original entity firing the event
#		<triggers>
#	}
#	hidden = yes																		# Event is hidden away from the country, no title or description needed in that case
#	immediate = {																		# Effects which happen the moment the event fires. root = defined scope from type
#		<effects>
#	}
#	after = {																			# Effects which happen AFTER any event option has been selected. root = defined scope from type
#		<effects>
#	}
#	on_trigger_fail = {																	# This will be run if a queued event (or one triggered immediately from script) does not fulfill its trigger. Events failing to trigger from an on-action will *not* run this
#		<effects>
#	}
#	fire_only_once = yes																# Event will fire only once per campaign
#	interface_lock = no																	# Event pauses the game when fired in single player. Default: yes
#	dynamic_historical_event = {														# The time window for the event to occur, only tags specified in it can get the event
#		tag = <country tag>																# Can have more than one tag in it
#		from = 1337.1.1
#		to = 1837.1.1
#		monthly_chance = <int>
#	}
#	orphan = yes																		# The game will not log an error about this event being unreferenced. Useful for debug events
#	hide_portraits = yes																# Event won't show the character portraits if any character is a saved event target in the immediate
#	outcome = positive/neutral/negative													# The direction for the audio. Default: neutral
#	category = disaster_event/situation_event/international_organization_event			# Determines what icon the event should have. Does NOT show any icon when it is a generic_event which is the default
#	illustration_tags = {																# Tags for the event picture. See existing events to see what tags are used ..
#		<tags>
#	}
#	weight_multiplier = {																# Used to manipulate the weight of this on_action if it is a candidate in a random_on_action list (see below). Only relevant for events which are called in any random lists such as random_list or random_events
#		base = 1
#		modifier = {
#			add = 1
#			<triggers>
#		}
#	}
#	image = "<event image path>"														# The picture displayed for the event
#	option = {																			# You can have x amounts of options in a single event
#		name = <event id name>.<id number>.a
#		historical_option = yes															# Highlights this option as a historical option
#		trigger = {																		# This option is only visible if the triggers here are fulfilled
#			<triggers>																	# root = defined scope from type. Note: use hidden_trigger = {} if you do not want the game say "this is available because x"
#		}
#		<effects>																		# root = defined scope from type
#		fallback = yes																	# This event option will be available when all the others are not, even if the triggers here are unfulfilled
#		exclusive = yes																	# All non-exclusive event options are not shown if that event option is available
#		original_recipient_only = yes													# This event option is only available to the country which triggers the event for
#       moral_option = yes                                                              # ???
#       evil_option = yes                                                               # ???
#       high_risk_option = yes                                                          # ???
#       high_reward_option = yes                                                        # ???
#       ai_will_select = {                                                              # Defines AI willingness to pick this event option using script math. Overrules ai_chance
#           <script math>
#       }
#		ai_chance = {																	# Defines AI likelihood to pick this event option, old school mtth style
#			base = 1
#			modifier = {
#				add = 1
#				<triggers>
#			}
#		}
#
#		### NOT IMPLEMENTED ###
#		# If the event is invalid, but this trigger is valid, then the option will be shown (but disabled).
#		# This behavior is also influenced by the EVENT_OPTIONS_SHOWN_HIDE_UNAVAILABLE or SCHEME_PREPARATION_OPTIONS_SHOWN_HIDE_UNAVAILABLE defines depending on event type.
#		show_as_unavailable = {}
#	}
#}