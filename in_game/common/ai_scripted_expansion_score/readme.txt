# Scripted expansion scores add or subtract score from potential expansion targets when Ai evaluates future wars
# <name> = {
#    attacker_potential = <trigger> #root - attacker, if this evaluates to false the score won't be applied
#    target_trigger = <trigger> #root - target, scope:attacker - attacker, if this evaluates to false the score won't be applied
#    score = <script value> #scope:attacker - attacker, scope:target - target, adds extra scpre to the overall final score before the multiplier is applied, related to EXPANSION_TARGET_SCORE_NEEDED_TO_PICK define
#    multiplier = <script value> #scope:attacker - attacker, scope:target - target, multiplies the overall final score, not just the score value above, related to EXPANSION_TARGET_SCORE_NEEDED_TO_PICK define
#    never_attack = <trigger>, #scope:attacker - attacker, scope:target - target, if this evaluates to true, the final score will always be 0
# }

