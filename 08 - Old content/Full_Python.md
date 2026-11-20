i#### Display the version of python in your machine ( Linux ) : 

| in order to search for `python` version installed in your machine you need to run some cuple commands in the terminal .
| `python -v or python --version` this command will display the version unless you don't have many versions installed 
| `which python` search for python file location 
| `wereis python` search deeply for any python file.
| `python3` open interactive mode REPL ' Read Eveluate Print Loop'
| `pip install python3.10` install python

##### What is ipython ?
| `ipython` ( or Interactive python ) is a enhanced version of the python REPL.
| to install it run `pip install ipython3`
| `timeit` to test time of execution of your code.

#### Difference between module, package
| `pypi` or **python package index** 


##### python packages
| `os`
```python 
import os 
os.getcwd() # get current working dir 
os.uname()  # return os name
```

| `sis`
```python 
import sys 

sys.path()  # locations that python lock in to find packages 
```
##### what pip ?

>`pip`  or package installer for python
  `pip list` this command will list all packages installed
  `pip show os`  this command shows info about a specific package installed.

#### Virtual envirements and testing in python 
>install venv 
  `sudo apt install python3.11-venv`
  to create a virtual envirement you need to run this command : 
  `python3 -m venv <env_name>` 
  in order to activate this venv you need to do the following : 
  `source env_name/bin/activate` this will activate the virtual envirement
  `deactivate`  this command will deactivate the venv

| <font color="#75aa84">Remarque</font> 
The activation of a venv will change the `prompt` to tell you that you are in a virtual env and it will affect also the `sys.path` which means that any installed packages in the venv won't be asseccible outside it like a `container`

#### Anaconda ?
<font color="">Anaconda</font> is a data science toolkit  

#### Jupiter note book 
> `jupiter` notebook is an execution envirement used by data scientists to visualise and tell the process as a story

## Python closer look 

### 1. variables 

variables and Assignements statements
> `x = 'b'` and `y = 5` in case of a constant : `NAME = 'anis`
> naming convention : <font color='#F5F56F'>snake_case</font>
> you can also write huge numbers in this format : `100_000_000_000` to make it more readable and clear.
> to assign multiple variables in the same time : `x, y, z = 5, 7, 9`
> to assign multiple variables with the same value : `x = y = 200`

#### Data types or data structures in python : 
- int 
- float 
- str 
- dict 
- list 
- set 
- tuple 
- None 
### 2.  Numbers 

##### 2-1.  Assignment operators


| operator | Exemple | same as    |
| -------- | ------- | ---------- |
| =        | x  = 5  | x = 5      |
| +=       | x += 5  | x = x + 5  |
| -=       | x -= 2  | x = x - 2  |
| *=       | x *= 2  | x = x * 2  |
| /=       | x /= 2  | x = x / 2  |
| %=       | x %= 3  | x = x % 3  |
| //=      | x //= 2 | x = x // 2 |
| **=      | x **= 2 | x = x ** 2 |
| &=       | x &= 20 | x = x & 20 |
| \|=      | x \|= 1 | x \|= 1    |
| ^=       | x ^= 23 | x = x ^ 23 |
| >=       | x >= 12 | x = x > 12 |
| >>=      | ...     | x = x >> 2 |
| <<=      | ...     | x = x << 2 |

##### Exemple : 

``` python
x = 10 

x += 10 # x = x + 10 
print(x)

x -= 5  # x = x - 10 
print(x)

```


#### Arithmetic operators : 
| Operation                               __ | Result                                                                                                                                                                              |
| ------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `x + y`                                    | sum of x and                                                                                                                                                                        |
| `x - y`                                    | difference of x an                                                                                                                                                                  |
| `x * y`                                    | product of x a                                                                                                                                                                      |
| `x / y`                                    | quotient of x                                                                                                                                                                       |
| `x // y`                                   | floored quotient of x                                                                                                                                                               |
| `x % y`                                    | reminder of                                                                                                                                                                         |
| `-x`                                       | x                                                                                                                                                                                   |
| `+x`                                       | x                                                                                                                                                                                   |
| `abs(x)`                                   | absolute value of                                                                                                                                                                   |
| `int(x)`                                   | x conve                                                                                                                                                                             |
| `float(x)`                                 | x converted to a                                                                                                                                                                    |
| `complex(rel, img)`                        | comple a complex number with real and imaginary _im_ default is  nd imaginary _Ex :_ `my_comp = complex(2, 10)` to access real part `my_comp.real` and the imaginary `my_comp.imag` |
| `c.conjugate()`                            | conjugate of the complex number `c` which is the inverted value of the `c` provided `x = (1+2j)` _conjugate_ `x = (1-2j)`                                                           |
| `divmod(x, y)`                             | the paire `(x // y, x % y)`                                                                                                                                                         |
| `pow(x, n)`                                | x to power of n                                                                                                                                                                     |
| `x ** n`                                   | x to power of n                                                                                                                                                                     |

```python 
x = 7 / 4  # 1.75
x = 7 // 4 # 1 it returns the smallest value between : 1 .. x .. 2
```

## Python continue ...

#### Mathimatical operations

##### Mathimatical shorthand 

```python 
a = 1
a = a + 1 
a += 1  
print(a) # 3
// # intger devision  
/  # floor devision
```

##### Mathimatical percendence 

```python
parenthecies -> then -> ** -> then -> (*, /, //, %) -> then -> +, -
```

##### Mathimatical rounding 
1. `python`  when it commes to rounding it does it in a different way for exemple when we round a num it will return the closest even number to the number that we have
```python
a = 3.4
b = 3.5
c = 2.5
print(round(a))  # 3
print(round(b))  # 4
print(round(c))  # 2
# To change the behavior of our rounding method we can use the second argument in the round method 
total = 20 / 3 # 6.66666667
print(round(total))  7
print(round(total, 1))  6.7
print(round(totsl, 2))  6.67
print(round(total, 3))  6.667
total = 200 / 3
print(round(total, 2))  66.67
print(round(total, -2)) 100



```




#### Strings operations

##### 1. Type `Casting` in python
```python 
	a = '1'
	float(2)
	str(1)
	complex(5)
	...
	print(type(int(a))) # <class 'int'>
```

##### 2. Escape char or sequance
```python 
# new line \n
print('hello \n world')
# tab \t
print('hello \t world')
# delete space before \b
print('hello \b world') #helloworld
# vertical tab \v
print('soukaina\vbachar') # soukaina
						  #			bechar
```

##### 3. String methods 
```python 
name = 'Itsmesam'
name.upper()
name.lower()
name.startsWith('A')
name.endsWith('G')
name.center()  # this method centers the text passed to it
name.capitalise()
input().strip() # remove empty spces (trailing spaces)
name.isdigit() # return true if all chars in the string are false
name.isspace() # return true if all chars are spaces 
name.find()    # return the index of a char in a string
name.zfill()   # Fill the string with zeros until a certain amount
name.title()   # capitalise the first letter of each word in the sentance
name.index()   # returns the index of a given char : index('A') - 4
name.replace(old, new) # replace something by another
name.find('@') # return index of the of the char given if not found return -1
name.split(sep, maxsplit)   # split the string into an array of words default any white space [" ", \n, \t] maxsplit default value is -1 
```

we can chaine methods 
```python 
name: str = input('Enter name : ').strip().title() 
```

##### 5. formated String 
```python 
name: str = 'kali'
print(f'{name:_<5}') # ____Kali
print(f'{name:_>5}') # Kali____
print(f'{name:_^5}') # __Kali__
# controlling floats 
num: float = 15.554
print(f'{num:,.2f}') 15.55
```

##### how to exec code after a certain amount of time in python ?
```python 
import time 
time.sleep(3) # in seconds
```

1. how we can use the datetime module to get the current year, month and day 
```python
from datetime import date
my_date: date = date.today()
year: int  = my_date.year
month: int = my_date.month
day: int   = my_date.day
```

##### Exercice :
![]("C:\Users\houss\Downloads\Task.png")
```python 
# get username

name: str = input('Enter Your name : ').strip().lower().title()

# get the year of birth

year: int = int(input('Enter Your Birth Year : '))

# get the month of birth

month: int = int(input('Enter Your Birth Month : '))

# get the year of birth

day: int = int(input('Enter Your Birth Day : '))

# create the username

username: str = f"{name.replace(' ', '_')}_{month}_{day}_{year}@codezilla.com"

# output

print('-'* 30)

print('Your username is ...')

time.sleep(2)

print(f"-> {username}")
```

## What is an expression vs statement ?
1. an `expression` is a value that can be stored in a variable or be printed.
2. a `statement`  or an `assignement statement` is a value that can not be printed like :

```python
print(x = 2) # this syntax will throw an error.
# or assignement statement
```
3. `print()` is an a expression and statement at the same time because it it can be stored in a variable and also it can be printed.

### How to skip a statement you still don't know what to write in it ? 
1. the keyword `pass` is used when 
```
```

2. `or , and ` syntax :
```python 
if x == 3 or == 4 : # this is wrong 
if x == 4 or 3 :    # this is also wrong 
---------
# this is the right way to do it 
if x == 2 or x = 3: 
# same thing for and 
```


## List data type : 

- this data types help us to hold many data 
```python
# without list
name1 = 'ahmed'
name2 = 'yassin'
name3 = 'bali'

# with list 
names = ['ayoub', 'amine', 'khaled']
```

><mark color="#F00">Remarque : </mark>
>we can't access to nested elements using `in` 
>Exemple :
```python 
nums: list = [12, [2, 3], 22]
num : int  = 3

if num in nums:
	print('Found')
else:
	print('Not found')

# Output : not found.
```

### List slicing :

[begin: end (not included)]

```python 
names: list = ['name1', 'name2', 'name3', 'name4',
               'name5', 'name6', 'name7', 'name8']
# names from 1 to 4  
print(names[:3])  
# names from 6 to last  
print(names[5:])  
# all without last  
print(names[:-1])  
# last two names  
print(names[-3:])
```

### List manipulation 

1. add element to the array | list

```python
nums = [1, 2, 3, 4]
num  = [5]
nums = nums + num
print(nums * 2) # repete the content iside the array two time 
# output : [1, 2, 3, 4, 1, 2, 3, 4]
-----
# replacing enthesies 
nums[:3] = [3, 66]

```

2. `string slicing`

```python
name = 'houssam'
print(name[3:])   # ssam
print(name[-4:])  # ssam
```

#### List unpacking : 
- this syntax will throw an error if nums of variabales are bigger than number of elements of the list
```python 
nums: list = [12, 23, 33, 42]
num1, num2, num3, num4 = nums # valid syntaxe
num1, num2, num3, num4, num5 = nums # this is an unvalid syntaxe
```

### List functions :

1. we gonna cover all the list methods & functions including `max` , `min` , `avg` .
```python 
max(array)  # return the highest number in the list
min(array)  # return the lowest  value in the list
sum(array)  # the sum of all items in the array
', '.join(array) # join the array using coma space 
array.pop(index) # remove an element at specified position
array.append(element) # add element to the end of the list
array.clear()   # removes all the elements of the array
array.extend()  # add array to the end of current array "merge"
array.insert(index) # add an element in a specific position
array.remove()  # remove the first item of the list
array.reverse() # reverse the order of the list
array.index(element) # return the index of the element
```
##### sorting lists

1. pay attention you can't store the sorted array in a new variable cause the value that will be stored is `None` because the sort function modifies the original array so you don't need to create a new variable
```python 
array.sort(key, reverse)  # sorts the array applied to 
# Exemple 
my_array: list = [2, 3, 6, 4. 1, 0]
# we need to sort the array first 
my_array.sort()
# what are the 5 highest
print(my_array[-5:])
# what are the 5 lowest nums
print(my_array[1:5])
```

#### diffrent array methods : 

```python 
names: list = ['jack', 'yassin', 'houssam', 'jamal', 'ayoub']  
  
print(names) # ['jack', 'yassin', 'houssam', 'jamal', 'ayoub']
names.append('haytham')  
print(names) # ['jack', 'yassin', 'houssam', 'jamal', 'ayoub', 'haytham']
names.insert(0, 'reda')  
print(names) # ['reda', 'jack', 'yassin', 'houssam', 'jamal', 'ayoub', 'haytham']  
names.pop(1)  
print(names) # ['reda', 'yassin', 'houssam', 'jamal', 'ayoub', 'haytham']
names.extend(['samir', 'ahmed'])
print(names) # [ all elemtnt, 'samir', 'ahmed']
names.clear()  
print(names) # []
--------
# pay attention !!! 
array.extent('new')
print(array) # ['one', 'two', 'n', 'e', 'w']
array.extend(['new'])
print(array) # ['one', 'two', 'new']

--------
array.extend(new_array) = array + new_array


--------- make copy of an array ------------
new_array = array.copy() 
# or 
new_array = array[:]

```


### Truthy falsy values ?

1. falsy values : 
```python
[]             # empty array
{}             # empty set or dict
()             # empty tuple
""             # empty string
range(0)       # range of 0
int: 0         # 0
float: 0.0     # 0.0
complex: 0j    # complex 0+0j
bool: false    # false expression
```


# Measure the time 

1. we mainly use the `time` module
```python
import time 
start: time = time.time()
end_tm: time = time.time - start
```


# String library 

1. in this example we gonna use the `string` library to generate a strong password

```python
import string
import random

# take a random char
char: str = random.choice([iterable])


# generate letters small
small_letters: str = string.ascii_letters
capital_letters: str = string.ascii_uppercase
digits: str = string.digits
punctuation: str = string.punctuation
```


#### Generate random floats 

```python
from random import uniform 

num: float = uniform(1, 19)
```


# Loops 

1. while Loop

```python
while True: 
	process ...
```

2. for loop 

```python 
nums: list = [1, 2, 3, 4, 5, 6]
for num in nums: 
	print(num)
```

# To print multiple elements in the same line

1. we use the `end` arg in the print function

```python 
# output : "1,3,5,7,9,11,13,15,17,19,21,23,25,27,29"                            
nums: list = [1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 
25, 27, 29]
print('"', end="")
for num in nums[:-1]:
	print(f"{num}", end=",")
print(f"{nums[-1]}\"")
print()
```

# Range function 

1. `range` function returns a sequance of numbers sep by default is 1 , not includes the end it takes three params : 

```
start : were to start default is 0 [opt]
stop  : stop not included [req / man]
step  : the steps default is 1 [opt]
range(start, stop, step)
```

2. How to use range to generate desired amount of nums in a list 

```python 
nums: list = list(range(5))
print(nums) # [0, 1, 2, 3, 4]
```

### Help()

1. help function can help us to display the docs of a func 

```python 
print(help(range))
```


# Tuple data type : 

1. `Lists` are mutable data types, `tuples` are not which mean tuple doesn't support value changing 

# zip function

1. this function merges two or more lists, tuples ...
2. when zip starts working if it doesn't find a value to merge it will not show that value

```python 
name = ['ahmed', 'lamia', 'mouhaila', 'zoubida']
grade = [12, 14, 13]
print(list(zip(name, grade)))  # [[ahmed, 12], [lamia, 14], [nouhaila, 13]]
```


## enumerate function 

1. is a function used to numerate an iterable given as params and returns an enumerate object, `enumerate()` it's the optimal way to write python code in a pythonic way cause it gets deleted from the memory after beign used.

```python
names = ['ahmed', 'salim', 'rehab']
numbred_names = enumerate(names)
print(list(numbred_names))
```


## List comprehension 

```python
numbers: list = [10, 12, 3, 43, 1, 32, 4, 14, 5]
new_numbers: list = [num-2 if num >= 10 else num for num in numbers]
print(numbers)      # [10, 12, 3, 43, 1, 32, 4, 14, 5] 
print(new_numbers)  # [8, 10, 3, 41, 1, 30, 4, 12, 5]
```


# Unpacking operator 

1. we use `*` for arrays and `**` for objects

```python
sentences: list = ['Hello from Codezilla', 'Python Course is awesome', 'I enjoy learning Python with Codezilla']
new_sente: list = []
add_sente: list = ['I\'m houssam', 'and this is an additional text']
all_sente: list = [*sentences[:], *add_sente[:]]
```

2. Another use case of the unpacking 

```python
nums: list [12, 3, 43, 55, 64]
first, *rest, last = nums
print(first, rest, last)  # 12, [3, 45, 55], 64
```

# dir() function 

1. is a function used to display all the functions of a certain data type

# Set data type 

1. is a data type that holds only unique values 
2. methods 

```python
set.add()
set.clear()
set.copy()
set.differance()
set.union()
set.update
```

### Throw away variable 

1. we use the throw away variable in severale cases but mostly when we loop over something and we dont use the looper syntax `_`

```python
for __ in nums:
	...pass
```


# Dictionary data type

1. in dict we can use only brakets notation 

```python 
names: dict = {
	num1: 1, 
	num2: 2
}

print(names['num1']
```

2. add a new record 

```python 
price["phone2"] = 12_000
```

## del statement

- del statement is a statment like `if, else, ...` used to delete a recored in a dict

```python 
$ delete a record 
del prices["phone2"]
```

- also the `dict` key has to be an emutable like : `string, tuple` not `array, set`

#### sub dictionaries

```python
students: dict = {
	"Ahmed": {
		"grades": [89, 88, 90]
	},
	"mohamed": {
		"grades": [87, 99, 78]
	}, 
	"salim": {
		"grades": [95, 65, 76]
	}}
print(students["Ahmed"]["grades"])

```

### add elements to the dict

```python 
menu: dict = {
"Cheese pizza": 100,
"Veggie pizza": 120,
"Hawaiian pizza": 150,
"Coke": 30,
"Sprite": 25,
"Fanta": 25,
"Pepsi": 30
}

print(f'before : {menu}')
menu["Ice cream"] = 30
menu["Chocolate Cake"] = 60
menu["Cheese cake"] = 70
menu["Brownie"] = 40
menu["Donut"] = 30
print(f"after : {menu}")
```

# update()

1. this function helps us to add multiple records to our object 

```python
burgers: dict = {...}
new_burgers = {one: 12, two: 13, three: 8}
burgers.update(new_burgers)
```


# another syntax to add to the object

```python 
dict1 = {}
dict2 = {}
dict3 = dic1 | dict2
```

# dict unpacking 

```python 
dict1 = {}
dict2 = {}
new_dict = {**dict1, **dict2}
```

## Another syntax to define a dict

```python
my_dict = dict(one=1, two=2, three=3)
```


# Fix dictionary changed size during iteration

1.  The Python "RuntimeError: dictionary changed size during iteration" occurs when we change the size of a dictionary when iterating over it. so to solve it we create a copy of our main dict

```python
# search for the item 
	for item in menu.copy(): 
		if item_name == item:
			confirm: str = Confirm.ask(f'Do you want to delete {item}')
			if confirm:
				del menu[item]

```


# Python getters & setters

1. the `get` method is a dict method that searches for a dict key and brings it value if the key doesn't exist it will return None by default but we can change the value of that in the second argument of the method 

```python
dict.get(key, value to return if key doesn't exist default None)
# exemple
names: {
	name1: 'sosks'
}
if names.get(name1):
	print('found')
else: 
	print('not found')
```

2. the `setdefault` searches for an dict key to and if not exists it will create it and assign to it the second arg of the method which is `none` by default

```python
names: {
	ahmed: 23
}
names.setdefault('salim', 20)
print(names) # { ahmed : 23, salim : 20}
```

# dict methods chaining

```python
items: dict = {
    'panadol': {
        'price': 32,
        'quantity': 23
    },
    'zinc': {
        'price': 43,
        'quantiy': 43
    },
    'omega 3': {
        'price': 34,
        'quantity': 12
    }
}
# get user input 
name: str = input('Enter treatement name : )
price: int = items.get(name, {}).get(price)
print(price)
```


# Python tutor

website to visualise execution of a script


# Functions in python 

1. functions with default values : always args with defaullt value are the last

```python 
# wrong 
def name(age=12, city="beni mellal", country)
# true
def name(country, city="", age=12)
```

2. when function call we call them `parameters` and when function definition we call them `arguments`

# \*Args and \*\*Kwargs

```python 
def my_func(*args):
	print(args) # ----> tuple'

def special_sum(numbers, **kwargs):
    print(kwargs) # this code is a hint to see what is inside kwargs
    if kwargs.get("only_even"):
        return sum([number for number in numbers if number % 2 == 0])

numbers = [1, -2, -3, 4, -5, -6, -7, 8, 9, -10, 11, 12, 13, 14, -15, -16, 17, 18, 19, 20]

print(f"Sum of all numbers: {special_sum(numbers)}")
print(f"Total even numbers: {special_sum(numbers, only_even=True)}")
print(f"Total odd numbers: {special_sum(numbers, only_odd=True)}")
print(f"Total positive numbers: {special_sum(numbers, only_positive=True)}")
print(f"Total negative numbers: {special_sum(numbers, only_negative=True)}")
print(f"Total positive even numbers: {special_sum(numbers, only_positive_even=True)}")
print(f"Total positive odd numbers: {special_sum(numbers, only_positive_odd=True)}")
print(f"Total negative even numbers: {special_sum(numbers, only_negative_even=True)}")
print(f"Total negative odd numbers: {special_sum(numbers, only_negative_odd=True)}")
```


# pythonic functions & ternary operators

```python 
# ternary operator
valie if condition1 else value2'
['even' if num % 2 == 0 else 'odd' for num in nums]
```


# Deepcopy 

```python 
from copy import deepcopy

main: list = [{"one": 1, "two": 2, "Three": 3}]
second: list = deepcopy(main)

print(main)
print(second)
```

# one line condition in python

1. in one line condition we can perform multiple operation by seperating them with semi colone

```python
if not tasks: print('there are not tasks'); return
```


# Pythonic way of writing functions

1. always write ur main code in a `main()` function 
2. there are different ways to import from another `.py` file

```python 
import file
from file import func1
from file impoert func1 as f1
from file import *
```

3. always use `if __name__ == '__main__'` so that u would be able to use that code in another python file without executing the whole file

```python 
if __name__ == "__main__":
	main()
```


# Error handling 

`valueError`  --> handles type casting from an int to a str for example
`IndexError`  --> handles passing an index out of range
`TypeError`    -->
`ZeroDivisionError`  --> handles division by 0 errors
`Exception`  --> generale exeption

1. we can use multiple `except` to handle an error

```python 
def mark_task():
    view_task(tasks)
    if not tasks:
        print('[yellow]Warnning[/yellow] Please enter tasks before')
        return
    # get task to mark as complete
    try:
        task: int = int(Prompt.ask('[yellow]Please enter the task to mark as complete '))
        if task < 1 or task > len(tasks):
            raise IndexError('[red]Error : [/red]Please enter a valid task number')
        # change the complete value to true
        tasks[task - 1]["complete"] = True
        print('[green]Success : [/green] task was marked as completed')
    except ValueError:
        print(f"[red]Error : [/red]Please enter a number to continue")

```


# File handling

> - In general we have three mods of file manipulation we have the `r : read` , `w : write`, `a : append`

### Read the content of a file 

1. first we need to `open` file 

```python 
file = open('./employes.txt') # by default read r
```

2. read content of the file 

```python
file.read() # reads all the content of the file and returns a string
file.readline() # returns a line 
file.readlines() # reads all the content of a text file and returns an array of content
```

> <font color="#f00">Remarque</font> : the content get's deleted from the memory after the first time we read the content of the file, to get the content again we need to `open` the file again which is a bit long so to solve this problem you **should** store the content of the file in a variable

3. to prevent memory leak we need to close the file after `file.close()`

##### Second syntax to open file which closes the file automaticly

1. `with` syntax

```python
with open('path', method) as file:
	data = file.readline()

print(data)
```

### Edit file via python "write"

1. in order to write inside a file we use the `w` mode which help us to write inside a specific file and if the file doesn't exist it will be created automatically

```python 
with open('file1.txt', 'w') as file:
	...
```

2. to write content inside the file we use the `write()` function 

```python
with open('fileOne', 'w') as file:
	file.write('line1')
	file.write('line2')
```

3. we can also use `writelines` which accepts an array of lines to write

```python
all = [...]
with open('./file.txt', 'w') as file:
	file.writelines(all)
```
### append to the content of a file 

1. the `append` method is mainly used in file handling to append or add content to an existing file without deleting it's base text, throws error if file doesn't exists

```python
with open('path', 'a') as file:
	file.write('...text')
```


#### Raw string 

1. we use raw strings to fix the problem of `\` back slaches that could be counted sometimes as `escape char` to fix that we do the following :

```python
with open(r"...", 'r') as file:
	file.read()
```


#### Relative and absolute path 

`relative path` :  `./main.py`
`absolute path` :  `/users/user1/download/main.py`

```python 
with open('/mnt/d/Python_all/dir1/employes.txt') as f:
    emp_data = f.readlines()

with open('file.txt', 'w') as f:
    for emp in emp_data:
        new_emp: list = emp.strip().split('-')
        new_salary = float(new_emp[-1]) * 2
        f.write(f"{new_emp[0]} {new_emp[1]} {new_emp[2]} {new_salary}\n")
```



#### Smart slicing

`[start:stop:step]

```python
nums: list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

print(nums[:5:2])  # [1, 3, 5]

print(nums[::-1])  # [10, 9, 8, 7, 6, 5, ...]

print(nums[0::3])  # [1, 4, 7, 10]
```


### Old way to do formating 

```python
print('hello my name is () and my age is ()'.format(name, age))
print('hello my name is (0) and my age is (1)'.format(name, age))
-----------------------------------------------------------------
print('hello my name is %s' % name)
d : digit
print('hello my name is %d' %age)
```



# Os library 

1. get the current working directory we use `getcwd()`

```python 
import os
current_dir: str = os.getcwd()
```

2. list all the sub files in a directory we use `listdir()` method

```python 
import os 
all_files: list = os.listdir()
```

#### Simple files application

1. in this script we are going to read data of all files located in a directory and create a new file that contains all the data that we've got + each file title above 

```python 
from enum import CONFORM
import os

current_dir: str = os.getcwd()
files: list = os.listdir()

# string that will contain all the content of the files
all_files: str = ''

# now we need to loop through the files and get there inner text
for file in files:
    with open(f'{current_dir}/{file}', 'r') as f:
        if file == 'all_files.txt':
           continue
        book_name: str = ' '.join(file.split('.')[0].split('_')[:-1])
        content: str = f.read()
        all_files += f"{book_name} : \n{content}\n"


# now let's create a new file
with open(f"{current_dir}/all_files.txt", 'w') as file:
    file.write(all_files)

```


## RegeEx or regular expressions in python

`\d` -> one digit
`\D` -> one not digit
`\s` -> one whiteSpace
`\S` -> one not-whitespace
`\w`  -> one word char --> (__all + '_' except punctuatiom)
`\W` --> one non-word character



## Quantifiers in regex : 

`{..}` --> we use curly braces to 
`.`  --> any character without new line `\n`
`+`  --> one or more chars
`()` --> match only what is inside brackets 
`[abc]` --> find the a, b, and c letters in the text 
`[ab-d]` --> find chars from a to d
`[a-zA-z] or [A-z]` --> all chars from a to z lower and upper case
`[^a-s]` --> return everything except letters from a to s
`a|b`  --> either a or b

`^N`  --> start of string is N  --> start of string
`$S`  --> ends with the string S  --> end of string 

- we use escape char in regex in order to match some chars that means something in regex like `.` which selects any char except `\n` so if we want to select the dot we need to do the following :    `\.` --> search for dot in the string

```python 
find salary in a string : $5000
--> (\$\d+) first method
--> (\$.+) second method
```


### The re module 

1. `re` module is the module that contains all regex methods in python 

	- `findall` : which returns a list containing all matches
```python 
import re
txt = 'Ai is the future'
txt: list = re.findAll('Ai', txt)
print(txt)
```

- `search` : return a match object if there is a match anywhere in the string 
- `match object` -> is an object containing information's about the search and the results
	- the match object has properties and methods : 
		- `span()`   --> return tuple containing the start, and the end index of the match
		- `string`   --> returns the string passed into the func
		- `group()` --> returns the part of string where there was a match
```python
import re
result = re.search('Future', txt.lower())
print(result.group())
```

- `sub` : replace one or many matches with a string

```python 
import re as regex
new_txt = regex.sub('old_word', 'new_word', txt)
```

#### Application 

1. find name, email, dob

```python
# extract name , email, and dob
name: str = re.findall(r'name:(.+)', txt.lower())[0]
format: str = r"email: (\S+)"
email: str = re.findall(format, txt.lower())[0]
dob: str = re.findall(r'dob: (\d{2})/(\d{2})/(\d{4})', txt.lower())[0]
day, month, year = dob
print("Name :", name)
print("Email :", email)
print("dob :", day, month, year)
```


# Csv files (Coma seperated values)

1. to read from a csv file we use the `reader` function provided by the build in csv module this func returns a list of lists 

```python
import csv 
with opne('file.csv') as f:
	emp = csv.reader(f)
	
```

2. this is called a doc string or document string : `""" """`
3. `sorted(iterable, reverse, key)` is a function to sort an iterable based on a criteria it returns only list type no matter what is the input type the function sortes by default based on the first index that meets to change that behavior we use the key parameter 
	the `key` is a function to determine the sorting approach
4.  the `sorted()` function is a must use when it commes to sorting 2d lists or objects based on a certain criteria this function returns a list of lists if input was of type `list` else it return a list of `tuples` if the input was of a object type 

```python
my_object: dict = {
    "orage": 22,
    'apple': 12,
    'pineapple': 26,
    'grapes': 21
}
item = (orange, 22) # in each iteration the iten var will store a tuple
print(sorted(my_object.items(), key= lambda item: item[-1]))
```

#### DictReader()

- this method returns a reader object that can be resolved to a list of object or a tuple of objects or a set of objects 

```python 
import csv 
with open(path) as file: 
	csv_reader = csv.DictReader(file)
	content: list = list(csv_reader)
```

### write in a csv module

1. we use the `writer()` method returns a `writer object`

```python 
import csv 
with open('./file.csv', 'w', newline='') as file:
	# create file
	csv_writer = csv.writer(file)
	# insert list of rows 
	csv_writer.writerows(list(sorted_emp))
	

```

##### Lambda function in python 

```python
name = lambda x: f"hello {x}"
print(name("soukaina"))

---
items: list = [
    # All items
    ["dell laptop", 9, 1_000],
    ['hp laptop', 3, 800],
    ['lenovo laptop', 7, 1_000],
    ['asus laptop', 4, 1_200],
    ['acer laptop', 6, 900],
    ['macbook laptop', 2, 2_000]
]

# sort the available items based on the price
print(sorted(items, key=(lambda item : item[-1])))
# sorting based price or quantity
print(sorted(items, key=lambda item: (item[-1], item[-2])))
```

### Comparisson : 

```python 
print((2000, 23, 9) > (2000, 23, 2)) # True
```


## Help function & document your code best practice 

1. in order to document our code we mainly use document string inside our function as well as type hinting which

```python 
def test_funct(par1: str, par2: int)-> str:
	"""
		this function is a test function 
		parameters:
			par1 : this is the first parameter
			par2 : this is the second parameter
		return: 
			the function returns a test string
	"""
```


# Handling json files :




---




# Object Oriented Programming

- oop important  concepts 
	- `Abstraction`
	- `Encapsulation`
	- `Enheritance`
	- `Polymorphism`

- Everything around us is an object

1. how we can notice the object type of every data type in python ?

```python 
def main():
	...

print(type(main)) # <class 'function'>
we add brakets if we want to call / trigger the function
--------------------------
print(type(len)) <class 'builtin-function-or-method'>
```


##### What is oop ?
- oop is a paradigm in programming 

##### Identify classes in python 

```python 
name = "code"
empty_str = str()

num = 1
empty_num = int()

my_list = [1, 2, 3]
empty_list = list()

print(type(name))
print(type(empty_str))

print('-'*20)

print(type(num))
print(type(empty_num))

print('-'*20)

print(type(my_list))
print(type(empty_list))

-------- Resultat ------------
<class 'str'>                                                      
<class 'str'>                                                      
--------------------
<class 'int'>
<class 'int'>                                
--------------------
<class 'list'>
<class 'list'>

```

#### Create a new class 

1. create an employe class with method that calculates the salary
	1. Name convention : First letter of the class is always uppercase 
	2. first param of each object method is a reference to the object its self
	3. always object method's first argument is : `self`
	
```python 
class Employee:

	def calc_salary(self, hours, rate)-> str:
		print(f"salary = {hours * rate:,}$")

	def print_info(self, name, age, job_title)-> str:
		print(f"Name : {name}\nAge : {age}\nJob : {job_title}")


emp = Employee()
emp.calc_salary(12, 14.12)
emp.print_info("soukaina", 24, "Topography")

```

##### Initialisor Or Constructor in python & object attributes

`__init__` -> special method = magic method = dunder (double underscore) method 
each object has : 
-> attributes 
-> methods

#### Edit an object attribute 

```python 
class Emp:
	def _init_(self, name):
		self.name = name

new_emp = Emp("Ahmed")
--- Edit name ---
new_emp.name = "Yassin"
--- Add new attr after initialisaion ---
new_emp.departement = "Sales"
```

#### str dunder method 

1. this method help us to control the output of priniting an object instance

```python 
def _str_(self):
	return f"Name : ${self.name}"
```

```python 
class Employee:
	def __init__(self, name, age, job):
		self.name = name
		self.age  = age
		self.job  = job

	def __str__(self):
		return f"Name: {self.name}\nAge : {self.age}\nJob : {self.job}"

emp_1 = Employee("Ahmed Ali", 23, "Software tester")
print(emp_1)
```

###### Exemple 1 : Class Item 

```python
from rich import print

class Item:
	def __init__(self, name: str, price: float, quantity: int)-> None:
		self.name = name
		self.price = price
		self.quantity = quantity

	def display(self):
		total_price: float = self.price * self.quantity
		print(f"Name : [yellow]{self.name}")
		print(f"Price : [cyan]{self.price}$")
		print(f"quantity : [yellow]{self.quantity}")
		print(f"Total price : [cyan]{self.price}$")


item1 = Item("Atomic Habits", 10, 2)
item2 = Item("Deep work", 20, 1)

item1.display()
print('-'*20)
item2.display()
```

###### Exemple 2 : Class BankAccount 

```python 
class BankAccount:
	def __init__(self, number: str, balance: float)-> None:
		self.number = number
		self.balance = balance

	def display_balance(self)-> float:
		print(f"Account {self.number} balance : {self.balance}")

	def add_money(self, amount)-> None:
		if amount < 0:
			print("Unvalid amount. amount must be positif")
			return
		self.balance += amount
		print(f"Added {amount} into {self.number}")

	def withdraw(self, amount)-> None:
		if amount > self.balance:
			print("Insufficent funds or invalid amount")
			return
		self.balance -= amount
		print(f"withdraw {amount} from {self.number}")	


account1 = BankAccount("5577", 1000)

account1.display_balance()
account1.add_money(500)
account1.display_balance()
account1.add_money(-100)
account1.display_balance()
account1.withdraw(200)
account1.display_balance()
account1.withdraw(1500)
account1.display_balance()
```


### Class attributes & __repr__

1. we can set a default value to an attribute by doing the following 

```python 
def __init__(self, job="uknown"):
	self.job = job
```

2. class attriutes are attributes that could be accessed either from the class it self or the instance of the class, `class attriutes` can be defined as the following

```python
class Emp:
	company: str = "My_Company"
	def __init__(self):
		...
```

- useful case of class attributes 

```python
class Employe:
	company: str = "GMSOFT"
	num_emps: int = 0

	def __init__(self, name, age, job)-> None:
		self.name = name
		self.age  = age
		self.job  = job
		Employe.num_emps += 1
```

3. What is `represent` method or `__repe__` this method is like `__str__` method but used when we want to display a list of our instances | `repr` is for debugging while `str` is for printing
- so what is the difference between `__str__` and `__repr__` ? 
	- `__str__`   --> used to display a friendly message to the user
	- `__repr__` --> mainly used for debugging only for developers not for the user also for replicating the class
- `__repr__` method can replace `__str__` if not defined in the class but not the reverse
- best practice of writing `__repr__` method in your class

```python 
def __repr__(self)-> list[str]:
	return f"Class_name attr1 : {self.value} , attr2 : {self.value}"
---
print(repr(object_instance))
```

- Example

```python
class Employe:
	company: str = "GMSOFT"
	num_emps: int = 0
	all_emps: list = []

	def __init__(self, name, age, job)-> None:
		self.name = name
		self.age  = age
		self.job  = job
		Employe.num_emps += 1
		Employe.all_emps.append(self)

	def __str__(self)-> str:
		return f"Name : {self.name} | Age : {self.age} | Job : {self.job}"

	def __repr__(self)-> list[str]:
		return f"Employe name : {self.name} - age : {self.age} ..."
		
print(Employe.all_emps)

emp1 = Employe("soukaina", 23, "software")
emp2 = Employe("houssam", 22, "developer")

print(Employe.all_emps)
```

###### Application 1 :

```python 
class Item:
	num_of_items: int = 0
	all_items: list = []

	def __init__(self, name: str, price: float, quantity: int)-> None:
		self.name = name
		self.price = price
		self.quantity = quantity
		self.total = price * quantity
		Item.num_of_items += 1
		Item.all_items.append(self)

	def __str__(self)-> str:
		return f"#Result\nName : {self.name}\nPrice : {self.price}$\nQuantity : {self.quantity}\nTotal : {self.total}"

	def __repr__(self)-> list[str]:
		return f"Item('{self.name}', {self.price}, {self.quantity})"



#Create an item
item1 = Item("Atomic Habits", 10, 2)
item2 = Item("Deep Work", 20, 1)
item3 = Item("So Good They Can't Ignore You", 15, 3)
item4 = Item("Digital Minimalism", 12, 2)


# display the number of items 
print(f"Number of items : {Item.num_of_items}")

# Display all items
print(Item.all_items)

# Display each item 
for item in Item.all_items:
	print(item)
	print('-'*20)
```

###### Application 2 :

```python 
from rich import print

class BankAccount:
    bank_name: str = "CIH"
    num_of_accounts: int = 0
    all_accounts: list = []

    def __init__(self, num: str, balance: float)-> None:
        self.num = num
        self.balance = balance
        BankAccount.num_of_accounts += 1
        BankAccount.all_accounts.append(self)

    def __str__(self):
        return f"Account {self.num}\nBalance {self.balance}"

    def __repr__(self):
        return f"BankAccount('{self.num}', {self.balance})"

    def display_balance(self)-> None:
        print(f"Account {self.num} Balance {self.balance}")

    def add_money(self, amount)-> None:
        if amount < 0:
            print("[red]Error : [/red]Unable to add this amount")
            return
        self.balance += amount
        print(f"[green]SUCCESS : [/green]Added {amount} to {self.num}")

    def withdraw(self, amount)-> None:
        if amount < 0 or amount > self.balance:
           print("[red]ERROR : [/red]Unable to add withdraw this amount")
           return
        self.balance -= amount
        print(f"[green]SUCCESS : [/green]withdraw {amount} from {self.num}")



print(BankAccount.bank_name) # Codezilla
account1 = BankAccount("5577", 1000)
account2 = BankAccount("1234", 2000)
print(BankAccount.num_of_accounts)
# 2
print(BankAccount.all_accounts)
# [BankAccount('5577', 1000), BankAccount('1234', 2000)]
account1.display_balance()
# Account 5577 balance: 1000
account2.display_balance()
# Account 1234 balance: 2000
account1.add_money(500) # added 500 into account 5577.
account1.display_balance() # Account 5577 balance: 1500
account2.withdraw(1000) # Withdrew 1000 from account 1234.
account2.display_balance() # Account 1234 balance: 1000
account1.withdraw(2000) # Insufficient funds or invalid
account1.withdraw(-1000) # Insufficient funds or invalid amount
print(account1)
print(account2)

```


## Encapsulation 

1. incapsulation is used for privacy perpaces it's simply a practice of preveting user from changing or editing our instance
2. to make an attribute private we simply add `__` 2 underscores in the beginning of our attr 
- `private` --> ___ --> two underscores
- `protected` --> __ --> one underscore --> could be accessed within subclasses

```python 
def __init__(self, id):
	self.__id = id
```
3. we use `getters` and `setters` to access these private attr
```python 
def get_id(self)-> str:
	print(f"Name {self.__id}")
```
4. There is a way to bypass this by dowing the folowing this is called `name manglling` in python
```python 
print(instance._ClassName__PrivateAttr)
--- Exemple ---
print(emp._Employee__phone)
```


## Class Methods

1. class method can be defined by adding `@classmethod` decorator as well as `cls` reference to the class

```python 
class Emp:
	@classmethod
	def class_method(cls, params):
		...
```

2. we can use the class reference to create instance which a good practice if we want to edit the class name later 

```python 
@classmethod 
def reder(cls, path):
	cls(one, two, three)
--- Exemple ----
@classmethod
    def read_csv(cls, path):
        with open(path) as file:
            csv_reader = csv.DictReader(file)
            for row in csv_reader:
                name: str = row["name"]
                age : str = row["age"]
                job: str = row["job_title"]
                id: str = row["id"]
                phone: str = row["phone"]
                bank: str = row["bank_account"]
                # create instances -> cls references to the class
                cls(name, age, job, id, phone, bank)
```

## Static methods 

- can't affect instance attributes or class attributes, called `utility functions` as well which means it doesn't perform any actions towards object attr or class attr
- to define a static method we write a decorator before the method : `@staticmethod`
- can be accessed only from the class like a class method or static attr 

```python 
@staticmethod 
def main()-> None:
	do_something()
	...
--- Call ---
Class.main()
```

- Exemple :

```python 
@staticmethod
def isValid_phone(phone: str)-> bool:
    return phone.startswith("+20") and len(phone) == 12

def get_phone(self)-> str:
    return self.__phone

def set_phone(self, phone: str)-> None:
    if not Employee.isValid_phone(phone):
        print("Unvalid format")
        return
    self.__phone = phone
```

## Property, setters and pravate method

1. the `@proprety` is used when we want to define a instance getter, this decorator make it possible for us to invoke a method without brackets

```python 
@proprety
def phone(self)-> str:
	return self.__phone
```
2. Now it's time to define the setter of this attribute for this reason we use the property name followed by `period` and the `setter` decorator like the following :

```python 
@phone.setter
def set_phone(self, phone: str)-> None:
	self.__phone = phone

--- In order to call it ---
emp1 = Employee(...)
emp1.set_phone = "..."
```
##### Private method 

1. to define a private method we only add `__` double underscore 

```python
def __calc_month_deduction(self):
	do_something()
```

## More dunder methods

1. `__eq__` what happends when i compare two instance of the class

```python
def __eq__(self, other)-> bool:
	return self.net_salary() == other.net_salary()
```

2. we can also specify the criteria for other comparissons like : 
	1. `__lt__` --> less than
	2. `__gt__` --> grater than
	3. `__eq__` --> is equal
	4. `__le__` --> less than or equal
	5. `__ge__` --> grater than or equal
3. mathematical operators 
	1. `__add__` --> addition
	2. `__sub__` --> subtraction
	3. `__mul__` --> multiplication
	4. `__div__` --> division
4. length of an instance 
	1. `__len__` --> length 
5. destructor of our instance 
	1. `__del__` --> instance destructor

## Differences Between `__new__` and `__init__`

- `__new__` is a static method, while `__init__` is an instance method.
- `__new__` is responsible for creating and returning a new instance, while `__init__` is responsible for initializing the attributes of the newly created object.
- `__new__` is called before `__init__`.
- `__new__` happens first, then `__init__`.
- `__new__` can return any object, while `__init__` must return `None`.


# Seperation of concernes

1. this concept is about breaking your main class into subclasses that will make the code shorter and more readable 

```python 
import csv

from Lessons.script import read_csv

class Employee:
    PHONE_PREFIX = "+21"
    PHONE_LENGTH = 12
    num_emps: int = 0

    def __init__(self, name: str, age: str, job_title: str, id: str, phone: str, bank_account: str)-> None:
        self.name = name
        self.age  = age
        self.job = job_title
        self.__id   = id
        self.__phone = phone
        self.__bank_account = bank_account
        Employee.num_emps += 0
        AllEmps.add_emps(self)


    def __str__(self)-> str:
        info: str = f"Id : {self.__id}\nName : {self.name}\nAge: {self.age}\nJob: {self.job}\nPhone : {self.__phone}"
        return info

    def __repr__(self)-> str:
        return f"Emplye({self.__id}, {self.name}, {self.age}, {self.job}, {self.__phone})"

    @staticmethod
    def isValid_phone(phone: str)-> bool:
        return phone.startswith(Employee.PHONE_PREFIX) and len(phone) == Employee.PHONE_LENGTH

    @property
    def phone(self)-> str:
        return self.__phone
    @phone.setter
    def phone(self, phone: str)-> None:
        if not Employee.isValid_phone(phone):
            print("Unvalid format")
            return
        self.__phone = phone

    @property
    def id(self)-> str:
        return self.__id

    @id.setter
    def id(self, id: str):
        if isinstance(id, str) and id.isdigit and not id.strip() == '':
            self.__id = str(id)
            return
        raise ValueError("Non empty string + composed only digits")

class Finance:

    TAX_THRESHHOLD = 30_000
    TAX_LOW = 0.1
    TAX_HIGH = 0.3
    INSURANCE = 100
    RETIREMENT_CONTRIBUTION_RATE = .05

    @staticmethod
    def calc_tax(salary: float)-> float:
        if salary < Finance.TAX_THRESHHOLD:
            return salary * Finance.TAX_LOW
        return salary * Finance.TAX_HIGH

    @staticmethod
    def cal_net_salary(gross_salary: float)-> float:

class AllEmps:
    __all_Emps: list = []

    @classmethod
    def add_emps(cls, emp)-> None:
        cls.__all_Emps.append(emp)

    @classmethod
    def list_all_emps(cls)-> list:
        return cls.__all_Emps

    @classmethod
    def find_by_id(cls, id: str)-> str:
        emp: list = [  if emp.id == id emp else "Employe not found" emp for emp in cls.__all_Emps ]
        return emp[0]

    @classmethod
    def del_by_id(cls, id: str)-> None:
        cls.__all_Emps = [emp for emp in cls.__all_Emps if emp.id != id]

class EmpFileHandler:

    @staticmethod
    def read_csv(path):
        All_emps: list = []
        with open(path) as file:
            csv_reader = csv.DictReader(file)
            for row in csv_reader:
                name: str = row["name"]
                age : str = row["age"]
                job: str = row["job_title"]
                id: str = row["id"]
                phone: str = row["phone"]
                bank: str = row["bank_account"]
                # create instances -> cls references to the class
                Emp = Employee(name, age, job, id, phone, bank)
                All_emps.append(Emp)
        return All_emps


    @staticmethod
    def read_add_toemps(filename):
        emp_list: list = read_csv(filename)
        for emp in emp_list:
            AllEmps.add_emps(emp)

```


## Flags

1. we add attributes with default values to prevent certain bugs like the following : if we didn't add `from_file = false` attr all the instance will be added two times if we create them from a csv file 

```python
def __init__(self, name: str, age: int, job: str, id: str, email: str, phone: str, bank_acc: str, hours: int = 160, rate: float = 1, from_file: bool=False)-> None: 
        self.name = name
        self.age  = age
        self.job  = job 
        self.hours = hours
        self.rate = rate
        self.__id = id
        self.__email = email
        self.__phone = phone 
        self.__bank_acc = bank_acc
        Employe.__num_emps += 1
        if not from_file:
            AllEmployees.employees.append(self)
```


## Inheritance & polymorphism 

1. inheritance : 

```python
class Employe:
	...

class Manager:
	def __init__(self, *args, **kwargs)-> None:
		super().__init__(*args, **kwargs)
```


2. `polymorphism` --> has many shapes
	1. it's the action of redefining an existing method to do an action in a different way -> it's also called `method overiding` 


## Abstract class & interface & more polymorphisme

- python doesn't implement `interfaces` unlike [ java or c# ] that's why we use abstract classes to illustrate interfaces concept in python

-> Abstract class = Base class = Blue print
-> this abstract class plays the role of a blue print for other class, in other term this class defines how the other classes should be built
-> in a simple way abstract class is like a hidden contract between the `absract class` and these instance which obligates these instances to have the same form of the base class in addition to there own form or `methods`
##### How to define an abstract class 

`ABC = abstract base class`

```python 
from abc import ABC, abstractclass

class Shape:

	@abstractclass
	def area(self)-> None:
		pass | ...

class Circle(Shape):
	PI = 3.14
	def __init__(self, radius)-> None:
		self.radius = radius

	def area(self)-> float:
		return PI * self,radius ** 2

class Rectangle(Shape):

	def __init__(self, width, height)-> None: 
		self,width = width
		self.height = height

	def area(self)-> float:
		return self.width * self.height
```

##### What is Runtime polymorphisme ? 

1. print the class name : `__class__.__name__`

```python
name: str = shape.__class__.__name__

def print_area(shape)-> str:
	print(f"The area of {shape.__class__.__name__} is : {shape.area()})
```

##### Example 

```python
from abc import ABC, abstractmethod

class BankAccount:
    def __init__(self):
        self.balance = 0

    def deposit(self, amount):
        return self.balance += amount

    def withdraw(self, amount):
        if amount > self.balance:
            raise("Insufficient funds")
        return self.balance -= amount

    @abstractmethod
    def calc_intrest(self)-> None:
        pass

class SavingAccount(BankAccount):
    INTREST_RATE: float = .84

    def calc_intrest(self) -> float:
        return self.balance * SavingAccount.INTREST_RATE
    
class CheckingAccount(BankAccount):
    INTREST_RATE: float = .01

    def calc_intrest(self) -> flaoat:
        return self.balance * CheckingAccount.INTREST_RATE

```


- In general we use `abstract classes` when we 
-> java : doesn't support multiple inheritance
-> python : support multiple inheritance but it's more ... to use composition in stead of mul inheriitance

##### Multiple inheritance example :

```python
class Bird:
	def fly(self):
		pass

class Fish:
	def swim()
		pass

class FlyingSwimingCreature(Bird, Fly):
	pass

creature1 = Flying...()
creature1.swim()
creature1.fly()
```



## Data class

1. this concept is used only in python which is a new type of classes
2. Designed to mostly hold data values, usually doesn't contain methods 
3. this type of classes comes with constructor method already implemedted

```python 
from dataclasses import dataclass

@dataclass 
class Person:
	name: str = 'name1' -> default value
	age: int = '...'
	height: float = '...'
	email: str = '...'

pre_1 = Person()
print(per_1.name)

```

1. `order` -> sorting instance based on a criteria
2. `__post_init__()` -> this method is were we put the condition of our criteria
3. `frozen` -> capable to change the attr value or not false -> capable | true -> uncapable

```python
```