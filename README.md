# BANK MANAGEMENT SYSTEM

accounts = {}

while True:
    print("\n===== BANK MANAGEMENT SYSTEM =====")
    print("1. Create Account")
    print("2. Deposit Money")
    print("3. Withdraw Money")
    print("4. Check Balance")
    print("5. Account Details")
    print("6. Exit")

    choice = input("Enter your choice: ")

    # Create Account
    if choice == "1":
        account_no = input("Enter account number: ")

        if account_no in accounts:
            print("Account already exists!")
        else:
            name = input("Enter account holder name: ")
            balance = float(input("Enter initial deposit: "))

            accounts[account_no] = {
                "name": name,
                "balance": balance
            }

            print("Account created successfully!")

    # Deposit
    elif choice == "2":
        account_no = input("Enter account number: ")

        if account_no in accounts:
            amount = float(input("Enter deposit amount: "))

            if amount > 0:
                accounts[account_no]["balance"] += amount
                print("Money deposited successfully!")
                print("New Balance: ₹", accounts[account_no]["balance"])
            else:
                print("Enter a valid amount.")
        else:
            print("Account not found!")

    # Withdraw
    elif choice == "3":
        account_no = input("Enter account number: ")

        if account_no in accounts:
            amount = float(input("Enter withdrawal amount: "))

            if amount <= 0:
                print("Enter a valid amount.")
            elif amount > accounts[account_no]["balance"]:
                print("Insufficient balance!")
            else:
                accounts[account_no]["balance"] -= amount
                print("Money withdrawn successfully!")
                print("Remaining Balance: ₹",
                      accounts[account_no]["balance"])
        else:
            print("Account not found!")

    # Check Balance
    elif choice == "4":
        account_no = input("Enter account number: ")

        if account_no in accounts:
            print("Current Balance: ₹",
                  accounts[account_no]["balance"])
        else:
            print("Account not found!")

    # Account Details
    elif choice == "5":
        account_no = input("Enter account number: ")

        if account_no in accounts:
            print("\n----- ACCOUNT DETAILS -----")
            print("Account Number:", account_no)
            print("Account Holder:", accounts[account_no]["name"])
            print("Balance: ₹", accounts[account_no]["balance"])
        else:
            print("Account not found!")

    # Exit
    elif choice == "6":
        print("Thank you for using the Bank Management System!")
        break

    else:
        print("Invalid choice. Please try again.")
