* [1. Getting Started](#1-getting-started)
* [2. Variables and Simple Data Types](#2-variables-and-simple-data-types)
* [3. Introducing Lists](#3-introducing-lists)
* [4. Working with Lists](#4-working-with-lists)
* [5. if Statements](#5-if-statements)
* [6. Dictionaries](#6-dictionaries)
* [7. User Input and while loops](#7-user-input-and-while-loops)
* [8. Functions](#8-functions)
* [9. Classes](#9-classes)
* [10. Files and Exceptions](#10-files-and-exceptions)
* [11. Testing Your Code](#11-testing-your-code)
* [Project 1. Alien Invasion](#project-1-alien-invasion)
* [Project 2. Data Visualization](#project-2-data-visualization)
* [Project 3. Web Applications](#project-3-web-applications)

# 1. Getting Started
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

# 2. Variables and Simple Data Types
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

# 3. Introducing Lists
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
del fruit[1] # remove
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

sorted() for sorting temporarily
```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
print('Sorted List: ')
print(sorted(cars))
print('Original List: ')
print(cars)
```

sorted() for sorting temporarily in reverse order
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

# 4. Working with Lists
```python
magicians = ['alice', 'david', 'carolina']
for magician in magicians:
    print(magician.title() + ", that was a great trick!")
    print("I can't wait to see your next trick, " + magician.title() + ".\n")
print("Thank you, everyone. That was a great magic show!")
```

