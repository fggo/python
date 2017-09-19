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
# python is pre-installed in Ubuntu 16.04; Run python interpreter and check versions by typing
python
python3

# compile
python3 -m py_compile "%f"

# execute
python3 "%f"
```

# Variables and Simple Data Types
```python
str_0 = 'ada lovelace'
print(str_0.upper())
print(str_0.lower())
print(str_0.title())

# White spaces
'\tHello'
'\nHello'

name = '  python  '
name.rstrip()
name.lstrip()
name.strip()

# Quote inside quote
ok_msg = "monty's best friend"
ok_msg2 = 'Albert Einstein once said, \'A person who never made a mistake never tried anything new.\''
# wrong_msg = 'monty's best friend' # Error!
```

## operator
```python
# Arithmetic operator + - * /
# Exponential operator **
bool_0 = (1 + 1 == 3) # False
bool_1 = (9 == 3 ** 2) # True

# Floating number
.1 + .1 # .2000000000001
```

## Avoid type errors
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
"""
this is a
python block
comment
"""
```

The Zen of Python
```python
import this
```

# Introducing Lists
```python
bicycles = ['trek', 'cannondale', 'redline', 'specialized']
print(bicycles) # print entire list
print(bicycles[0].title()) # 'Trek'
print(bicycles[-1]) # 'specialized'

bicycles[2] = 'electric bike' # change an element
```

## list methods
```python
""" append(str) """
fruit = ['apple', 'orange', 'grapes', 'blueberry', 'watermelon']
fruit.append('strawberry') # append at the end

""" insert(i, str) """
fruit.insert(0, 'banana') # add at the beginning
fruit.insert(len(fruit) - 1, 'melon') # add at the end

""" del list[i] """
fruit = ['apple', 'orange', 'grapes', 'blueberry', 'watermelon']
del fruit[1] # remove first element

""" pop() """
motorcycles = ['honda', 'yamaha', 'suzuki']
last_owned = motorcycles.pop() # remove and return the last element
print("The last motorcycle I owned was a " + last_owned.title() + ".") # 'suzuki'
print(motorcycles)

""" pop(i) removes and returns the i th element """"
first_owned = motorcycles.pop(0)
print('The first motorcycle I owned was a ' + first_owned.title() + '.')

""" remove(str) remove item by specifying the value.
remove(str) deletes only the first occurrence of the value you specify.
use a loop to determine if all occurrences have been removed. """
motorcycles.remove('honda')
print(motorcycles)

too_expensive = 'ducati'
motorcycles.remove(too_expensive)
print(motorcycles)
print("\nA " + too_expensive.title() + " is too expensive for me.")

""" sort() """
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort()
print(cars)

""" sort(reverse = True) """
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort(reverse = True) # sort and reverse
print(cars)

""" sorted(list) for sorting temporarily """
cars = ['bmw', 'audi', 'toyota', 'subaru']
print('Sorted List: ')
print(sorted(cars))
print('Original List: ')
print(cars)

""" sorted(list, reverse = True) """
loc = ['tokyo', 'los angeles', 'new york', 'seoul']
print(sorted(loc, reverse = True)) # in reverse order
print(loc)

""" sorting alphabetically when some values are not in lowercase. """
loc = ['tokyo', 'los angeles', 'New York', 'Seoul'] # reassign
sorted(loc, key=str.lower) # sorted disregarding lower/uppercase preferences

""" reverse() """
cars = ['bmw', 'audi', 'toyota', 'subaru']
print(cars)
cars.reverse() # reverse only, but it does not sort
print(cars)

""" len() """
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
- missing or unnecessary indentation
- missing colons

## Numerical Lists
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


# min(list) max(list) sum(list)
digits = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
min_val = min(digits)
max_val = max(digits)
sum_val = sum(digits)
```

## List Comprehensions
```python
# allows you to generate the same list in just one line of code.
squares = [value ** 2 for value in range(1, 11)]
print(squares) # [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

cubes = [value ** 3 for value in range(1, 11)]
print(cubes) # [1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]
```

## Slicing a list
```python
players = ['charles', 'martina', 'michael', 'florence', 'eli']
print(players[0:3]) # ['charles', 'martina', 'michael']
print(players[:4]) # ['charles', 'martina', 'michael', 'florence']
print(players[2:]) # ['michael', 'florence', 'eli']

for player in players[:3]:
    print(player.title()) # Charles Martina Michael
```

## Copying a list
```python
my_foods = ['pizza', 'falafel', 'carrot cake']
friend_foods = my_foods[:]

my_foods.append('cannoli')
friend_foods.append('ice cream')

print(my_foods) # ['pizza', 'falafel', 'carrot cake', 'cannoli']
print(friend_foods) # ['pizza', 'falafel', 'carrot cake', 'ice cream']
```

Copying a list using assignment (not working as expected)
```python
my_foods = ['pizza', 'falafel', 'carrot cake']
friend_foods = my_foods # both variables point to the same list

my_foods.append('cannoli')
friend_foods.append('ice cream')

print(my_foods) # ['pizza', 'falafel', 'carrot cake', 'cannoli', 'ice cream']
print(friend_foods) # ['pizza', 'falafel', 'carrot cake', 'cannoli', 'ice cream']
```

## Tuples
```python
# sometimes you’ll want to create a list of items that cannot change.
# tuple is an immutable(values that cannot change) list;
dimensions = (200, 50)
for dimension in dimensions:
    print(dimension)
dimensions[0] = 250 # error! immutable!
```

assign new tuples
```python
dimensions = (200, 50)
for dimension in dimensions:
    print(dimension) # 200 50

dimensions = (400, 100)
for dimension in dimensions:
    print(dimension) # 400 100
```
When compared with lists, tuples are simple data structures. Use them when you want to store a set of values that should not be changed throughout the life of a program.

Styling Your Code
1. indent 4 spaces with tab key to avoid unpredictable errors
2. line length less than 72 or 80 
3. place a blank line between the two sections (no more than 2 blank lines)
4. [PEP8 style guide](https://python.org/dev/peps/pep-0008/)

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
test_0 = car.upper() == 'bmw'.upper() # False
test_1 = car.lower() == 'audi' # True

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

Omitting the else block; Sometimes it is clearer to use an additional elif statement 
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
# check all of the conditions of interest, rather than checking one specific condition
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
    if user.upper() in [user.upper() for user in current_users]:
        print("Hey! Your username, " + user + " is already in use!")
    else:
        print("Your username, " + user + " is available to use!")

# 5-11
numbers = range(1, 11)
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
collection of key-value pairs. Each key is connected to a value, and you can use a key to access the value associated with that key. In fact, you can use any object that you can create in Python as a value in a dictionary.
```python
alien = {'color': 'green', 'points': 5}
print(alien) # {'color': 'green', 'points': 5}
print(alien['color'])
print(alien['points'])

new_points = alien['points']
print("You just earned " + str(new_points) + " points!")

""" Adding New Key-Value pairs """
alien['x_position'] = 0
alien['y_position'] = 25
print(alien) # {'color': 'green', 'points': 5, 'y_position': 25, 'x_position': 0}

""" Starting with an empty dictionary """
alien = {}
alien['color'] = 'green'
alien['points'] = 5
print(alien) # {'color': 'green', 'points': 5}

""" Modifying Values in a dictionary """
alien = {'x_position' : 0, 'y_position' : 25, 'speed' : 'medium', 'color' : 'green'}

# modify color value
alien['color'] = 'yellow'

# modify position value
print("Original x-position: " + str(alien_0['x_position']))
if alien['speed'] == 'slow':
    x_increment = 1
elif alien['speed'] == 'medium':
    x_increment = 2
elif alien['speed'] == 'fast':
    x_increment = 3

alien['x_position'] += x_increment
# Python variables are scoped to the innermost function or module; 
# control blocks like if and while blocks don't count. 
# (IIUC, this is also how JavaScript's var-declared variables work.)
print("New x-position: " + str(alien['x_position']))

""" Removing Key-Value pairs """
alien = {'color': 'green', 'points': 5}
print(alien)
del alien['points'] # remove key-value pair
print(alien)

""" A Dictionary of Similar Objects """
# When you know you’ll need more than one line to define a dictionary
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

## Looping Through a Dictionary
```python
# 1. Looping through all Key-Value pairs
# Notice again that the key-value pairs are not returned in the order in which they were stored, even when looping through a dictionary. Python doesn’t care about the order in which key-value pairs are stored; it tracks only the connections between individual keys and their values.
user_0 = {
    'username': 'foobar12341',
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

## Nesting
```python
# 1. A List of Dictionaries
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

print("Total number of aliens: " + str(len(aliens)))

# aliens are changing color and moving faster as the game progresses. 
# we can use a for loop and an if statement to change the color of aliens.
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

# 2. A List in a Dictionary
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
You should not nest lists and dictionaries too deeply.

```python
# 3. Dictionary in a Dictionary
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

Try it yourself
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
- you should use the raw_input() function when prompting for user input.

## Introducing while loops
```python
current_number = 1
while current_number <= 5:
    print(current_number)
    current_number += 1

prompt = "\nTell me something ('quit' or 'q' to end the program.)"
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

## Use break to Exit a Loop
```python
while True:
    city = input("\nEnter a city you would like to visit. 'q' to quit: ")
    if city == 'q':
        break
    else:
        print('I would like to visit ' + city.title() + '!')
```

## Use continue in a Loop
```python 
# return to the beginning of the loop based on the result of a conditional test
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

## Using a while Loop with Lists and Dictionaries
```python
""" Moving Items from One List to Another """
unconfirmed_users = ['alice', 'brian', 'candace']
confirmed_users = []
while unconfirmed_users:
    current_user = unconfirmed_users.pop()
    print("Verifying user: " + current_user.title())
    confirmed_users.append(current_user)

print("\nThe following users have been confirmed:")
for confirmed_user in confirmed_users:
    print(confirmed_user.title())

""" Removing All Instances of Specific Values from a List """
pets = ['dog', 'cat', 'dog', 'goldfish', 'cat', 'rabbit', 'cat']
while 'cat' in pets:
    pets.remove('cat')
print(pets)

""" Filling a Dictionary with User Input """
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

Try it yourself
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
- pass information to functions.
- write functions whose job is to display information or process data and return a value or set of values. 
- store functions in separate files called modules to help organize your main program files.

```python
def greet_user():
    """Display a simple greeting"""
    print("Hello!")
greet_user()

# Docstrings are enclosed in triple quotes, which Python looks for when it generates documentation for the functions in your programs.
```

## Arguments and Parameters
```python
# the argument 'jesse' was passed to the function greet_user(), and the value was stored in the parameter username.
def greet_user(username):
    print("Hello, " + username.title() + "!")
greet_user('jesse')


""" Positional Arguments """
# Order Matters in Positional Arguments
def describe_pet(animal_type, pet_name):
    print("\nMy " + animal_type + "'s name is " + pet_name.title() + ".")

describe_pet('hamster', 'harry')
describe_pet('dog', 'willie')


""" Keyword arguments """
# Order does Not matter in Keyword Arguments 
# be sure to use the exact names of the parameters in the function’s definition.
def describe_pet(animal_type, pet_name):
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")

describe_pet(animal_type='hamster', pet_name='harry')
describe_pet(pet_name='harry', animal_type='hamster') # same result


""" Default Values """
# When writing a function, you can define a default value for each parameter.  
# When you use default values, any parameter with a default value needs to be listed 
# after all the parameters that don’t have default values. 
# This allows Python to continue interpreting positional arguments correctly.
def describe_pet(pet_name, animal_type='dog'):
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")

describe_pet(pet_name = 'willie')
describe_pet('willie') # simpler way 
describe_pet(pet_name='harry', animal_type='hamster') # an animal other than a dog

""" Equivalent Function Calls """
def describe_pet(pet_name, animal_type='dog'):
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")

describe_pet('willie') # A dog named Willie.
describe_pet(pet_name='willie')

describe_pet('harry', 'hamster') # A hamster named Harry.
describe_pet(pet_name='harry', animal_type='hamster')
describe_pet(animal_type='hamster', pet_name='harry')


""" Avoiding Argument Errors """
def describe_pet(pet_name, animal_type='dog'):
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet() # ERROR!
```

## Return Values
```python
def get_formatted_name(first_name, last_name):	
    """Return a full name, neatly formatted."""
    full_name = first_name + ' ' + last_name
    return full_name.title()
musician = get_formatted_name('jimi', 'hendrix')
print(musician)


""" Making an Argument Optional """
def get_formatted_name(first_name, last_name, middle_name=''):
    """Return a full name, neatly formatted."""
    if middle_name:
        full_name = first_name + ' ' + middle_name + ' ' + last_name
    else:
        full_name = first_name + ' ' + last_name
    return full_name.title()

musician = get_formatted_name('jimi', 'hendrix')
print(musician)
musician = get_formatted_name('john', 'hooker', 'lee')
print(musician)


""" Returning a Dictionary """
# This function takes in simple textual information and puts it into a more meaningful data structure that lets you work with the information beyond just printing it
def build_person(first_name, last_name, age=''):
    """Return a dictionary of information about a person."""
    person = {'first': first_name, 'last': last_name}
    if age:
        person['age'] = age
    return person
musician = build_person('jimi', 'hendrix', age=27)
print(musician)
```

## Using a Function with a while Loop
```python
def get_formatted_name(first_name, last_name):
    """Return a full name, neatly formatted."""
    full_name = first_name + ' ' + last_name
    return full_name.title()
while True:
    print("\nPlease tell me your name:")
    print("(enter 'q' at any time to quit)")
    f_name = input("First name: ")
    if f_name == 'q':
        break
    l_name = input("Last name: ")
    if l_name == 'q':
        break
    formatted_name = get_formatted_name(f_name, l_name)
    print("\nHello, " + formatted_name + "!")
```

## Passing a List
```python
def greet_users(names):
    for name in names:
        msg = "Hello, " + name.title() + "!"
        print(msg)
user_names = ['hannah', 'ty', 'margot']
greet_users(user_names)
```

```python
unprinted_designs = ['iphone case', 'robot pendant', 'dodecahedron']
completed_models = []
while unprinted_designs:
    current_design = unprinted_designs.pop()
    print("Printing model: " + current_design)
    completed_models.append(current_design)

print("\nThe following models have been printed:")
for completed_model in completed_models:
    print(completed_model)
```

```python
""" Modifying a List in a Function """
def print_models(unprinted_designs, completed_models):
    while unprinted_designs:
        current_design = unprinted_designs.pop()
        print("Printing model: " + current_design)
        completed_models.append(current_design)

def show_completed_models(completed_models):
    print("\nThe following models have been printed:")
    for completed_model in completed_models:
        print(completed_model)

unprinted_designs = ['iphone case', 'robot pendant', 'dodecahedron']
completed_models = []

print_models(unprinted_designs, completed_models)
show_completed_models(completed_models)


""" Preventing a Function from Modifying a List """
def print_models(unprinted_designs, completed_models):
    # same
def show_completed_models(completed_models):
    # same
unprinted_designs = ['iphone case', 'robot pendant', 'dodecahedron']
completed_models = []

# pass the function a copy of the list, not the original. 
# The copied list will be modified, leaving the original intact.
print_models(unprinted_designs[:], completed_models)
show_completed_models(completed_models)
```

## Passing an Arbitrary Number of Arguments
```python
# make an empty tuple called toppings and pack whatever values it receives into this tuple.
def make_pizza(*toppings):
    print(toppings)
make_pizza('pepperoni')
make_pizza('mushrooms', 'green peppers', 'extra cheese')


""" Mixing Positional and Arbitrary Arguments """
def make_pizza(size, *toppings):
    """Summarize the pizza we are about to make."""
    print("\nMaking a " + str(size) +
          "-inch pizza with the following toppings:")
    for topping in toppings:
        print("- " + topping)

make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')


""" Using Arbitrary Keyword Arguments """
# to accept an arbitrary number of arguments, but you won’t know what kind of information will be passed to the function. 
# In this case, you can write functions that accept as many key-value pairs as the calling statement provides.
# The definition of build_profile() expects a first and last name, and then it allows the user to pass in as many name-value pairs as they want. The double asterisks before the parameter **user_info cause Python to create an empty dictionary called user_info and pack whatever name-value pairs it receives into this dictionary.
def build_profile(first, last, **user_info):
    """Build a dictionary containing everything we know about a user."""
    profile = {}
    profile['first_name'] = first
    profile['last_name'] = last
    for key, value in user_info.items():
        profile[key] = value
    return profile

user_profile = build_profile('albert', 'einstein', 
    location='princeton', 
    field='physics')
print(user_profile)
```

## Storing Your Functions in Modules
```python
# store your functions in a separate file called a module and then import that module into your main program.
# A module is a file ending in .py that contains the code you want to import into your program. 

# pizza.py
def make_pizza(size, *toppings):
    print("\nMaking a " + str(size) + 
        "-inch pizza with the following toppings:")
    for topping in toppings:
        print("- " + topping)


""" Importing an Entire Module """
# making_pizzas.py
import pizza # tells python to open the file pizza.py and copy all the functions from it into this program

# module_name.function_name()
pizza.make_pizza(16, 'pepperoni')
pizza.make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')

# This first approach to importing, in which you simply write import followed by the name of the module, makes every function from the module available in your program. 


""" Importing Specific Functions """
# With this syntax, you don’t need to use the dot notation when you call a function.
# from module_name import function_name
# from module_name import function_0, function_1, function_2

from pizza import make_pizza
make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')


""" Using as to Give a Function an Alias """
# If the name of a function you’re importing might conflict with an existing name in your program or if the function name is long, you can use a short, unique alias—an alternate name similar to a nickname for the function.
from pizza import make_pizza as mp
mp(16, 'pepperoni')
mp(12, 'mushrooms', 'green peppers', 'extra cheese')


""" Using as to Give a Module an Alias """
# You can also provide an alias for a module name. Giving a module a short alias, like p for pizza
# import module_name as mn
import pizza as p
p.make_pizza(16, 'pepperoni')
p.make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')


""" Importing All Functions in a Module """
# this apporach is NOT recommended
# You can tell Python to import every function in a module by using the asterisk (*) operator:
# Because every function is imported, you can call each function by name without using the dot notation.
 
# However, it's best not to use this approach when you’re working with larger modules that you didn't write: if the module has a function name that matches an existing name in your project, you can get some unexpected results.
# The best approach is to import the function or functions you want, or import the entire module and use the dot notation. This leads to clear code that’s easy to read and understand
# from module_name import *
from pizza import *
make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```

Styling Functions
- descriptive function name with only lowercase and underscore
- comment should appear immediately after the function definition and use the docstring format.
- default value for a parameter: no spaces should be used on either side of the equal sign. e.g. param='default value'
- also same convention for arguments in function call. e.g. func(val_0, param='value')
```python
def function_name(
        parameter_0, parameter_1, parameter_2,
        parameter_3, parameter_4, parameter_5):
function body...
```
- if a module has more than 1 function, you can separate by 2 blank lines between functions
- all import statements should be at the beginning of a file.
- exceptions are comments at the beginning of the file to describe the overall program

# Classes
- create objects with unique traits
- instantiate; make an object from a class
- actions and information for an object
- write classes that extends the functionality of existing classes
- store classes in modules and import classes written by other programmers into your own program files

## Creating and Using a Class
```python
# __init__() method runs automatically whenever we create a new instance based on the Dog class
# self parameter is required in the method definition, and it must come first before the other parameters
# it gives the individual instance access to the attributes and methods in the class.
# Variables (name, age) that are accessible through instances like this (self.name and selft.age) are called attributes.
class Dog():
    """A simple attempt to model a dog."""
    
    def __init__(self, name, age):
        """Initialize name and age attributes."""
        self.name = name
        self.age = age
    
    def sit(self):
        """Simulate a dog sitting in response to a command."""
        print(self.name.title() + " is now sitting.")
    
    def roll_over(self):
        """Simulate rolling over in response to a command."""
        print(self.name.title() + " rolled over!")
```

python 2.7 class definition
```python
class ClassName(object):
    # put object inside parentheses
```

Making an Instance from a Class
```python
class Dog():
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def sit(self):
        print(self.name.title() + " is now sitting.")
    
    def roll_over(self):
        print(self.name.title() + " rolled over!")

my_dog = Dog('willie', 6)

# Accessing attributes
print("My dog's name is " + my_dog.name.title() + ".")
print("My dog is " + str(my_dog.age) + " years old.")

# Calling Methods
my_dog.sit()
my_dog.roll_over()

# Creating Multiple Instances
your_dog = Dog('lucy', 3)
print("\nYour dog's name is " + your_dog.name.title() + ".")
print("Your dog is " + str(your_dog.age) + " years old.")
your_dog.sit()
```

## Working with Classes and Instances
```python
class Car():
    """A simple attempt to represent a car."""

    def __init__(self, make, model, year):
        """Initialize attributes to describe a car."""
        self.make = make
        self.model = model
        self.year = year
        # Setting a Default Value for an Attribute
        self.odometer_reading = 0

    def get_descriptive_name(self):
        """Return a neatly formatted descriptive name."""
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model
        return long_name.title()

    def read_odometer(self):
        """Print a statement showing the car's mileage."""
        print("This car has " + str(self.odometer_reading) + " miles on it.")

my_new_car = Car('audi', 'a4', 2016)
print(my_new_car.get_descriptive_name())
my_new_car.read_odometer()
```

Modifying Attribute Values
```python
""" 1. Modifying an attribute’s Value Directly """
from car import Car

my_new_car = Car('audi', 'a4', 2017)
my_new_car.odometer_reading = 23 # modify 1
```

```python
""" 2. Modifying an attribute’s Value through a Method """
class Car():
    def __init__(self, make, model, year):
        """Initialize attributes to describe a car."""
        self.make = make
        self.model = model
        self.year = year
        # Setting a Default Value for an Attribute
        self.odometer_reading = 0
    
    def update_odometer(self, mileage):
        """
        Set the odometer reading to the given value.
        Reject the change if it attempts to roll the odometer back.
        """
        if mileage >= self.odometer_reading:
            self.odometer_reading = mileage
        else:
            print("You can't roll back an odometer!")

my_new_car = Car('audi', 'a4', 2017)
my_new_car.update_odometer(23) # modify 2
```

```python
""" 3. Incrementing an attribute’s Value through a Method """
# Sometimes you’ll want to increment an attribute’s value by a certain amount rather than set an entirely new value
# You can easily modify this method to reject negative increments so no one uses this function to roll back an odometer
class Car():
    def __init__(self, make, model, year):
        """Initialize attributes to describe a car."""
        self.make = make
        self.model = model
        self.year = year
        # Setting a Default Value for an Attribute
        self.odometer_reading = 0
    
    def increment_odometer(self, miles):
        """Add the given amount to the odometer reading."""
        self.odometer_reading += miles

my_used_car = Car('subaru', 'outback', 2013)
my_used_car.increment_odometer(100) # modify 3
```

## Inheritance
When one class inherits from another, it automatically takes on all the attributes and methods of the first class. The child class inherits every attribute and method from its parent class but is also free to define new attributes and methods of its own.
```python
from car import Car

class ElectricCar(Car):
    """Represent aspects of a car, specific to electric vehicles."""

    def __init__(self, make, model, year):
        """Initialize attributes of the parent class."""
        super().__init__(make, model, year)

my_tesla = ElectricCar('tesla', 'model s', 2016)
print(my_tesla.get_descriptive_name())
```

Inheritance in Python 2.7
```python
# The super() function needs two arguments: a reference to the child class and the self object.
from car import Car

class ElectricCar(Car):
    def __init__(self, make, model, year):
        """Initialize attributes of the parent class."""
        super(ElectricCar, self).__init__(make, model, year)
```

Defining Attributes and Methods for the Child Class
```python
from car import Car

class ElectricCar(Car):
    def __init__(self, make, model, year):
        super().__init__(make, model, year)
        self.battery_size = 70
    
    def describe_battery(self):
        print('battery: ' + str(self.battery_size) + '-kWh')

my_tesla = ElectricCar('tesla', 'model s', 2016)
print(my_tesla.get_descriptive_name())
my_tesla.describe_battery()
```

Overriding Methods from the Parent Class
```python
from car import Car

class ElectricCar(Car):
    """
    define a method in the child class with the same name as the method you want to override in the parent class.
    Now if someone tries to call fill_gas_tank() with an electric car, 
    Python will ignore the method fill_gas_tank() in Car and run this code instead
    """
    
    def fill_gas_tank(self):
        print('Electric Car does not need Gas!')
```

Instances as Attributes
```python
from car import Car

class Battery():
    
    def __init__(self, battery_size=70):
        self.battery_size = battery_size
    
    def describe_battery(self):
        print('battery: ' + str(self.battery_size) + '-kWh')

    def get_range(self):
        """Print a statement about the range this battery provides."""
        if self.battery_size == 70:
            range = 240
        elif self.battery_size == 85:
            range = 270
        
        message = "This car can go approximately " + str(range)
        message += " miles on a full charge."
        print(message)

class ElectricCar(Car):
    def __init__(self, make, model, year):
        super().__init__(make, model, year)
        self.battery = Battery() # battery instance as an attribute

my_tesla = ElectricCar('tesla', 'model s', 2016)
print(my_tesla.get_descriptive_name())

my_tesla.battery.describe_battery()
my_tesla.battery.get_range()

my_tesla.battery.upgrade_battery()
my_tesla.battery.get_range()
```

Modeling Real-World Objects
- As you begin to model more complicated items like electric cars, you’ll wrestle with interesting questions. Is the range of an electric car a property of the battery or of the car?

## Importing Classes

1. Importing a Single Class
```python
# store classes (e.g. Car, User) in modules (e.g car.py, user.py) 
# and then import the classes you need into your main program.
# any program that uses this module will need a more specific filename, e.g. my_car.py

# my_car.py
from car import Car

my_new_car = Car('audi', 'a4', 2016)
print(my_new_car.get_descriptive_name())
```

2. Storing Multiple Classes in a Module
```python
# car.py
class Car(): # each class in a module should be related somehow.
class Battery():
class ElectricCar():
```
```python
# my_electric_car.py
from car import ElectricCar

my_tesla = ElectricCar('tesla', 'model s', 2016)
print(my_tesla.get_descriptive_name())

my_tesla.battery.describe_battery()
my_tesla.battery.get_range()
```

3. Importing Multiple Classes from a Module
```python
# my_cars.py
from car import Car, ElectricCar

my_beetle = Car('volkswagen', 'beetle', 2016)
print(my_beetle.get_descriptive_name())

my_tesla = ElectricCar('tesla', 'roadster', 2016)
print(my_tesla.get_descriptive_name())
```

4. Importing an Entire Module
```python
import car

my_beetle = car.Car('volkswagen', 'beetle', 2016)
print(my_beetle.get_descriptive_name())
my_tesla = car.ElectricCar('tesla', 'roadster', 2016)
print(my_tesla.get_descriptive_name())
```

5. Importing All Classes from a Module
```python
# This method is not recommended for two reasons. First, it’s helpful
# to be able to read the import statements at the top of a file and get a clear
# sense of which classes a program uses. Secondly, this approach can lead to confusion 
# with names in the file. If you accidentally import a class with the same name as 
# something else in your program file, you can create errors that are hard to diagnose. 
from module_name import *
```

6. Importing a Module into a Module
```python
# When you store your classes in several modules, you may find that a class 
# in one module depends on a class in another module. When this happens, 
# you can import the required class into the first module.

# car.py
class Car():
```
```python
# electric_car.py
from car import Car

class Battery():
class ElectricCar(Car):
```

```python
# my_cars.py
from car import Car
from electric_car import ElectricCar

my_beetle = Car('volkswagen', 'beetle', 2016)
print(my_beetle.get_descriptive_name())

my_tesla = ElectricCar('tesla', 'roadster', 2016)
print(my_tesla.get_descriptive_name())
```

Finding Your Own Workflow
```python
# When you’re starting out, keep your code structure simple. Try doing everything 
# in one file and moving your classes to separate modules once everything is working.
```

The Python Standard Library
```python
# If you’re creating a dictionary and want to keep track of the order in which key-value 
# pairs are added, you can use the OrderedDict class from the collections module.
# You can also download modules from external sources. You’ll see a number of these
# examples in Part II, where we’ll need external modules to complete each project.
from collections import OrderedDict

# OrderedDict() creates an empty ordered dictionary
# Instances of the OrderedDict class behave almost exactly like dictionaries
# except they keep track of the order in which key-value pairs are added.
favorite_languages = OrderedDict()

favorite_languages['jen'] = 'python'
favorite_languages['sarah'] = 'c'
favorite_languages['edward'] = 'ruby'
favorite_languages['phil'] = 'python'

for name, language in favorite_languages.items():
    print(name.title() + "'s favorite language is " 
        + language.title() + '.')
```
```python
# die.py
from random import randint

class Die():
    def __init__(self, sides):
        self.sides = sides

    def roll_die(self):
        # prints a random number between 1 and the number of sides
        x = randint(1, self.sides)
        print(str(self.sides) + '-side die result = ' + str(x))

die_6 = Die(6)
die_10 = Die(10)
die_20 = Die(20)

for i in range(10):
    die_6.roll_die()
    die_10.roll_die()
    die_20.roll_die()
    print()
```

Go to [python module of the week](http://pymotw.com/) and look at the table of contents . Find a module that looks interesting to you and read about it, or explore the documentation of the collections and random module

Styling Classes
- Class names should be written in CamelCaps and should not use underscores
- Instance and module names should be written in lowercase with underscores between words
- Every class/function should have a docstring immediately following the class/function definition 
- Each module should also have a docstring describing what the classes in a module can be used for 
- Within a class, one blank line between methods
- Within a module, two blank lines to separate classes
- Place the import statement for the standard library module first. 
- Then add a blank line and the import statement for the module you wrote. 

# Files and Exceptions

## Reading from a File

Reading an Entire File
```python
# Save the text file (pi_digits.txt) in the same directory where you’ll store this chapter’s programs.
# 'with' keyword closes the file once access to it is no longer needed
# 'with' lets Python open and close the file properly
# read() reads the entire contents of the file
# read() returns an empty string when it reaches the end of the file
# open(): an object representing the file and its contents is stored in the variable
with open('pi_digits.txt') as file_object:
    contents = file_object.read() # returns an empty string when it reaches the end of the file
    print(contents) # results in an additional empty line at the end
    # print(contents.rstrip()) # remove the empty line at the end
```

File Paths
```python
# relative path
with open('text_files/filename.txt') as file_object:
    contents = file_object.read()
    print(contents)

# absolute path
with open('/home/user/workspace/python/text_files/filename.txt') as file_object:
    contents = file_object.read()
    print(contents)
```

Reading Line by Line
```python
# two newlines: one from the file and one from the print statement
filename = 'pi_digits.txt'
with open(filename) as file_object:
    for line in file_object:
        print(line)

# to avoid two new lines
filename = 'pi_digits.txt'
with open(filename) as file_object:
    for line in file_object:
        print(line.rstrip())
```

Making a List of Lines from a File
```python
filename = "pi_digits.txt"
with open(filename) as file_object:
    lines = file_object.readlines()

for line in lines:
    print(line.rstrip())
```

Working with a File’s Contents
```python
filename = 'pi_digits.txt'
with open(filename) as file_object:
    lines = file_object.readlines()

pi_string = ''
for line in lines:
    pi_string += line.strip()

print(pi_string)
print(len(pi_string))
```

Large Files: One Million Digits
```python
filename = 'pi_million_digits.txt'
with open(filename) as file_object:
    lines = file_object.readlines()

py_string = ''
for line in lines:
    py_string += line.strip()

print(py_string[:52] + "...") # 3.14159265358979323846264338327950288419716939937510...
print(len(py_string)) # 1000002
```

```python
filename = 'pi_million_digits.txt'
with open(filename) as file_object:
    lines = file_object.readlines()

pi_string = ''
for line in lines:
    pi_string += line.strip()

birthday = input('Enter your birthday, in the form mmddyy: ')
if birthday in pi_string:
    print('Your birthday appears in the first million digits of pi!')
else:
    print('Your birthday does not appear in the first million digits of pi.')
```

## Writing to a File

Writing to an Empty File
```python
filename = 'programming.txt'

# read mode ( 'r' ), write mode ( 'w' ), append mode ( 'a' )
with open('filename', 'w') as file_object:
    file_object.write('I love programming.\n')
    file_object.write('I love python language')

# Python can only write strings to a text file. 
# If you want to store numerical data in a text file, use str() function
```

Appending to a File
```python
filename = 'programming.txt'
with open(filename, 'a') as file_object: #append
    file_object.write("I also love finding meaning in large datasets.\n")
    file_object.write("I love creating apps that can run in a browser.\n")
```

Try it yourself
```python
filename = 'guest_book.txt'
flag = True
while flag:
    name = input("guest name('q' to quit): ")
    if name != 'q' and name:
        print('\tHi, ' + name + '. Welcome back!')
        with open(filename, 'a') as file_object:
            file_object.write(name + '\n')
    else:
        print()
        break

with open(filename) as file_object:
    for line in file_object:
        print(line.strip())
```

## Exceptions
Whenever an error occurs during a program's execution, exceptions objects are created to manage errors. If you don’t handle the exception, the program will halt and show a traceback, which includes a report of the exception that was raised. Exceptions are handled with try - except blocks.


ZeroDivisionError
```python
try:
    print(5/0)
except ZeroDivisionError:
    print('You cannot divide by zero!')
```

```python
print("Give me two numbers, and I'll divide them.")
print("Enter 'q' to quit.")
while True:
    first_number = input("\nFirst number: ")
    if first_number == 'q':
        break
    second_number = input("Second number: ")
    try:
        answer = int(first_number) / int(second_number)
    except ZeroDivisionError:
        print("You can't divide by 0!")
    else:
        print(answer)
```

FileNotFoundError
```python
filename = 'alice.txt'

try:
    with open(filename) as f_obj:
        contents = f_obj.read()
except FileNotFoundError:
    msg = "Sorry, the file, " + filename + " does not exist."
    print(msg)
```

Analyzing Text
```python
filename = 'alice.txt'

try:
    with open(filename) as f_obj:
        contents = f_obj.read()
```

