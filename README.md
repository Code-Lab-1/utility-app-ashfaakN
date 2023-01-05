fruits_menu = [
    { 
    'itemname' : 'apple',
    'itemno' : 1,
    'price' : 3,
    'qty' : 4,
     },

         { 
    'itemname' : 'watermelon',
    'itemno' : 2,
    'price' : 2,
    'qty' : 2,
     },

         { 
    'itemname' : 'orange',
    'itemno' : 3,
    'price' : 2,
    'qty' : 1,
     },
     
              { 
    'itemname' : 'strawberry',
    'itemno' : 4,
    'price' : 6,
    'qty' : 3,
     },
     
              { 
    'itemname' : 'banana',
    'itemno' : 5,
    'price' : 2,
    'qty' : 1,
     },
     
         { 
    'itemname' : 'pomergranate',
    'itemno' : 6,
    'price' : 4,
    'qty' : 4,
     },

         { 
    'itemname' : 'grape',
    'itemno' : 7,
    'price' : 6,
    'qty' : 7,
     },

         { 
    'itemname' : 'blueberries',
    'itemno' : 8,
    'price' : 5,
    'qty' : 1,
     },
     
              { 
    'itemname' : 'lemon',
    'itemno' : 9,
    'price' : 1,
    'qty' : 12,
     },
     
              { 
    'itemname' : 'avocados',
    'itemno' : 10,
    'price' : 12,
    'qty' : 9,
     },
         { 
    'itemname' : 'cucumber',
    'itemno' : 11,
    'price' : 2,
    'qty' : 4,
     },

         { 
    'itemname' : 'carrot',
    'itemno' : 12,
    'price' : 2,
    'qty' : 2,
     },

         { 
    'itemname' : 'cauliflower',
    'itemno' : 13,
    'price' : 6,
    'qty' : 14,
     },
     
              { 
    'itemname' : 'cabbage',
    'itemno' : 14,
    'price' : 4,
    'qty' : 1,
     },
     
              { 
    'itemname' : 'potato',
    'itemno' : 15,
    'price' : 5,
    'qty' : 6,
     },

         { 
    'itemname' : 'tomatoes',
    'itemno' : 16,
    'price' : 4,
    'qty' : 4,
     },

         { 
    'itemname' : 'Onion',
    'itemno' : 17,
    'price' : 3,
    'qty' : 2,
     },

         { 
    'itemname' : 'broccoli',
    'itemno' : 18,
    'price' : 9,
    'qty' : 1,
     },
     
              { 
    'itemname' : 'capsicum',
    'itemno' : 19,
    'price' : 7,
    'qty' : 1,
     },
     
              { 
    'itemname' : 'lettuce',
    'itemno' : 20,
    'price' : 5,
    'qty' : 8,
     },
]

#printing fruits n veggies and logo
def fruits():
  print("--------5star-Vending-Machine--------")
  print("            -FRUITS-            ")
  fruits = {
    "01 apple" : "3 AED", 
    "02 watermelon" : "2 AED",
    "03 orange" : "2 AED",
    "04 strawberry" : "6 AED",
    "05 banana" : "2 AED",
    "06 pomergranate" : "4 AED",
    "07 grape" : "6 AED",
    "08 blueberries" : "5 AED",
    "09 lemon" : "1 AED",
    "10 avocados" : "12 AED",
}
  for item, price in fruits.items():
    print(f" {item:30}, {price}")

#printing veggies
def veggies():
  print("            -VEGGIES-            ")
  veggies_items = {
    "11 cucumber" : "2 AED", 
    "12 carrot" : "2 AED",
    "13 califlower" : "6 AED",
    "14 cabbage" : "4 AED",
    "15 potatoes" : "5 AED",
    "16 tomatoes" : "4 AED",
    "17 Onion" : "3 AED",
    "18 broccoli" : "9 AED",
    "19 capsicum" : "7 AED",
    "20 lettuce" : "5 AED",
}
#a for loop system that prints out the dictionary like a menu
  for item, price in veggies_items.items():
    print(f" {item:30}, {price}")
  print()


#printing the menu function
def menu():
  fruits()
  veggies()

#the main ordering system
def order():

  #a while loop that starts the function
  while True:
    
    #prints the menu
    menu()

    #asks user input of the credits
    credits = int(input('Please insert an amount :\n'))

    #invalid amount
    if credits <= 0:
      print('Please enter a valid amount\n')
      order()

    #asks user input of the displayed items
    iteminput = int(input('Please input the number of your desired item\n'))

    #product does not exist message
    if iteminput >= 21 or iteminput <= 0:
      print('Product does not exist or is invalid')
      
    cart = []
    total_sum = []

    for di in fruits_menu:

          #insufficient funds
          if iteminput == di['itemno'] and credits <= di['price'] :
            print('Insufficient funds, please kindly re-enter the appropriate amount\n')
            order()

          #out of stock
          if iteminput == di['itemno'] and di['qty'] <= 0:
            print(f"{di['itemname']} is currently out of stock please choose another item \n")
            order()

          #inputting the item 
          if iteminput == di['itemno'] and credits >= di['price']:

            #displays the item the user picked
            print('.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.\n')
            print(f"You picked {di['itemname']}\n")
            print('.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.\n')

            #reduces the stock quantity by 1
            di['qty'] = di.get('qty', 0) - 1

            #appends the price into the list of total_sum
            total_sum.append(di.get('price'))
            
            #appends the item into the cart
            cart.append(di.get('itemname'))

            #prints the remaining stock of the item
            print(f"Amount of {di['itemname']} remaining: {di['qty']}\n")

            #prints the the item being dispensed
            print('=======================================\n')
            print("Please take the items that has been dispensed:\n")

            #prints the cart
            print(cart, '\n')
            print('=======================================\n')

            #prints the total
            total=sum(total_sum)
            print("And here is your total amount:\n\n\t", total, "AED\n")

            #prints the change
            change = credits - total
            print("And your change is:\n\n\t", change, "AED\n")

            #prints the final message
            print('=======================================\n')
            print("Thank you for your purchase!\n")
            print('=======================================\n')
            #breaks the for loop function and starts over again
            break

#renaming the function to vending machine
def vendingmachine():
  order()

#output:
vendingmachine()

