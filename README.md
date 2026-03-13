
import csv

def add_expense():
    try:
        # Error Handling: Ensuring the amount is a number
        amount = float(input("Enter amount spent: ")) 
        category = input("Enter category (Food/Travel/Rent): ")
        date = input("Enter date (DD-MM-YYYY): ")
        
        with open('my_expenses.csv', 'a', newline='') as file:
            writer = csv.writer(file)
            writer.writerow([date, category, amount])
        print("✅ Expense saved successfully!\n")
    except ValueError:
        print("❌ Error: Please enter a numeric value for the amount.\n")

def show_total():
    total = 0
    try:
        with open('my_expenses.csv', 'r') as file:
            reader = csv.reader(file)
            for row in reader:
                # row[2] is the amount column
                total += float(row[2])
        print(f"💰 Your Total Spending so far: ₹{total}\n")
    except FileNotFoundError:
        print("⚠️ No expenses found yet. Add one first!\n")

while True:
    print("--- 📊 My CSE Expense Tracker ---")
    print("1. Add Expense")
    print("2. View Total Spending")
    print("3. Exit")
    
    choice = input("Choose an option: ")
    
    if choice == '1':
        add_expense()
    elif choice == '2':
        show_total()
    elif choice == '3':
        print("Goodbye, Akanksha!")
        break
    else:
        print("Invalid choice, try again.")
