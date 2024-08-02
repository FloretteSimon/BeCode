#Let's built a robot barista

print("Hello, welcome to Bibi's Coffee!")

#name
name = input("What is your name?\n")

if name == "Ben" or name == "Patricia":
    evil = input("Are you evil?\n")
    deeds = int(input("How many good deeds have you done today? "))
    if evil == "Yes" and deeds < 4:
        print("You're not welcome here " + name + "!!")
        exit()
    else:
        print("You can come today evil  " + name + "!!")

else:
    print("Hello " + name + " thank you for coming today.")


#order

menu = "Americano \nCapuccino \nIced Coffee\n"

print("Here is the menu:\n" + menu)

order = input("What do you want to order? ")

if order == "Americano" or order == "Capuccino" or order == "Iced Coffee":
    quantity = input("How many coffee would you like to order? ")
else:
    print("Sorry, we don't have that option.")
    exit()
#price
if order == "Americano":
    Cream = input("Do you want cream? ")
    if Cream == "Yes":
        price = 7
    else:
        price = 6
elif order == "Capuccino":
    Cream = input("Do you want cream? ")
    if Cream == "Yes":
        price = 9
    else:
        price = 8
elif order == "Iced Coffee":
    Cream = input("Do you want cream? ")
    if Cream == "Yes":
        price = 13
    else:
        price = 12


total = price * int(quantity)

print("Thank you for ordering " + quantity +" "+ order + " the price is " + str(total) + "€")
