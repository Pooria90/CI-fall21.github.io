# Computational Intelligence

- Instructor   : [Sepideh Hajipour](http://sharif.edu/~hajipour/)
- Assistant    : [Pooria Ashrafian](https://pooria90.github.io/)

This page accompanies the class material of EE25-729 course at [the Sharif University of Technology](https://en.sharif.edu/). Feel free to write your questions/comments to <pooria.ashrafian@gmail.com>.

- [A gentle intro to Python](#a-gentle-intro-to-python)
  * [Writing Python](#writing-python)
  * [Installing a Python package](#installing-a-python-package)
  * [Python shell](#python-shell)
  * [Data types](#data-types)
- [numpy](#numpy)
- [matplotlib](#matplotlib)
- [pytorch](#pytorch)
- [pyeasyga](#pyeasyga)

## A gentle intro to Python

Python was developed in the early 90's by Guido van Rossum at the National Research Institute for Mathematics and Computer Science in the Netherlands. 

Python is designed to be highly readable. It uses English keywords frequently, and it has fewer syntactical constructions than other languages.

- **Python is interpreted**: You don't need to compile your code. It is processed at runtime like MATLAB.
- **Python is interactive**: You can use command prompt and interact with the interpreter, like command line in MATLAB.
- **Python is object-oriented**: You can define custom classes and objects, and use inheritance from parent classes.

You can download a suitable version from [python.org](https://www.python.org). 



### Writing Python

To run Python codes, you may either write your code in a Python script (`.py` format) or a Python notebook (`.ipynb` format).

For writing Python scripts you can either use the default Python editor in Python standard library, **IDLE**, or any other editor for this purpose like **VS Code** or **PyCharm**.

Notebooks provide you with the the capability called **cell**. You can add several cells in a notebook and run each cell separately. You can either install **Jupyter notebook** after installing Python, or use Colab notebooks at [colab.research.google.com](https://colab.research.google.com/). The benefit of using Colab is that you have access to many preinstalled Python packages.



### Installing a Python package

After you successfully installed Python and set up Python path, you can open your command prompt and install additional packages by using `pip`. For example, in order to install Jupyter notebook you can run:

```shell
pip install jupyter-notebook
```



### Python shell

From now on, you can use scripts, notebooks, or even command prompt to run code. At the beginning, I strongly recommend you to write some statements in Python shell for getting used to it. Python shell is an enviornment where you can run single Python statements and see the result in place. Type `python` in your command prompt and press `enter`. The Python shell opens like this:

```shell
C:\Users\Asus>python
Python 3.8.3 (tags/v3.8.3:6f8c832, May 13 2020, 22:20:19) [MSC v.1925 32 bit (Intel)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

Try to interact with the interpreter. Two basic functions to try are `print` and `type`. With the former you can show a variable to the user, and by using the latter you can use data type (or *class*) of a variable. An example of playing with the shell can be like the following box. As you may notice, `#` is used to define single-line comments in Python. The interpreter ignores everything after `#`.

```shell
>>> print ('Hello World!') # Strings can be defined by '' or "".
Hello World!
>>> x = 216
>>> print (x)
216
>>> type(x) # x is integer because it is define without a floating point
<class 'int'>
>>> y = 12.56 # y is floating point number
>>> type(y)
<class 'float'>
```

To define a variable, you may use lower or upper case letters, or underscore.

```shell
>>> family_name = 'Ashrafian'
>>> print (family_name)
Ashrafian
>>> type(family_name) # it is a string (str) variable
<class 'str'>
>>> Course = 'Computational Intelligence'
>>> print (Course)
Computational Intelligence
```

 

### Basic data types

**Numbers**: You have already seen integer and float numbers. In the following example you get familiar with arithmetic and assignment operators.

```python
x = 12  # = is assignment operator; As you have seen in C or MATLAB

print (type (x))  # prints <class 'int'>

print (x + 2)  # prints 14
print (x - 3)  # prints 9

print (x / 4)  # prints 3.0; / is float division. It means the result is a float
print (type (x/4)) # prints <class 'float'>

print (x // 5)  # prints 2; // is the integer division, or so called 'quotient'
print (x ** 2)  # prints 144; ** is the power operation

# Assignment operators
x += 3
print (x)  # prints 15
x -= 1
print (x)  # prints 14
x *= 3
print (x)  # prints 42
x **= 2
print (x)  # what do you think?
```



**Booleans**: They can be either `True` or `False`. Logical operators (`and`, `or`, `not`) and comparison (`==`, `>`, `>=`, `!=` (not equal), ...) operators work on them.

```python
x = True
print (type (x))  # prints <class 'bool'>
print (not x)  # prints False

y = 15
print (y > 5)  # prints True

p = y > 5
print (type (p)) # prints <class 'bool'>
print (y == 12)  # prints False

print ((y > 3) and (y < 10))  # prints False; because one of them is False
print ((y > 3) or (y != 10))  # prints True; because one of them is Ture
```



**Strings**: We said that they are either defined by single quote (`''`) or double quote (`""`).

```python
s1 = 'computational'
s2 = 'intelligence'

L1 = len (s1)  # len counts the number of characters
print (L1)  # 13 characters; yeah?

print (s1 + s2)	# prints computationalintelligence (+ for str = concatenation)
s_cat = s1 + ' ' + s2
print (s_cat)  # prints computational intelligence
print (f'hello from {s_cat}')  # You see that f and {}? Those are for formatted output; prints hello from computational intelligence
```

Strings have useful methods. Wait...What is a method?

- Method is a function. However, unlike the functions that `print` and `len` that we have already seen, it is defined for its object. So, without defining a string, there is **no string method**. Methods are applied using a `.` after the variable. For example:

```python
s = 'Pooria'
print(s.upper())  # makes everything uppercase: 'POORIA'
print(s.lower())  # makes everything lowercase: 'pooria'

s = 'i am pooria'
print(s.capitalize()) # make first letter capital: 'I am...
print(s.find('p'))  # finds the index of 'p' by starting from zero; prints 5
print(s.split())  # splits s into a list of words: ['i', 'am', 'pooria']
```

For a complete list refer to Python documentations in [here](https://docs.python.org/3/library/stdtypes.html#string-methods).



### Lists

A `list` in Python is an ordered collection of elements. When we say *element*, we mean that it doesn't matter that the members of the list are not the same type. To define a `list` you can use square brackets (`[]`).

```python
L1 = []  # empty list
print (type(L1))  # prints <class 'list'>

L2 = [2, 4.5, 'hello', [1,2,3]]  # a list of different element types
print(len(L2))  # prints 4; L2 has 4 elements
```

**index**: Similar to the arrays in C or C++, the first index in a list is 0 (the first element). In Python, there is also an index system that start at the end of the list. The final element is indexed as -1, the element before the last is -2, and so on.

```python
L = [12, 5, 13, 18, 15]
print (len(L))  # a list of 5 elements

print (L[0])  # prints 12; the first element
print (L[2])  # prints 13; the third element

print (L[-1])  # prints 15; the last element
print (L[-2])  # prints 18; the last element
```

**methods**: Maybe, the most useful method for working with a `list` object is `append`. It is used to add a single element at the end of a `list`. For a complete list of methods, check out Python documentations.

```python
L = [10, 8, 6]
print (L)  # prints [10, 8, 6]

L.append(2)
L.append(5)
L.append(8)
print (L)  # prints [10, 8, 6, 2, 5, 8]

L.remove(8)  # removes the first 8 that is in the list
print (L)  # prints [10, 6, 2, 5, 8]

L.reverse()  # reverses the order of the list
print (L)  # prints [8, 5, 2, 6, 10]

z = L.pop(-1)  # removes the element at the specified position and returns that element
print (L)  # prints [8, 5, 2, 6]

L.extend([20, 10])  # adds the list in the () to L
print (L)  # prints [8, 5, 2, 6, 20, 10]
```

Remember an important point about `list` objects. When you assign a `list` to another one using `=`, the Python assigns the reference of the primary `list`. So, both of the variables point to the same memory space. As a result, any alternation in one of the lists will happen similarly in the other one.

To avoid this, you can do the assignment with `copy` method.

```python
L1 = [4, 5, 'salam', 'hello']
L2 = L1
L1.append('hey')  # 'hey' is appended to both lists
print (L1)  # prints [4, 5, 'salam', 'hello', 'hey']
print (L2)  # prints [4, 5, 'salam', 'hello', 'hey']

L3 = L1.copy()
L1.remove('hello')
print (L1)  # prints [4, 5, 'salam', 'hey']
print (L2)  # prints [4, 5, 'salam', 'hey']
print (L3)  # prints [4, 5, 'salam', 'hello', 'hey']; L3 is not affected
```

**slicing**: There several ways to slice a `list` (taking elements of some indices).

```python
# L[beg:end] ; returns the elements starting at index beg, ending at end-1
# L[beg:end:step] ; returns the elements starting at index beg, increasing with step, ending at end-1
# L[:end] ; from the begining to end-1
# L[beg:] ; from beg to the last element

L = [3, 4, 10, 45, 6, 13, 9]
print (L[1::2])  # prints [4, 45, 13]; end not specified (means until the last element)
print (L[:-2])  # prints [3, 4, 10, 45, 6]
print (L[1:5])  # prints [4, 10, 45, 6]

L[1:4] = [1, 2, 3]  # change part of the list
print (L)  # prints [3, 1, 2, 3, 6, 13, 9]
```



### Tuples

Tuples are very similar to lists, for example they are ordered. However, unlike lists, they are *immutable*. It means that you can't change a single element of a tuple, or append something to it. If you want to change something in a tuple, you have to assign a whole new tuple to that. Tuples are defined using `()`. The indexing and slicing methods also work here.

```python
t = (21, 10, 'sepideh', 'hajipour', 5.5, 10, 55)
print (type(t))  # prints <class 'tuple'>
print (t[-1])  # prints 55
print (t[1:3])  # prints (10, 'sepideh')

print (t.count(10))  # prints 2; there are two 10s in the tuple
print (t.index('hajipour'))  # prints 3; 'hajipour' is in the index 3

t[1] = 40  # TypeError: 'tuple' object does not support item assignment
```



### Dictionaries

A dictionary stores (key, value) pairs. Think of the key as a *word* and the value as its *meaning* in an English dictionary like Merriam Webster.

The value can be any kind of element, but the key should be an immutable element (so the key cannot be a list). To define a dictionary you can use `{}` and separate a key from its value using `:`. 

```python
d1 = {'ali':1, 10:30, 20:[4,5]}
print (type(d1))  # prints <class 'dict'>

d1['eli'] = 3  # adding another (key, value) pair
print (d1)  # prints {'ali': 1, 10: 30, 20: [4, 5], 'eli': 3}
```

**methods**: There are some useful dictionary methods in Python.

 ```python
 d = {1:1, 2:4, 3:9, 4:16}
 
 print (d.keys())  # prints dict_keys([1, 2, 3, 4])
 print (d.values())  # prints dict_values([1, 4, 9, 16])
 print (d.items())  # prints dict_items([(1, 1), (2, 4), (3, 9), (4, 16)])
 
 # You can easily convert each of the following to a list by applying list()
 L = list(d.items())
 print (L)  # prints [(1, 1), (2, 4), (3, 9), (4, 16)]
 
 print (d.get(2))  # prints the value of the key 2; prints 4
 print (d.get(5))  # prints None because 5 is not in the keys
 
 d.update({5:25, 6:36})  # updates d with the dictionary in ()
 print (d)  # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36}
 ```



### Conditional statements

In Python, we use `if`, `elif` (called else if in C), and `else` to define conditional statements. The general structure is given below. Recall that in C, when a condition was true, everything inside a `{}` block was executed. But in Python we just *indent* (usually using a tab or 4 white space) the block.

```markdown
if condition1:
	do something (pay attention to the indent)
elif condition2:
	do something else
elif condition3:
	do something else
else:
	do something else if none of the above conditions hold
```

Here is a child example:

```python
grade = int(input('Enter your computational intelligence grade: '))

if grade >= 18:
    print ('Wow you did great!')
elif grade >= 15:
    print ('You did well.')
elif grade >= 10:
    print ('You need to study more.')
else:
    print ('You have failed the course.')
```



### Loops

#### For loops

You can use a for loop to iterate over lists, tuples, dictionary keys or values or items, or range of integer numbers. Just like the conditional statements you have to use `:` and indent to define the block inside the loop.

```python
L = [1, 3, 5] # or a tuple like (1, 3, 5)
for item in L:
    print (item ** 2)
# prints 1, 9, 25

d = {'ali':1, 'pooria':2, 'ahmad':3}

for name in d.keys():
    print (name)
# prints 'ali', 'pooria', 'ahmad'

for k,v in d.items(): # iterate over (key,value) pairs
    print (f'key: {k} --- value: {v}')
# prints key: 'ali' --- value: 1 ...

# range(start, stop, step)
# start and step are optional. Default value for start is 0 and for step is 1
# range(5): 0,1,2,3,4
# range(2,6): 2,3,4,5
# range(2,7,2): 2,4,6

for i in range(100):
    if i%15 == 0: # or simply 'for i in range(0,100,15)' and without 'if'
        print (i)
# prints 0, 15, ..., 90
```

#### While loops

As you already know, while loops are defined using a condition (a *Boolean statement*). The indented statements after the while loop will be executed until the the condition is `True`.

```python
counter = 0
while counter < 10:
    counter += 1
    print (f'Execution number {counter}')
# prints Execution number 1, ... , Execution number 10
```

#### Loop control

You can use `continue` and `break` to control the execution of a loop under certain condition. For example in the following loop ignores multipliers of 3 and prints natural numbers of the forms 3k+1 and 3k+2. When the counter equals 100, the execution ends.

```python
j = 0
while True:
    j += 1
    if j%3 == 0:
        continue
    if j == 100:
        break
    print (j)
    
# prints 1,2,4,5,...,94,95,97,98
```



### Functions

To define a function in Python you can use the following structure using the keyword `def`.

```markdown
def function_name (input1, input2, ...):
	statement 1
	statement 2
	...
	return something (or nothing!)
```

For example the following function checks whether the input is prime or not (you may notice that we don't specify the type of input variable. For checking that the input is correct or not one approach is using the built-in function `isinstance` and the keyword `assert`. Search them!).

```python
def isprime(n):
    result = True
    for i in range(2,n):
        if n%i == 0:
            result = False
            break
    return result

print (isprime(21)) # prints False
print (isprime(23)) # prints True
```

You can also define functions using inputs with default values. In this case if you do not specify the value of those inputs, the function uses the default value when called.

```python
def devide(a, b=10):
    return a/b

print (devide(5))  # prints 0.5; uses default value of b
print (devide(3,4)) # prints 0.75; here b=4
print (devide(b=50,a=5))  # prints 0.1; note that you can call a function by telling exactly which variable has what value. In this case the order of the inputs doesn't matter.
```



### Classes

You have already seen several Python built-in classes like `list` and `dict`. You can define your custom classes. To do so, you should specify the attributes (or variables) and methods of your objects. The general structure is like below:

```markdown
class class_name ():
	def __init__(self, input1, input2, ...): (This is the constructor of your objects; tells the Python how to intialize the objects)
		self.attribute1 = something
		self.attribute2 = something
		...
		statement1
		statement2
		...
	
	def method1(self, some inputs):
		some statements
		
	def method2(self, some inputs):
		some statements
		
	...
```

`self` represents the instance of the class. By using the `self` keyword we can access the attributes and methods inside the class to write out statements.

And you can define the object like this:

```markdown
object = class_name(input1, input2, ...)
object.attribute1
object.method1(some inputs)
```

 Look at the example below. In this example we define a point in 2D space.

```python
import math

class point():
    def __init__(self,x,y,name='A'):
        self.x = x  # height
        self.y = y  # width
        self.name = name  # label of the point
    
    def distance(self, p): # computes distance from another point
        d = math.sqrt ( (p.x - self.x)**2 + (p.y - self.y)**2 )
        return d
    
    def norm(self):  # euclidean norm or distance from origin
        n = math.sqrt (self.x**2 + self.y**2)
        return n

a = point(x=3,y=4,name='A')
print (a.x, a.y, a.name)  # prints 3, 4, A
print (a.norm())  # prints sqrt(3^2+4^2)=5

b = point(x=0,y=4,name='B')
print (a.distance(b))  # prints 3; a and b in 2D space are 3 units apart
```

For a complete explanation for classes, check out the [documentations](https://docs.python.org/3.5/tutorial/classes.html)

## numpy



## matplotlib

For our visualizations, `matplotlib.pyplot` is all we need. Let's import the module and set up figure and axes.
```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots()
```
`plt.subplots()` is a function that returns a tuple containing a figure and axes object(s). `fig` is useful for saving what we have drawn using `ax`. 
Now I draw a sine wave to show how `ax` works.

```python
import numpy as np

t = np.linspace(0, 1, 100)
f = 5
x = np.sin(2 * np.pi * f * t)

ax.plot(t,x)
plt.show() # To display open figures; fig in here
```

After running we see this:

![image](images/sine_1.png)

Let's make it prettier using `ax`'s methods:

```python
ax.plot(t, x)
ax.set_title(f'Sine wave with freq={f}')
ax.set_xlabel('Time')
ax.set_ylabel('Signal value')
ax.grid(True)
plt.show()
```

There we go:

![sine_2](images/sine_2.png)





## keras



## pyeasyga


<!---
You can use the [editor on GitHub](https://github.com/CI-fall21/CI-fall21.github.io/edit/main/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/CI-fall21/CI-fall21.github.io/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
--->
