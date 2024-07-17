# ATM Simulation

This repository contains a simple ATM simulation implemented in Python.

## Features

- Account balance inquiry
- Cash withdrawal
- Cash deposit
- PIN change
- Transaction history

## Usage

To use the ATM simulation, run the `atm_simulation.py` file.

```python
class ATM:
    def __init__(self, pin, balance=0):
        self.pin = pin
        self.balance = balance
        self.transaction_history = []
    
    def verify_pin(self, pin):
        return self.pin == pin
    
    def check_balance(self):
        return self.balance
    
    def withdraw(self, amount):
        if amount > self.balance:
            return "Insufficient funds"
        self.balance -= amount
        self.transaction_history.append(f"Withdrew ${amount}")
        return f"${amount} withdrawn successfully"
    
    def deposit(self, amount):
        self.balance += amount
        self.transaction_history.append(f"Deposited ${amount}")
        return f"${amount} deposited successfully"
    
    def change_pin(self, old_pin, new_pin):
        if self.verify_pin(old_pin):
            self.pin = new_pin
            return "PIN changed successfully"
        return "Incorrect old PIN"
    
    def get_transaction_history(self):
        return self.transaction_history

# Sample Usage
if __name__ == "__main__":
    atm = ATM(pin=1234, balance=1000)
    
    # Check balance
    print("Current Balance:", atm.check_balance())
    
    # Withdraw cash
    print(atm.withdraw(200))
    print("Balance after withdrawal:", atm.check_balance())
    
    # Deposit cash
    print(atm.deposit(500))
    print("Balance after deposit:", atm.check_balance())
    
    # Change PIN
    print(atm.change_pin(1234, 5678))
    
    # Check transaction history
    print("Transaction History:", atm.get_transaction_history())
