class FinanceTracker:
    def __init__(self):
        self.balance = 0.0
        self.transactions = []

    def add_income(self, amount):
        self.balance += amount
        self.transactions.append(f"Доход: +{amount}")

    def add_expense(self, amount):
        self.balance -= amount
        self.transactions.append(f"Расход: -{amount}")

    def display_balance(self):
        print(f"Текущий баланс: {self.balance:.2f}")

    def display_transactions(self):
        if not self.transactions:
            print("История транзакций пуста.")
        else:
            print("\nИстория транзакций:")
            for transaction in self.transactions:
                print(transaction)

def main():
    tracker = FinanceTracker()

    while True:
        print("\nДоступные команды:")
        print("1. Добавить доход")
        print("2. Добавить расход")
        print("3. Посмотреть баланс")
        print("4. Посмотреть историю транзакций")
        print("5. Выйти")

        command = input("Введите номер команды: ")

        if command == "1":
            try:
                amount = float(input("Введите сумму дохода: "))
                if amount < 0:
                    print("Сумма должна быть положительной.")
                else:
                    tracker.add_income(amount)
                    print(f"Доход {amount} добавлен.")
            except ValueError:
                print("Пожалуйста, введите корректное число.")

        elif command == "2":
            try:
                amount = float(input("Введите сумму расхода: "))
                if amount < 0:
                    print("Сумма должна быть положительной.")
                else:
                    tracker.add_expense(amount)
                    print(f"Расход {amount} добавлен.")
            except ValueError:
                print("Пожалуйста, введите корректное число.")

        elif command == "3":
            tracker.display_balance()

        elif command == "4":
            tracker.display_transactions()

        elif command == "5":
            print("Выход из программы.")
            break

        else:
            print("Неверная команда. Попробуйте снова.")

if __name__ == "__main__":
    main()
