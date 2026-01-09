<h1>Menu</h1>

Create a dictionary to manage items on a menu. Allow the user to insert, update, and delete items from the dictionary.

Parameter: None
Return value: None
def displayChoices():
    print()
    print("Manage the Menu")
    print("\ta) Add a menu item")
    print("\tb) Update the price")
    print("\tc) Show the price")
    print("\td) Delete a menu item")
    print("\te) Show the menu")
    print("\tx) Exit")

# Parameter: numStr is a string containing input from the user
# Return value: a Boolean (True or False) depending on whether numStr contains a
# float
def isFloat(numStr):
    numStr = numStr.replace(".", "", 1)
    if numStr.isdigit():
        return True
    else:
        return False

# Parameter: menuDict is a dictionary representing the menu
# Return value: None
def addItem(menuDict):
    foodItem = input("Enter a food item to add: ")
    foodItem = foodItem.strip()  # get rid of the new line
    foodItem = foodItem.title()
    if foodItem not in menuDict:
        priceInput = input("Enter the price: ")
        while not isFloat(priceInput):
            priceInput = input("Enter the price: ")
        convertFloat = float(priceInput)
        menuDict[foodItem] = convertFloat
        print(foodItem, "has been added to the menu!!")
    else:
        print(foodItem, "is already on the menu!!!")

# Parameter: menuDict is a dictionary representing the menu
# Return value: None
def updatePrice(menuDict):
    foodItem = input("Enter a food item to update: ")
    foodItem = foodItem.strip()  # get rid of the new line
    foodItem = foodItem.title()
    if foodItem in menuDict:
        print(foodItem, " costs $", menuDict[foodItem], sep="")
        newPrice = input("Enter the price: ")
        newPrice = newPrice.strip()
        while not isFloat(newPrice):
            newPrice = input("Enter the price: ")
        menuDict[foodItem] = newPrice
        print(foodItem, " now costs $", str(newPrice), sep="")
    else:
        print(foodItem, "is not in the menu")

# Parameter: menuDict is a dictionary representing the menu
# Return value: None
def showPrice(menuDict):
    findItem = input("Enter a food item to find: ")
    findItem = findItem.strip()  # get rid of the new line
    findItem = findItem.title()
    if findItem in menuDict:
        print(findItem, " costs $", str(menuDict[findItem]), sep="")
    else:
        print(findItem, "is not on the menu")

# Parameter: menuDict is a dictionary representing the menu
# Return value: None
def deleteItem(menuDict):
    foodItem = input("Enter a food item to find: ")
    foodItem = foodItem.strip()  # get rid of the new line
    foodItem = foodItem.title()
    if foodItem in menuDict:
        del menuDict[foodItem]
        print(foodItem, "was deleted from the menu")
    else:
        print(foodItem, "is not on the menu")

# Parameter: menuDict is a dictionary representing the menu
# Return value: None
def showMenu(menuDict):
    for menu in menuDict:
        value = menuDict[menu]
        print(menu, "costs $" + str(value))

def main():
    foodItems = {"Chicken":9.99, "Pizza":8.99, "Hamburger":8.99, "Coffee":4.49, "Tea":2.49}
    userInput = "" # it is a do while loop, create a variable and test against the variable
    while userInput != "x": # this tells us that the input is not x at all
        displayChoices()
        userInput = input("Choice: ")
        userInput = userInput.strip()
        userInput = userInput.lower()
        if userInput == "a":
            addItem(foodItems)

        elif userInput == "b":
            updatePrice(foodItems)

        elif userInput == "c":
            showPrice(foodItems)

        elif userInput == "d":
            deleteItem(foodItems)

        elif userInput == "e":
            showMenu(foodItems)
        elif userInput == "x":
            print("Thank you!!")
        else:
            print("Invalid choice")

main()
