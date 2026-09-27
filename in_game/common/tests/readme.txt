#<test id> = {
#	year = <year>   #the start year when the test is started to be checked
#	success = {
#		<triggers>  #the triggers the test need to fulfill for it to pass
#	}
#	failure = {
#		<triggers>  #the triggers the test need to fulfill for it to fail
#	}
#	end_year = <year>   #the test will be inactive once this year is passed
#	fail_on_end_year = <yes/no> #the test will automatically fail if that date passes if set to yes, defaults to no
#	success_effect = {
#		<effects>   #effects which happen if the test passes, make sure to only use test_log though
#	}
#	failure_effect = {
#		<effects>   #effects which happen if the test passes, make sure to only use test_log though
#	}
#}
#
# success_child = {
#     desc = "<label>"       # human-readable label shown in the log
#     trigger = { <triggers> }  # the condition that identifies this branch
# }
#   Optional, repeatable. Defined at the test level (not inside success = {}).
#   After the test passes, each success_child trigger is evaluated in order;
#   the first one that is true appends [SUCCEEDED][<label>] to the log line:
#     [TEST_NAME][...][RESULT][PASS][DATE][...][SUCCEEDED][<label>]
#
#   Example:
#   success = {
#       NOT = {
#           c:MLO ?= { months_since_war > 12 }
#           c:NAP ?= { months_since_war > 12 }
#       }
#   }
#   success_child = { desc = "MLO"  trigger = { c:MLO ?= { months_since_war > 12 } } }
#   success_child = { desc = "NAP"  trigger = { c:NAP ?= { months_since_war > 12 } } }