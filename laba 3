class Store:
    def __init__(self):
        self.products = {
            1: ["Хліб", 3290, 12], 2: ["Молоко", 4590, 8],
            3: ["Кава", 18990, 6], 4: ["Шоколад", 6990, 10],
            5: ["Чай", 12450, 5]}
        self.cart = {}

    def price(self, c): return f"{c // 100:03d}.{c % 100:02d}грн"
    def total(self): return sum(map(lambda x: self.products[x[0]][1] * x[1], self.cart.items()))

    def run(self):
        while True:
            print("\n1 Каталог  2 Додати  3 Видалити  4 Кошик\n5 Купити  6 Адмін  0 Вихід")
            choice = input("Ваш вибір: ").strip()
            try:
                if choice == "1":
                    for i, p in self.products.items(): print(f"{i}. {p[0]} — {self.price(p[1])}")
                elif choice == "2":
                    i, q = int(input("Номер: ")), int(input("Кількість: "))
                    if i not in self.products or q < 1 or self.cart.get(i, 0) + q > self.products[i][2]:
                        print("Немає товару або недостатньо залишку.")
                    else:
                        self.cart[i] = self.cart.get(i, 0) + q
                        print("Додано.")
                elif choice == "3":
                    print("Видалено." if self.cart.pop(int(input("Номер: ")), None) else "Немає в кошику.")
                elif choice == "4":
                    if not self.cart: print("Кошик порожній.")
                    for i, q in self.cart.items(): print(f"{self.products[i][0]} × {q} — {self.price(self.products[i][1] * q)}")
                    if self.cart: print("Разом:", self.price(self.total()))
                elif choice == "5":
                    if not self.cart: print("Кошик порожній.")
                    elif any(q > self.products[i][2] for i, q in self.cart.items()): print("Недостатньо товару.")
                    else:
                        amount = self.total()
                        for i, q in self.cart.items(): self.products[i][2] -= q
                        self.cart.clear()
                        print("Покупку оформлено:", self.price(amount))
                elif choice == "6":
                    if input("Логін: ") == "admin" and input("Пароль: ") == "admin123":
                        for p in self.products.values(): print(f"{p[0]}: {p[2]} шт.")
                    else: print("Неправильний логін або пароль.")
                elif choice == "0": break
                else: print("Невідома команда.")
            except ValueError:
                print("Введіть коректне число.")


Store().run()