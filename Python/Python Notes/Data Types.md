Data types define:
# “what kind of value a variable stores”

Example:
- number
- text
- true/false
- collection of items

Every programming language has data types.

Since you know JS/TS already, this will feel familiar.

But Python has some important differences.

---
# WHY DATA TYPES MATTER

Because operations depend on data type.

Example:

```
10 + 20
```

works differently than:

```
"10" + "20"
```

Output:

```
1020
```

NOT:

```
30
```

So Python needs to know:
- what type the value is

---
# PYTHON BASIC DATA TYPES

Main primitive/basic types:

|Type|Example|
|---|---|
|int|10|
|float|10.5|
|str|"Hello"|
|bool|True|
|NoneType|None|

---
# 1. INTEGER (int)

Integers are:
# whole numbers

---
# Examples

```
age = 24 
price = 1000 
temperature = -5
```

---
# Type Check

```
print(type(age))
```

Output:

```
<class 'int'>
```

---
# IMPORTANT

Python integers have:
# arbitrary precision

Meaning Python can store VERY large integers.

Example:

```
big_num = 999999999999999999999999999999
```

Still valid.

---
# Arithmetic with int

```
a = 10b = 3print(a + b)print(a - b)print(a * b)
```

---
# Division Behavior

```
print(10 / 2)
```

Output:

```
5.0
```

Notice:
# float returned

Python division always returns float.

---
# 2. FLOAT (float)

Float means:
# decimal numbers

---
# Examples

```
price = 99.99
pi = 3.14
temperature = -10.5
```

---
# Type

```
print(type(price))
```

Output:

```
<class 'float'>
```

---
# Float Precision Issue

VERY IMPORTANT.

```
print(0.1 + 0.2)
```

Output:

```
0.30000000000000004
```

This happens because of:
# binary floating-point precision

Very important programming concept.

---
# For Financial Apps

Use:

```
Decimal
```

from:

```
decimal module
```

NOT regular float.

Important backend engineering point.

---
# 3. STRING (str)

Strings are:
# text data

---
# Examples

```
name = "Harshit"
city = 'Delhi'
```

---
# Type

```
print(type(name))
```

Output:

```
<class 'str'>
```

---
# Strings Are Immutable

VERY IMPORTANT.

Meaning:
# cannot change original string

---
# Example

```
name = "Harshit"
name[0] = "M"
```

This gives error.

---
# Why?

Strings are immutable objects.

---
# String Indexing

```
name = "Harshit"
print(name[0])
```

Output:

```
H
```

---
# Negative Indexing

```
print(name[-1])
```

Output:

```
t
```

---
# String Slicing

VERY IMPORTANT.

```
print(name[0:4])
```

Output:

```
Hars
```

---
# Slice Syntax

```
[start:end]
```

End excluded.

---
# String Methods

---
## upper()

```
print(name.upper())
```

---
## lower()

```
print(name.lower())
```

---
## strip()

```
text = " hello "print(text.strip())
```

---
## replace()

```
print(name.replace("H", "M"))
```

---
## split()

```
text = "a,b,c"print(text.split(","))
```

Output:

```
['a', 'b', 'c']
```

---
# F-STRINGS

VERY IMPORTANT.

```
name = "Harshit"age = 24print(f"My name is {name}")
```

---
# 4. BOOLEAN (bool)

Boolean means:
# True or False

---
# Examples

```
is_admin = True
is_logged_in = False
```

---
# IMPORTANT

Capitalized:

```
True
False
```

NOT:

```
true
false
```

---
# Type

```
print(type(True))
```

Output:

```
<class 'bool'>
```

---
# Comparison Operations Return Boolean

```
print(10 > 5)
```

Output:

```
True
```

---
# Boolean Logic

```
print(True and False)
print(True or False)
print(not True)
```

---
# 5. NONE (None Type)

Equivalent of JS:

```
null
```

Python:

```
None
```

---
# Example

```
user = None
```

Meaning:
- no value
- empty state
- missing object

---
# Type

```
print(type(None))
```

Output:

```
<class 'NoneType'>
```

---
# BEST PRACTICE

Check None using:

```
is None
```

Example:

```
if user is None:    
	print("No user")
```

NOT:

```
if user == None
```

---
# WHY?

Because:

```
is
```

checks identity properly.

Pythonic approach.

---
# MUTABLE VS IMMUTABLE

This is one of the MOST IMPORTANT Python concepts.

---
# IMMUTABLE TYPES

Cannot change after creation.

Examples:
- int
- float
- str
- bool
- tuple

---
# MUTABLE TYPES

Can change after creation.

Examples:

- list
- dict
- set

---
# Example

---

# Immutable

```
name = "Harshit"
name = "Mohit"
```

Actually creates new string object.

---
# Mutable

```
nums = [1, 2, 3]
nums.append(4)
```

Original list changed.

---
# WHY THIS IS IMPORTANT

This affects:
- memory
- performance
- bugs
- concurrency
- function behavior

VERY important for backend engineering.

---
# TYPE CONVERSION

---
# int()

```
age = int("24")
```

---
# float()

```
price = float("99.99")
```

---
# str()

```
num = str(100)
```

---
# bool()

```
print(bool(1))
print(bool(0))
```

---

# TRUTHY & FALSY VALUES

VERY IMPORTANT.

---
# Falsy Values

```
False
None
00.0
""
[]
{}
set()
```

Everything else usually truthy.

---
# Example

```
name = ""
if name:    
   print("Exists")
else:    
   print("Empty")
```

Output:

```
Empty
```

---
# DYNAMIC TYPING

Python is:
# dynamically typed

---
# Meaning

Variable type can change.

```
x = 10
x = "Hello"
```

Valid.

---
# BUT TYPES STILL EXIST

Python is:
# dynamically typed

NOT:
# typeless

Huge difference.

---
# TYPE HINTS

Modern Python uses typing heavily.

Example:

```
name: str = "Harshit"
age: int = 24
```

---
# Function Typing

```
def add(a: int, b: int) -> int:    
    return a + b
```

---
# WHY IMPORTANT?

For:
- readability
- IDE support
- scalability
- static checking

Very important in production Python.

---
# TYPE CHECKING

---
# type()

```
print(type(10))
```

---
# isinstance()

BETTER approach.

```
print(isinstance(10, int))
```

Output:

```
True
```

---
# WHY isinstance() IS BETTER

Works with:
- inheritance
- OOP
- polymorphism

Professional approach.

---
# MEMORY UNDERSTANDING

Variables in Python:
# store references to objects

NOT raw values directly.

Example:

```
a = [1, 2]
b = a
```

Now both reference same list.

---
# Example

```
b.append(3)
print(a)
```

Output:

```
[1, 2, 3]
```

VERY important concept.

---
# PYTHON OBJECT MODEL

Everything in Python is:
# object

Even:
- int
- string
- function

---
# Example

```
print(type(10))
```

Output:

```
<class 'int'>
```

Even integers are objects.

Huge Python philosophy.