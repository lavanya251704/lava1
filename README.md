# Initialize an empty inventory (using a dictionary to store items and their quantities)
inventory = {}

def display_inventory():
    """Function to display the current inventory."""
    if not inventory:
        print("\nInventory is empty.")
    else:
        print("\nCurrent Inventory:")
        for item, quantity in inventory.items():
            print(f"{item}: {quantity}")

def add_item():
    """Function to add an item to the inventory."""
    item_name = input("\nEnter the name of the item to add: ").strip()
    if item_name in inventory:
        print(f"{item_name} already exists in the inventory.")
        quantity_to_add = int(input(f"How many of {item_name} would you like to add? "))
        inventory[item_name] += quantity_to_add
        print(f"{quantity_to_add} added to {item_name}. New quantity: {inventory[item_name]}")
    else:
        quantity = int(input(f"How many {item_name}s would you like to add? "))
        inventory[item_name] = quantity
        print(f"{item_name} added to inventory with quantity: {quantity}")

def remove_item():
    """Function to remove an item from the inventory."""
    item_name = input("\nEnter the name of the item to remove: ").strip()
    if item_name in inventory:
        quantity_to_remove = int(input(f"How many of {item_name} would you like to remove? "))
        if quantity_to_remove <= inventory[item_name]:
            inventory[item_name] -= quantity_to_remove
            print(f"{quantity_to_remove} removed from {item_name}. New quantity: {inventory[item_name]}")
            if inventory[item_name] == 0:
                del inventory[item_name]  # Remove the item completely if quantity is zero
        else:
            print("You cannot remove more than the current quantity in stock.")
    else:
        print(f"{item_name} does not exist in the inventory.")

def search_item():
    """Function to search for an item in the inventory."""
    item_name = input("\nEnter the name of the item to search: ").strip()
    if item_name in inventory:
        print(f"{item_name} is in the inventory with quantity: {inv
