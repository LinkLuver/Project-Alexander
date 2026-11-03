# Scripted expansion targets add potential expansion targets when Ai evaluates future wars, it allows to evaluate countries that otherwise would have been ignored
# <name> = {
#    attacker_potential = <trigger> #root - attacker, if this evaluates to false the score won't be applied
#    candidate_list = <effect> #root - attacker, gives us a list of possible candidates to look at. Fill the list with add_to_list = source on the scope object
#    casus_belli = <casus_belli> #root - attacker, scope:target - target, which casus belli to use. Can be left empty to make the AI choose
#    ignore_antagonism = <yes/no> #Will this expansion path ignore an already existing group of countries with high antagonism. Only checked when declaring, not when taking land
#    score = <script value> #scope:attacker - attacker, scope:target - target, sets the score of the expansion target, related to EXPANSION_TARGET_SCORE_NEEDED_TO_PICK define
#    sort_value = <script value> #scope:attacker - attacker, scope:target - target, used when sorting expansion targets, if left empty it will be the same as the score value. Sorting value might differ from the score value when you want to ensure certain position of a target without influencing the value needed for the define threshold 
# }

