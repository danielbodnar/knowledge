---
title: "Python Quick Reference"
topic: "Python"
category: "Development"
tags: [python, programming, cheatsheet, reference, syntax]
date_created: "2026-01-17"
last_updated: "2026-01-17"
---

# Python Cheatsheet

## Quick Reference

Essential Python syntax and commands.

### Basic Syntax

```python
# Variables
name = "Alice"
age = 30
pi = 3.14159
is_valid = True

# Print
print("Hello, World!")
print(f"Name: {name}, Age: {age}")

# Comments
# This is a comment
"""
Multi-line
comment
"""
```

## Data Types

| Type | Example | Description |
|------|---------|-------------|
| `int` | `42` | Integer |
| `float` | `3.14` | Floating point |
| `str` | `"hello"` | String |
| `bool` | `True/False` | Boolean |
| `list` | `[1, 2, 3]` | Ordered collection |
| `tuple` | `(1, 2, 3)` | Immutable list |
| `dict` | `{"key": "value"}` | Key-value pairs |
| `set` | `{1, 2, 3}` | Unique values |

## Control Flow

```python
# If-else
if age >= 18:
    print("Adult")
elif age >= 13:
    print("Teen")
else:
    print("Child")

# For loop
for i in range(5):
    print(i)

for item in [1, 2, 3]:
    print(item)

# While loop
count = 0
while count < 5:
    print(count)
    count += 1

# List comprehension
squares = [x**2 for x in range(10)]
even_squares = [x**2 for x in range(10) if x % 2 == 0]
```

## Functions

```python
# Basic function
def greet(name):
    return f"Hello, {name}!"

# Default arguments
def greet(name="World"):
    return f"Hello, {name}!"

# Multiple returns
def min_max(numbers):
    return min(numbers), max(numbers)

# Lambda
square = lambda x: x**2
add = lambda x, y: x + y

# *args and **kwargs
def func(*args, **kwargs):
    print(args)    # Tuple of positional args
    print(kwargs)  # Dict of keyword args
```

## Lists and Strings

```python
# List operations
lst = [1, 2, 3, 4, 5]
lst.append(6)           # Add to end
lst.insert(0, 0)        # Insert at index
lst.remove(3)           # Remove first occurrence
lst.pop()               # Remove and return last
lst.extend([7, 8])      # Add multiple items
lst.sort()              # Sort in place
sorted_lst = sorted(lst) # Return sorted copy

# List slicing
lst[0]      # First element
lst[-1]     # Last element
lst[1:4]    # Slice from index 1 to 3
lst[::2]    # Every second element
lst[::-1]   # Reverse list

# String operations
s = "Hello, World!"
s.lower()               # Lowercase
s.upper()               # Uppercase
s.strip()               # Remove whitespace
s.split(",")            # Split into list
"_".join(["a", "b"])    # Join list
s.replace("Hello", "Hi") # Replace
s.startswith("Hello")   # Check prefix
```

## Dictionaries

```python
# Create dictionary
person = {
    "name": "Alice",
    "age": 30,
    "city": "NYC"
}

# Access
person["name"]          # Get value
person.get("name", "")  # Get with default

# Modify
person["age"] = 31      # Update
person["email"] = "alice@example.com"  # Add

# Iterate
for key in person:
    print(key, person[key])

for key, value in person.items():
    print(f"{key}: {value}")

# Dictionary comprehension
squares = {x: x**2 for x in range(5)}
```

## File Operations

```python
# Read file
with open("file.txt", "r") as f:
    content = f.read()          # Read all
    lines = f.readlines()       # Read lines
    for line in f:              # Iterate lines
        print(line.strip())

# Write file
with open("file.txt", "w") as f:
    f.write("Hello\n")
    f.writelines(["Line 1\n", "Line 2\n"])

# Append
with open("file.txt", "a") as f:
    f.write("Appended text\n")

# JSON
import json

data = {"name": "Alice", "age": 30}
with open("data.json", "w") as f:
    json.dump(data, f, indent=2)

with open("data.json", "r") as f:
    data = json.load(f)
```

## Classes

```python
class Person:
    # Class variable
    species = "Homo sapiens"
    
    # Constructor
    def __init__(self, name, age):
        self.name = name    # Instance variable
        self.age = age
    
    # Method
    def greet(self):
        return f"Hi, I'm {self.name}"
    
    # String representation
    def __str__(self):
        return f"Person({self.name}, {self.age})"

# Inheritance
class Student(Person):
    def __init__(self, name, age, grade):
        super().__init__(name, age)
        self.grade = grade
```

## Exception Handling

```python
try:
    result = 10 / 0
except ZeroDivisionError as e:
    print(f"Error: {e}")
except Exception as e:
    print(f"Unexpected error: {e}")
else:
    print("No error occurred")
finally:
    print("Always executed")

# Raise exception
if age < 0:
    raise ValueError("Age cannot be negative")
```

## Common Built-in Functions

```python
# Type conversion
int("42")           # String to int
str(42)             # Int to string
float("3.14")       # String to float
list("abc")         # String to list

# Math
abs(-5)             # Absolute value
round(3.7)          # Round
max(1, 2, 3)        # Maximum
min(1, 2, 3)        # Minimum
sum([1, 2, 3])      # Sum

# Sequence
len([1, 2, 3])      # Length
range(5)            # 0 to 4
enumerate(lst)      # Index and value
zip(lst1, lst2)     # Combine lists

# Type checking
type(x)             # Get type
isinstance(x, int)  # Check type
```

## Tips & Tricks

- Use f-strings for formatting: `f"Value: {var}"`
- Use `enumerate()` instead of manual indexing
- Use `with` statements for file operations
- List comprehensions are faster than loops
- Use `is` for None checks: `if x is None:`
- Use `get()` for dictionary access with defaults
- Use `pathlib` for file path operations
- Virtual environments: `python -m venv venv`

## Common Patterns

```python
# Swap variables
a, b = b, a

# Multiple assignment
x, y, z = 1, 2, 3

# Ternary operator
value = "yes" if condition else "no"

# Check if key exists
if "key" in dictionary:
    pass

# Get or create
value = dictionary.setdefault("key", default_value)

# Merge dictionaries (Python 3.9+)
merged = dict1 | dict2

# Remove duplicates
unique = list(set(my_list))

# Flatten list
flat = [item for sublist in nested_list for item in sublist]
```

## Resources

- [Official Python Documentation](https://docs.python.org/3/)
- [Python Tutorial](https://docs.python.org/3/tutorial/)
- [PEP 8 Style Guide](https://pep8.org/)
- [Real Python](https://realpython.com/)
