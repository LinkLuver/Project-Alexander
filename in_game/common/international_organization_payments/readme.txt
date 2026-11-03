# International Organization Payments
#
# A regular monthly payment that [optionally] goes from some members of the organization [optionally] to others.
#
# ATTRIBUTES
#
# - get_payer_list: effect to populate a list with the payers. Payers can be anything that has an account - that means countries or estates. Use add_to_local_variable_list = payers in the scope of the objects you want to add. (root = international organization)
# - get_payee_list: effect to populate a list with the payees. Payees can be anything that has an account - that means countries or estates. Use add_to_local_variable_list = payees in the scope of the objects you want to add. (root = international organization)
# - price: base price of the total payment
# - price_multiplier: <script value> how much to multiply the price by to arrive at the total amount to be transferred (root = international organization)
# - uses_maintenance: (yes/no) does this payment add a maintenance slider?
# - maintenance_modifier: modifier that affects the country according to the amount of payment maintenance they're doing - use this to penalise countries that don't pay their full share
# - proportion_for_payer: <script value> how much of the price will the country pay (root = potential country, scope:recipient = international organization)
# - proportion_for_payee: <script value> how much of the price will the country receive (root = potential country, scope:recipient = international organization)
# - min_slider_value: <float> 0..1 how much a payment slider will affect the total payment. Between this value and 100%. Default is 0.5 (50%).
# - ai_maintenance_value: <script value> should be between 0 and 1. Sets the slider value for Ai, root - country, recipient - IO, if left empty will use the AI_DEFAULT_IO_MAINETANCE_VALUE define.
# - ai_maintenance_ignore_saving: <yes/no> should the ai_maintenance_value even when in saving mode. AI in saving mode tries to limit all expenses and stabilize their country. Default is no.