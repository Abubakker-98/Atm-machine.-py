# Atm-machine.-py
simple python code simulation of ATM machine

# ATM Simulator

This is a simple ATM simulator program written in Python. It allows users to check their balance, withdraw funds, deposit funds, and exit the system.

## Features

- **Check Balance:** View the current balance in your account.
- **Withdraw Balance:** Withdraw a specified amount from your account, with checks for insufficient funds.
- **Deposit Balance:** Deposit a specified amount into your account.
- **Exit:** Exit the ATM simulator.

## Usage

1. Run the program.
2. Insert your card (simulated by a sleep delay).
3. Enter your ATM PIN.
4. Choose an option from the menu:
    - Check Balance
    - Withdraw Balance
    - Deposit Balance
    - Exit

## Code

```python
import time

print("Please insert your CARD")
time.sleep(2)

password = 1234

# Loop until the correct pin is entered
while True:
    try:
        pin = int(input("Enter your ATM pin: "))
        if pin == password:
            break
        else:
            print("Wrong pin, please try again")
    except ValueError:
        print("Please enter a valid 4-digit pin")

balance = 9999999

while True:
    print("""
    1 == Check Balance
    2 == Withdraw Balance
    3 == Deposit Balance
    4 == Exit
    """)
    try:
        option = int(input("Please enter your choice: "))
    except ValueError:
        print("Please enter a valid option")
        continue

    if option == 1:
        print(f"Your balance is {balance}")
        print("###########################################################")
    elif option == 2:
        try:
            withdraw_amount = int(input("Please enter withdraw amount: "))
            if withdraw_amount > balance:
                print("Insufficient balance")
            else:
                balance -= withdraw_amount
                print(f"{withdraw_amount} is debited from your account")
                print(f"Your current balance is {balance}")
        except ValueError:
            print("Please enter a valid amount")
        print("###########################################################")
    elif option == 3:
        try:
            deposit_amount = int(input("Please enter deposit amount: "))
            balance += deposit_amount
            print(f"{deposit_amount} is credited to your account")
            print(f"Your updated balance is {balance}")
        except ValueError:
            print("Please enter a valid amount")
        print("###########################################################")
    elif option == 4:
        print("Thank you for using the ATM. Goodbye!")
        break
    else:
        print("Please enter a valid option")
