Double underscore is called a dunder.

Write with underscores, not camelCase.

You can put underscores in your numbers just for readability.
```
>> 1_000_000_000
1000000000
```

---

#### Strings
```python
astring = "Hello world!"
print(astring)
print('wazzup')
print("double quotes work too")
print("single quotes within double show ' ', and vice versa")
print('but you have to do this: \' for a single quote to work within another single quote')
print(len(astring))
```
```
Hello World!
wazzup
double quotes work too
single quotes within double show ' ', and vice versa
but you have to do this: ' for a single quote to work within another single quote
12
```
***
#### Here are some basic argument specifiers you should know:
`%s` - String (or any object with a string representation, like numbers)

`%d` - Integers

`%f` - Floating point numbers

`%.<number of digits>f` - Floating point numbers with a fixed amount of digits to the right of the dot.

`%x/%X` - Integers in hex representation (lowercase/uppercase)

Example
```python
name = "Ryan"
age = 22
print("%s is %d years old." % (name, age))
```
```
Ryan is 22 years old.
```
***
#### Printing Conditions
```python
x = 2
print("x == 2 :",x == 2) # prints out True
print("x == 3 :",x == 3) # prints out False
print("x == 4 :",x == 4) # prints out True
```
```
x == 2 : True
x == 3 : False
x == 4 : False
```
***
#### If Statements 
**and** / **or**
```python
name = "Ryan"
age = 21
if name == "Ryan" and age < 22 or age > 22:
    print("Your name is Ryan, but you aren't 22. You're %d." % age)
```
```
Your name is Ryan, but you aren't 22. You're 21.
```
**in**
```python
name = "Luke"
brothers = ["Ryan","Luke","Matthew"]
if name in brothers:
    print("You are a Johnson boy.")
    print("Your name is %s." %name)
```
```
You are a Johnson boy.
Your name is Luke.
```
Python uses indentation to define code blocks, instead of brackets. The standard Python indentation is 4 spaces, although tabs and any other space size will work, as long as it is consistent. Notice that code blocks do not need any termination.

Here is an example for using Python's "if" statement using code blocks and using **is**:
```python
statement = False
another_statement = False
if statement is True:
    print(1)
elif another_statement is True: # else if
    print(2)
else:
    print(3)
```
```
3
```
***
#### For
```python
primes = [2, 3, 5, 7]
for prime in primes:
    print(prime)
```
```
2
3
5
7
```
#### While
```python
count = 0
while count < 5:
    print(count)
    count += 1
```
```
0
1
2
3
4
```
**break** / **continue**

break is used to exit a for loop or a while loop, whereas continue is used to skip the current block, and return to the "for" or "while" statement.

**else**

unlike languages like C, C++, and Java, we can use else for loops. When the loop condition of "for" or "while" statement fails then code part in "else" is executed. If break statement is executed inside for loop then the "else" part is skipped.
***
#### Functions
```python
def my_function():
    print("Hello From My Function!")

def my_function_with_args(username, greeting):
    print("Hello, %s, From My Function, I wish you %s"%(username, greeting))

def sum_two_numbers(a, b):
    return a + b

my_function()

my_function_with_args("Ryan", "a merry Christmas!")

x = sum_two_numbers(1,2)
print(x)
```
```
Hello From My Function!
Hello, Ryan, From My Function, I wish you a merry Christmas!
3
```
***
### Classes
```python
class Vehicle:
    name = ""
    kind = "car"
    color = ""
    value = 100.00
    def description(self):
        desc_str = "%s is a %s %s worth $%.2f." % (self.name, self.color, self.kind, self.value)
        return desc_str
    
car1 = Vehicle()
car2 = Vehicle()
car1.name = "Fer"
car1.kind = "convertible"
car1.color = "red"
car1.value = 60000.00
car2.name = "Jump"
car2.color = "blue"
car2.kind = "van"
car2.value = 10000.00

print(car1.description())
print(car2.description())
```
```
Fer is a red convertible worth $60000.00.
Jump is a blue van worth $10000.00.
```
***
### Self
self represents the instance of the class. By using the “self” keyword we can access the attributes and methods of the class in python. It binds the attributes with the given arguments.

The reason you need to use self. is because Python does not use the @ syntax to refer to instance attributes. Python decided to do methods in a way that makes the instance to which the method belongs be passed automatically, but not received automatically: the first parameter of methods is the instance the method is called on

Essentially, self should be in every method definition within a class. 

Self is a convention and not a real python keyword
self is a parameter in the function and the user can use another parameter name in place of it, but it is advisable to use self because it increase the readability of code.
***
### Dictionaries
```python
phonebook = {
   "John" : 938477566,
   "Jack" : 938377264,
   "Jill" : 947662781
}
phonebook["Ryan"] = 665774839
print(phonebook)
phonebook.pop("John")
for name, number in phonebook.items():
    print("The phone number of %s is %d" % (name, number))
```
```
{'John': 938477566, 'Ryan': 665774839, 'Jack': 938377264, 'Jill': 947662781}
The phone number of Ryan is 665774839
The phone number of Jack is 938377264
The phone number of Jill is 947662781
```
***
### Numpy Arrays

used to perform computations on each element of an array
```python
weight_kg = [81.65, 97.52, 95.25, 92.98, 86.18, 88.45]
import numpy as np
np_weight_kg = np.array(weight_kg)
np_weight_lbs = np_weight_kg * 2.2
print(np_weight_lbs)
```
```
[ 179.63   214.544  209.55   204.556  189.596  194.59 ]
```
***
### Generators (yield)
```python
import random

def lottery():
    for i in range(3):
        yield random.randint(1, 151)
    for i in range(2):
        yield random.randint(152, 251)
    yield random.randint(252, 386)

for random_number in lottery():
    print("And the next party member is number... %d!" %(random_number))
```
```
And the next party member is number... 45!
And the next party member is number... 107!
And the next party member is number... 84!
And the next party member is number... 238!
And the next party member is number... 249!
And the next party member is number... 363!
```
```python
def fib():
    x, y = 1, 1
    yield x
    yield y
    while True:
        x = x + y
        yield x
        y = x + y
        yield y

import types
if type(fib()) == types.GeneratorType:
    print("Good, The fib function is a generator.")
    counter = 0
    for n in fib():
        print(n)
        counter += 1
        if counter == 10:
            break
```
```
Good, The fib function is a generator.
1
1
2
3
5
8
13
21
34
55
```
***
### List Comprehension
```python
sentence = "the quick brown fox jumps over the lazy dog"
words = sentence.split()
word_lengths = [len(word) for word in words if word != "the"]
print(words)
print(word_lengths)
```
```
['the', 'quick', 'brown', 'fox', 'jumps', 'over', 'the', 'lazy', 'dog']
[5, 5, 3, 5, 4, 4, 3]
```
```python
numbers = [34.6, -203.4, 44.9, 68.3, -12.2, 44.6, 12.7]
newlist = [int(x) for x in numbers if x > 0]
print(newlist)
```
```
[34, 44, 68, 44, 12]
```
***
### Functions with a variable number of arguments
```python
def foo(a, b, c, *extra):
    return len(extra)

def bar(a, b, c, **extra):
    if extra.get("magicnumber") == 7:
        return True
    else:
        return False

if foo(1,2,3,4) == 1:
    print("Good.")
if foo(1,2,3,4,5) == 2:
    print("Better.")
if bar(1,2,3,magicnumber = 6) == False:
    print("Great.")
if bar(1,2,3,magicnumber = 7) == True:
    print("Awesome!")
```
```
Good.
Better.
Great.
Awesome!
```
***
### Sets
```python
a = set(["Jake", "John", "Eric"])
b = set(["John", "Jill"])
print(a.difference(b)) # a - b
print(a.union(b)) # a + b
print(a.intersection(b)) # a & b
print(a.symmetric_difference(b)) # a | b
```
```
{'Eric', 'Jake'}
{'John', 'Eric', 'Jill', 'Jake'}
{'John'}
{'Eric', 'Jill', 'Jake'}
```
***
### Logging

You have to `import logging` before you can use this, but it is just super handy. Throughout your code, you can print messages of different levels, namely DEBUG, INFO, WARNING, ERROR, and CRITICAL. Then, just by specifying which level you want at the beginning of your run you can get the appropriate printed responses to your program.
```
import logging
logging.basicConfig(format='%(levelname)s:%(message)s', level=logging.DEBUG)
logging.debug('This message should appear on the console')
logging.info('So should this')
logging.warning('And this, too')
```
When `level=logging.WARNING`, then WARNING, ERROR, and CRITICAL logs will be printed, but during a `level=logging.DEBUG` run, then all logs will be printed. 

This can be nice to implement alongside a `--verbose` functionality.

***

### Argparse
When you use argparse, you can set arguments that can be specified by the user, and then parse them into variables. It's pretty handy. I'll just put here an example from `fpga-tool-perf`. 
```
def main():
    import argparse

    parser = argparse.ArgumentParser(
        description=
        'Analyze FPGA tool performance (MHz, resources, runtime, etc)'
    )

    parser.add_argument('--verbose', action='store_true', help='')
    parser.add_argument('--overwrite', action='store_true', help='')
    parser.add_argument('--board', default=None, help='Target board')
    parser.add_argument(
        '--params_file', default=None, help='Use custom tool parameters'
    )
    parser.add_argument(
        '--params_string', default=None, help='Use custom tool parameters'
    )
    parser.add_argument(
        '--strategy', default=None, help='Optimization strategy'
    )
    add_bool_arg(
        parser,
        '--carry',
        default=None,
        help='Force carry / no carry (default: use tool default)'
    )
    parser.add_argument(
        '--toolchain', help='Tools to use', choices=get_toolchains()
    )
    parser.add_argument('--list-toolchains', action='store_true', help='')
    parser.add_argument(
        '--project', help='Source code to run on', choices=get_projects()
    )
    parser.add_argument('--list-projects', action='store_true', help='')
    parser.add_argument(
        '--seed',
        default=None,
        help='31 bit seed number to use, possibly directly mapped to PnR tool'
    )
    parser.add_argument('--list-seedable', action='store_true', help='')
    parser.add_argument(
        '--check-env',
        action='store_true',
        help='Check if environment is present'
    )
    parser.add_argument('--out-dir', default=None, help='Output directory')
    parser.add_argument(
        '--out-prefix',
        default=None,
        help='Auto named directory prefix (default: build)'
    )
    parser.add_argument('--build', default=None, help='Build number')
    parser.add_argument('--build_type', default=None, help='Build type')
    args = parser.parse_args()
    if args.verbose:
        logging.basicConfig(format='%(message)s', level=logging.DEBUG)
```
There is also automatically a -h (help) option that prints all of the argument options and descriptions for the user.

***

### With
```
def run(self):
    with Timed(self, 'total'):
        ...
```
`with` has a very useful little function. Whatever class you assign to it (Timed in the above example) has an `__enter__` function and an `__exit__` function, that are executed when the with block starts and ends (see the example below). Pretty handy, especially in the example from `fpga-tool-perf`, where it saves the time when a certain named process starts and then when it ends, it subtracts that from the current time to give you the runtime of that section of code and save it. Super cool! 
```
class Timed:
    def __init__(self, t, name):
        self.t = t
        self.name = name
        self.start = None

    def __enter__(self):
        self.start = time.time()

    def __exit__(self, type, value, traceback):
        end = time.time()
        self.t.add_runtime(self.name, end - self.start)
```
P.S. Every class has an `__init__` function.

Also you could have the `__enter__` function give a return value and add `as <variable_name>` to the end of your with statement.
```
with Timed(self, 'total') as start:
    ...
```
```
def __enter__(self):
    self.start = time.time()
    return self.start
```

Here is an online explanation that may help explain more:
>A high-level explanation of the context management protocol is:
>- The expression is evaluated and should result in an object called a "context manager". The context manager must have `__enter__()` and `__exit__()` methods.
>- The context manager's `__enter__()` method is called. The value returned is assigned to VAR. If no 'as VAR' clause is present, the value is simply discarded.
>- The code in BLOCK is executed.
>- If BLOCK raises an exception, the `__exit__(type, value, traceback)` is called with the exception details, the same values returned by sys.exc_info(). The method's return value controls whether the exception is re-raised: any false value re-raises the exception, and True will result in suppressing it. You'll only rarely want to suppress the exception, because if you do the author of the code containing the 'with' statement will never realize anything went wrong.
>- If BLOCK didn't raise an exception, the `__exit__()` method is still called, but type, value, and traceback are all None.

***

### Inheritance

Any class can be a parent class, and the syntax is the same. Then to make a child class, make a class and include the parent class in parentheses:
```
class Student(Person):
  def __init__(self, fname, lname, year):
    super().__init__(fname, lname)
    self.graduationyear = year
```
In the above example, `Student` is a child of the parent class `Person`. Below is an example from `fpga-tool-perf`:
```
class VPR(Toolchain):
    '''VPR using Yosys for synthesis'''

    def __init__(self, rootdir):
        Toolchain.__init__(self, rootdir)
        self.toolchain = 'vpr'
        self.files = []
        self.fasm2bels = False
        self.dbroot = None
```
If you add a method in the child class with the same name as a function in the parent class, the inheritance of the parent method will be overridden.

***

### Modules

Importing modules is frequently done and important. Just importing the module name will give you access to the module, but you still need to use the name before acessing any of its functions or variables. 
```
import mod
mod.do_thing()
```
You can import and assign your own name to the module.
```
import mod as m
m.do_thing()
```
You can import any number of functions directly from a given module.
```
from mod import do_thing
do_thing()
```
You can also assign your own name to functions
```
from mod import do_thing as do_this
do_this()
```
To see what is contained in an imported module run dir().
```
import mod
dir(mod)
```

***

### Packages

The `__init__.py` files are required to make Python treat directories containing the file as packages. In the simplest case, __init__.py can just be an empty file, but it can also execute initialization code for the package

***

### Function that returns a Function
```
funct(1)(2)
```
In the above example `funct(1)`, a function with `1` as an argument, **returns** a certain function which is then called with `2` as its argument. So yes, pretty interesting.

---

### Python Unit Tests



----------------------------------
Initially created by Ryan Johnson, July 2020.