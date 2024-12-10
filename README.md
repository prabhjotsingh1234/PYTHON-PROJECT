# PYTHON-PROJECT

class Expense: 

    def __init__(self, name, category, amount) -> None:
        self.name = name
        self.category = category
        self.amount = amount

    def __repr__(self):
        return f'<Expense: {self.name}, {self.category}, ${self.amount:.2f}>'












from expenses import Expense


def main():
    print(f"Running Expense Tracker!") 
    expense_file_path = 'expenses.csv'

    # User inputs expense 
    expense = get_user_expense()
    

    # Write their expense to a file 
    save_expense_to_file(expense, expense_file_path)

    # Read file and summarize expenses.
    summarize_expenses(expense_file_path)
    pass


def get_user_expense():
    print(f"Get User Expense!") 
    expense_name = input('Enter expense name: ')
    expense_amount = float(input('Enter expense amount: '))
    expense_categories = [
        "🍕Food", 
        "🏠Home", 
        "🧑‍💼Income", 
        "🥳Entertainment", 
        "⛽Gas", 
    ]

    while True:
        print('Select a category: ')
        for i, category_name in enumerate(expense_categories):
            print(f'  {i + 1}. {category_name}')

        value_range = f'(1 - {len(expense_categories)})'
        selected_index = int(input(f'Enter a category number {value_range}: ')) - 1

        if selected_index in range(len(expense_categories)):
            selected_category = expense_categories[selected_index]
            new_expense = Expense(name=expense_name, category= selected_category, amount = expense_amount)
            return new_expense
        else:
            print('Invalid category. Please try again!')


def save_expense_to_file(expense: Expense, expense_file_path):
    print(f"Save User Expense!: {expense} to {expense_file_path}")
    with open(expense_file_path, 'a') as f:
        f.write(f'{expense.name},{expense.category},{expense.amount}\n')


    
def summarize_expenses(expense_file_path):
    print(f"Summarize User Expense!") 
    with open(expense_file_path, 'r') as f:
        lines = f.read.lines()
        for line in lines:
            stripped_line = line.strip()
            print(expense_name, expense_amount, expense_category)
            line_expense = Expense



if __name__ == "__main__":
    main()
