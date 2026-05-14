Strings are one of the MOST IMPORTANT data types in Python.

You’ll use strings everywhere:
- APIs
- user input
- database data
- authentication
- logging
- JSON
- URLs
- file handling
- backend responses

A huge part of backend engineering is basically:
# processing strings correctly

---
# WHAT IS A STRING?

A string is:
# sequence of characters

Example:

```
name = "Harshit"
```

Here:

```
H a r s h i t
```

is a sequence of characters.

---
# STRING CREATION

---
# Double Quotes

```
name = "Harshit"
```

---
# Single Quotes

```
city = 'Delhi'
```

Both work same.

---
# Triple Quotes

Used for multiline strings.

```
text = """HelloWorld"""
```

---
# WHY TRIPLE QUOTES ARE IMPORTANT

Used heavily for:
- SQL queries
- multiline messages
- documentation
- templates

---
# STRING TYPE

```
name = "Harshit"
print(type(name))
```

Output:

```
<class 'str'>
```

---
# STRINGS ARE IMMUTABLE

This is one of the MOST IMPORTANT string concepts.
# Immutable means:

cannot change original string.

---
# Example

```
name = "Harshit"
name[0] = "M"
```

ERROR.

---
# WHY?

Python strings are immutable objects.

---
# What actually happens?

When you "modify" string:

```
name = "Harshit"
name = "Mohit"
```

Python creates:
# new string object

instead of changing old one.

---
# STRING INDEXING

VERY IMPORTANT.

Strings are sequences.

Each character has index.

---
# Example

```
name = "Harshit"
```

---
# Index Positions

```
H  a  r  s  h  i  t
0  1  2  3  4  5  6
```

---
# Access Character

```
print(name[0])
```

Output:

```
H
```

---
# Another Example

```
print(name[3])
```

Output:

```
s
```

---
# NEGATIVE INDEXING

VERY IMPORTANT.

Python supports reverse indexing.

---
# Example

```
H  a  r  s  h  i  t
-7 -6 -5 -4 -3 -2 -1
```

---

# Example

```
print(name[-1])
```

Output:

```
t
```

---
# WHY NEGATIVE INDEXING IS POWERFUL

Very useful for:
- file extensions
- parsing
- backend processing

Example:

```
filename = "photo.png"
print(filename[-3:])
```

Output:

```
png
```

---
# STRING SLICING

Slicing means:
# extracting part of string

---
# Syntax

```
[start:end]
```

End excluded.

---
# Example

```
name = "Harshit"
print(name[0:4])
```

Output:

```
Hars
```

---
# WHY?

Because:
- start included
- end excluded

So:

```
0 → 3
```

---
# More Examples

---
## From index 2 onward

```
print(name[2:])
```

Output:

```
rshit
```

---
## Beginning to index 4

```
print(name[:4])
```

Output:

```
Hars
```

---
## Entire String

```
print(name[:])
```

---
# STEP SLICING

VERY IMPORTANT.

Syntax:

```
[start:end:step]
```

---
# Example

```
print(name[::2])
```

Output:

```
Hrh t
```

Actually:

```
Hrht
```

Because every second character.

---
# Reverse String

VERY famous Python trick.

```
print(name[::-1])
```

Output:

```
tihsraH
```

---
# STRING CONCATENATION

Joining strings.

---
# Example

```
first = "Harshit"last = "Kumar"
full = first + " " + last
print(full)
```

Output:

```
Harshit Kumar
```

---
# STRING REPETITION

```
print("Hi " * 3)
```

Output:

```
Hi Hi Hi
```

---
# STRING LENGTH

VERY IMPORTANT.

Use:

```
len()
```

---
# Example

```
name = "Harshit"
print(len(name))
```

Output:

```
7
```

---
# STRING METHODS

These are EXTREMELY important.

---
# 1. upper()

Converts to uppercase.

```
name = "harshit"
print(name.upper())
```

Output:

```
HARSHIT
```

---
# 2. lower()

```
name = "HARSHIT"
print(name.lower())
```

Output:

```
harshit
```

---
# USE CASE

Case-insensitive comparison.

```
user_input = "Admin"
if user_input.lower() == "admin":   
   print("Matched")
```

Very common in backend systems.

---
# 3. strip()

VERY IMPORTANT.

Removes spaces from ends.

```
text = "   hello   "print(text.strip())
```

Output:

```
hello
```

---
# WHY IMPORTANT?

User input often contains extra spaces.

---
# 4. lstrip()

Left spaces remove.

---
# 5. rstrip()

Right spaces remove.

---
# 6. replace()

VERY useful.

```
text = "Hello World"
print(text.replace("World", "Python"))
```

Output:

```
Hello Python
```

---
# 7. split()

Used heavily in backend development.

Splits string into list.

---
# Example

```
text = "apple,banana,mango"
print(text.split(","))
```

Output:

```
['apple', 'banana', 'mango']
```

---
# WHY split() IS HUGE

Used in:
- CSV parsing
- tokenization
- APIs
- logs
- URLs

---
# 8. join()

Opposite of split().

---
# Example

```
arr = ["apple", "banana", "mango"]
result = ",".join(arr)
print(result)
```

Output:

```
apple,banana,mango
```

---
# WHY join() MATTERS

Efficient string building.

---
# IMPORTANT PERFORMANCE FACT

This is BAD:

```
text = ""
for i in range(1000):    
    text += "a"
```

Because strings immutable.

---
# Better:

```
arr = []
for i in range(1000):    
    arr.append("a")
    text = "".join(arr)
```

Much more efficient.

Very important performance concept.

---
# 9. startswith()

```
filename = "photo.png"
print(filename.startswith("photo"))
```

---
# 10. endswith()

```
print(filename.endswith(".png"))
```

Very common in backend/file handling.

---
# 11. find()

Returns index.

```
text = "Hello World"
print(text.find("World"))
```

Output:

```
6
```

---
# If not found

```
print(text.find("Python"))
```

Output:

```
-1
```

---
# 12. count()

```
text = "banana"
print(text.count("a"))
```

Output:

```
3
```

---
# 13. isdigit()

VERY useful validation method.

```
num = "123"
print(num.isdigit())
```

Output:

```
True
```

---
# 14. isalpha()

```
name = "Harshit"
print(name.isalpha())
```

---
# 15. isalnum()

Checks:
- alphabet
- numeric

---
# MEMBERSHIP OPERATOR

Very useful.

```
text = "Hello World"
print("World" in text)
```

Output:

```
True
```

---
# STRING COMPARISON

```
print("abc" == "abc")
```

---
# IMPORTANT

String comparison is:
# case-sensitive

```
print("Admin" == "admin")
```

Output:

```
False
```

---
# F-STRINGS (SUPER IMPORTANT)

Modern Python formatting.

---
# Example

```
name = "Harshit"
age = 24
print(f"My name is {name} and I am {age}")
```

---
# Expressions inside f-string

```
a = 10b = 20
print(f"Sum = {a + b}")
```

---
# WHY F-STRINGS ARE IMPORTANT

They are:
- readable
- fast
- modern

Used heavily everywhere.

---
# ESCAPE CHARACTERS

---
# New Line

```
print("Hello\nWorld")
```

---
# Tab

```
print("Hello\tWorld")
```

---
# Quotes Inside String

```
print("He said \"Hello\"")
```

---
# RAW STRINGS

VERY useful for:
- regex
- file paths

---
# Example

```
path = r"C:\newfolder\test"
```

Without raw string:

```
\n
```

becomes newline accidentally.