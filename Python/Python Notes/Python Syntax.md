Python syntax is basically:
# “how Python code is written”

Since you already know JavaScript/TypeScript, the fastest way to learn Python syntax is by comparing it mentally with JS.

Python is:
- cleaner
- more readable
- indentation-based
- dynamically typed

---
# 1. PRINTING OUTPUT

In JS:

```
console.log("Hello")
```

In Python:

```
print("Hello")
```

---
# Example

```
print("Hello World")print(10)print(True)
```

---
# MULTIPLE VALUES

```
name = "Harshit"age = 24print(name, age)
```

Output:

```
Harshit 24
```

---
# 2. COMMENTS

Single line:

```
# this is comment
```

---
# Multiline

```
"""This is multiline comment"""
```

Technically this is a multiline string, but often used like comments/documentation.

---
# 3. VARIABLES

In JS:

```
let name = "Harshit"
```

In Python:

```
name = "Harshit"
```

No:
- let
- const
- var

Python automatically creates variable.

---
# IMPORTANT

Python is:
# dynamically typed

Meaning:

```
x = 10x = "hello"
```

Both valid.

---
# VARIABLE NAMING RULES

Allowed:

```
user_name = "Harshit"age2 = 24
```

Not allowed:

```
2age = 24
```

---
# Python convention

Use:
# snake_case

Example:

```
user_nametotal_price
```

NOT:

```
camelCase
```

---
# 4. INDENTATION (VERY IMPORTANT)

This is one of the BIGGEST syntax differences.

JS uses:

```
{}
```

Python uses:
# indentation

---
# JS

```
if (true) {   console.log("Hello")}
```

---
# Python

```
if True:    print("Hello")
```

---
# IMPORTANT RULES

After:

```
:
```

indentation starts.

Usually:

- 4 spaces

---
# WRONG

```
if True:print("Hello")
```

Error.

---
# CORRECT

```
if True:    print("Hello")
```

---
# Python uses indentation to define blocks.

This is CORE Python syntax.

# VERY IMPORTANT PYTHON SYNTAX DIFFERENCES FROM JS

| JavaScript        | Python      |
| ----------------- | ----------- |
| {} blocks         | indentation |
| ;                 | not needed  |
| let/const         | none        |
| true/false        | True/False  |
| null              | None        |
| && / \|           | and / or    |
| function          | def         |
| ===               | ==          |
| template literals | f-strings   |