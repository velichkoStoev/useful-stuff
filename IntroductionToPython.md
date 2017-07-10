# Introduction to Python

##  Setup

### Installing Python3 
Python 3.6 is the current latest release.

#### For Windows and Mac OS users
Check [this page](https://www.python.org/downloads/release/python-360/) (the download links are in the botton of the page). Download the appropriate installer (the executable installer for Windows is a good one) and run it (during the installation select the `Add Python to PATH` option).


#### For Linux users 
Usually the newer distros come with Python 2 and 3 pre-installed. Run `python3 -V` in your Terminal to check the current version. If Python is not present, run `sudo apt-get install python3` to install it.

After the installation open a console window (Command Prompt on Win and Terminal on Mac/Ubuntu) and run the `python` command. You should see something like that.  

<img src="http://i.imgur.com/ZaxZk6A.png" width="400" alt="Python on Windows">

Python is up and running!

## First steps

### Code Snippet

```python
x = 34 - 23   # A comment.
y = "Hello"   # Another one.
z = 3.45

if z == 3.45 or y == "Hello":
  x = x + 1
  y = y + " World"          # String concat.

print x
print y
```
### Understanding the example

- Assignment uses = and comparison uses ==.
- For numbers + - * / % are as expected.
- Special use of + for string concatenation.
- Special use of % for string formatting (as with printf in C)
- Logical operators are words (and, or, not) not symbols
- The basic printing command is print.
- The first assignment to a variable creates it.
- Variable types don't need to be declared.
- Python figures out the variable types on its own.

### Basic datatypes

- Integers
- Floats
- Strings 

```python
i = 4
f = 5.6
st1 = 'abc'
st2 = "abcd"
```

### Whitespaces

Whitespace is meaningful in Python: especially indentation and placement of newlines.
 - Use a newline to end a line of code.
 - No braces { } to mark blocks of code in Python… Use consistent indentation instead.
    - The first line with less indentation is outside of the block.
    - The first line with more indentation starts a nested block
 - Often a colon appears at the start of a new block. (E.g. for function and class definitions.)
 
 ### Comments
 
 - Start comments with # – the rest of line is ignored.
 - Can include a "documentation string" as the first line of any new function or class that you define.
 - The development environment, debugger, and other tools use it: it's good style to include one.

```python
def my_function(x, y):
  """This is the docstring. This
  function does blah blah blah."""
  # The code would go here...
```

### Assignment 

Binding a name to a datatype is called assignment.  

```python
x = 3
str = 'Aveiro'
```
If you try to access a name before it's been properly created (by placing it on the left side of an assignment), you'll get an
error. 

```python
>>> y
Traceback (most recent call last):
 File "<pyshell#16>", line 1, in -toplevel-
 y
NameError: name 'y' is not defined
>>> y = 3
>>> y
3
```

### More on assignment
- For simple built-in datatypes (integers, floats, strings), assignment behaves as you would expect:
```python
>>> x = 3 # Creates 3, name x refers to 3
>>> y = x # Creates name y, refers to 3.
>>> y = 4 # Creates ref for 4. Changes y.
>>> print x # No effect on x, still ref 3.
3
```
- For other data types (lists, dictionaries, user-defined types), assignment works differently.
  - These datatypes are "mutable." 
  - When we change these data, we do it in place.
  - We don't copy them into a new memory address each time.
  - If we type y=x and then modify y, both x and y are changed.
  
```python
>>> a = [1, 2, 3] # a now references the list [1, 2, 3]
>>> b = a # b now references what a references
>>> a.append(4) # this changes the list a references
>>> print b # if we print what b references,
[1, 2, 3, 4] # SURPRISE! It has changed…
```


### Naming rules
  - Names are case sensitive and cannot start with a number. They can contain letters, numbers, and underscores.
    ``` bob Bob _bob _2_bob_ bob_2 BoB ```
  - There are some reserved words: ```and, assert, break, class, continue, def, del, 
      elif, else, except, exec, finally, for, from,
      global, if, import, in, is, lambda, not, or, pass, print, raise, return, try, while```


## Sequence types: Tuples, Lists, and Strings
1. Tuple
  - A simple immutable ordered sequence of items
  - Items can be of mixed types, including collection types
2. Strings
  - Immutable
  - Conceptually very much like a tuple
3. List
  - Mutable ordered sequence of items of mixed types

### Defining sequence types
```python
>>> tu = (23, 'abc', 4.56, (2,3), 'def')
>>> li = ["abc", 34, 4.34, 23]
>>> st = "Hello World"
>>> st = 'Hello World'
>>> st = """This is a multi-line
string that uses triple quotes."""
```

We can access individual members of a tuple, list, or string using square bracket "array" notation. Note that all of them are zero based.
```python
>>> tu = (23, 'abc', 4.56, (2,3), 'def')
>>> tu[1] # Second item in the tuple.
 'abc'
>>> li = ["abc", 34, 4.34, 23]
>>> li[1] # Second item in the list.
 34
>>> st = "Hello World"
>>> st[1] # Second character in string.
 'e'
```
We can use both positive and negative indices to access values in a sequence object.
```python
>>> t = (23, 'abc', 4.56, (2,3), 'def')
>>> t[1]
'abc'
>>> t[-3]
4.56 
```
### The 'in' operator
 - Boolean test whether a value is inside a container:
```python
>>> t = [1, 2, 4, 5]
>>> 3 in t
False
>>> 4 in t
True
>>> 4 not in t
False
```
 - For strings, tests for substrings
```python
>>> a = 'abcde'
>>> 'c' in a
True
>>> 'cd' in a
True
>>> 'ac' in a
False
```

- Be careful: the in keyword is also used in the syntax of for loops and list comprehensions.

### The '+' operator

The + operator produces a new tuple, list, or string whose value is the concatenation of its arguments.

```python
>>> (1, 2, 3) + (4, 5, 6)
 (1, 2, 3, 4, 5, 6)
>>> [1, 2, 3] + [4, 5, 6]
 [1, 2, 3, 4, 5, 6]
>>> "Hello" + " " + "World"
 'Hello World'
```

### The '*' operator

The * operator produces a new tuple, list, or string that "repeats" the original content.

```python
>>> (1, 2, 3) * 3
(1, 2, 3, 1, 2, 3, 1, 2, 3)
>>> [1, 2, 3] * 3
[1, 2, 3, 1, 2, 3, 1, 2, 3]
>>> "Hello" * 3
'HelloHelloHello'
```
## Mutability: Tuples vs. Lists

Tuples are immutable!

```python
t = (23, 'abc', 4.56, (2,3), 'def')
>>> t[2] = 3.14
Traceback (most recent call last):
 File "<pyshell#75>", line 1, in -toplevel-
 tu[2] = 3.14
TypeError: object doesn't support item assignment
You can't change a tuple.
```

You can make a fresh tuple and assign its reference to a previously used
name.
```python
>>> t = (23, 'abc', 3.14, (2,3), 'def')
```
Lists are mutable!

```python
>>> li = ['abc', 23, 4.34, 23]
>>> li[1] = 45
>>> li
['abc', 45, 4.34, 23]
```

- We can change lists in place.
- Name `li` still points to the same memory reference when we're done.
- The mutability of lists means that they aren't as fast as tuples. 

### Operations on lists only
```python
>>> li = [1, 11, 3, 4, 5]
>>> li.append('a') # Our first exposure to method syntax
>>> li
[1, 11, 3, 4, 5, 'a']
>>> li.insert(2, 'i')
>>>li
[1, 11, 'i', 3, 4, 5, 'a']
>>> li.extend([9, 8, 7])
>>>li
[1, 2, 'i', 3, 4, 5, 'a', 9, 8, 7]
>>> li.append([10, 11, 12])
>>> li
[1, 2, 'i', 3, 4, 5, 'a', 9, 8, 7, [10, 11, 12]]
>>> li = ['a', 'b', 'c', 'b']
>>> li.index('b') # index of first occurrence
1
>>> li.count('b') # number of occurrences
2
>>> li.remove('b') # remove first occurrence
>>> li
['a', 'c', 'b']
>>> li = [5, 2, 6, 8]
>>> li.reverse() # reverse the list *in place*
>>> li
 [8, 6, 2, 5]
>>> li.sort() # sort the list *in place*
>>> li
 [2, 5, 6, 8]
```

### Tuples vs Lists
- Lists slower but more powerful than tuples.
 - Lists can be modified, and they have lots of handy operations we can
perform on them.
- Tuples are immutable and have fewer features.

To convert between tuples and lists use the list() and tuple()
functions:
```python
li = list(tu)
tu = tuple(li)
```

## Dictionaries

Dictionaries store a mapping between a set of keys and a set of values.

 - Keys can be any immutable type.   
 - Values can be any type
 - A single dictionary can store values of different types
 - You can define, modify, view, lookup, and delete the key-value pairs in the dictionary.
 
 ```python
>>> d = {'user':'bozo', 'pswd':1234}
>>> d['user']
'bozo'
>>> d['pswd']
1234
>>> d['bozo']
Traceback (innermost last):
 File '<interactive input>' line 1, in ?
KeyError: bozo
>>> d = {'user':'bozo', 'pswd':1234}
>>> d['user'] = 'clown'
>>> d
{'user':'clown', 'pswd':1234}
>>> d['id'] = 45
>>> d
{'user':'clown', 'id':45, 'pswd':1234}
>>> d = {'user':'bozo', 'p':1234, 'i':34}
>>> del d['user'] # Remove one.
>>> d
{'p':1234, 'i':34}
>>> d.clear() # Remove all.
>>> d
{}
>>> d = {'user':'bozo', 'p':1234, 'i':34}
>>> d.keys() # List of keys.
['user', 'p', 'i']
>>> d.values() # List of values.
['bozo', 1234, 34]
>>> d.items() # List of item tuples.
[('user','bozo'), ('p',1234), ('i',34)] 
```
## Functions

 - def creates a function and assigns it a name
 - return sends a result back to the caller
 - Arguments are passed by assignment
 - Arguments and return types are not declared
``` 
 def <name>(arg1, arg2, ..., argN):
<statements>
return <value>```
```python
def times(x,y):
return x*y
```
 - Can define defaults for arguments that need not be passed
```python
def func(a, b, c=10, d=100):
  print a, b, c, d
>>> func(1,2)
1 2 10 100
>>> func(1,2,3,4)
1,2,3,4
```

## Control of flow

```python
if x == 3:
  print "X equals 3."
elif x == 2:
  print "X equals 2."
else:
  print "X equals something else."
print "This is outside the 'if'."

x = 3
while x < 10:
  if x > 7:
    x += 2
    continue
  x = x + 1
  print "Still in the loop."
  if x == 8:
    break
print "Outside of the loop."

for x in range(10):
  if x > 7:
    x += 2
    continue
  x = x + 1
  print "Still in the loop."
  if x == 8:
    break
print "Outside of the loop."
```
## File I/O
```python
fileptr = open('filename')
somestring = fileptr.read()
for line in fileptr:
 print line
fileptr.close()
```


## Classes and objects

### What is a class?
A blueprint for creating a new datatype.

### What is an Object?
A software item that contains variables and methods. An instance of a class.

```python
class atom(object):
  def __init__(self,atno,x,y,z):
    self.atno = atno
    self.position = (x,y,z)
    
  def symbol(self):
    return Atno_to_Symbol[atno]

  def __repr__(self): # overloads printing
    return '%d %10.4f %10.4f %10.4f' % (self.atno, self.position[0], self.position[1],self.position[2])

>>> at = atom(6,0.0,1.0,2.0)
>>> print at
6 0.0000 1.0000 2.0000
>>> at.symbol()
'C'
```
### Public and private data
In Python anything with two leading underscores is private
 ```__a, __my_variable```
- Anything with one leading underscore is semiprivate, and you should feel guilty accessing this data directly.
 ```_b```
 
 ### Exceptions
```python
>>> try:
...   1 / 0
... except:
...   print('That was silly!')
... finally:
...   print('This gets executed no matter what')
...
That was silly!
This gets executed no matter what```
