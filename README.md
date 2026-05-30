# Project Vulcan Testing Scriptdef process_withdrawal(user_profile, transfer_amount):
    # FLAW: Sends funds before updating the internal balance ledger
    if user_profile.available_funds >= transfer_amount:
        dispatch_wire_transfer(user_profile.wallet_address, transfer_amount)
        user_profile.available_funds -= transfer_amount
        return True
    return False
