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
# python is pre-installed in Ubuntu; check python versions
python3
# compile and execute
python3 -m py_compile "%f"
python3 "%f"
```

# Variables and Simple Data Types
```python
name = 'ada lovelace'
print(name.upper())
print(name.lower())
print(name.title())

# White spaces
greeting = '\tHello\n'

word = '  python  '
word.rstrip()
word.lstrip()
word.strip()

# Quote inside quote
msg_valid = "monty's best friend"
msg2_valid = 'I said, \'Hi Monty.\''
# msg_invalid = 'monty's best friend' # Error!
```

## operator
```python
# Arithmetic operator + - * / and Exponential operator **
bool_0 = (10 + 2 * 3 / 3 - 5 == 7)
bool_1 = (1024 == 2 ** 10)

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
# python line comment
"""
python
block comment
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
fruit = ['apple', 'orange', 'grapes', 'blueberry', 'watermelon']

# append(str)
fruit.append('strawberry') # append at the end

# insert(i, str)
fruit.insert(0, 'banana') # add at the beginning
fruit.insert(len(fruit) - 1, 'melon') # add at the end

# del list[i]
del fruit[0] # remove first element

# pop()
motorcycles = ['honda', 'yamaha', 'suzuki']
last_owned = motorcycles.pop()
print("The last motorcycle I owned was a " + last_owned.title() + ".")

# pop(i) removes and returns the i th element
first_owned = motorcycles.pop(0)
print('The first motorcycle I owned was a ' + first_owned.title() + '.')

# remove(str) remove item (first occurrence) by specifying the value
motorcycles.remove('honda') # use a loop to remove all occurrences

too_expensive = 'ducati'
motorcycles.remove(too_expensive)
print("\nA " + too_expensive.title() + " is too expensive for me.")
print(motorcycles)

# sort()
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort()

# sort(reverse = True)
cars.sort(reverse = True) # sort and reverse

# sorted(list) for sorting temporarily
print('Sorted List: ')
print(sorted(cars))
print('Original List: ')
print(cars)

# sorted(list, reverse = True)
location = ['tokyo', 'los angeles', 'new york', 'seoul']
print(sorted(location, reverse = True)) # in reverse order
print(location) # original list

# sort alphabetically when some values are not in lowercase
location = ['tokyo', 'los angeles', 'New York', 'Seoul'] # reassign
sorted(location, key=str.lower) # disregard lower/uppercase preferences

# reverse()
cars.reverse() # reverse only; it does not sort
print(cars)

# len()
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
```

Avoiding Indentation Errors
- missing or unnecessary indentations or colons

## Numerical Lists
```python
for value in range(1, 6):
    print(value) # 1\n2\n3\n4\n5

numbers = list(range(1,6)) # [1, 2, 3, 4, 5]
even_numbers = list(range(2, 11, 2)) # [2, 4, 6, 8, 10]

# square numbers from 1 to 11 and make it as a list [1, 4, ... , 100] 
squares = []
for value in range(1, 11):
    squares.append(value ** 2)

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
friend_foods = my_foods[:] # copied list (distinct from original)

my_foods.append('cannoli')
friend_foods.append('ice cream')

print(my_foods) # ['pizza', 'falafel', 'carrot cake', 'cannoli']
print(friend_foods) # ['pizza', 'falafel', 'carrot cake', 'ice cream']
```

Copying a list using assignment (not working as expected)
```python
my_foods = ['pizza', 'carrot cake']
friend_foods = my_foods # both variables will point to the same list

my_foods.append('cannoli')
friend_foods.append('ice cream')

print(my_foods) # ['pizza', 'carrot cake', 'cannoli', 'ice cream']
print(friend_foods) # same result as above!
```

## Tuples
tuples are simple data structures to store an immutable set of values 
```python
# sometimes you’ll want to create a list of items that cannot change.
# tuple is an immutable(values that cannot change) list;
dimensions = (200, 50)
for dimension in dimensions:
    print(dimension)

# error! immutable!
dimensions[0] = 250

# Assign new tuples
dimensions = (400, 100)
for dimension in dimensions:
    print(dimension) # 400 100
```

Styling Your Code
1. Indent 4 spaces with 'tab' key to avoid unpredictable errors
2. Line length less than 72 or 80 
3. Blank line between the two sections (no more than 2 blank lines)
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
# Sometimes it is clearer to use an additional elif, omitting else block
# elif age >= 65
```

Testing Multiple conditions
```python
# check all conditions of interest, rather than checking one specific
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
requested_toppings = [] 
if requested_toppings: # returns True if non-empty list
    for requested_topping in requested_toppings:
        print("Adding " + requested_topping + ".")
    print("\nFinished making your pizza!")
else:
    print("Are you sure you want a plain pizza?")
```

Using multiple lists
```python
available_toppings = ['mushrooms', 'olives', 'pepperoni', 'pineapple']
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
current_users = ['foo', 'bar']
new_users = ['FOo', 'baR', 'AAa', 'Bbb', 'ccc']
for user in new_users:
    if user.upper() in [user.upper() for user in current_users]:
        print("Hey! Your username, " + user + " is already in use!")
    else:
        print("Your username, " + user + " is available to use!")
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

# Starting with an empty dictionary
alien = {}

# Adding New Key-Value pairs
alien['color'] = 'green'
alien['points'] = 5
alien['x_position'] = 0
alien['y_position'] = 25

# Modifying Values in a dictionary
alien['color'] = 'yellow' # modify color

if alien['speed'] == 'slow':
    x_increment = 1
elif alien['speed'] == 'medium':
    x_increment = 2
elif alien['speed'] == 'fast':
    x_increment = 3

alien['x_position'] += x_increment # modify position
print("New x-position: " + str(alien['x_position']))
# Python variables are scoped to the innermost function or module; 
# control blocks like if and while blocks don't count. 
# (IIUC, this is also how JavaScript's var-declared variables work.)

# Removing Key-Value pairs
del alien['points'] # remove key-value pair

# A Dictionary of Similar Objects
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

# key-value pairs are not returned in the order they were stored 
# Python tracks only the connections between individual keys and their values
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

# 3-2. A set has unique items 
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

# Using a Flag
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
- make sure a loop does not run forever!

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
```

Removing All Instances of Specific Values from a List
```python
pets = ['dog', 'cat', 'dog', 'goldfish', 'cat', 'rabbit', 'cat']
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

# Docstrings are enclosed in triple quotes, which Python looks for 
# when it generates documentation for the functions in your programs
```

## Arguments and Parameters
```python
# the argument value 'jesse' is stored in the parameter username
def greet_user(username):
    print("Hello, " + username.title() + "!")
greet_user('jesse')
```

Positional Arguments
```python
# order matters in Positional Arguments
def describe_pet(animal_type, pet_name):
    print("\nMy " + animal_type + "'s name is " + pet_name.title() + ".")

describe_pet('hamster', 'harry')
describe_pet('dog', 'willie')
```

Keyword arguments
```python
# order does Not matter in Keyword Arguments 
# use the exact names of the parameters in the function’s definition
def describe_pet(animal_type, pet_name):
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")

describe_pet(animal_type='hamster', pet_name='harry')
describe_pet(pet_name='harry', animal_type='hamster') # same result
```

Default Values
```python
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
```

Equivalent Function Calls
```python
def describe_pet(pet_name, animal_type='dog'):
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")

# A dog named Willie.
describe_pet('willie')
describe_pet(pet_name='willie')

# A hamster named Harry.
describe_pet('harry', 'hamster')
describe_pet(pet_name='harry', animal_type='hamster')
describe_pet(animal_type='hamster', pet_name='harry')
```

Avoiding Argument Errors
```python
def describe_pet(pet_name, animal_type='dog'):
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet() # ERROR! pet_name argument value was not provided
```

## Return Values
```python
def get_formatted_name(first_name, last_name):	
    full_name = first_name + ' ' + last_name
    return full_name.title()

musician = get_formatted_name('jimi', 'hendrix') # Jimi Hendrix
```

Making an Argument Optional
```python
def get_formatted_name(first_name, last_name, middle_name=''):
    """Return a full name, neatly formatted."""
    if middle_name:
        full_name = first_name + ' ' + middle_name + ' ' + last_name
    else:
        full_name = first_name + ' ' + last_name
    return full_name.title()

musician = get_formatted_name('jimi', 'hendrix')
musician = get_formatted_name('john', 'hooker', 'lee')
```

Returning a Dictionary
```python
# takes in textual information and returns a meaningful data structure
def build_person(first_name, last_name, age=''):
    """Return a dictionary of information about a person."""
    person = {'first': first_name, 'last': last_name}
    if age:
        person['age'] = age
    return person

musician = build_person('jimi', 'hendrix', age=27)
# {'first': 'jimi', 'last': 'hendrix', 'age': 27}
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

Modifying a List in a Function
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
# reorganize the above code
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
```

Preventing a Function from Modifying a List
```python
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
# make an empty tuple called toppings 
# and pack whatever values it receives into this tuple.
def make_pizza(*toppings):
    print(toppings)
make_pizza('pepperoni')
make_pizza('mushrooms', 'green peppers', 'extra cheese')
```

Mixing Positional and Arbitrary Arguments
```python
def make_pizza(size, *toppings):
    """Summarize the pizza we are about to make."""
    print("\nMaking a " + str(size) +
          "-inch pizza with the following toppings:")
    for topping in toppings:
        print("- " + topping)

make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```

Using Arbitrary Keyword Arguments
```python
# to accept an arbitrary number of arguments 
# as many key-value pairs as the calling statement provides
# **user_info cause Python to create an empty dictionary, user_info 
# and pack whatever name-value pairs it receives into this dictionary.
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
# store your functions in a separate file called a module(.py) 
# and then import that module into your main program. 
# pizza.py
def make_pizza(size, *toppings):
    print("\nMaking a " + str(size) + 
        "-inch pizza with the following toppings:")
    for topping in toppings:
        print("- " + topping)
```

Importing an Entire Module
```python
# making_pizzas.py
import pizza

# module_name.function_name()
pizza.make_pizza(16, 'pepperoni')
pizza.make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')

# import module makes every function from the module available in your program 
```

Importing Specific Functions
```python
# With this syntax, you don’t need to use the dot notation when you call a function.
# from module_name import function_name
# from module_name import function_0, function_1, function_2
from pizza import make_pizza
make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```

Using as to Give a Function an Alias
```python
# use a short, unique alias—an alternate name for the function.
from pizza import make_pizza as mp
mp(16, 'pepperoni')
mp(12, 'mushrooms', 'green peppers', 'extra cheese')
```

Using as to Give a Module an Alias
```python
# alias for a module name
# import module_name as mn
import pizza as p
p.make_pizza(16, 'pepperoni')
p.make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```

Importing All Functions in a Module
```python
# this approach is Not recommended
# if the module has a function name that matches an existing name 
# in your project, you can get some unexpected results.
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
    function_body
```
- in a module, separate functions by 2 blank lines
- import statements should be at the beginning of a file
- exceptions are comments at the beginning to describe the program

# Classes
- create objects with unique traits
- instantiate; make an object from a class
- actions and information for an object
- write classes that extends the functionality of existing classes
- store classes in modules and import classes written by other programmers into your own program files

## Creating and Using a Class
```python
# __init__() runs automatically whenever we create a new instance
# 'self' parameter must come first before the other parameters
# it gives the individual instance access to the attributes and methods
# variables accessible through 'self' are called attributes (name, age)
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
# put object inside parentheses
class ClassName(object):
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
# car.py
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
        print("This car has " + str(self.odometer_reading) + " miles.")

my_new_car = Car('audi', 'a4', 2016)
print(my_new_car.get_descriptive_name())
my_new_car.read_odometer()
```

Modifying Attribute Values
```python
# 1. Modifying an attribute’s Value Directly
from car import Car

my_new_car = Car('audi', 'a4', 2017)
my_new_car.odometer_reading = 23 # modify 1
```

```python
# 2. Modifying an attribute’s Value through a Method
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
# 3. Incrementing an attribute’s Value through a Method
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
# super() needs two arguments: a reference to the child class and the self object
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
    """say fill_gas_tank() is defined both in Car and ElectricCar classes 
    Python will ignore fill_gas_tank() in Car and run this code instead"""
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
# any program that uses this module will need a more specific filename,
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
# from module_name import *
from car import *
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
# dictionary that keeps track of the order in which key-value pairs are 
# added, you can use the OrderedDict class from the collections module.
from collections import OrderedDict

# OrderedDict() creates an empty ordered dictionary
# OrderedDict objects behave like dictionaries except it is ordered
favorite_languages = OrderedDict()

favorite_languages['jen'] = 'python'
favorite_languages['sarah'] = 'c'
favorite_languages['edward'] = 'ruby'
favorite_languages['phil'] = 'python'

for name, language in favorite_languages.items():
    print(name.title() + "'s favorite language : " + language.title())
```

```python
# die.py
from random import randint

class Die():
    def __init__(self, sides):
        self.sides = sides

    def roll_die(self):
        # random number between 1 and the number of sides
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
- Class names should be written in CamelCaps with no underscores
- Instance and module names should be written in lowercase and underscores
- class/function should have a docstring immediately following the definition 
- module should also have a docstring describing the classes in a module 
- Within a class, one blank line between methods
- Within a module, two blank lines to separate classes
- Place the import statement for the standard library module first. 
- Then add a blank line and the import statement for the module you wrote. 

# Files and Exceptions

## Reading from a File

Reading an Entire File
```python
# 'with' lets Python open and close the file properly
# 'with' keyword closes the file once access to it is no longer needed
# read() reads the entire contents of the file
# read() returns an empty string when it reaches the end of the file
# open(): returns a file object and its contents is stored in the variable
with open('pi_digits.txt') as file_object:
    contents = file_object.read() # contains an empty string at the end
    print(contents) # additional empty line at the end
```

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
filename = 'pi_digits.txt'
with open(filename) as file_object:
    for line in file_object:
        print(line) # two newlines: from end of each line and 'print'
        # print(line.rstrip()) # avoid two new lines 
```

Making a List of Lines from a File
```python
filename = "pi_digits.txt"
with open(filename) as file_object:
    lines = file_object.readlines()

for line in lines:
    print(line.rstrip())
```

```python
# Working with a File’s Contents
filename = 'pi_digits.txt'
with open(filename) as file_object:
    lines = file_object.readlines()

pi_string = ''
for line in lines:
    pi_string += line.strip()

print(pi_string)
print(len(pi_string))
```

```python
# Large Files: One Million Digits
filename = 'pi_million_digits.txt'
with open(filename) as file_object:
    lines = file_object.readlines()

pi_string = ''
for line in lines:
    pi_string += line.strip()

print(pi_string[:52] + "...") # 3.1415926535897932384626433832795028...
print(len(pi_string)) # 1000002

birthday = input('Enter your birthday, in the form mmddyy: ')
if birthday in pi_string:
    print('Your birthday appears in the first million digits of pi!')
else:
    print('Your birthday does not appear in the first million digits.')
```

## Writing to a File

Writing to an Empty File
```python
filename = 'programming.txt'

# read('r'), write('w'), append('a') mode
with open('filename', 'w') as file_object:
    file_object.write('I love programming.\n')
    file_object.write('I love python language')

# only strings can be written to a text file.
# use str() for storing numerical data
```

Appending to a File
```python
filename = 'programming.txt'
with open(filename, 'a') as file_object: #append
    file_object.write("I love finding meaning in large data sets.\n")
    file_object.write("I love creating apps.\n")
```

Try it yourself
```python
filename = 'guest_book.txt'
flag = True
while flag:
    name = input("Type your name ('q' to quit) >> ")
    if not name:
        print("Empty name is not allowed, please type again...\n")
        continue
    elif name != 'q':
        print('\tHi, ' + name + '. Welcome back!')
        with open(filename, 'a') as f_obj:
            f_obj.write(name + '\n')
    else:
        print("Exiting the program...")
        break

with open(filename) as f_obj:
    for line in f_obj:
        print(line.strip())
```

## Exceptions
Whenever an error occurs during a program's execution, exceptions objects are created to manage errors. If you don’t handle the exception, the program will halt and show a traceback, which includes a report of the exception that was raised. Exceptions are handled with try-except blocks.

ZeroDivisionError
```python
try:
    print(5/0)
except ZeroDivisionError:
    print('You cannot divide by zero!')
```

```python
# if try block is executed successfully, else block is run
print("Give me two numbers, and I'll divide them.")
print("Enter 'q' to quit.")
while True:
    first_number = input("\nFirst number: ")
    if first_number == 'q':
        break
    second_number = input("Second number: ")
    if second_number == 'q':
        break
    try:
        answer = int(first_number) / int(second_number)
    except ZeroDivisionError:
        print("You can't divide by 0!")
    else:
        print(answer)
```

FileNotFoundError
```python
def count_words(filename):
    """Count the approximate number of words in a file."""
    try:
        with open(filename) as f_obj:
            contents = f_obj.read()
    except FileNotFoundError:
        msg = "Sorry, the file '" + filename + "' does not exist."
        print(msg)
    else:
        # count the approximate number of words in the file
        words = contents.split()
        num_words = len(words)
        print("'" + filename + "' has " + str(num_words) + " words")

filenames = ['alice.txt', 'moby_dick.txt', 'little_women.txt']
for filename in filenames:
    count_words(filename)
```

Failing Silently
```python
# Deciding Which Errors to Report
# you don’t need to report every exception you catch.
def count_words(filename):
    """Count the approximate number of words in a file."""
    try:
        # --snip--
    except FileNotFoundError:
        pass
    else:
        # --snip--
```

Try it yourself
```python
def add_numbers():
    while True:
        num1 = input("integer num1 ('q' to quit) > ")
        if num1 == 'q':
            break
        num2 = input("integer num2 ('q' to quit) > ")
        if num2 == 'q':
            break
        try:
            division = int(num1) / int(num2)
        except ValueError:
            print('One of your inputs are not divisible; ValueError!\n')
        except ZeroDivisionError:
            print('Cannot be divided by 0\n')
        else:
            print("num1 / num2 = " + str(division) + '\n')

add_numbers()

# Count words
line = "Row, row, row your boat."
print(line.count('row')) # 2
print(line.lower().count('row')) # 3
```

## Storing Data
The json module allows you to dump simple Python data structures into a file and load the data from that file the next time the program runs. You can also use json to share data between different Python programs. JSON(JavaScript Object Notation) data format is not specific to Python, so you can share data you store in the JSON format with people who work in many other programming languages.

Using json.dump() and json.load()
```python
# number_writer.py
import json

numbers = [2, 3, 5, 7, 11, 13]
filename = 'numbers.json'
with open(filename, 'w') as f_obj:
    json.dump(numbers, f_obj) # stores a piece of data to a file object
```

```python
# number_reader.py
import json

filename = 'numbers.json'
with open(filename) as f_obj:
    numbers = json.load(f_obj) # reads numbers back into memory

print(numbers) # [2, 3, 5, 7, 11, 13]
```

Saving and Reading User-Generated Data
```python
import json
# Load the username, if it has been stored previously.
# Otherwise, prompt for the username and store it.
filename = 'username.json'
try:
    with open(filename) as f_obj:
        username = json.load(f_obj)
except FileNotFoundError:
    username = input("What is your name? ")
    with open(filename, 'w') as f_obj:
        json.dump(username, f_obj)
        print("We'll remember you when you come back, " + username + "!")
else:
    print("Welcome back, " + username + "!")
```

Refactoring
```python
""" Often, you’ll come to a point where your code will work, but you’ll recog-
nize that you could improve the code by breaking it up into a series of func-
tions that have specific jobs. This process is called refactoring. Refactoring
makes your code cleaner, easier to understand, and easier to extend.
We can refactor remember_me.py by moving the bulk of its logic into one
or more functions."""
import json

def get_stored_username():
    """Get stored username if available."""
    filename = 'username.json'
    try:
        with open(filename) as f_obj:
            username = json.load(f_obj)
    except FileNotFoundError:
        return None
    else:
        return username

def get_new_username():
    """Prompt for a new username."""
    filename = 'username.json'
    username = input("What is your name? ")
    with open(filename, 'w') as f_obj:
        json.dump(username, f_obj)
    return username

def greet_user():
    """ Greet the user by name """
    username = get_stored_username()
    if verify_user(username):
        print("Welcome back, " + username + "!")
    else:
        username = get_new_username()
        print("We'll remember you, " + username + "!")

def verify_user(username):
    if username:
        answer = input("Is username, '" + username + "' correct?(y/n)")
        if answer.lower() == 'y':
            return True
        else:
            return False
    else:
        return False

greet_user()
```

# Testing Your Code

## Testing a Function
```python
# name_function.py
def get_formatted_name(first, last):
    """ Generate a neatly formatted full name. """
    full_name = first + ' ' + last
    return full_name
```

```python
# names.py
from name_function import get_formatted_name

while True:
    print("Enter 'q' at any time to quit.")
    first = input("Your first name >> ")
    if first == 'q':
        break
    last = input("Your last name >> ")
    if last == 'q':
        break
    formatted_name = get_formatted_name(first, last)
    print("\tNeatly formatted name : " + formatted_name + ".")
```

Unit Tests and Test Cases
```python
""" A unit test verifies that one specific aspect of a function’s
behavior is correct. A test case is a collection of unit tests that together prove
that a function behaves as it’s supposed to, within the full range of situations 
you expect it to handle """
# test_name_function.py
# Assert methods verify that a result you received matches the expected one
# The method name must start with test_ so the method runs automatically when we run test_name_function.py.
 
import unittest
from name_function import get_formatted_name

class NamesTestCase(unittest.TestCase):
    """Tests for 'name_function.py'"""
    
    def test_first_last_name(self):
        """Do names like 'Janis Joplin' work?"""
        formatted_name = get_formatted_name('janis', 'joplin')
        self.assertEqual(formatted_name, 'Janis Joplin')

unittest.main()
```

Check error messages after changing get_formatted_name implementation, or fix the code to avoid the error
```python
def get_formatted_name(first, last, middle=''):
    if middle:
        full_name = first + ' ' + middle + ' ' + last
    else:
        full_name = first + ' ' + last
    return full_name
```

Adding New Tests
```python
import unittest
from name_function import get_formatted_name

class NamesTestCase(unittest.TestCase):
    """Test for 'name_function.py'"""
    
    def test_first_last_name(self):
        """Do names like 'Janis Joplin' work?"""
        formatted_name = get_formatted_name('janis', 'joplin')
        self.assertEqual(formatted_name, 'Janis Joplin')
        
    def test_first_last_middle_name(self):
        """Do names like 'Wolfgang Amadeus Mozart' work?"""
        formatted_name = get_formatted_name('wolfgang', 'mozart', 'amadeus')
        self.assertEqual(formatted_name, 'Wolfgang Amadeus Mozart')

unittest.main()
```

Try it yourself
```python
# city_functions.py
def get_city_country(city, country, population=''):
    if population:
        location_info = city.title() + ', ' + country.title() \
                    + ' - population ' + str(population)
    else:
        location_info = city.title() + ', ' + country.title()
    return location_info
```
```python
# test_city_functions.py
import unittest
from city_functions import get_city_country


class CityCountryTestCase(unittest.TestCase):
    def test_city_country(self):
        location = get_city_country('aaa bbb', 'ccc')
        self.assertEqual(location, "Aaa Bbb, Ccc")

    def test_city_country_population(self):
        location = get_city_country('aaa bbb', 'ccc', 1000)
        self.assertEqual(location, "Aaa Bbb, Ccc - population 1000")

unittest.main()
```

## Testing a Class
Python provides a number of assert methods in the 'unittest.TestCase' class. You can use these methods only in a class that inherits from 'unittest.TestCase'
<table>
    <tr>
        <th>Method</th>
        <th>Use</th>
    </tr>
    <tr>
        <td>assertEqual(a, b)</td>
        <td>Verify that a == b</td>
    </tr>
    <tr>
        <td>assertNotEqual(a, b)</td>
        <td>Verify that a != b</td>
    </tr>
    <tr>
        <td>assertTrue(x)</td>
        <td>Verify that x is True</td>
    </tr>
    <tr>
        <td>assertFalse(x)</td>
        <td>Verify that x is False</td>
    </tr>
    <tr>
        <td>assertIn(item, list)</td>
        <td>Verify that item is in list</td>
    </tr>
    <tr>
        <td>assertNotIn(item, list)</td>
        <td>Verify that item is not in list</td>
    </tr>
</table>

A Class to Test
```python
# survey.py
class AnonymousSurvey():
    """Collect anonymous answers to a survey question."""

    def __init__(self, question):
        """Store a question, and prepare to store responses."""
        self.question = question
        self.responses = []

    def show_question(self):
        """Show the survey question."""
        print(self.question)

    def store_response(self, new_response):
        """Store a single response to the survey."""
        self.responses.append(new_response)

    def show_results(self):
        """Show all the responses that have been given."""
        print("Survey results:")
        for response in self.responses:
            print('- ' + response)
```
```python
# language_survey.py
from survey import AnonymousSurvey

# Define a survey, and make a survey
question = "What language did you first learn to speak?"
my_survey = AnonymousSurvey(question)

# Show the question, and store responses to the question
my_survey.show_question()
print("Enter 'q' at any time to quit.\n")
while True:
    response = input("Lanugage: ")
    if response == 'q':
        break
    my_survey.store_response(response)

# Show the survey results.
print("\nThank you to everyone who participated in the survey!")
my_survey.show_results()
```
```python
# test_survey.py
import unittest
from survey import AnonymousSurvey


class TestAnonymousSurvey(unittest.TestCase):
    """
    Tests for the class AnonymousSurvey
    The method test_store_single_response() verifies that the first response in
    self.responses—self.responses[0]—can be stored correctly, and test_store_
    single_response() verifies that all three responses in self.responses can be
    stored correctly.
    """

    def setUp(self):
        """
        Create a survey and a set of responses for use in all test methods.
        """
        question = "What language did you first learn to speak?"
        self.my_survey = AnonymousSurvey(question)
        self.responses = ['English', 'Spanish', 'Mandarin']

    def test_store_single_response(self):
        """Test that a single response is stored properly"""
        self.my_survey.store_response(self.responses[0])
        self.assertIn(self.responses[0], self.my_survey.responses)

    def test_store_three_responses(self):
        """Test that three individual responses are stored properly."""

        for response in self.responses:
            self.my_survey.store_response(response)

        for response in self.responses:
            self.assertIn(response, self.my_survey.responses)

unittest.main()
```

Try it yourself
```python
# employee.py
class AnonymousEmployee():
    def __init__(self, first, last, annual_salary):
        self.first = first
        self.last = last
        self.annual_salary = int(annual_salary)

    def give_raise(self, annual_raise=5000):
        if annual_raise:
            self.annual_salary += annual_raise
        else:
            self.annual_salary += 5000
```
```python
# test_employee.py
import unittest
from employee import AnonymousEmployee


class TestAnonymousEmployee(unittest.TestCase):
    def setUp(self):
        self.annual_salary = 80000
        self.my_employee = AnonymousEmployee('aaa', 'bbb',
                                             self.annual_salary)

    def test_give_default_raise(self):
        self.my_employee.give_raise()
        self.assertEqual(85000, self.my_employee.annual_salary)

    def test_give_custom_raise(self):
        self.my_employee.give_raise(8000)
        self.assertEqual(88000, self.my_employee.annual_salary)

unittest.main()
```


# Project 1. Alien Invasion

## install pip in Linux
```
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade

sudo apt -y install python3-pip

# check version
pip3 -V
```

## download and install [pip](https://bootstrap.pypa.io/get-pip.py) in Windows
```
python -m pip --version
python get-pip.py
```

## install pygame Linux
If you’re running Python 3, two steps are required: installing the libraries Pygame depends on, and downloading and installing Pygame.

The following is for python 3.5
```
# libraries for pygame
sudo apt-get install python3.5-dev mercurial
sudo apt-get install libsdl-image1.2-dev libsdl2-dev libsdl-ttf2.0-dev

# more libraries
sudo apt-get install libsdl-mixer1.2-dev libportmidi-dev
sudo apt-get install libswscale-dev libsmpeg-dev libavformat-dev libavcodec-dev
sudo apt-get install python-numpy

pip3 install --user hg+http://bitbucket.org/pygame/pygame

# if previous commands give "freetype-config" error try the following
sudo apt-get install libfreetype6-dev
```

To install pygame on python 3.6, check [here](https://askubuntu.com/questions/401342/how-to-download-pygame-in-python3-3)
```
# 1. Change to your home directory.
cd ~

# 2. Get Pygame source code.
sudo apt-get install mercurial
hg clone https://bitbucket.org/pygame/pygame
cd pygame

# 3. Install dependencies.
sudo apt-get install python3-dev python3-numpy libsdl-dev libsdl-image1.2-dev \
  libsdl-mixer1.2-dev libsdl-ttf2.0-dev libsmpeg-dev libportmidi-dev \
  libavformat-dev libswscale-dev libjpeg-dev libfreetype6-dev

# 4. Build and install Pygame.
python3.6 setup.py build
sudo python3.6 setup.py install
```

## download and install [pygame](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pygame) in Windows
```
python -m pip install --user pygame-1.9.3-cp36-cp36m-win32.whl
```


# Project 2. Data Visualization

## install matplotlib in Linux
```
sudo apt update
sudo apt install python3-matplotlib
sudo apt install python3.6-dev python3.6-tk tk-dev
sudo apt install libfreetype6-dev g++
pip3 install --user matplotlib
```

## download and install [matplotlib](http://www.lfd.uci.edu/~gohlke/pythonlibs/#matplotlib) in Windows
```
python -m pip install --user matplotlib-2.1.0-cp36-cp36m-win32.whl
```

mpl_squares.py
```python
import matplotlib.pyplot as plt

input_values = [1, 2, 3, 4, 5]
squares = [1, 4, 9, 16, 25]
plt.plot(input_values, squares, linewidth=5)

# Set chart title and label axes.
plt.title("Square Numbers", fontsize=24)
plt.xlabel("Value", fontsize=14)
plt.ylabel("Square of Value", fontsize=14)

# Set size of tick labels.
plt.tick_params(axis='both', labelsize=14)

plt.show()
```

scatter_squares.py
```python
import matplotlib.pyplot as plt

x_values = list(range(1, 1001))
y_values = [x**2 for x in x_values]

# plt.scatter(x_values, y_values, edgecolor='none', s=40)
# plt.scatter(x_values, y_values, c='red', edgecolor='none', s=40)
# plt.scatter(x_values, y_values, c=(0, 0, .8), edgecolor='none', s=40)
plt.scatter(x_values, y_values, c=y_values, cmap=plt.cm.Blues,
            edgecolor='none', s=40)

# Set chart title, and label axes.
plt.title("Square Numbers", fontsize=24)
plt.xlabel("Value", fontsize=14)
plt.ylabel("Square of Value", fontsize=14)

# Set size of tick labels.
plt.tick_params(axis='both', which='major', labelsize=14)

# Set the range for each axis.
plt.axis([0, 1100, 0, 1100000])

plt.savefig('squares_plot.png', bbox_inches='tight')

plt.show()
```

Random Walks
```python
# random_walk.py
from random import choice

class RandomWalk():
    """A class to generate random walks."""
    
    def __init__(self, num_points=5000):
        """Initialize attributes of a walk."""
        self.num_points = num_points
        
        # All walks start at (0, 0).
        self.x_values = [0]
        self.y_values = [0]

    def fill_walk(self):
        """Calculate all the points in the walk."""
        
        # Keep taking steps until the walk reaches the desired length.
        while len(self.x_values) < self.num_points:
            
            # Decide which direction to go, and how far to go in that direction.
            x_step = self.get_step()
            y_step = self.get_step()
            
            # Reject moves that go nowhere.
            if x_step == 0 and y_step == 0:
                continue
            
            # Calculate the next x and y values.
            next_x = self.x_values[-1] + x_step
            next_y = self.y_values[-1] + y_step
            
            self.x_values.append(next_x)
            self.y_values.append(next_y)
            
    def get_step(self):
        direction = choice([1, -1])
        distance = choice([0, 1, 2, 3, 4])
        return direction * distance
```

```python
# rw_visual.py
import matplotlib.pyplot as plt

from random_walk import RandomWalk

# Keep making new walks, as long as the program is active.
while True:
    # Make a random walk, and plot the points.
    rw = RandomWalk(50000)
    rw.fill_walk()
    
    # Set the size of the plotting window.
    plt.figure(dpi=128, figsize=(10, 6))
    
    point_numbers = list(range(rw.num_points))
    plt.scatter(rw.x_values, rw.y_values, c=point_numbers,
                cmap=plt.cm.Blues, edgecolor='none', s=1)
    # Emphasize the first and last points.
    plt.scatter(0, 0, c='green', edgecolors='none', s=100)
    plt.scatter(rw.x_values[-1], rw.y_values[-1], c='red',
                edgecolors='none', s=100)
    
    # Remove the axes.
    plt.axes().get_xaxis().set_visible(False)
    plt.axes().get_yaxis().set_visible(False)
    
    plt.show()
    
    keep_running = input("Make another walk? (y/n): ")
    if keep_running == 'n':
        break
```

## install pygal in Linux
```
pip3 install --user pygal
```

## install pygal in Windows
```
python -m pip install --user pygal
```

```python
# die.py
from random import randint

class Die():
    def __init__(self, num_sizes=6):
        self.num_sizes = num_sizes

    def roll(self):
        return randint(1, self.num_sizes)
```

```python
# different_dice.py
import pygal

from die import Die

die_1 = Die()
die_2 = Die(10)

results = []
for i in range(50000):
    result = die_1.roll() + die_2.roll()
    results.append(result)

frequencies = []
max_result = die_1.num_sides + die_2.num_sides
for value in range(2, max_result + 1):
    frequency = results.count(value)
    frequencies.append(frequency)

print(frequencies)

hist = pygal.Bar()

hist.title = "Results of rolling D6 and D10 50000 times."
hist.x_labels = ['2', '3', '4', '5', '6', '7', '8', '9', '10', '11',
                 '12', '13', '14', '15', '16']
hist.x_title = "Result"
hist.y_title = "Frequency of Result"

hist.add('D6 + D10', frequencies)
hist.render_to_file('dice_visual.svg')
```

## Downloading Data
You’ll download data sets from online sources and create working visualizations of that data.

We’ll use Python’s csv module to process data stored in the CSV format and analyze. Then use matplotlib to generate a chart based on downloaded data to display variations in temperature in two very different environments. Later, we’ll use the json module to access data stored in the JSON format and use Pygal to draw a population map by country.

At the end, you’ll be prepared to work with different types and formats of data sets, and you’ll have a deeper understanding of how to build complex visualizations. The ability to access and visualize online data of different types and formats is essential to working with a wide variety of real-world data sets.

### The CSV File Format
Python’s csv module in the standard library parses the lines in a CSV file and allows us to quickly extract the values we’re interested in. 
```python
# highs_lows.py

import csv
from datetime import datetime

from matplotlib import pyplot as plt

# filename = 'sitka_weather_2014.csv'
filename = 'death_valley_2014.csv'

try:
    with open(filename) as f:
        reader = csv.reader(f)
        header_row = next(reader)

        # for index, column_header in enumerate(header_row):
        #     print(index, column_header)

        # Get dates and high temperatures from file.
        dates, highs, lows = [], [], []
        for row in reader:
            try:
                current_date = datetime.strptime(row[0], "%Y-%m-%d")
                high = int(row[1])
                low = int(row[3])
            except ValueError:
                print(current_date, 'missing data')
            else:
                dates.append(current_date)
                highs.append(high)
                lows.append(low)

        highs = [int((x - 32) / 1.8) for x in highs]
        lows = [int((x - 32) / 1.8) for x in lows]

except FileNotFoundError:
    msg = "\nSorry, the file '" + filename + "' does not exist."
    print(msg)
else:
    print("\nFile '" + filename + "' was successfully processed...")

# Plot data using matplotlib.
fig = plt.figure(dpi=128, figsize=(10, 6))
plt.plot(dates, highs, c='red', alpha=.5)
plt.plot(dates, lows, c='blue', alpha=.5)
plt.fill_between(dates, highs, lows, facecolor='blue', alpha=.1)

# Format plot.
title = "Daily high and low temperatures - 2014\nDeath Valley, CA"
plt.title(title, fontsize=20)
plt.xlabel('', fontsize=12)
fig.autofmt_xdate()
plt.ylabel("Temperature (F)", fontsize=12)
plt.tick_params(axis='both', which='major', labelsize=12)

plt.show()
```


## The JSON File Format
```python
# this does not works
from pygal.i18n import COUNTRIES
```

install pygal_maps_world module
```
# linux
pip3 install --user pygal_maps_world
# windows
python -m pip install --user pygal_maps_world
```

```python
# world_population.py
import json
from country_codes import get_country_code

filename = 'population_data.json'
with open(filename) as f:
    pop_data = json.load(f)

for pop_dict in pop_data:
    if pop_dict['Year'] == '2010':
        country_name = pop_dict['Country Name']
        population = int(float(pop_dict['Value']))
        code = get_country_code(country_name)
        if code:
            print(code + ": " + str(population))
        else:
            print('ERROR - ' + country_name)
```

```python
# countries.py
from pygal_maps_world import i18n
from pygal.maps.world import COUNTRIES

for country_code in sorted(COUNTRIES.keys()):
    print(country_code, COUNTRIES[country_code])
```

```python
# country_codes.py
from pygal_maps_world import i18n
from pygal.maps.world import COUNTRIES


def get_country_code(country_name):
    """Return the Pygal 2-digit country code"""
    for code, name in COUNTRIES.items():
        if name == country_name:
            return code
    return None
```

