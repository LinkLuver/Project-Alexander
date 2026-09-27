# AI Lists for Generic Actions
#
# Let's us group a bunch of generic actions together for the AI so it can evaluate if **any** of them are possible.
# This way we can optimize the AI evaluation by clearing a larger chunk of them in one go.
#
# A Generic action can be in several lists at once. If a generic action is not given any list then it's put into the
# global one. 
#
# These lists should be used to eliminate out generic actions that are only used by some countries. 
# Like situations as the 100 year war or other similar things.
#
#
# potential = trigger, root scope is the country evaluating actions
# actions = list, all the actions part of this list
