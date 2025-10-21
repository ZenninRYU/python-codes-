class coffee:
    def __init__(self,name,price):
        self.name = name
        self.price = price

class Order:
    def __init__(self):
        self.items = []

    def add_item(self,coffee):
        self.items.append(coffee)
        print(f"Add {coffee.name} to your Order")
    
    def total (self):
        return sum(item.price for item in self.items)
    
    def show_Order(self):
        if not self.items:
            print("No items in Order.")
            return
        print("\nYour Order")
        for i, item in enumerate(self.items,1):
            print(f"{i}. {item.name} - ${item.price}")
        print(f"Total: ${self.total()}\n")
    def checkout(self):
        if not self.items:
            print("Your cart is empty.")
            return
        self.show_Order()
        confirm = input("Procced to checkout? (Yes/No)").strip().lower()
        if confirm == 'yes':
            print("Your Oreder compelete")
            self.items.clear()
        else:
            print("Order canceled")

def main():
    Menu = [
        coffee("Espresso",50),
        coffee("Latte",60),
        coffee("Capputchino",60),
        coffee("Americano",55)
    ] 
    order = Order()
    while True:
        print("\n--- COFFEE MENUE ")
        for i, c in enumerate(Menu, 1):
            print(f"{i}.{c.name}- ${c.price}")
        print("5.  View Order")
        print("6.Checkout")
        print("7.Exit")
        choice = input("Choose an opption:")
        if choice in ['1','2','3','4']:
            order.add_item(Menu[int(choice)-1])
        elif choice == '5':
            order.show_Order()
        elif choice == '6':
            order.checkout()   
        elif choice == '7':
            print("Thanks For visiting. See you later")
            break
        else:
            print("Invalid choice.Pls try again ")

if __name__ == "__main__":
    main()
