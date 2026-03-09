class Item:
    def __init__(self, name, price):
        self.name = name
        self.price = float(price)

    def __repr__(self):
        return f"{self.name} (${self.price:.2f})"


class Cart:
    def __init__(self):
        self.items = {} 

    def add(self, name, price, qty=1):
        if qty <= 0:
            raise ValueError("qty>0")
        p, q = self.items.get(name, (price, 0))
        self.items[name] = (price, q + qty)

    def remove(self, name, qty=1):
        if name not in self.items:
            raise KeyError(name)
        p, q = self.items[name]
        if qty >= q:
            del self.items[name]
        else:
            self.items[name] = (p, q - qty)

    def total(self):
        return sum(p * q for p, q in self.items.values())

    def show(self):
        if not self.items:
            print("Cart is empty.")
            return
        for n, (p, q) in self.items.items():
            print(f"{n} x{q} = ${p * q:.2f}")
        print(f"Total: ${self.total():.2f}")

    def checkout(self):
        if not self.items:
            print("Cart is empty.")
            return
        self.show()
        print("Thank you!")
        self.items.clear()


def main():
    c = Cart()
    print("Commands: add / remove / view / checkout / quit")
    while True:
        cmd = input("> ").strip().lower()
        if cmd in ("quit", "exit"):
            break
        if cmd == "add":
            try:
                name = input("name: ").strip()
                price = float(input("price: ").strip())
                qty = int(input("qty [1]: ").strip() or 1)
                c.add(name, price, qty)
                print("Added.")
            except Exception:
                print("Invalid input.")
        elif cmd == "remove":
            try:
                name = input("name: ").strip()
                qty = int(input("qty [1]: ").strip() or 1)
                c.remove(name, qty)
                print("Removed.")
            except Exception as e:
                print("Error:", e)
        elif cmd == "view":
            c.show()
        elif cmd == "checkout":
            c.checkout()
        else:
            print("Unknown command.")


if __name__ == "__main__":
    main()
