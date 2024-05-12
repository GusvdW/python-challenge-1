# python-challenge-1
menu_itmes = {
    "Snacks": {
        "Cookie": .99,
        "Banana": .69,
        "Apple": .49,
        "Granola bar": 1.99
    },
    "Meals": {
        "Burrito": 4.49,
        "Teriyaki Chicken": 9.99,
        "Sushi": 7.49,
        "Pad Thai": 6.99,
        "Pizza": {
            "Cheese": 8.99,
            "Pepperoni": 10.99,
            "Vegetarian": 9.99
        },
        "Burger": {
            "Chicken": 7.49,
            "Beef": 8.49
        }
    },
    "Drinks": {
        "Soda": {
            "Small": 1.99,
            "Medium": 2.49,
            "Large": 2.99
        },
        "Tea": {
            "Green": 2.49,
            "Thai iced": 3.99,
            "Irish breakfast": 2.49
        },
        "Coffee": {
            "Espresso": 2.99,
            "Flat white": 2.99,
            "Iced": 3.49
        }
    },
    "Dessert": {
        "Chocolate lava cake": 10.99,
        "Cheesecake": {
            "New York": 4.99,
            "Strawberry": 6.49
        },
        "Australian Pavlova": 9.99,
        "Rice pudding": 4.99,
        "Fried banana": 4.49
    }
}

customer_order = []
def main_menu():
    print("Main Menu:")
    print("1. View Sub Menu")
    print("2.Exit")


def print_submenu():
    print ("Sub Menu:")
    print ("1. Option 'Snacks'")
    print ("2. Option 'Meals'")
    print ("3. Option 'Drinks'")
    print ("4. Option 'Dessert'")

menu_items = {
    1: {"name": "Cookie", "price": .99},
    2: {"name": "Banana", "price": .69},
    3: {"name": "Apple", "price": .49},
    4: {"name": "Grenola Bar", "price": 1.99}
}

order_list = []
main_menu: any

customer_choice = input("Enter your choice: ")
if customer_choice == '1':
    print_submenu()
    print(menu_items)
    menu_selection = input("Enter your selection from the sub-menu: ")
    
    if menu_selection.isdigit():
        menu_selection = int(menu_selection)
        if menu_selection in menu_items:
            item_name = menu_items [menu_selection]["name"]
            item_price = menu_items [menu_selection]["price"]
            quantity_input = input (f"Enter the quantity for {item_name}: ")
            if quantity_input.isdigit():
                quantity = int(quantity_input)
            else:
                print("Invalid selection. Minimum quantity is 1")
                quantity = 1
            order_list.append({"Item name": item_name, "Price": item_price, "Quantity": quantity})                  
            print("Order Added Successfully")                    
         
        if menu_selection in menu_items:
            print("You selected:", menu_items[menu_selection])
        else:
            print("Invalid Selection. Please choose another option")
    else:
        print("Invalid input. Please enter a number.")
elif customer_choice == '2':
    print("Exiting...Thank You") 
else:
    print("Invalid Selection")

while True:
    place_order = False
    continue_order = input("Would you like to order again? (Y/N): ")
    match continue_order.lower():
        case 'y':
            place_order = True
        case 'n':
            print ("Thanks for your order")
            break
        case _:
            print("Invalid Input. Please re-enter 'Y' or 'N'.")
    if place_order:
        print(menu_items) 
        menu_selection = input("Enter your selection from the sub-menu: ")
        if menu_selection.isdigit():
            menu_selection = int(menu_selection)
        if menu_selection in menu_items:
            item_name = menu_items [menu_selection]["name"]
            item_price = menu_items [menu_selection]["price"]
            quantity_input = input (f"Enter the quantity for {item_name}: ")
            if quantity_input.isdigit():
                quantity = int(quantity_input)
            else:
                print("Invalid selection. Minimum quantity is 1")
                quantity = 1
            order_list.append({"Item name": item_name, "Price": item_price, "Quantity": quantity})                  
            print("Order Added Successfully")                    
         
        if menu_selection in menu_items:
            print("You selected:", menu_items[menu_selection])
        else:
            print("Invalid Selection. Please choose another option")
    else:
        print("Invalid input. Please enter a number.")

else:
    print("Invalid Selection")


item_name_format = "{:30}"
price_format = "{:^8}"
quantity_format = "{:>10}"
line_format = "-" * 31 + "|" + "-" * 10 + "|" + "-" * 11

for order in order_list:
    item_name = order ["Item name"]
    price = order["Price"]
    quantity = order["Quantity"]

    item_name_spaces = " " * (30 - len(item_name))
    price_spaces = " " * (8 - len(str(price)))
    quantity_spaces = " " * (10 - len(str(quantity)))

    receipt_line = f"{item_name_format.format(item_name)} | {price_format.format(price)} | {quantity_format.format(quantity)}"
    print(receipt_line)

print(line_format)

total_price = sum(order["Price"] * order["Quantity"] for order in order_list)
print(f"Total Price: {total_price:2f}")
