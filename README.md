
# Inventory Tracker without OOP in Python

# Initialize an empty dictionary to store inventory items
inventory = {}

# Function to display the menu
def display_menu():
    print("\n----- Inventory Tracker -----")
    print("1. Add item")
    print("2. Remove item")
    print("3. View inventory")
    print("4. Exit")

# Function to add item to inventory
def add_item():
    item_name = input("Enter the name of the item to add: ").strip()
    if item_name:
        quantity = int(input(f"Enter the quantity of {item_name}: "))
        if item_name in inventory:
            inventory[item_name] += quantity
        else:
            inventory[item_name] = quantity
        print(f"{quantity} of {item_name} added to inventory.")
    else:
        print("Item name cannot be empty!")

# Function to remove item from inventory
def remove_item():
    item_name = input("Enter the name of the item to remove: ").strip()
    if item_name in inventory:
        quantity = int(input(f"Enter the quantity of {item_name} to remove: "))
        if quantity <= inventory[item_name]:
            inventory[item_name] -= quantity
            if inventory[item_name] == 0:
                del inventory[item_name]  # Remove item from inventory if quantity becomes zero
            print(f"{quantity} of {item_name} removed from inventory.")
        else:
            print("You don't have enough quantity to remove!")
    else:
        print(f"{item_name} not found in inventory.")

# Function to view the inventory
def view_inventory():
    if not inventory:
        print("Inventory is empty!")
    else:
        print("\n----- Current Inventory -----")
        for item, quantity in inventory.items():
            print(f"{item}: {quantity}")

# Main program loop
def main():
    while True:
        display_menu()
        choice = input("Choose an option (1-4): ").strip()

        if choice == '1':
            add_item()
        elif choice == '2':
            remove_item()
        elif choice == '3':
            view_inventory()
        elif choice == '4':
            print("Exiting the program...")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
