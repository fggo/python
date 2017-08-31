* [1. Getting Started](#getting-started)
* [2. Variables and Simple Data Types](#variables-and-simple-data-types)
* [3. Introducing Lists](#introducing-lists)
* [4. Working with Lists](#working-with-lists)
* [5. if Statements](#if-statements)
* [6. Dictionaries](#dictionaries)
* [7. User Input and while loops](#user-input-and-while-loops)
* [8. Functions](#functions)
* [9. Classes](#classes)
* [10. Files and Exceptions](#files-and-exceptions)
* [11. Testing Your Code](#testing-your-code)
* [Project 1. Alien Invasion](#project-1-alien-invasion)
* [Project 2. Data Visualization](#project-2-data-visualization)
* [Project 3. Web Applications](#project-3-web-applications)

# Getting Started
```
# python is pre-installed in Ubuntu Gnome 16.04; Check versions by typing
/*use python interpreter*/
python
python3
>>> print("Hello Python interpreter!")
```

Running a python program
```
/*compile*/
python3 -m py_compile "%f"

/*execute*/
python3 "%f"
```

# Variables and Simple Data Types
```python
full_name = 'ada lovelace'
print(full_name.upper())
print(full_name.lower())
print(full_name.title())
```

White space 
```python
'\tHello'
'\nHello'

name = '  python  '
name.rstrip()
name.lstrip()
name.strip()
```

Quote inside quote
```python
msg = "monty's best friend" # ok
msg2 = 'Albert Einstein once said, \'A person who never made a mistake never tried anything new.\'' # ok
# wrong_msg = 'monty's best friend' # Error!
```

Arithmetic + - * / exponential **
```python
booleanVal = (9 == 3 ** 2) # True
```

Floating number
```python
.1 + .1 # .2000000000001
```

Avoid type errors
```python
age = 23
message = "Happy " + str(age) + "rd Birthday!"
```

Integers in python2
```python
# this does not apply in python3
3/2 # 1
3.0/2 # 1.5
3/2.0 # 1.5
3.0/2.0 # 1.5
```

Comments
```python
# this is a python line comment
```

```
this is a
python block
comment
```

The Zen of Python
```python
import this
```

# Introducing Lists
```python
bicycles = ['trek', 'cannondale', 'redline', 'specialized']
print(bicycles) # ['trek', 'cannondale', 'redline', 'specialized']
print(bicycles[0].title()) # 'Trek'
print(bicycles[-1]) # 'specialized'
```

append(str)
```python
fruit = ['apple', 'orange', 'grapes', 'blueberry', 'watermelon']
fruit[2] = 'grapefruit' # change
fruit.append('strawberry') # add
```

insert(i, str)
```python
fruit = ['apple', 'orange', 'grapes', 'blueberry', 'watermelon']
fruit.insert(0, 'banana') # add at the beginning
fruit.insert(len(fruit) - 1, 'melon') # add at the end
```

del list[i]
```python
fruit = ['apple', 'orange', 'grapes', 'blueberry', 'watermelon']
del fruit[1] # remove 1st element
```

pop() removes and returns the last element 
```python
motorcycles = ['honda', 'yamaha', 'suzuki']
last_owned = motorcycles.pop()
print("The last motorcycle I owned was a " + last_owned.title() + ".") # 'suzuki'
print(motorcycles)
```

pop(i) removes and returns the i th element
```python
motorcycles = ['honda', 'yamaha', 'suzuki']
first_owned = motorcycles.pop(0)
print('The first motorcycle I owned was a ' + first_owned.title() + '.')
```

remove(str) remove item by specifying the value
```python
motorcycles = ['honda', 'yamaha', 'suzuki', 'ducati']
motorcycles.remove('honda')
print(motorcycles)
    
too_expensive = 'ducati'
motorcycles.remove(too_expensive)
print(motorcycles)
print("\nA " + too_expensive.title() + " is too expensive for me.")
```

The remove(str) deletes only the first occurrence of the value you specify. If there’s a possibility the value appears more than once in the list, you’ll need to use a loop to determine if all occurrences of the value have been removed. You’ll learn how to do this in Chapter 7.

sort()
```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort()
print(cars)
```

sort(reverse = True)
```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort(reverse = True) # sort and reverse
print(cars)
```

sorted(list) for sorting temporarily
```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
print('Sorted List: ')
print(sorted(cars))
print('Original List: ')
print(cars)
```

sorted(list, reverse = True) in reverse order
```python
loc = ['tokyo', 'los angeles', 'new york', 'seoul']
print(sorted(loc, reverse = True))
print(loc)
```

Sorting a list alphabetically is a bit more complicated when all the values are not in lowercase. There are several ways to interpret capital letters when you’re deciding on a sort order, and specifying the exact order can be more complex than we want to deal with at this time. However, most approaches to sorting will build directly on what you learned in this section.

reverse()
```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
print(cars)
cars.reverse() # reverse only, but it does not sort
print(cars)
```

len()
```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
len(cars)
```

Avoiding index errors
```python
cars = ['honda', 'audi']
print(cars[2]) # index error
cars = []
print(cars[0]) # index error
```

# Working with Lists
```python
magicians = ['alice', 'david', 'carolina']
for magician in magicians:
    print(magician.title() + ", that was a great trick!")
    print("I can't wait to see your next trick, " + magician.title() + ".\n")
print("Thank you, everyone. That was a great magic show!")
```

Avoiding Indentation Errors
```python
# forget to indent
magicians = ['alice', 'david', 'carolina']
for magician in magicians:
    print(magician)
print("show me next trick, " + magician.title() + ".\n") # error!

# unnecessarily indent
message = 'Hello world!'
    print(message) # error!

# unnecessarily indent 2
for magician in magicians:
    print(magician)

    print("Thank you, everyone. That was a great magic show!") # considered as inside for loop

# forgotten the colon
for magician in magicians # error!
    print(magician)
```

Numerical Lists
```python
for value in range(1, 6):
    print(value) # 1\n2\n3\n4\n5

numbers = list(range(1,6))
print(numbers) # [1, 2, 3, 4, 5]

even_numbers = list(range(2,11, 2))
print(even_numbers)# [2, 4, 6, 8, 10]

# square numbers from 1 to 11 and make it as a list
squares = []
for value in range(1, 11):
    squares.append(value ** 2)
print(squares) # [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

min(list) max(list) sum(list)
```python
digits = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
minVal = min(digits)
maxVal = max(digits)
sumVal = sum(digits)
```

List Comprehensions
```python
# allows you to generate the same list in just one line of code.
squares = [value ** 2 for value in range(1, 11)]
print(squares) # [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

cubes = [value ** 3 for value in range(1, 11)]
print(cubes) # [1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]
```

Slicing a list
```python
players = ['charles', 'martina', 'michael', 'florence', 'eli']
print(players[0:3]) # ['charles', 'martina', 'michael']
print(players[:4]) # ['charles', 'martina', 'michael', 'florence']
print(players[2:]) # ['michael', 'florence', 'eli']

for player in players[:3]:
    print(player.title()) # Charles Martina Michael
```

Copying a list
```python
my_foods = ['pizza', 'falafel', 'carrot cake']
friend_foods = my_foods[:]

my_foods.append('cannoli')
friend_foods.append('ice cream')

print("My favorite foods are:")
print(my_foods) # ['pizza', 'falafel', 'carrot cake', 'cannoli']
print("\nMy friend's favorite foods are:")
print(friend_foods) # ['pizza', 'falafel', 'carrot cake', 'ice cream']
```

Copying a list using assignment (not working as expected) 
```python
my_foods = ['pizza', 'falafel', 'carrot cake']
friend_foods = my_foods # this does not work because now both variables points to the same list

my_foods.append('cannoli')
friend_foods.append('ice cream')

print("My favorite foods are:")
print(my_foods) # ['pizza', 'falafel', 'carrot cake', 'cannoli', 'ice cream']
print("\nMy friend's favorite foods are:")
print(friend_foods) # ['pizza', 'falafel', 'carrot cake', 'cannoli', 'ice cream']
```

Tuples
```python
# However, sometimes you’ll want to create a list of items that cannot change. Tuples allow you to do just that.
# Python refers to values that cannot change as immutable, and an immutable list is called a tuple.
dimensions = (200, 50)
for dimension in dimensions:
    print(dimension)
dimensions[0] = 250 # error! immutable!
```

assign new tuples
```python
dimensions = (200, 50)
print("Original dimensions:")
for dimension in dimensions:
    print(dimension) # 200 50

dimensions = (400, 100)
print("\nModified dimensions:")
for dimension in dimensions:
    print(dimension) # 400 100
```
When compared with lists, tuples are simple data structures. Use them when you want to store a set of values that should not be changed throughout the life of a program.

## Styling Your Code
1. indent four spaces with tab key to avoid unpredictable errors
2. line length less than 72 or 80 
3. it’s appropriate to place a blank line between the two sections (no more than two blank lines)
4. PEP8 style guide (https://python.org/dev/peps/pep-0008/)

# if Statements
```python
cars = ['audi', 'bmw', 'subaru', 'toyota']
for car in cars:
    if car == 'bmw':
        print(car.upper())
    else:
        print(car.title())
```

Conditional Tests
```python
car = 'Audi'
car == 'bmw'.upper() # False
car.lower() == 'audi' # True

requested_topping = 'mushrooms'
if requested_topping != 'anchovies':
    print("Hold the anchovies!")

age = 18
if age == 18:
    print("You're 18 years old")
if age > 18:
    print("You're old")
if age < 18:
    print("You're too young")
if age <= 18:
    print("You're 18 years old or younger")

age_0 = 22
age_1 = 18

if (age_0 >= 21) and (age_1 >= 21):
    print('both of you are 21 years old or older')
if (age_0 >= 21) or (age_1 >= 21):
    print('either of you are 21 years old or older')

requested_toppings = ['mushrooms', 'onions', 'pineapple']
if 'mushrooms' in requested_toppings:
    print('mushrooms are in the toppings')
if 'mushrooms' not in requested_toppings:
    print('mushrooms are not in the toppings')
```

Boolean Expressions
```python
game_active = True
can_edit = False
```

if elif else block
```python
age = 12
if age < 4:
    price = 0
elif age < 18:
    price = 5
elif age < 65:
    price = 10
else:
    price = 5

print("Your admission cost is $" + str(price) + ".")
```

Omitting the else block; Python does not require an else block at the end of an if- elif chain. Sometimes an else block is useful; sometimes it is clearer to use an additional elif statement that catches the specific condition of interest
```python
age = 12
if age < 4:
    price = 0
elif age < 18:
    price = 5
elif age < 65:
    price = 10
elif age >= 65:
    price = 5

print("Your admission cost is $" + str(price) + ".")
```


Testing Multiple conditions
```python
# Sometimes it’s important to check all of the conditions of interest, rather than checking one specific condition
requested_toppings = ['mushrooms', 'extra cheese']

if 'mushrooms' in requested_toppings:
    print("Adding mushrooms.")
if 'pepperoni' in requested_toppings:
    print("Adding pepperoni.")
if 'extra cheese' in requested_toppings:
    print("Adding extra cheese.")

print("\nFinished making your pizza!")
```

Using if statement with Lists
```python
requested_toppings = ['mushrooms', 'green peppers', 'extra cheese']
for requested_topping in requested_toppings:
    if requested_topping == 'green peppers':
        print("Sorry, we are out of green peppers right now.")
    else:
        print("Adding " + requested_topping + ".")

print("\nFinished making your pizza!")
```

Checking that a list is not Empty
```python
# Python returns True if the list contains at least one item; an empty list evaluates to False.
requested_toppings = []
if requested_toppings:
    for requested_topping in requested_toppings:
        print("Adding " + requested_topping + ".")
    print("\nFinished making your pizza!")
else:
    print("Are you sure you want a plain pizza?")
```

Using multiple lists
```python
available_toppings = ['mushrooms', 'olives', 'green peppers', 'pepperoni', 'pineapple', 'extra cheese']
requested_toppings = ['mushrooms', 'french fries', 'extra cheese']
for requested_topping in requested_toppings:
    if requested_topping in available_toppings:
        print("Adding " + requested_topping + ".")
    else:
        print("Sorry, we don't have " + requested_topping + ".")

print("\nFinished making your pizza!")
```

Try it yourself
```python
# 5-10
current_users = ['foo', 'bar']
new_users = ['FOo', 'baR', 'AAa', 'Bbb', 'ccc']
for user in new_users:
    if user.upper() in [cur_user.upper() for cur_user in current_users]:
        print("Hey! Your username, " + user + " is already in use!")
    else:
        print("Your username, " + user + " is available to use!")

# 5-11
numbers = range(1, 11)
read = ''
for num in numbers:
    if num == 1:
        read = '1st'
    elif num == 2:
        read += ' 2nd'
    elif num == 3:
        read += ' 3rd'
    else:
        read += (' ' + str(num) + 'th')
print(read)
```

# Dictionaries
A dictionary in Python is a collection of key-value pairs. Each key is connected to a value, and you can use a key to access the value associated with that key. In fact, you can use any object that you can create in Python as a value in a dictionary.
```python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0['color'])
print(alien_0['points'])

new_points = alien_0['points']
print("You just earned " + str(new_points) + " points!")
```

Adding New Key-Value pairs
```python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0) # {'color': 'green', 'points': 5}
alien_0['x_position'] = 0
alien_0['y_position'] = 25
print(alien_0) # {'color': 'green', 'points': 5, 'y_position': 25, 'x_position': 0}
```

Starting with an empty dictionary
```python
alien_0 = {} # alien_0 = dict()
alien_0['color'] = 'green'
alien_0['points'] = 5
print(alien_0) # {'color': 'green', 'points': 5}
```

Modifying Values in a dictionary
```python
alien_0 = {'x_position' : 0, 'y_position' : 25, 'speed' : 'medium', 'color' : 'green'}

# change color
print("The alien is " + alien_0['color'] + ".")
alien_0['color'] = 'yellow'
print("The alien is now " + alien_0['color'] + ".")

# change position
print("Original x-position: " + str(alien_0['x_position']))
if alien_0['speed'] == 'slow':
    x_increment = 1
elif alien_0['speed'] == 'medium':
    x_increment = 2
elif alien_0['speed'] == 'fast':
    x_increment = 3
alien_0['x_position'] += x_increment
# Python variables are scoped to the innermost function or module; control blocks like if and while blocks don't count. (IIUC, this is also how JavaScript's var-declared variables work.)
print("New x-position: " + str(alien_0['x_position']))
```

Removing Key-Value pairs
```python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)
del alien_0['points'] # remove key-value pair
print(alien_0)
```

A Dictionary of Similar Objects
```python
# When you know you’ll need more than one line to define a dictionary, 
# press enter after the opening brace. Then indent the next line one level 
# (four spaces), and write the first key-value pair, followed by a comma. 
# This example also shows how you can break up a long print statement
# over several lines.
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
}
print("Sarah's favorite language is " +
      favorite_languages['sarah'].title() +
      ".")
```

Looping Through a Dictionary
```python
# 1. Looping through all Key-Value pairs
# Notice again that the key-value pairs are not returned in the order in which they were stored, even when looping through a dictionary. Python doesn’t care about the order in which key-value pairs are stored; it tracks only the connections between individual keys and their values.
user_0 = {
    'username': 'raboof',
    'first': 'foo',
    'last': 'bar',
}
for key, value in user_0.items():
    print('\nKey: ' + key)
    print('Value: ' + value)

favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
}
for name, language in favorite_languages.items():
    print(name.title() + "'s favorite language is " + language.title() + ".")

# 2-1. Looping Through All the Keys in a Dictionary
for name in favorite_languages.keys():
    print(name.title())

for name in favorite_languages: # is actually the default behavior when looping through a dictionary
    print(name.title())

friends = ['phil', 'sarah']
for name in favorite_languages.keys():
    print(name.title())
    if name in friends:
        print(" Hi " + name.title() 
        + ", I see your favorite language is " 
        + favorite_languages[name].title() + "!")

if 'erin' not in favorite_languages.keys():
    print("Erin, please take our poll!")

# 2-2. Looping Through a Dictionary’s Keys in Order
for name in sorted(favorite_languages.keys()):
    print(name.title() + ", thank you for taking the poll.")

# 3-1. Looping Through All Values in a Dictionary
# This approach pulls all the values from the dictionary without checking for repeats.
print("The following languages have been mentioned:")
for language in favorite_languages.values():
    print(language.title())

# 3-2. To see each language chosen without repetition, we can use a set. A set is similar to a list except that each item in the set must be unique:
print("The following languages have been mentioned:")
for language in set(favorite_languages.values()):
    print(language.title())
```

Nesting

1. A List of Dictionaries
```python
# A List of Dictionaries
alien_0 = {'color': 'green', 'points': 5}
alien_1 = {'color': 'yellow', 'points': 10}
alien_2 = {'color': 'red', 'points': 15}
aliens = [alien_0, alien_1, alien_2]
for alien in aliens:
    print(alien)

# Make an empty list for storing aliens.
aliens = []
# Make 30 green aliens.
for alien_number in range(30):
    new_alien = {'color': 'green', 'points': 5, 'speed': 'slow'}
    aliens.append(new_alien)
# Show the first 5 aliens:
for alien in aliens[:5]:
    print(alien)
print("...")
# Show how many aliens have been created.
print("Total number of aliens: " + str(len(aliens)))

# Imagine that one aspect of a game has some aliens changing color and moving faster as the game progresses. When it’s time to change colors, we can use a for loop and an if statement to change the color of aliens.
aliens = []

for i in range(30):
    alien = {
        'color': 'green',
        'speed': 'slow',
        'point': 5,
    }
    aliens.append(alien)

for alien in aliens[:3]:
    if alien['color'] == 'green':
        alien['color'] = 'yellow'
        alien['speed'] = 'medium'
        alien['point'] = 10
    elif alien['color'] == 'yellow':
        alien['color'] = 'red'
        alien['speed'] = 'fast'
        alien['point'] = 15
for alien in aliens[:5]:
    print(alien)
```

2. A List in a Dictionary
```python
pizza = {
    'crust': 'thick',
    'toppings': ['mushroom', 'extra cheese'],
}
print('You ordered a ' + pizza['crust'] + '-crust pizza with the following toppings: ')
for topping in pizza['toppings']:
    print('\t' + topping)

favorite_languages = {
    'jen': ['python', 'ruby'],
    'sarah': ['c'],
    'edward': ['ruby', 'go'],
    'phil': ['python', 'haskell'],
}
for name, languages in favorite_languages.items():
    print('\n' + name.title() + "'s favorite languages are: ")
    for lang in languages:
        print('\t' + lang)
```
You should not nest lists and dictionaries too deeply. If you’re nesting items much deeper than what you see in the preceding examples or you’re working with someone else’s code with significant levels of nesting, most likely a simpler way to solve the problem exists.


3. Dictionary in a Dictionary
```python
users = {
    'aeinstein': {
        'first' : 'albert',
        'last': 'einstein',
        'location': 'princeton',
    },
    'mcurie': {
        'first': 'marie',
        'last': 'curie',
        'location': 'paris',
    }
}

for username, user_info in users.items():
    print('\nUsername: ' + username)
    full_name = user_info['first'] + user_info['last']
    
    print('\tFull name: ' + full_name.title())
    print('\tLocation: ' + user_info['location'].title())
```

```python
# 6-9
favorite_places = {
    'foo': ['los angeles', 'house', 'home'],
    'bar': ['new york', 'mama', 'lalala'],
    'fugu': ['san francisco', 'dadada', 'wiwiwi'],
}
for key in favorite_places.keys():
    print(key + "'s favorite place: ")
    for place in favorite_places[key]:
        print('\t' + place)
```
# User Input and while loops
```python
prompt = "If you tell us who you are, we can personalize the messages you see."
prompt += "\nWhat is your first name? "
name = input(prompt)
print("\nHello, " + name + "!")
```

int()
```python
height = input("How tall are you, in inches? ") # store string value '71' 
height = int(height) # converted to integer 71 
if height >= 36:
    print("\nYou're tall enough to ride!")
else:
    print("\nYou'll be able to ride when you're a little older.")
```

The Modulo Operator
```python
number = input("Enter a number, and I'll tell you if it's even or odd: ")
number = int(number)
if number % 2 == 0:
    print("\nThe number " + str(number) + " is even.")
else:
    print("\nThe number " + str(number) + " is odd.")
```

Accepting Input in Python 2.7
- If you’re using Python 2.7, you should use the raw_input() function when prompting for user input. This function interprets all input as a string, just as input() does in Python 3.

Introducing while loops
```python
current_number = 1
while current_number <= 5:
    print(current_number)
    current_number += 1

prompt = '\nTell me something, and I will repeat it back to you: '
prompt += "\nEnter 'quit' or 'q' to end the program."
message = ""
while message != 'quit' and message != 'q':
    message = input(prompt)
    if message != 'quit' and message != 'q':
        print(message)
```

Using a Flag
```python
flag = True
while flag:
    message = input("\nEnter anything. 'q' to quit: ")
    if  message == 'q':
        flag = False
    else:
        print(message)
```

Use break to Exit a Loop
```python
while True:
    city = input("\nEnter a city you would like to visit. 'q' to quit: ")
    if city == 'q':
        break
    else:
        print('I would like to visit ' + city.title() + '!')
```

Use continue in a Loop
```python
# Rather than breaking out of a loop entirely without executing the rest of its code, you can use the continue statement to return to the beginning of the loop based on the result of a conditional test.
current_number = 0
while current_number < 10:
    current_number += 1
    if current_number % 2 == 0:
        continue
    print(current_number)
```

Avoiding Infinite Loops
```python
# This loop runs forever!
x = 1
while x <= 5:
    print(x)
    # x += 1
```


Using a while Loop with Lists and Dictionaries

Moving Items from One List to Another
```python
# Start with users that need to be verified,	
# and an empty list to hold confirmed users.
unconfirmed_users = ['alice', 'brian', 'candace']
confirmed_users = []

# Verify each user until there are no more unconfirmed users.
# Move each verified user into the list of confirmed users.
while unconfirmed_users:
    current_user = unconfirmed_users.pop()
    
    print("Verifying user: " + current_user.title())
    confirmed_users.append(current_user)

# Display all confirmed users.
print("\nThe following users have been confirmed:")
for confirmed_user in confirmed_users:
    print(confirmed_user.title())
```

Removing All Instances of Specific Values from a List
```python
pets = ['dog', 'cat', 'dog', 'goldfish', 'cat', 'rabbit', 'cat']
print(pets)

while 'cat' in pets:
    pets.remove('cat')

print(pets)
```

Filling a Dictionary with User Input
```python
responses = {}
active = True
while active:
    name = input("\nWhat's your name? ")
    mountain = input('Which mountain do you want to climb? ')
    responses[name] = mountain
    answer = input('do you want us to add another person? (yes/no) ')
    if answer.lower() == 'no':
        active = False
print('\nPolling result >>>>>>')
for name, mountain in responses.items():
    print(name + ' would like to climb ' + mountain + '.')
```

```python
sandwich_orders = ['peanut', 'pastrami', 'cheese', 'pastrami',
                   'burrito', 'pastrami']

print('Sorry guys but, we ran out of pastrami sandwiches.')
while 'pastrami' in sandwich_orders:
    sandwich_orders.remove('pastrami')

finished_sandwiches = []

while sandwich_orders:
    order = sandwich_orders.pop()
    print("we're making your " + order + ' sandwich. Please Wait.')
    finished_sandwiches.append(order)

print('\nFinished dishes : ')
print('\t' + str(finished_sandwiches))
```

# Functions
