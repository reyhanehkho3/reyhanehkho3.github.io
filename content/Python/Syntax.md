---
title: Syntax
publish:
date created: 2026-07-21
tags:
  - python
  - syntax
---
### Curly Braces
```python
# Other languages:
if (x > 5) {
    doSomething();  // Braces define block
}

# Python:
if x > 5:
    do_something()      # 4 spaces (or 1 tab, but DON'T mix!)
    another_thing()     # Same indentation = same block
print("done")           # Dedented = outside if block
```

### For Loop and If condition
```python
if x > 5:
	for i in range(10):
```

```python
# if-elif-else (note: elif, not else if)
if score >= 90:
    grade = "A"
elif score >= 80:    # no "else if" — it's "elif"
    grade = "B"
else:
    grade = "F"

# while
i = 0
while i < 5:
    print(i)
    i += 1   # no i++

# for = foreach
for item in [1, 2, 3]:   # iterates over list elements
    print(item)

# If you need index:
for i, value in enumerate([10, 20, 30]):
    print(f"index {i}: {value}")
```

### And, Or and Not
```python
`and`, `or`, `not`
```

### Increment
We don't have `x++` or `++x`. We have `x += 1` or just `x = x + 1`.


### Everything is an Object

```python
# You can assign functions to variables
def greet(name):
    return f"Hello {name}"

say_hello = greet   # no parentheses!
print(say_hello("Alice"))  # works
```

### No `new` or `public/private/static`
```python
# Java: MyClass obj = new MyClass();
# Python:
obj = MyClass()   # just call the class

# No access modifiers — everything is "public" by convention.
# _name means "private, don't touch" (just a hint)
```


### Functions can return anything (or nothing)
```python
def add(a, b):
    return a + b   # returns int

def do_nothing():
    pass           # pass = no-op (like empty {})

def returns_multiple():
    return 1, 2, 3  # actually returns a TUPLE

x, y, z = returns_multiple()  # tuple unpacking — very common
```

```python
def greet(name: str) -> str:   # "name should be str, returns str"
    return f"Hello {name}"

# These ALL work (Python doesn't care):
greet("Alice")      #  works
greet(123)          #  works (no error!)
greet(["list"])     #  works
```

The `f` Before Strings = f-strings (Formatted Strings). **What it does:** Injects variables directly into strings.

```python
name = "Rex"
age = 3
# Old way (Java-like):
print("My dog " + name + " is " + str(age) + " years old")
# Python f-string (cleaner):
print(f"My dog {name} is {age} years old")
#                           ^^            ^^ variables go in { }
```

```python
x = 5
print(f"{x} squared is {x*x}")           # "5 squared is 25"
print(f"Pi is {3.14159:.2f}")            # "Pi is 3.14" (formatting)
print(f"{'hello'.upper()}")              # "HELLO" (call methods)
```

The `enumerate()` Function. **What it does:** Gives you both index AND value when looping.

```python
# Without enumerate (C/Java style):
items = [10, 20, 30]
i = 0
for value in items:
    print(f"index {i}: {value}")
    i += 1
# With enumerate (Pythonic):
for i, value in enumerate([10, 20, 30]):
 #  ^       ^                     ^
# index  value            list
    print(f"index {i}: {value}")
# Output:
# index 0: 10
# index 1: 20
# index 2: 30

```

```python
# Find index of an item
for i, value in enumerate(my_list):
    if value == target:
        print(f"Found at index {i}")
        break
```
### The Data Types That Confuse Java/C People

| C/Java concept   | Python equivalent           | Notes                                      |
| ---------------- | --------------------------- | ------------------------------------------ |
| Arrays           | `list` = `[1, 2, 3]`        | Mutable, can mix types `[1, "hello", 3.5]` |
| Fixed arrays     | `tuple` = `(1, 2, 3)`       | **Immutable** — like `final` array         |
| HashMaps / Dicts | `dict` = `{"key": "value"}` | `my_dict["key"]` or `my_dict.get("key")`   |
| `null`           | `None`                      | Capital N. `if x is None:` (not `==`)      |
| `boolean`        | `True`, `False`             | Capital T/F.                               |
Note:

```java
# This creates a reference, not a copy!
a = [1, 2, 3]
b = a        # b points to same list
b.append(4)
print(a)     # [1, 2, 3, 4]  ← a changed!

# To copy: b = a.copy() or b = a[:]
```


### List Comprehensions
```python
# Java-style:
squares = []
for x in range(10):
    squares.append(x*x)

# Pythonic:
squares = [x*x for x in range(10)]   # read: "make a list of x*x for each x in range"

# With condition:
evens = [x for x in range(20) if x % 2 == 0]
# Reads like English!
```


### The`with`Statement (Resource Management)

Instead of `try/finally` for files/sockets:
```python
# Java: try-with-resources
# Python:
with open("file.txt", "r") as f:
    content = f.read()
# File automatically closed when block exits — even on error.
```


### Classes
```python
class Dog:
    # Constructor (__init__ = initialize)
    def __init__(self, name):    # "self" = "this"
        self.name = name         # instance variable
        self._age = 0            # convention: private

    # Method
    def bark(self):
        print(f"{self.name} says woof!")

    # Static method (no self)
    @staticmethod
    def info():
        return "Dogs are mammals"

# Usage:
d = Dog("Rex")
d.bark()          # Rex says woof!
print(Dog.info()) # Dogs are mammals
```

- No interfaces, no abstract classes (unless you import `abc`).

### Imports
```
import math                    # math.sqrt(25)
from math import sqrt          # sqrt(25) — no prefix
from collections import defaultdict  # very common
import numpy as np             # alias (common for libraries)
```

### The 3 Most Confusing Things (With Fixes)

| Confusion            | Why                                                                        | Python way                                                                                 |
| -------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| **`==` vs `is`**     | `==` checks value, `is` checks identity (memory address)                   | Use `==` for equality. Use `is` only for `None`, `True`, `False`.                          |
| **Mutable defaults** | `def f(lst=[]):` reuses same list!                                         | Use `def f(lst=None):` and create new inside.                                              |
| **Variable scope**   | Functions can read outer vars but can't assign without `global`/`nonlocal` | If you assign to a variable inside a function, it's local. Use `global x` to modify outer. |

### Quick Cheat Sheet for Reading Python Code

| What you see                 | What it means                                                |
| ---------------------------- | ------------------------------------------------------------ |
| `if __name__ == "__main__":` | This file is being run directly (not imported)               |
| `*args, **kwargs`            | Variable-length arguments (`*` for list, `**` for dict)      |
| `lambda x: x*2`              | Anonymous function (like arrow functions in JS, but limited) |
| `@decorator`                 | A function that wraps another function (like annotations)    |
| `_` (single underscore)      | Convention: "I don't care about this value"                  |
| `x: int = 5`                 | **Type hint** (optional, not enforced) — just documentation  |
| `raise ValueError("msg")`    | Throws exception                                             |
#### `*args` and `**kwargs` — Variable Arguments
**What they do:** Let your function accept any number of arguments.
```python
# *args = "arguments" (tuple of positional args)
def sum_all(*args):
    total = 0
    for num in args:
        total += num
    return total
print(sum_all(1, 2, 3))        # 6
print(sum_all(10, 20, 30, 40)) # 100
# args is (1,2,3) or (10,20,30,40)
# **kwargs = "keyword arguments" (dict of named args)
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")
print_info(name="Alice", age=30, city="NYC")
# Output:
# name: Alice
# age: 30
# city: NYC
# kwargs is {"name": "Alice", "age": 30, "city": "NYC"}
```

```python
def greet(greeting, *names, **options):
    # greeting = required first param
    # *names = any number of additional args
    # **options = any number of named args
    print(greeting, names, options)

greet("Hello", "Alice", "Bob", excited=True)
# Hello ('Alice', 'Bob') {'excited': True}
```
### A simple example:
```python
def main():
    numbers = [1, 2, 3, 4, 5]
    total = 0
    for num in numbers:
        total += num
    print(f"Sum: {total}")

if __name__ == "__main__":
    main()
```



---
[[Python]]