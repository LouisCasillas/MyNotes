# Python Snippets

- Clear the screen on terminal
# install replit: $ pip3 install replit
from replit import clear
clear()

- Select random element of array
import random
x = []
random.choice(x)

- Get array indexes for some matching logic
x = []
[ i for i, letter in enumerate(x) if letter == 'l' ]

- Shuffle array
import random
x = []
random.shuffle(x)

- To import a module from another folder, you have to append the folder path to sys.path:
import sys
sys.path.append('path/to/module-folder/')
import my-module

- Using command-line arguments
import sys
print("Number of arguments: ", len(sys.argv))
print("Argument List: ", sys.argv)
print("Program name: ", sys.argv[0])    

- Merge dictionaries
dict1 = { 'id': 777, 'note': 'Good' }
dict2 = { 'id': 999, 'color': 'Red' }
dict3 = { 'id': 888, 'msg': 'Moo' }

# Note: common keys are overridden by the right-most dictionary 
all_dict = {**dict1, **dict2, **dict3}
print(all_dict)
out: {'id': 888, 'note': 'Good', 'color': 'Red', 'msg': 'Moo'} 

- Force keyword arguments to functions
def myfunction(*, user, birthday):
	pass

myfunction(user='Tedd', birthday='01/01/1980')

- Recursively yield using recursion
def myfunction(x=10):

	if x > 0:
		yield x
		yield from myfunction(x - 1)

print([i for i in myfunction(5)])

- Count length of iterators or generators
# _ tells python I don't care about the actual element value
number_of_elements = sum(1 for _ in mygenerator)

- Slice strings or arrays
x = "hello world"
# skip 5 characters and then print the rest of the string
print(x[5:])
# print the first 5 characters of the string
print(x[:5])
# print every 2nd character
print(x[::2])
# print the string reversed
print(x[::-1])

- dissaessemble python code
import dis

print(dis.dis(myfunction))
print(dis.dis("{}"))
print(dis.dis("int(5)")

- look into function
>>> def myfunction(hello='hello'):
>>>    print( f"'How are you?' {hello}" )

# Print all literal constants such as string literals or inner function names and pointers
# used by LOAD_CONST
>>> myfunction.__code__.co_consts
(None, "'How are you?' ")

# print any local names
# used by LOAD_FAST
>>> myfunction.__code__.co_varnames
('hello',)

# print any non-local names
# used by LOAD_GLOBAL
>>> myfunction.__code__.co_names
('print',)
    
- get python code (does not work in the interactive interpreter)
import inspect
def myfunction():
	print('moo')
	
print(inspect.getsource(myfunction))

- find how much memory something is taking
from sys import getsizeof
x = [1, 2, 3, 4, 5]
print(getsizeof(x))

- check if something is iterable
hasattr(x, '__iter__')

- slice generator in a memory efficient way
import itertools

# get the first 5 elements from the generator
x = itertools.islice(get_generator(), 5)
print( list(x) )

- save memory by telling python the object fields will not be changing so don't make copies of the fields
# defining __slots__ restricts values allowed in type but removes per instance dictionary storage, reducing memory and increasing access speed
class myClass:
	__slots__ = [ 'a', 'b', 'c', 'd' ]
	def __init__(self, a, b, c, d):
		self.a = a
		self.b = b
		self.c = c
		self.d = d

class myChildClass(myClass):
    # you don't re-add the same slots as the parent as the slots are inherited
	__slot__ = 'foo'

>>> x = myClass(4, 999, 222, 777)
>>> x.__getattribute__('__dict__')
Traceback (most recent call last):
     File "<stdin>", line 1, in <module>
AttributeError: 'myClass' object has no attribute '__dict__'
>>> x.__getattribute__('__slots__')
['a', 'b', 'c', 'd', 'e'] 

- create an abstract class
from abc import ABC, abstractmethod

class OurAbstractClass(ABC):
	@abstractmethod
	def dosomething(self, foo, bar):
		pass

- create a normal class that descends from an abstract class
class CoolClass(OurAbstractClass):
	def __init__(self, message)
	
	def speak(self):
		print( f"Hello! {self.message}" )
        
 - check if file exists
 from os import path
 
 path.exists('file.txt')
 
- timing code execution
    - timeit is more accurate by time is easier to use
 ===
# program to compute the time of
# execution of any python code using timit
 
# importing the required module
import timeit
 
# code snippet to be executed only once
mysetup = "from math import sqrt"
 
# code snippet whose execution time
# is to be measured
mycode = '''
def example():
    mylist = []
    for x in range(100):
        mylist.append(sqrt(x))
'''
 
# timeit statement
print ("The time of execution of above program is :",
       round(timeit.timeit(setup = mysetup,
                    stmt = mycode,
                    number = 10000), 2))
===

===
import time

start = time.time()

do_something()

end = time.time()

print( f"Time taken: {round(end - start}, 2)")
===

===
for datetime import datetime

start = datetime.now()

do_something()

end = datetime.now()

print( f"Time taken: {round(end - start, 2)}")
===

- profile code using cProfile
import cProfile
cProfile.run("[(a, b) for a in (1, 3, 5) for b in (2, 4, 6)]")

- find the most frequent element
def most_frequent(list):
    # how this works:
    # 1) take the unique elements of the list array
    # 2) for each unique element call the count function on the original array to get how many times that element is in the original array
    # 3) compare the count of unique elements for the max function
    return max(set(list), key=list.count)
    
mylist = [1, 1, 2, 3, 4, 2, 2]
print(most_frequent(mylist))

- compare mixed int and string elements as ints
list = ['1', '100', '2', 5.6]
max(list, key = lambda i: int(i))

- convert two lists into a dictionary or tuples
def list_to_dictionary(keys, values):
    return dict(zip(keys, values))
    
 def list_to_tuples(first, second):
    return list(zip(first, second))
    
 print(list_to_dictionary(['happy', 'zebra', 'monkey'], ['moo', 'giraffe', 555]))
 # {'happy': 'moo', 'zebra': 'giraffe', 'monkey': 555}
 
- error handling

try:
    5/0
except ZeroDivisionError:
    print('Cannot divide by zero')
except Exception as error:
    print('Something weird happened...')
finally:
    print('Thank you for playing!')
    
- quick array testing
list = [ 2, 99, 23 ]

# all elements are true
all(list)
>>> True

# at least one element is true
any(list)
>>> True

- create a 2D array
[ [1] * 3 for i in range(3) ]
>>> [[1, 1, 1], [1, 1, 1], [1, 1, 1]]

- Simple progress bar

def progress_bar(*, width = 80, percent = 0):
    percent = max(0, min(100, int(percent)))
    num_of_hashes = int(width * (percent/100.0))
    
    return f"{'|' * num_of_hashes}{'-' * (width - num_of_hashes)}" 

>>> progress_bar(width=50, percent=10)                                                                                                                  '|||||---------------------------------------------'

- Deep flatten list
def deep_flatten(deep_list):
        flattened_list = []

        while deep_list:
                element = deep_list.pop()

                if type(element) == list:
                        deep_list.extend(element)
                else:
                        flattened_list.insert(0, element)

        return flattened_list

x = [888, ['a', 'b'], ['c'], ['d', 'e', 'f'], [ 'g', 'h', [ 'i', 'j', 'k' ] ]]
print(deep_flatten(x))

- Object oriented inheritance example
class GrandFather:
    def __init__(self): 
        print('GrandFather born')

    def calculate_age(self, age):
        print('Age of GrandFather', age)

class Father(GrandFather):
    def __init__(self):
        super().__init__()
        print('Father born')

    def calculate_age(self, age):
        super().calculate_age(age + 25)
        print('Age of Father', age)

class Child(Father):
    def __init__(self):
        super().__init__()
        print('Child born')

    def calculate_age(self, age):
        super().calculate_age(age + 25)
        print('Age of Child:', age)
        
c = Child()
c.calculate_age(18)

- Object oriented inheritance example
class Animal: 
    def __init__(self, name):
        print(name, 'is an animal.')
        
class CannotFly(Animal):
    def __init__(self,name):
        print(name, "cannot fly.")
        super().__init__(name)

class Cat(CannotFly,Animal):
    def __init__(self):
        print('I am a cat.');
        super().__init__('Cat')

cat = Cat()

- Deep copy list
import copy
x = [4, 5, [1, 2, 3]]
y = copy.deepcopy(x)

- list values to keys of dictionary
x = [1, 2, 3, 4]
dict.fromkeys(x, 5)
# {1: 5, 2: 5, 3: 5, 4: 5}

- remove duplicates from list
x = [1, 2, 2, 3]
x = list(set(x))
# [1, 2, 3]

- Get numbers from string
x = "test 5953 hello 011"
[int(i) for i in x.split() if i.isdigit()] 
# [5953, 11]

- Add two arrays together
x = [1,2,3]
y = [7,8,9]
def add_fun(a,b):
    return a + b
list(map(add_fun, x, y))
[8, 10, 12]

- Loop through two arrays together
# if the lists don't have the same number of elements the extra elements are dropped
for a, b in zip(x,y):
    print(f"{a}---{b}")
# 1---7
# 2---8
# 3---9

- invert a dictionary that doesn't have lists for values
mydict = { 'a': 555, 'b': 666, 'c': 777, 'd': 666 }
inverted_dict = dict()

for key, value in mydict.items():
	try:
		if not type(inverted_dict[ value ]) == list:
			inverted_dict[ value ] = list(inverted_dict[ value ])
		
		inverted_dict[ value ].append( key )
			
	except KeyError:
		inverted_dict[ value ] = key

- Find if a substring exists in a string
x = 'monkey'
if 'monk' in x:
    print('monk was found')

- Read a CSV file
csv_mapping_list = []
with open("/path/to/data.csv") as my_data:
    line_count = 0
    for line in my_data:
        row_list = [val.strip() for val in line.split(",")]
        if line_count == 0:
            header = row_list
        else:
            row_dict = {}
            for i, key in enumerate(header):
                row_dict[key] = row_list[i]
            csv_mapping_list.append(row_dict)
        line_count += 1

- compare strings
if str1.lower() == str2.lower():
    echo 'moo'
# for the most generic including international characters use casefold
if str.casefold() == str2.casefold():
    echo 'moo'

- sort lists
x = ['zebra', 'happy', 'every', 'Gun', 'Apple']
# sorts alphabetically and case-sensitive
x.sort()
print(x)
# ['Apple', 'Gun', 'every', 'happy', 'zebra']

# sorts alphabetically and case-insensitive
x.sort(key=str.casefold)
print(x)
# ['Apple', 'every', 'Gun', 'happy', 'zebra']

# reverse sorts alphabetically and case-insensitive
x.sort(key=str.casefold, reverse=True)
print(x)
# ['zebra', 'happy', 'Gun', 'every', 'Apple']

# custom list sort using current locale
import locale
from functools import cmp_to_key
my_list = sorted(my_list, key=cmp_to_key(locale.strcoll))

- ascii to digit conversion and vice-versa
# int to str
ord('a') # -> 97
chr(97) # -> 'a'

- Printing an object
# the method __repr__ will be called when the object is being printed if __str__ is not defined
# __repr__ is used to print a representation of an object, usually it should be able to be passed to eval() and be rebuilt to equal itself, eval(repr(x)) == x => True
# __str__ is for humans to easily read

class MyClass:
    def __init__(self):
        pass
    def __repr__(self):
        return "Thank you for investigating me!"
 >>> y = MyClass()
 >>> print(y)
 Thank you for investigating me!
 >>> repr(y)
 Thank you for investigating me!

- Modifying a global variable
x = 1
def modify_me():
    global x
    x += 1
print(x)
modify_me()
print(x)

- Use constants
# use all uppercase variable, constants are just normal variables and can be changed
PI = 3.1415926

- Force the input of all function parameters as named variables
def give_me_all(*, x, y):
    print(x, y)
    
give_me_all(x='xxx', y='yyy')