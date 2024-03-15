import csv

def add_transaction(transactions):
    category = input("Enter category (Expense/Income): ")
    amount = float(input("Enter amount: "))
    date = input("Enter date (YYYY-MM-DD): ")

    transactions.append({"category": category, "amount": amount, "date": date})
    print("Transaction added successfully!")

def calculate_budget(transactions):
    total_income = sum(t["amount"] for t in transactions if t["category"] == "Income")
    total_expenses = sum(t["amount"] for t in transactions if t["category"] == "Expense")
    remaining_budget = total_income - total_expenses
    return remaining_budget

def main():
    transactions = []  # List to store transactions

    # Load existing data from a file (if any)

    while True:
        print("\nMenu:")
        print("1. Add Transaction")
        print("2. View Budget")
        print("3. Exit")
        choice = input("Enter your choice: ")

        if choice == "1":
            add_transaction(transactions)
        elif choice == "2":
            remaining_budget = calculate_budget(transactions)
            print(f"Remaining budget: ${remaining_budget:.2f}")
        elif choice == "3":
            # Save transactions to a file
            break
        else:
            print("Invalid choice. Try again.")

if __name__ == "__main__":
    main()
