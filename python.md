# Interaction with System

## Invoking the Interpreter

On Unix:
usually installed as `/usr/local/bin/python3.11`

put `/usr/local/bin` in your Unix shell to use it

Other locations are possible  

On Windows:
`python3.11` available when installed from Microsoft Store


Typing an end-of-file character (`Control-D` on Unix, `Control-Z` on Windows) at the primary prompt causes the interpreter to exit with a zero exit status.

>the quickest check to see whether command line editing is supported is typing Control-P to the first Python prompt you get. If it beeps, you have command line editing

To invoke python module as scripts

`python -m module [arg] ...`


## Argument Passing
To access arguments:

```py
import sys
arg0 = sys.argv[0]
```

## Intepreter and environment
```py
#!/usr/bin/env python3
# -*- coding: encoding -*-
# specifies the encoding and make the script executable on Unix

```

```shell
$ chmod +x script.py
```

> On Unix the Python 3.x interpreter is by default not installed with the executable named python, so that it does not conflict with a simultaneously installed Python 2.x executable.

> Interactively a compound statement like a whole for loop, must be followed by a indented blank line


# Introduction

## Numbers
operators with mixed type operands convert the integer operand to floating point:

> **In interactive mode, the last printed expression is assigned to the variable `_`. (read_only)**

python support int, float, Fraction(fractions module), Decimal(decimal mod) and complex numbers (`z=3+5j`,`z.real`,`z.imag`)
## Strings
### Raw Strings
To prevent special characters to be interpreted:
```py
str = r'C:\some\name' # raw string
# Note that backslash at the end will escape the quote
str = r'C:\some\name\' 
# Error, quote escaped, instead,
str = 'C:\\some\\name\\' 
```
### Can span multiple lines 
```py
# escape the first end of line and last eol
print("""\
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to\
""")
```
### Auto Concatenation
```py
string1 = "abc" "def"
string2 = "abc" + "def" # equivalent
string3 = string1 "def" # error
```
only use auto-concat with literals not between literals and variables/expressions, use `+` instead

### String slicing
To remember:
```
+---+---+---+---+---+---+
| P | y | t | h | o | n |
+---+---+---+---+---+---+
0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1
```
Note how the start is always included, and the end always excluded. This makes sure that s[:i] + s[i:] is always equal to s:

Attempting to use an index that is too large will result in an error:

However out of range slicing is allowed
```py
>>> word = "python:
>>> word[4:42]
'on'
>>> word[42:]
''
>>> word[-1:-4]
''
>>> word[-4:-1]
'tho'
```

Python strings are **immutable**

## List

python lists are **mutable**  
Like string, support indexing and slicing,
but support mutation through indexing and slicing
```py
list = [1,2,3,4,5]
list[0] = 2 # mutation through indexing
list[2:3] = [1] # mutation through slicing
assert(list == [2,2,1,4,5])
list[:] = [] # empties the list, eqvly del list[:]
```

All slicing returns a new item, so list[:] returns a list of shallow copies of the items, a list of references to the original items

>```python
>print("1 + 1 is", 1+1) # a white space is auto >inserted between items
>```


# Control Flows

Strategies To loop over and modify a collection: it is better to create a copy than messing around the orignal
```py
users = {"John": "active", "Lee": "inactive"}

# loop over a copy
for user, status in users.copy().items():
    if status == "inactive":
        del users[user]

# create a new collection
active_users = {}
for user, status in users.items():
    if status == "active":
        active_users[user] = "active" # !!!
```

## range()
in many ways the object returned by range() is like a list. But it is actually a `iterable` object, a target for functions (`sum()`) or constructs (`for ... in ...`) to ask for successive items until the supply is exhausted. It does not really make the list, thus saving space.

```py
sum(range(4)) == 6
```

## loop keywords
in loops, `else` statement runs when no `break` occurs

## pass Statements

The pass statement is useful when a statement is syntactically required but the program requires no action

```python
while True:
    pass # busy waiting for keyboard interrupt
class myEmptyClass:
    pass # minimal class

def myFunction(*args):
    pass # come back to implement
```

## match statement
pass, new in python3.10

## function definition
symbol table
local -> enclosing local -> global -> built-in

functions without return statement returns None

```py
i = 5

def f(arg=i): 
    # default val is evaluated only once at defining 
    print(arg)

i = 6
f() # prints 5
```
ways to define functions with variable argument number
1. default arguments  
   Common pitfall on mutable default argument
   ```py
   def f(a, L=[]):
       L.append(a)
       return L

   print(f(1))
   print(f(2))
   print(f(3))
   ```
   this block should output:
   ```
   [1]
   [1, 2]
   [1, 2, 3]
   ```
   because the default anonymous list is mutable, created only once at function definition and accumulated across the calls

   Instead, write
   ```
   def f(a, L=None):
    if L is None:
        L = []
    L.append(a)
    return L
   ```

2. keyword arguments  
   > note that positional arguments cannot come after keyword arguments

   optionally can add a last argument  
   `**kwargs` to contain those keyword arguments at last that does not have a corresponding formal parameter, perserves their order  

3. special characters
a way to explicitly define positional/keyword arguments
```py
def f(pos1, pos2, /, pos_or_kwd, *, kwd1, kwd2):
    pass
```
4. positional arguments  
   to add a argument to capture all the positional arguments before the keyword arguments:  
   add `*args` to contain those positional arguments that does not corresponds to a formal parameter, perserves their order

Argument Use case:
- Use positional-only:
  - if you want the name of the parameters to not be available to the user. This is useful when parameter names have no real meaning,
  - if you want to enforce the order of the arguments when the function is called 
  - or if you need to take some positional parameters and arbitrary keywords.
- Use keyword-only 
  - when names have meaning and the function definition is more understandable by being explicit with names 
  - or you want to prevent users relying on the position of the argument being passed.
- For an API, use positional-only to prevent breaking API changes if the parameter’s name is modified in the future.

## Unpacking Argument Lists
unpack list with `*` and dictionaries with `**` to deliver positional and keyword arguments

## Lambda Expressions
definition: syntax suger
```py
def make_incrementor(n):
    return lambda x: x+n # restricted to be a single expression
f = make_incrementor(42)
f(0) # 42
```

can be passed as an argument:
```py
# sort by key
pairs = [(1, 'one'), (2, 'two'), (3, 'three'), (4, 'four')]
pairs.sort(key=lambda pair: pair[1])
# [(4, 'four'), (1, 'one'), (3, 'three'), (2, 'two')]
```

## Documentation Strings
first line short purpose summary, second line blank, the rest description

```py
def my_function():
    """Do nothing, but document it.

    No, really, it doesn't do anything.
    """
    pass

print(my_function.__doc__)
```

## Function Annotations
only effect is changing the `__annotations__` attribute of the function
```py
def f(ham: str, eggs: str = 'eggs') -> str:
    print("Annotations:", f.__annotations__)
# Annotations: {'ham': <class 'str'>, 'return': <class 'str'> 'eggs': <class 'str'>}
```

## Coding Style
- 4-space indentation
- no more than 79 chars in a line
- put comments on a seperate line
- docstrings
- spaces around operators and after commas
- UpperCamelCase for class and lowercase_with_underscores for fucntions and methods
- no non-ASCII characters(for Python2, must mark encoding at start if containing non-ASCII characters 
```py
# -*- coding: utf-8 -*-
```
- use default encoding(utf-8) for international users

# Data Structures

## Lists
### methods
> `[parameter]` means optional parameter   

`a.append(x)` eq `a[len(a):] = [x]`  eq `l.insert(len(a),x)`  return None  
`a.extend(iterable)` eq `a[len(a):] = iterable`  return None  
`a.insert(i,x)` return None insert x at index i, shift the rest by 1, eq `a[i:i]=[x]`
`a.remove(x)`  ValueError if not found  
`a.pop([i])`  pop the ith element
`a.clear()` eq `del a[:]`  eq `l[:]=[]`
`a.index(x[, start[, end]])` ValueError if not found, search in `[start:end]`, takes no keyword argument  
`a.count(x)`  
`a.sort(*, key=None, reverse=False)` ascending, 0,1,2... return None  
`sorted(a)` defined for all iterables 
`a.reverse()` return None eq `a=a[::-1]`  
`reversed(a)· defined for all iterables 
`a.copy()` eq `a=a[:]`  

### List as Stacks
```py
stack.append(6)
stack.pop()
```
### List as Queues
can be used as queue but slow, need to shift left by one when inserted at start  
instead, use `collections.deque` (double-end queue)

```py
from collections import deque
queue = deque([1,2,3])
queue.append(6)
queue.popleft()
# [2, 3, 6]
```
### List Comprehensions
provides a brief and readable way to create lists by applying operation on other sequences

example:
```py
# create a list of squares of 0 to 9
squares = []
for x in range(10):
    squares.append(x)
# OK but have side effects, x overwritten and still exist after loop

squares = list(map(lambda x: x**2, range(10)))

#  not readable
squares = [x**2 for x in range(10)]

# combine elems of 2 lists if not equal
combined = [(x, y) for x in list1 for y in list2 if x != y]
# the order of the for and if are the same as if they are written vertically
# flatten a nested list
list = [[1,2,3], [4,5,6], [7,8,9]]
flat_list = [x for elem in list for x in elem]
```

### Nested List Comprehensions
```py
# transpose a matrix
matrix = [
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12],
]
t = [[row[j] for row in matrix] for j in range(4)]
# inner expression evaluated in the context of the outer loop

# in the real world:
t = list(zip(*matrix))
```

## `del` Statement
a way to delete values in a list or clear the list given index

```py
del a[:]
del a
```

## Tuples and Sequences
strings and lists are 2 examples of sequence data types  
tuple are immutable but could contain mutable objects like list, its elements are usually heterogeneous and accessed by unpacking or indexing (or even by attribute in the case of `namedtuples`)

lists are mutable, elements are usually homogeneous and accessed by iteration

```py
t = 1, 2, 3
m = [1, 2, 3]
s = "123"
a, b, c = t
a, b ,c = m
a, b ,c = s

# 1-tuple definition
t = 1,
```
> multiple assignment is an application of tuple packing and sequence unpacking

- what is sequence unpacking?
- A: Sequence unpacking are, for sequences like tuple or string, when passed as a argument list, is going to be unpacked to feed each argument required, the number must match
- when the number does not match, use * the catch the remainder:
```py
a, *args = 1,2,3,4,5
```
## Sets
sets are unordered, contains unique elements
```py
# def sets
s = {1,2,2,3}
s = set()
# only way to create empty set
t = set("345")
# in s not in t
s - t
# intersection
s & t
# union
s | t
# not in both
s ^ t


# set comprehension

s = {c for c in "adfasdf" if c not in "asd"}
```

## Dictionaries
dictionaries are sets of unique key-value pairs, other names are "associative arrays"  
keys are usually numbers and strings, but any immutable can be keys, like tuples that only contains numbers, strings and tuples

```py
# def
d = dict([(1,1), (2,4), (3,9), (1,2)]) # (1,1) will overwritten by (1,2)
# The dict() constructor builds dictionaries 
# directly from sequences of key-value pairs:
d = {1:1, 2:4, 3:9}
list(d) == [1,2,3]
sorted(d) == [1,2,3]

# if keys are strings, just specify as keyword arguments
d = dict(first = 1, second = 2, third = 3)

d[1] = 1
del d[1]

# dictionary comprehension
d = {x: x**2 for x in range(10)}
```

## Looping techniques

### dicts
```py
d = {1:"one", 2:"two", 3:"three"}

for k,v in d.items():
    print(k, v)
```

### sequences
```py
s = [3,2,1]

for i,v in enumerate(s):
    print(i,v)
0 3
1 2
2 1
```

### 2 sequences
```py
s = [1,2,3]
t = ['one', 'two', 'three']

for a, b in zip(s, t):
    print(f"{a} is {b}")
```

### loop uniquely/sortedly/reversely
```py
s = [1,2,2,3]
for e in reversed(sorted(set(s))):
    pass
```

### changing a list while looping over it is dangerous
```py
import math
raw_data = [12.4, float("NaN"), 3.7]

filtered = []
for n in raw_data:
    if not math.isnan(n):
        filtered.append(n)
```

## Conditions
operator evaluating order:  
numerical > comparison > not > and > or 

```py
(1 < 2 < 3) == True
# chain comparison is allowed
```

and/or when used as a general value and not as a Boolean, the return value of a short-circuit operator is the last evaluated argument.

```py
string1, string2, string3 = '', 'Trondheim', 'Hammer Dance'
non_null = string1 or string2 or string3 # 'Trondheim'
```

> in python unlike C assignment in expression must use `:=`

## Comparing Sequences and other types
sequence comparison uses a recursive lexicographical ordering

> if one is initial sub-sequence of the other, it's smaller

# Modules

## Definition
python module is a .py file

## Import Module
```py
import mymodule
# importing does not add the functions into the namespace, 
# only the module name
mymodule.__name__
```

A module can contain executable statements and function definitions (which are also executable, introduces function name into the module global namespace upon execution)

These statements are to initialize the module, they are executed only the first time the module name is encountered in an import statement when the module is used as a script

> Each module has a private global namespace, avoiding clashing author's global var with user's, 
> 
> Can introduce module global var with `modname.varname` as well

Module can also import other modules, usually placed at the top to allow the imported module into the module's global namespace
- [x] Can it be directtly refered as `modname.modname`   NO unless re-exported
```py
# mod2
import mod3

from mod3 import functionname
``` 
```py
# mod1
from mod2 import functionname
```
- [ ] is import statement inside a local scope not available outside

`from module import *` imports all the names except for those beginning with `_`

`as` keyword creates alias

> For efficiency reasons, each module is only imported once per interpreter session. Therefore, if you change your modules, you must restart the interpreter – or, if it’s just one module you want to test interactively, use importlib.reload(), e.g. import importlib; importlib.reload(modulename).

## Execute modules as scripts
when using `python module <arguments>`, `__name__` is set to be `__main__`

so to make a module script, write
```py
if __name__ = "__main__":
    # do stuff
    pass
```
this is usually to create a convenient user interface for a module or to create a script that executes a test suite

## The Module Search Path
When trying to import a module, the interpreter first searches for a built-in module, then sys.path, which is initialized with system PATH env vars to contain a list of directories including the directory that contains the current running script (or the current directory if no script is running e.g. in interactive mode)


## Compiled Python files
Python caches compiled version of each module in the `__pycache__` folder under the name `module.version.pyc`, this speeds up module loading. The compiled modules are platform-independent.

This does not reduce running time, only loading time

## Standard Modules
The `sys` module provide access to operating system primitives

```py
import sys
sys.path.append('usr/path')
# can be treated like lists
# by default = PYTHONPATH
```

## dir()
The dir() function is used to find out what names a module defines,
including function, variable, module names

does not list the names of built-in functions and variables, they are defined in the std module `builtins`

## Packages

With package, authors of collections of modules does not need to worry about clashing with names in other collections

To make a folder a package, there must be a `__init__.py` file, can be empty
```py
import sound.effects.echo
from sound.effects import echo
from sound.effects.echo import echofilter
```

## Import * from a package
When using `from package import *`, only imports the names defined by `__init__.py`, and the names in `__all__`
```py
__all__ = ["echo", "surround", "reverse"]
```
Note that the name in `__all__` may be shadowed by local names in `__init__.py`

for Intra-package references, Always use absolute import

`__path__`  This is initialized to be a list containing the name of the directory holding the package’s `__init__.py` before the code in that file is executed

# Input and Output
## Output formatting
- f-string
- str.format()
- str() for human reading
- repr() for intepreter reading

## Formatted String Literals (f-str)
Can use optional format specifiers
- `.3f` rounds number to 3 places after the decimal
- `10` forces the str field to have a minimum width
- `10d` forces the decimal field to 
- `!r` `repr()`
- `!a` `ascii()`
- `!s` `str()`
- `=` show the shown expression

## The Format() Method
Can use positional and/or keyword format arguments

Use a (unpacked)dictionary as the argument is advised with a long list of format fields

> very useful combined with vars()/locals() but need to the names of the vars want to check

## Manual string Formatting
`str.rjust()``str.ljust()``str.center()`  
these methods does not write anything, only return a new str, does not truncate, returns the str given if too long  
`str.zfill()` pads numerical string with 0s on the left, it understands about +/- signs
```py
>>>'12'.zfill(5)
'00012'
>>> '-3.14'.zfill(7)
'-003.14'
>>> '3.14159265359'.zfill(5)
'3.14159265359'
```
## Old string formating
printf-style %

## Reading and Writing Files
`open(filename, mode='r', encoding=None)` returns a file object
flags:  
`r` default  
`w` writing only, truncates if exist  
`x` creating only, fail if exist
`+` updating
`a` append  
`b` binary mode
`t` default txt mode
```py
with open('file', 'w', encoding='utf-8') as f:
    data = f.read()

f.close() # alternatively
assert(f.closed==1)
```

`f.read(size)` returns a string or a bytes object

read the whole file when size is negative or omitted

returns `''` at end of line

`f.readline()` returns a string with a `\n` at the end if not at the last line, returns `''` at end of file

```py
with open('filename') as f:
    for line in f:
        print(line, end='')
# memory effcient, fast and simple

# read all the lines at once:
list(f)
f.readlines()
```

`f.write(string)` returns the number of characters written

`f.tell()` gives the cursor position counting from the beginning

`f.seek(offset, whence)` moves the cursor, whence=0=beginning, 1=current, 2=end

>In text files (those opened without a b in the mode string), only seeks relative to the beginning of the file are allowed (the exception being seeking to the very file end with seek(0, 2)) and the only valid offset values are those returned from the f.tell(), or zero. Any other offset value produces undefined behaviour.

JUMPing and write causes writing of NUL val 

## Reading and Writing JSON
```py
import json
x = []
json.dumps(x) # write to a str
json.dump(x,f) # write to a file
x =json.load(f) # read from a file, must use utf-8
```
> This can handle lists and dicts, others requires a bit more effort

# Errors and Exceptions

## Handling Exceptions
`KeyboardInterupt` is also a built-in exception

An except clause may name multiple exceptions as a parenthesized tuple, for example:
```py
... except (RuntimeError, TypeError, NameError):
...     pass
```

> 当在 try 块或 except 块中遇到 return 语句时，Python 实际上并不会立即返回。相反，它会暂时记住这个返回值，然后检查是否有 finally 块需要执行。

### Exception Arguments
builtin exception types define __str__() to print all the arguments without explicitly accessing .args.
```py
try:
    raise Exception('spam', 'eggs')
except Exception as inst:
    print(type(inst))    # the exception type
    print(inst.args)     # arguments stored in .args
    print(inst)          # __str__ allows args to be printed directly,
                         # but may be overridden in exception subclasses
    x, y = inst.args     # unpack args
    print('x =', x)
    print('y =', y)
```
<class 'Exception'>
('spam', 'eggs')
('spam', 'eggs')
x = spam
y = eggs

**`BaseException`** is the base class for all exceptions, while its subclass`Excpetion` is base class of all the non-fatal exceptions

> Fatal exceptions includes `KeyboardInterrupt` and `SystemExit`

### Log and Re-raise
The most common pattern for handling Exception is to print or log the exception and then re-raise it (allowing a caller to handle the exception as well):
```py
try:
    ...
except ...
except Exception as err:
    print(f"Unexpected {err=}, {type(err)=})
    raise
```
### Try-Except-Else
The use of the else clause is better than adding additional code to the try clause because it avoids accidentally catching an exception that wasn’t raised by the code being protected by the try … except statement.

### Raising Exceptions
when raise takes a class as argument, it calls the constructor with no argument

`raise ... from exc` enforces exception chaining, while `raise ... from None` disables exception chaining

### Finally Clause
If the try statement reaches a break, continue or return statement, the finally clause will execute just prior to the break, continue or return statement’s execution. If the finally clause executes a break, continue or return statement, exceptions not handled are not re-raised. 
**So usually no break/continue/return statement in the finally clause, just releasing external resources like connections or files**

## Raising and Handling Multiple Unrelated Exceptions
This is desirable in concurrency frameworks, using the built-in **`ExceptionGroup`**

By using except* instead of except, we can selectively handle only the exceptions in the group that match a certain type.

Note that the exceptions nested in an exception group must be instances, not types. This is because in practice the exceptions would typically be ones that have already been raised and caught by the program, along the following pattern:

```py
excs = []
for test in tests:
    try:
        test.run()
    except Exception as e:
        excs.append(e)

if excs:
   raise ExceptionGroup("Test Failures", excs)
```

To add more information after the exception was caught (as opposed to the creation of the exception), use `e.add_note()`
Useful when we want to add context info before collecting indivdual into a exception group


# Classes
In general, calling a method with a list of n arguments is equivalent to calling the corresponding function with an argument list that is created by inserting the method’s instance object before the first argument.

## Namespace Lifetime
Namespaces are created at different moments and have different lifetimes. The namespace containing the built-in names is created when the Python interpreter starts up, and is never deleted. The global namespace for a module is created when the module definition is read in; normally, module namespaces also last until the interpreter quits. The statements executed by the top-level invocation of the interpreter, either read from a script file or interactively, are considered part of a module called __main__, so they have their own global namespace. (The built-in names actually also live in a module; this is called builtins.)
# Standard Library
## Dates and Times
supplies classes for datetime manipulation, the module focuses on datetime arithmetic and output formatting, also support timezone-aware objects

```py
import datetime
now = datetime.date.today()

now.strftime("%m-%d-%y. %d %b %Y is a %A on the %d day of %B.")
# 12-02-03. 02 Dec 2003 is a Tuesday on the 02 day of December.

# dates support calendar arithmetic
birthday = date(1964, 7, 31)
age = now - birthday
age.days
```