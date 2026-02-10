# Python Interview Questions

This document contains a curated list of Python interview questions, covering a range of topics from basic to advanced. Use these questions to prepare for Python interviews or to test your knowledge.

## Quick Access Table
| Section           | Link                                         |
|-------------------|----------------------------------------------|
| Basics            | [Go to Basics](#basics)                      |
| Intermediate      | [Go to All Intermediate Questions](#all-intermediate-questions) |
| Advanced          | [Go to Advanced Topics](#advanced-topics)    |
| Coding Challenges | [Go to Coding Challenges](#code-challenges)|

---

## Basics
Absolutely! Let's dive into some **Python basics interview questions** with thorough explanations, so you not only know the answer but also understand **why** it works that way. I’ll start from core concepts and go deeper as we go.

---

### **1. What is Python and what are its key features?**

**Answer:**
Python is a high-level, interpreted, general-purpose programming language. It is dynamically typed and emphasizes readability.

**Key Features:**

* **Interpreted**: Python code is executed line by line, which makes debugging easier.
* **Dynamically Typed**: No need to declare variable types explicitly. Types are determined at runtime.
* **High-level**: Python abstracts complex details like memory management.
* **Object-oriented**: Supports classes, objects, inheritance, and encapsulation.
* **Extensive Libraries**: Libraries like NumPy, pandas, requests, and TensorFlow are available.
* **Cross-platform**: Works on Windows, Linux, and Mac.
* **Readable Syntax**: Easy to read and maintain.

**Deep Explanation:**
Python's interpreted nature means it uses an **interpreter**, not a compiler, so you can run scripts directly. Dynamic typing allows flexibility but requires careful coding to avoid runtime type errors. Its design philosophy emphasizes readability (“**There should be one—and preferably only one—obvious way to do it**”).

---

### **2. What are Python’s data types?**

**Answer:**
Python has several built-in data types:

* **Numeric types**: `int`, `float`, `complex`
* **Sequence types**: `list`, `tuple`, `range`
* **Text type**: `str`
* **Set types**: `set`, `frozenset`
* **Mapping type**: `dict`
* **Boolean type**: `bool`
* **None type**: `NoneType`

**Deep Explanation:**
Each data type is an object in Python. For example, `a = 5` is an object of type `int`. You can check type with `type(a)`. Python’s flexibility allows mixing types, but operations are type-specific.

Example:

```python
a = 5
b = 3.2
print(a + b)  # Output: 8.2 (int + float = float)
```

---

### **3. What is the difference between a list and a tuple?**

| Feature     | List                      | Tuple           |
| ----------- | ------------------------- | --------------- |
| Mutable     | Yes                       | No              |
| Syntax      | `[1, 2, 3]`               | `(1, 2, 3)`     |
| Methods     | Many (`append`, `remove`) | Few (immutable) |
| Performance | Slower                    | Faster          |

**Deep Explanation:**

* Lists are **mutable**, meaning you can change elements after creation. Tuples are **immutable**, meaning once created, they cannot be changed.
* Tuples are faster for iteration and safer for fixed data (like coordinates).
* Immutability is useful for dictionary keys, function arguments (hashable types), and preventing accidental modification.

---

### **4. What is Python’s `pass`, `continue`, and `break`?**

* **`pass`**: Does nothing; used as a placeholder.
* **`break`**: Exits the nearest enclosing loop.
* **`continue`**: Skips the current iteration and moves to the next.

```python
for i in range(5):
    if i == 2:
        continue
    if i == 4:
        break
    print(i)
# Output: 0, 1, 3
```

**Deep Explanation:**

* `pass` is useful when defining a function/class temporarily.
* `break` stops a loop entirely.
* `continue` is used when a certain condition should skip that iteration. They control flow in loops efficiently.

---

### **5. What is Python’s `*args` and `**kwargs`?**

* `*args` → collects **positional arguments** as a tuple.
* `**kwargs` → collects **keyword arguments** as a dictionary.

```python
def demo(*args, **kwargs):
    print("args:", args)
    print("kwargs:", kwargs)

demo(1, 2, 3, name="Alice", age=25)
# Output:
# args: (1, 2, 3)
# kwargs: {'name': 'Alice', 'age': 25}
```

**Deep Explanation:**

* `*args` allows functions to accept **variable positional arguments**, useful for flexible APIs.
* `**kwargs` allows **named parameters** dynamically, often used in configuration or passing options.
* Both can be combined for maximum flexibility in function design.

---

### **6. How does Python manage memory?**

**Answer:**
Python uses **automatic memory management** via:

1. **Reference Counting**: Every object keeps track of references. When count drops to 0, memory is freed.
2. **Garbage Collector**: Handles **cyclic references** that reference counting can’t free.

```python
import gc
print(gc.isenabled())  # True
```

**Deep Explanation:**

* Example of a cycle:

```python
a = []
b = [a]
a.append(b)
# Both a and b reference each other
del a
del b
# Garbage collector frees memory
```

Python abstracts memory handling, but developers should avoid unnecessary large objects to prevent memory pressure.

---

### **7. Difference between `is` and `==`**

* **`==`** checks **value equality**.
* **`is`** checks **object identity** (whether two references point to the same object).

```python
a = [1,2]
b = [1,2]
print(a == b)  # True (same content)
print(a is b)  # False (different objects)
```

**Deep Explanation:**

* `is` is often used for singletons like `None`: `if x is None:`
* `==` can be overridden in classes via `__eq__`.

---

### **8. What are Python’s scopes and namespaces?**

**Scopes (LEGB Rule):**

1. **Local** – inside a function
2. **Enclosing** – nested functions
3. **Global** – module-level variables
4. **Built-in** – Python built-ins

**Example:**

```python
x = "global"

def outer():
    x = "enclosing"
    def inner():
        x = "local"
        print(x)
    inner()

outer()  # Output: local
```

**Deep Explanation:**
Python uses a **LEGB lookup** to resolve variable names. Understanding this is crucial for debugging and designing functions that modify variables in the correct scope.

---

### **9. Explain Python’s `with` statement**

**Answer:**
Used for **resource management**, like files or network connections. It ensures proper cleanup.

```python
with open("file.txt", "r") as f:
    data = f.read()
# File automatically closed
```

**Deep Explanation:**

* Behind the scenes, `with` calls `__enter__` when entering and `__exit__` when leaving.
* Prevents memory leaks or unclosed files, which is safer than manual open/close.

---

### **10. What are Python decorators?**

**Answer:**
Decorators are **functions that modify other functions** or methods.

```python
def decorator(func):
    def wrapper():
        print("Before function")
        func()
        print("After function")
    return wrapper

@decorator
def say_hello():
    print("Hello!")

say_hello()
```

**Output:**

```
Before function
Hello!
After function


### **11. How do you comment in Python?**

**Answer:**

* Single-line comment: `# This is a comment`
* Multi-line comment: Use triple quotes (`''' comment '''` or `""" comment """`)

**Deep Explanation:**

* Single-line comments are ignored by the interpreter.
* Triple quotes are technically multi-line **strings**, but if not assigned, they act as comments.
* Comments improve code readability and are essential for maintainable code.

```python
# This prints hello
print("Hello")  

"""
This is a multi-line comment
explaining what the code does
"""
```

---

### **12. What are Python variables and how are they assigned?**

**Answer:**
Variables are **names that reference objects**. Python variables don’t need explicit declaration.

```python
x = 10      # integer
y = "Hello" # string
z = 3.5     # float
```

**Deep Explanation:**

* Python variables **point to objects in memory**, unlike languages that store values directly.
* Variable types are inferred automatically, and reassignment can change type dynamically.

```python
x = 10      # int
x = "Hello" # now str
```

---

### **13. What are Python operators?**

**Answer:**
Operators perform operations on variables and values.

* **Arithmetic**: `+ - * / % ** //`
* **Comparison**: `== != > < >= <=`
* **Logical**: `and, or, not`
* **Assignment**: `= += -= *= /=`
* **Membership**: `in, not in`
* **Identity**: `is, is not`

**Deep Explanation:**

* `**` is exponentiation, `//` is floor division (returns integer).
* `and/or` return the **last evaluated value**, not always True/False.
* `is` compares object identity (memory), `==` compares value equality.

---

### **14. What is the difference between mutable and immutable objects?**

| Feature      | Mutable (can change) | Immutable (cannot change) |
| ------------ | -------------------- | ------------------------- |
| Examples     | list, dict, set      | str, tuple, int, float    |
| Modification | Allowed              | Not allowed               |
| Memory usage | Can change in place  | New object created        |

**Deep Explanation:**

* Lists can be updated: `lst[0] = 10`
* Strings are immutable: `s = "hi"` → `s[0] = "H"` gives an error
* Immutables are safe as dictionary keys, for caching, and for concurrency.

---

### **15. How do you swap two variables in Python?**

**Answer:**
Python allows **tuple unpacking**:

```python
a = 5
b = 10
a, b = b, a
print(a, b)  # 10 5
```

**Deep Explanation:**

* Behind the scenes, Python creates a tuple `(b, a)` and unpacks it to `(a, b)`.
* No temporary variable is needed, unlike in C or Java.
* This is concise and idiomatic Python.

---

### **16. What is Python’s `None`?**

**Answer:**
`None` is a **special constant representing the absence of a value**.

```python
x = None
if x is None:
    print("x is empty")
```

**Deep Explanation:**

* `None` is an object of type `NoneType`.
* Used for default function arguments, uninitialized variables, or return value when nothing is returned.
* Always compare with `is None`, not `== None`.

---

### **17. How do Python functions work?**

**Answer:**
Functions are reusable blocks of code defined with `def`:

```python
def add(a, b):
    return a + b

print(add(2, 3))  # 5
```

**Deep Explanation:**

* Functions improve modularity and readability.
* They can take positional, keyword, default, `*args`, and `**kwargs` arguments.
* Functions are **first-class objects** in Python, meaning they can be passed around like variables.

---

### **18. What is the difference between `return` and `yield`?**

* **`return`**: Ends the function and returns a value.
* **`yield`**: Returns a generator object, producing values lazily.

```python
def gen_numbers():
    for i in range(3):
        yield i

for n in gen_numbers():
    print(n)
# Output: 0 1 2
```

**Deep Explanation:**

* `yield` allows **lazy evaluation**, saving memory when dealing with large sequences.
* Useful in iterators, streams, or pipelines.
* `return` is final and exits the function.

---

### **19. What are Python strings and how do you manipulate them?**

**Answer:**
Strings are **immutable sequences of characters**.

```python
s = "Python"
print(s.upper())   # PYTHON
print(s.lower())   # python
print(s.replace("P", "J"))  # Jython
```

**Deep Explanation:**

* Strings can’t be changed in-place; methods return new strings.
* Supports slicing: `s[0:3]` → `"Pyt"`
* Supports concatenation: `s + " rocks"` → `"Python rocks"`

---

### **20. What is the difference between `==` and `is`?**

I actually covered this earlier, but it’s **very common in basics**:

* `==` → checks **value equality**
* `is` → checks **object identity** (memory address)

```python
a = [1,2]
b = [1,2]
print(a == b)  # True
print(a is b)  # False
```

---
Absolutely! We can go even deeper for each concept to make it truly interview-ready and practical. Let me expand **21–50** with more detailed explanations, practical tips, and examples. I’ll start with the first few to show the style, then we can continue consistently for all.

---

### **21. What are Python lists and how do you use them?**

**Answer:**
Lists are **ordered, mutable sequences** that can store any data type, including other lists. They are one of Python’s most versatile data structures.

```python
lst = [1, "hello", 3.5, [7, 8]]
lst.append(10)          # Adds an element at the end
lst.insert(1, "world")  # Insert at index 1
lst.remove(3.5)         # Remove by value
print(lst)              # [1, 'world', 'hello', [7, 8], 10]
```

**Deep Explanation:**

* **Mutable:** You can update, delete, or insert elements without creating a new list.
* **Indexing:** Lists support positive and negative indexing:

  ```python
  print(lst[0])   # First element
  print(lst[-1])  # Last element
  ```
* **Slicing:** Extract sublists efficiently:

  ```python
  print(lst[1:4])  # ['world', 'hello', [7, 8]]
  ```
* **Iteration:** Can loop over elements:

  ```python
  for item in lst:
      print(item)
  ```
* **Common methods:**

  * `append()` – add single element
  * `extend()` – add multiple elements
  * `pop()` – remove by index and return element
  * `sort()` – sort elements (works only if types are compatible)
  * `reverse()` – reverse the list

**Interview Tip:** Lists are the go-to for dynamic collections. Show understanding of mutability, indexing, slicing, and common methods.

---

### **22. What are Python tuples and how do you use them?**

**Answer:**
Tuples are **ordered, immutable sequences**. Once created, you cannot change their elements.

```python
t = (1, 2, 3, "Python")
print(t[0])    # 1
a, b, c, d = t  # Unpacking
print(a, b)    # 1 2
```

**Deep Explanation:**

* **Immutable:** You cannot add, remove, or modify elements. Attempting to do so raises `TypeError`.
* **Performance:** Slightly faster than lists; useful for fixed collections.
* **Use in dictionaries:** Can be used as keys because they are immutable.
* **Nested tuples:** Can contain other tuples or lists:

  ```python
  t2 = ((1,2), (3,4))
  print(t2[1][0])  # 3
  ```
* **Common methods:**

  * `count()` – count occurrences of a value
  * `index()` – find the first index of a value

**Interview Tip:** Highlight immutability, unpacking, and performance benefits compared to lists.

---

### **23. How do you perform slicing in Python?**

**Answer:**
Slicing allows you to **extract a part of a sequence** (list, tuple, string) using `[start:stop:step]`.

```python
lst = [0, 1, 2, 3, 4, 5]
print(lst[1:4])   # [1, 2, 3]
print(lst[:3])    # [0, 1, 2]
print(lst[::2])   # [0, 2, 4]
print(lst[::-1])  # [5, 4, 3, 2, 1, 0] (reverse)
```

**Deep Explanation:**

* `start` – index to start (inclusive)
* `stop` – index to end (exclusive)
* `step` – step size, negative for reverse
* Negative indices count from the end: `lst[-1]` → last element
* Important: Slicing **creates a new sequence**; original remains unchanged

**Interview Tip:** Know slicing for strings and lists; reversing with `[::-1]` is a common trick question.

---

### **24. What are Python dictionaries?**

**Answer:**
Dictionaries are **unordered, mutable key-value pairs** for fast data lookup.

```python
d = {"name": "Alice", "age": 25}
print(d["name"])  # Alice
d["city"] = "Delhi"
print(d.get("country", "Not Found"))  # Not Found
```

**Deep Explanation:**

* Keys must be **immutable** (`str`, `int`, `tuple`), values can be any type.
* Fast **O(1) lookup** using keys.
* Useful for **JSON-like data** structures.
* Methods:

  * `keys()`, `values()`, `items()`
  * `pop(key)` – remove key and return value
  * `update()` – merge dictionaries
* Iteration:

  ```python
  for key, value in d.items():
      print(key, value)
  ```

**Interview Tip:** Be ready to explain **hashing**, uniqueness of keys, and dictionary comprehension:

```python
squared = {x: x*x for x in range(5)}
print(squared)  # {0:0,1:1,2:4,3:9,4:16}

### **25. What are Python sets?**

**Answer:**
Sets are **unordered collections of unique items**, useful for membership tests and mathematical set operations.

```python
s = {1, 2, 3, 3}
print(s)  # {1, 2, 3} duplicates removed

s.add(4)
s.remove(2)
print(s)  # {1, 3, 4}

# Set operations
a = {1,2,3}
b = {3,4,5}
print(a.union(b))        # {1,2,3,4,5}
print(a.intersection(b)) # {3}
print(a.difference(b))   # {1,2}
```

**Deep Explanation:**

* **Unordered:** Elements have no index; cannot access by position.
* **Unique elements:** Duplicates are automatically removed.
* **Mutable vs Immutable:** `set()` is mutable, `frozenset()` is immutable.
* **Performance:** Excellent for **membership tests** (`x in s`) – O(1) average case.

**Interview Tip:** Be prepared to explain **why sets are faster than lists for membership testing**. Using sets to **remove duplicates** from lists is a common coding trick:

```python
lst = [1,2,2,3,3,3]
unique = list(set(lst))
print(unique)  # [1,2,3]
```

---

### **26. Difference between `append()` and `extend()` in a list**

**Answer:**

```python
lst = [1,2]
lst.append([3,4])
print(lst)  # [1,2,[3,4]]

lst2 = [1,2]
lst2.extend([3,4])
print(lst2) # [1,2,3,4]
```

**Deep Explanation:**

* `append(obj)` – Adds the **entire object** as a single element at the end.
* `extend(iterable)` – Iterates over the iterable and adds each element individually.
* **Use Case:**

  * `append` → when adding one object, e.g., a sublist or a number.
  * `extend` → when merging lists.

**Interview Tip:** Confusing `append` vs `extend` is a classic trap; demonstrate both with examples.

---

### **27. What is Python list comprehension?**

**Answer:**
A **concise way to create lists** from iterables, optionally with conditions.

```python
lst = [x*x for x in range(5)]
print(lst)  # [0,1,4,9,16]

even = [x for x in range(10) if x % 2 == 0]
print(even)  # [0,2,4,6,8]
```

**Deep Explanation:**

* **Readable & efficient** alternative to loops.
* Can **include multiple loops**:

```python
pairs = [(x,y) for x in [1,2] for y in [3,4]]
print(pairs)  # [(1,3),(1,4),(2,3),(2,4)]
```

* Works with **lists, sets, dictionaries**:

```python
squared_dict = {x:x*x for x in range(5)}
print(squared_dict)  # {0:0,1:1,2:4,3:9,4:16}
```

**Interview Tip:** Be ready to explain **nested comprehensions**, conditionals, and differences from traditional loops.

---

### **28. What is a Python lambda function?**

**Answer:**
A **small anonymous function** defined using `lambda`.

```python
add = lambda x, y: x + y
print(add(2,3))  # 5

# With map
nums = [1,2,3]
doubled = list(map(lambda x: x*2, nums))
print(doubled)  # [2,4,6]
```

**Deep Explanation:**

* Can have **any number of arguments** but **only one expression**.
* Common use cases:

  * `map()` – transform lists
  * `filter()` – filter elements
  * `sorted()` – custom sorting

```python
words = ["apple","banana","kiwi"]
words_sorted = sorted(words, key=lambda x: len(x))
print(words_sorted)  # ['kiwi','apple','banana']
```

**Interview Tip:** Lambda functions are widely used in **functional programming** within Python. Know when to use **lambda vs def**.

---

### **29. How does Python handle exceptions?**

**Answer:**
Python uses **`try-except` blocks** to catch and handle errors gracefully.

```python
try:
    x = 1 / 0
except ZeroDivisionError as e:
    print("Error:", e)
finally:
    print("This always executes")
```

**Deep Explanation:**

* **`try`** – code that may raise exceptions
* **`except`** – handle specific or multiple exceptions
* **`else`** – executes if no exception occurred
* **`finally`** – always executes (cleanup)
* Avoids **program crashes** and allows graceful error recovery.

**Interview Tip:** Can be asked to **catch multiple exceptions** or create **custom exceptions**:

```python
class MyError(Exception):
    pass
```

---

### **30. Difference between `remove()`, `pop()`, and `del`**

```python
lst = [1,2,3,4]

lst.remove(2)  # removes by value
print(lst)     # [1,3,4]

val = lst.pop(0)  # removes by index and returns value
print(val)        # 1

del lst[1]        # deletes index, no return
print(lst)        # [3]
```

**Deep Explanation:**

* `remove(value)` – search and remove **first matching value**
* `pop(index)` – remove **by index**, returns removed element
* `del obj` – delete element or variable; can also delete slices
* Choosing correctly avoids **IndexError** or **ValueError**

**Interview Tip:** Discuss **time complexity**: `remove()` is O(n), `pop()` at the end is O(1).

---

### **31. What are Python boolean values?**

**Answer:**
`True` and `False` represent truth values. They are a subclass of `int`:

```python
x = 10
print(x > 5)  # True
print(True + True)  # 2
```

**Deep Explanation:**

* Used in **conditions, loops, and expressions**.
* Python treats **empty containers and zero** as `False`:

```python
bool([])   # False
bool([1])  # True
bool(0)    # False
bool(42)   # True
```

* Supports **logical operators**: `and`, `or`, `not`.

**Interview Tip:** Demonstrate boolean logic with **expressions** and explain **truthy/falsy** concepts.

---

### **32. What are Python modules and packages?**

**Answer:**

* **Module:** A single Python file (`.py`) containing functions, classes, or variables
* **Package:** A folder of modules with `__init__.py`

```python
# my_module.py
def hello():
    print("Hello Python")

import my_module
my_module.hello()  # Hello Python

from my_module import hello
hello()  # Hello Python
```

**Deep Explanation:**

* **Organizes code** and promotes **reusability**
* **Importing** allows using functions without redefining them
* **Standard library examples:** `math`, `os`, `json`
* Packages can be **nested**:

```
mypackage/
    __init__.py
    module1.py
    module2.py
```

**Interview Tip:** Be familiar with `import`, `from … import …`, `as` aliasing, and **module search paths (`sys.path`)**.

---

### **33. How to read and write files in Python?**

**Answer:**
Python handles file operations using built-in functions and **context managers**.

```python
# Writing
with open("file.txt", "w") as f:
    f.write("Hello World\n")

# Reading
with open("file.txt", "r") as f:
    content = f.read()
    print(content)
```

**Deep Explanation:**

* **Modes:**

  * `"r"` – read (default)
  * `"w"` – write (overwrite)
  * `"a"` – append
  * `"rb"` / `"wb"` – binary mode
* **`with` statement** – automatically closes the file, even if exceptions occur
* **Line iteration:**

```python
with open("file.txt") as f:
    for line in f:
        print(line.strip())
```

**Interview Tip:** Common questions include **reading large files efficiently** and **writing CSV/JSON data** using `csv` and `json` modules.

---

### **34. What are Python built-in data structures?**

**Answer:**
Python provides four core built-in data structures:

* **List** → ordered, mutable
* **Tuple** → ordered, immutable
* **Set** → unordered, unique elements
* **Dictionary** → key-value pairs

**Deep Explanation:**

* **Choosing the right structure** affects performance and readability:

  * **List** – dynamic sequences
  * **Tuple** – fixed collections, can be dict keys
  * **Set** – fast membership tests, removes duplicates
  * **Dict** – fast lookups by key, flexible data mapping
* **Memory & Performance:** Tuples are lighter than lists; sets/dicts use hashing for O(1) lookup.

**Interview Tip:** Often asked to **choose the optimal structure** for a problem (e.g., remove duplicates → set, preserve order → list).

---

### **35. What is Python slicing on strings?**

**Answer:**
Strings are **immutable sequences**, and slicing extracts a part of the string.

```python
s = "Python"
print(s[0:4])   # Pyth
print(s[-3:])   # hon
print(s[::-1])  # nohtyP (reverse)
```

**Deep Explanation:**

* **Syntax:** `[start:stop:step]`
* **Immutable:** Slicing **returns a new string**, original remains unchanged
* **Practical use:** Reversing strings, substring extraction, skipping characters

```python
s = "abcdefgh"
print(s[::2])  # aceg
```

* Works on **lists and tuples** similarly.

**Interview Tip:** Be ready to explain negative indexing and reversing strings efficiently.
Great! Let’s continue with **Python interview questions 36–50**, keeping the same deep explanations, practical examples, and interview insights.

---

### **36. How do you check type in Python?**

**Answer:**
Python provides `type()` and `isinstance()` to check an object’s type.

```python
x = 10
print(type(x))          # <class 'int'>
print(isinstance(x, int))  # True
print(isinstance(x, (int, float)))  # True
```

**Deep Explanation:**

* **`type(obj)`** → returns the exact type of the object.
* **`isinstance(obj, type_or_tuple)`** → checks if the object **is an instance of the class or subclass**, supports multiple types via tuple.
* **Use Case:** Useful in **type validation, dynamic function arguments, and debugging**.

**Interview Tip:** Know difference between `type()` vs `isinstance()`. `isinstance()` is preferred for **OOP polymorphism checks**.

---

### **37. What are Python keywords?**

**Answer:**
Keywords are **reserved words** with special meaning in Python; you cannot use them as variable names.

```python
import keyword
print(keyword.kwlist)  # ['False', 'None', 'True', 'and', 'as', ...]
```

**Deep Explanation:**

* Examples: `if, else, for, while, def, class, lambda, try, except`
* Keywords **define the syntax** of Python, e.g., `for` is used for iteration, `def` for defining functions.
* **Dynamic check:** `keyword.iskeyword("while")` → True

**Interview Tip:** Be ready to **identify keywords vs identifiers**; using a keyword as a variable is a common beginner error.

---

### **38. What is Python `range()`?**

**Answer:**
`range()` generates a sequence of numbers. Often used in loops.

```python
print(list(range(5)))       # [0,1,2,3,4]
print(list(range(1,10,2)))  # [1,3,5,7,9]
```

**Deep Explanation:**

* **Parameters:** `range(start, stop, step)`
* Generates numbers **lazily** (efficient for large ranges)
* Can use negative steps for reverse sequences:

```python
print(list(range(5,0,-1)))  # [5,4,3,2,1]
```

* Works well with `for` loops and comprehensions.

**Interview Tip:** Expect **questions on range() vs list(range())** and **negative steps** for interview coding questions.

---

### **39. Difference between deep copy and shallow copy**

**Answer:**
Shallow copy duplicates the **outer object only**, deep copy duplicates **everything recursively**.

```python
import copy

lst = [[1,2],[3,4]]
shallow = copy.copy(lst)
deep = copy.deepcopy(lst)

lst[0][0] = 100
print(shallow)  # [[100,2],[3,4]] – inner list affected
print(deep)     # [[1,2],[3,4]] – completely independent
```

**Deep Explanation:**

* **Shallow copy (`copy.copy`)** – new outer object; inner objects **still reference the original**
* **Deep copy (`copy.deepcopy`)** – duplicates all nested objects
* Important for **nested lists, dicts, or objects** to avoid accidental side effects.

**Interview Tip:** Can be asked to explain **mutability and references** in nested structures.

---

### **40. What is Python `pass`?**

**Answer:**
`pass` is a **null statement**; it does nothing.

```python
def func():
    pass  # placeholder for future code

class MyClass:
    pass
```

**Deep Explanation:**

* **Use Case:** Placeholder in **loops, functions, or classes**
* Allows code to **compile without implementation**.
* Often used in **stub methods** during development.

**Interview Tip:** Recognize that `pass` is different from `None` (which is a value) and `...` (ellipsis).

---

### **41. What is Python `id()`?**

**Answer:**
Returns the **unique identity (memory address)** of an object.

```python
x = 10
y = 10
print(id(x) == id(y))  # True, same object in memory
z = [1,2]
print(id(z))  # Unique memory address
```

**Deep Explanation:**

* Helps understand **object identity vs equality**.
* Used with `is` operator:

```python
print(x is y)  # True
print(x == y)  # True
```

* Mutable objects like lists often have **different ids even if values are equal**.

**Interview Tip:** Questions may test **`is` vs `==`** understanding.

---

### **42. What is Python `help()`?**

**Answer:**
Displays **documentation** for modules, functions, and classes.

```python
help(str)
help(len)
```

**Deep Explanation:**

* Interactive way to explore Python objects
* Shows **methods, parameters, and docstrings**
* Can be used in REPL for **quick reference without leaving Python**

**Interview Tip:** Useful for **self-learning and debugging**; often mentioned in Python best practices.

---

### **43. What is Python `dir()`?**

**Answer:**
Returns **list of attributes and methods** of an object.

```python
print(dir([]))  # ['append', 'clear', 'copy', 'count', 'extend', ...]
print(dir(str))
```

**Deep Explanation:**

* **Introspection tool** – explore what an object can do
* Works on **modules, classes, objects, and instances**
* Helps discover **hidden/private methods** with `_` prefix

**Interview Tip:** Knowing `dir()` and `help()` demonstrates **Pythonic debugging skills**.

---

### **44. What is Python `enumerate()`?**

**Answer:**
Adds **index while iterating** over a sequence.

```python
lst = ["a", "b", "c"]
for i, val in enumerate(lst):
    print(i, val)
# Output:
# 0 a
# 1 b
# 2 c
```

**Deep Explanation:**

* Avoids manual **counter variables**
* Can specify **start index**: `enumerate(lst, start=1)` → indices start from 1
* Common in **loops where both index and value are needed**

**Interview Tip:** Often asked in **list iteration coding questions** to simplify index tracking.

---

### **45. What is Python `zip()`?**

**Answer:**
Combines multiple iterables **element-wise**.

```python
a = [1,2]
b = ["x","y"]
print(list(zip(a,b)))  # [(1,'x'),(2,'y')]

# Unpacking back
nums, letters = zip(*zip(a,b))
print(nums, letters)  # (1,2) ('x','y')
```

**Deep Explanation:**

* Stops at the **shortest iterable**
* Useful in **pairing, creating dictionaries, or looping multiple sequences**

```python
students = ["Alice", "Bob"]
marks = [85, 90]
grades = dict(zip(students, marks))
print(grades)  # {'Alice':85,'Bob':90}
```

**Interview Tip:** Frequently tested in **iterable manipulation problems**.

---

### **46. How do Python’s `all()` and `any()` work?**

**Answer:**
Check boolean conditions over iterables.

```python
print(all([True, True]))  # True
print(all([True, False])) # False

print(any([False, False, True])) # True
print(any([]))  # False
```

**Deep Explanation:**

* **`all(iterable)`** → True if **all elements** are truthy
* **`any(iterable)`** → True if **any element** is truthy
* Works with **list comprehensions, generator expressions**:

```python
nums = [2,4,6]
print(all(n%2==0 for n in nums))  # True
```

**Interview Tip:** Often asked in **validation, filtering, or condition-checking scenarios**.

---

### **47. Difference between `is` and `==`**

**Answer:**

* `==` → checks **value equality**
* `is` → checks **object identity**

```python
a = [1,2]
b = [1,2]
print(a == b)  # True
print(a is b)  # False
```

**Deep Explanation:**

* `is` → True only if both refer to the **same memory location**
* `==` → True if **values are equal**, even for different objects
* Key for understanding **mutability and references**

**Interview Tip:** Classic Python question. Always explain with **lists vs numbers vs strings**.

---

### **48. What are Python’s logical operators?**

**Answer:**
Python supports `and`, `or`, `not` for boolean logic.

```python
x = True
y = False
print(x and y)  # False
print(x or y)   # True
print(not x)    # False
```

**Deep Explanation:**

* **Short-circuit evaluation**:

  * `and` → stops at first False
  * `or` → stops at first True
* Return **actual value** (not always True/False):

```python
print(0 and 5)  # 0
print(0 or 5)   # 5
```

* Useful in **conditions, default values, and validations**

**Interview Tip:** Expect questions on **short-circuiting behavior** and **truthy/falsy values**.

---

### **49. What is Python’s ternary operator?**

**Answer:**
A **compact if-else** expression.

```python
x = 10
result = "Even" if x%2==0 else "Odd"
print(result)  # Even
```

**Deep Explanation:**

* Syntax: `<value_if_true> if <condition> else <value_if_false>`
* Can be **nested**, but readability suffers:

```python
y = 5
result = "Positive" if y>0 else "Zero" if y==0 else "Negative"
```

* Useful for **inline assignments** and **return statements**

**Interview Tip:** Avoid overly complex nesting in real code; concise expressions are preferred.

---

### **50. What are Python’s `globals()` and `locals()`?**

**Answer:**
Return **dictionaries representing namespaces**.

```python
x = 10
print(globals())  # global namespace

def func():
    y = 20
    print(locals())  # local namespace

func()
```

**Deep Explanation:**

* `globals()` → all variables in the **global scope**
* `locals()` → all variables in the **current local scope**
* Use Cases: **dynamic evaluation, debugging, introspection, or executing code dynamically**

```python
for name, val in globals().items():
    if not name.startswith("_"):
        print(name, val)
```

**Interview Tip:** Questions may involve **dynamic variable creation or inspecting runtime variables**.







## Intermediate Python topics
Absolutely! Let’s move into **intermediate Python questions 51–75** with **deep explanations, practical examples, and interview-ready insights**. 


### **51. What is Python OOP and why is it used?**

**Answer:**
Python supports **Object-Oriented Programming (OOP)**, allowing you to model real-world entities as **objects** with attributes and behaviors.

```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    def drive(self):
        print(f"{self.brand} {self.model} is driving")

c = Car("Toyota", "Corolla")
c.drive()  # Toyota Corolla is driving
```

**Deep Explanation:**

* **Class:** Blueprint for objects.
* **Object/Instance:** Concrete implementation of a class.
* **Attributes:** Variables associated with an object.
* **Methods:** Functions associated with an object.
* **Use Case:** Organizes code, promotes reusability, supports **encapsulation, inheritance, and polymorphism**.

**Interview Tip:** Be ready to explain **OOP principles** with Python examples.

---

### **52. What is `self` in Python classes?**

**Answer:**
`self` refers to the **current instance of the class**. It allows access to **attributes and methods** of the object.

```python
class Person:
    def __init__(self, name):
        self.name = name

    def greet(self):
        print(f"Hello, {self.name}")

p = Person("Alice")
p.greet()  # Hello, Alice
```

**Deep Explanation:**

* `self` is **explicit in Python**, unlike other languages where it’s implicit.
* Used in **instance methods** to access or modify object data.
* Must be **first parameter** in instance methods.

**Interview Tip:** Questions often test **why self is required** and how it differentiates between class and instance variables.

---

### **53. Difference between class variables and instance variables**

```python
class Dog:
    species = "Canine"  # Class variable
    def __init__(self, name):
        self.name = name  # Instance variable

d1 = Dog("Buddy")
d2 = Dog("Charlie")
print(d1.species, d2.species)  # Canine Canine
print(d1.name, d2.name)        # Buddy Charlie
```

**Deep Explanation:**

* **Class variable:** Shared among all instances
* **Instance variable:** Unique to each object
* **Use Case:** Class variables store **common data**, instance variables store **object-specific data**

**Interview Tip:** Be ready for scenarios where **modifying a class variable affects all instances**.

---

### **54. What is inheritance in Python?**

```python
class Animal:
    def speak(self):
        print("Some sound")

class Dog(Animal):
    def speak(self):
        print("Woof")

d = Dog()
d.speak()  # Woof
```

**Deep Explanation:**

* Allows a class to **inherit properties and methods** from another class.
* **Single inheritance** → one parent
* **Multiple inheritance** → multiple parents
* **super()** → access parent class methods
* Supports **code reuse and polymorphism**.

**Interview Tip:** Prepare to explain **MRO (Method Resolution Order)** in multiple inheritance.

---

### **55. What is encapsulation in Python?**

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # Private variable

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance

acc = BankAccount(1000)
acc.deposit(500)
print(acc.get_balance())  # 1500
```

**Deep Explanation:**

* **Encapsulation:** Hides data inside a class
* Private variables: `__var` (name mangled)
* Accessed via **getter/setter methods**
* Protects **object integrity**

**Interview Tip:** Often asked along with **abstraction**: hiding implementation while exposing interface.

---

### **56. What is polymorphism in Python?**

**Answer:**

* **Polymorphism** → “many forms”
* Same interface, different behavior

```python
class Cat:
    def speak(self):
        print("Meow")

class Dog:
    def speak(self):
        print("Woof")

for animal in [Cat(), Dog()]:
    animal.speak()  # Meow Woof
```

**Deep Explanation:**

* Supports **method overriding** (runtime polymorphism)
* Works with **duck typing**: if an object behaves like the expected type, it’s acceptable

**Interview Tip:** Be ready to explain **overloading vs overriding in Python**, noting Python does not support traditional method overloading.

---

### **57. What are Python decorators?**

**Answer:**
A decorator is a **function that modifies another function**.

```python
def decorator(func):
    def wrapper():
        print("Before function")
        func()
        print("After function")
    return wrapper

@decorator
def say_hello():
    print("Hello")

say_hello()
# Before function
# Hello
# After function
```

**Deep Explanation:**

* Can **add functionality** without modifying original function
* Common use cases: logging, authentication, memoization
* Decorators can be **nested** and accept **arguments**

**Interview Tip:** Be able to **explain `@decorator` syntax** vs manually wrapping: `say_hello = decorator(say_hello)`.

---

### **58. What are Python generators?**

```python
def my_gen():
    for i in range(3):
        yield i

g = my_gen()
print(next(g))  # 0
print(next(g))  # 1
```

**Deep Explanation:**

* **Generators** produce **items lazily**, one at a time
* Created using `yield` keyword
* Memory efficient for **large datasets**
* Can be **iterated using `for` loops**

**Interview Tip:** Expect questions like **difference between list and generator comprehension**:

```python
# List comprehension
lst = [x*x for x in range(5)]  # memory used: list of 5 items
# Generator comprehension
gen = (x*x for x in range(5))  # memory efficient
```

---

### **59. Difference between iterator and iterable**

```python
lst = [1,2,3]      # Iterable
it = iter(lst)     # Iterator

print(next(it))    # 1
print(next(it))    # 2
```

**Deep Explanation:**

* **Iterable:** Can return an iterator (`__iter__`)
* **Iterator:** Has `__next__` method to fetch next item
* Generators are **iterators**
* Iterators support **lazy evaluation**

**Interview Tip:** Understand **creating custom iterators** with `__iter__` and `__next__`.

---

### **60. What is Python `__init__` method?**

* **`__init__`** initializes an object when it’s created.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

p = Person("Alice", 25)
print(p.name)  # Alice
```

**Deep Explanation:**

* Called **automatically** on object creation
* Can assign **default parameters**
* Used for **setting up instance variables**


### **61. What is Python `__str__` and `__repr__`?**

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        return f"Person(name={self.name}, age={self.age})"

    def __repr__(self):
        return f"Person('{self.name}', {self.age})"

p = Person("Alice", 25)
print(str(p))  # Person(name=Alice, age=25)
print(repr(p)) # Person('Alice', 25)
```

**Deep Explanation:**

* `__str__` → Human-readable string representation
* `__repr__` → Developer-focused representation (can be used to recreate the object)
* Used in **printing, debugging, and logging**

**Interview Tip:** Know the difference and when each is called (`print()` calls `__str__`, interactive shell calls `__repr__`).

---

### **62. What are Python magic methods?**

**Answer:**
Special methods that allow you to **define behavior of built-in operations**.

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

v1 = Vector(1,2)
v2 = Vector(3,4)
v3 = v1 + v2
print(v3.x, v3.y)  # 4 6
```

**Deep Explanation:**

* Also called **dunder methods** (`__init__`, `__add__`, `__len__`, `__getitem__`)
* Customize **arithmetic, comparison, iteration, string conversion**
* Crucial for **operator overloading and custom data structures**

**Interview Tip:** Questions often involve **operator overloading** with magic methods.

---

### **63. How to handle exceptions in Python?**

```python
try:
    x = 1 / 0
except ZeroDivisionError as e:
    print("Error:", e)
except Exception as e:
    print("General error:", e)
finally:
    print("Cleanup code")
```

**Deep Explanation:**

* **try-except** → catch errors
* **finally** → always executes
* **else** → runs if no exception
* Custom exceptions:

```python
class MyError(Exception):
    pass

raise MyError("Something went wrong")
```

**Interview Tip:** Be ready to explain **multiple except blocks and exception hierarchy**.

---

### **64. What are Python context managers and `with` statement?**

```python
with open("file.txt", "w") as f:
    f.write("Hello World")
```

**Deep Explanation:**

* Ensures **resource cleanup**, e.g., closing files
* `with` internally calls `__enter__` and `__exit__`
* Custom context manager:

```python
class MyContext:
    def __enter__(self):
        print("Enter")
        return self
    def __exit__(self, exc_type, exc_val, exc_tb):
        print("Exit")

with MyContext() as c:
    print("Inside block")
```

**Interview Tip:** Often asked in **file handling and resource management** questions.

---

### **65. What are Python modules and packages?**

```python
# my_module.py
def greet():
    print("Hello")

import my_module
my_module.greet()  # Hello
```

**Deep Explanation:**

* **Module:** Single Python file
* **Package:** Directory with `__init__.py`
* Promotes **code reuse and organization**
* `sys.path` → search path for imports
* Can import specific functions: `from module import func`

**Interview Tip:** Know **relative imports, aliasing with as**, and **standard library examples**.

---

### **66. What is Python `__dict__`?**

```python
class Person:
    def __init__(self, name):
        self.name = name

p = Person("Alice")
print(p.__dict__)  # {'name': 'Alice'}
```

**Deep Explanation:**

* `__dict__` → dictionary of object attributes
* Can **dynamically inspect and modify** attributes
* Useful for **debugging, serialization, or dynamic attribute assignment**

**Interview Tip:** Often asked with **dynamic attribute setting**: `setattr(obj, 'attr', value)`.

---

### **67. Difference between shallow copy and deep copy**

```python
import copy
lst = [[1,2],[3,4]]
shallow = copy.copy(lst)
deep = copy.deepcopy(lst)

lst[0][0] = 100
print(shallow)  # [[100,2],[3,4]]
print(deep)     # [[1,2],[3,4]]
```

**Deep Explanation:**

* Shallow copy → copies outer object, inner objects **shared**
* Deep copy → copies everything recursively
* Critical in **nested lists, dicts, and object copying**

**Interview Tip:** Common in **mutable vs immutable object handling**.

---

### **68. What are Python iterators and generators?**

```python
# Iterator
lst = [1,2,3]
it = iter(lst)
print(next(it))  # 1

# Generator
def gen():
    for i in range(3):
        yield i

g = gen()
print(list(g))  # [0,1,2]
```

**Deep Explanation:**

* **Iterable** → object that can return an iterator
* **Iterator** → object with `__next__`
* **Generator** → iterator created using `yield`, memory efficient

**Interview Tip:** Can be asked to **write custom iterators** with `__iter__` and `__next__`.

---

### **69. What is Python `map()`, `filter()`, and `reduce()`?**

```python
from functools import reduce

nums = [1,2,3,4]

# map
squared = list(map(lambda x: x**2, nums))  # [1,4,9,16]

# filter
even = list(filter(lambda x: x%2==0, nums))  # [2,4]

# reduce
sum_all = reduce(lambda x,y: x+y, nums)  # 10
```

**Deep Explanation:**

* **map()** → transform each element
* **filter()** → select elements meeting condition
* **reduce()** → cumulative computation
* Works well with **functional programming style**

**Interview Tip:** Expect **comparison with list comprehensions**.

---

### **70. What is Python `zip()` and `enumerate()`?**

```python
# zip
a = [1,2]
b = ["x","y"]
print(list(zip(a,b)))  # [(1,'x'),(2,'y')]

# enumerate
lst = ['a','b']
for idx, val in enumerate(lst, start=1):
    print(idx, val)
```

**Deep Explanation:**

* **zip()** → combines iterables element-wise
* **enumerate()** → adds index to iterable
* Useful in **pairing data, loops, and dictionary creation**

**Interview Tip:** Often used in **iterable processing and merging lists**.

---

### **71. Python `any()` vs `all()`**

```python
lst = [True, False, True]
print(any(lst))  # True
print(all(lst))  # False
```

**Deep Explanation:**

* **all()** → True if all elements are truthy
* **any()** → True if any element is truthy
* Supports **generator expressions** for memory efficiency

```python
nums = [2,4,6]
print(all(n%2==0 for n in nums))  # True
```

**Interview Tip:** Useful for **validating lists or conditions** in interview questions.

---

### **72. Difference between mutable and immutable objects**

```python
# Mutable
lst = [1,2]
lst.append(3)  # OK

# Immutable
tup = (1,2)
# tup[0] = 10  # Error
```

**Deep Explanation:**

* **Mutable** → can change after creation (list, dict, set)
* **Immutable** → cannot change (tuple, str, int)
* Impacts **copying, passing to functions, dictionary keys**

**Interview Tip:** Often asked with **function arguments and shared references**.

---

### **73. What are Python comprehensions?**

```python
# List comprehension
lst = [x*x for x in range(5)]  # [0,1,4,9,16]

# Dict comprehension
d = {x:x*2 for x in range(3)}  # {0:0,1:2,2:4}

# Set comprehension
s = {x*x for x in range(5)}    # {0,1,4,9,16}
```

**Deep Explanation:**

* Provides **concise, readable way** to create sequences
* Can include **conditions**: `[x for x in range(10) if x%2==0]`
* Memory-efficient with **generator comprehensions**: `(x*x for x in range(5))`

**Interview Tip:** Often used in **coding exercises to transform lists/dicts**.

---

### **74. Python `is` vs `==`**

```python
a = [1,2]
b = [1,2]
print(a == b)  # True (value)
print(a is b)  # False (identity)

x = 10
y = 10
print(x is y)  # True (same object)
```

**Deep Explanation:**

* `==` → compares **values**
* `is` → compares **object identities**
* Important for **mutable vs immutable types**

**Interview Tip:** Classic Python question to test **understanding references**.

---

### **75. Python `globals()` vs `locals()`**

```python
x = 10
print("Global:", globals().get('x'))  # 10

def func():
    y = 20
    print("Local:", locals())  # {'y': 20}

func()
```

**Deep Explanation:**

* **globals()** → dict of all global variables
* **locals()** → dict of all local variables
* Useful for **debugging, dynamic variable creation, or introspection**

**Interview Tip:** Often used with **dynamic code execution** or **debugging exercises**.


## Advanced Topics
### **76. What is Python multithreading?**

**Answer:** Python threads allow **concurrent execution** within a process.

```python
import threading
import time

def print_numbers():
    for i in range(5):
        print(i)
        time.sleep(0.5)

t1 = threading.Thread(target=print_numbers)
t2 = threading.Thread(target=print_numbers)

t1.start()
t2.start()
t1.join()
t2.join()
```

**Deep Explanation:**

* Threads **share memory space**, so **mutable objects** are shared.
* Python has **GIL (Global Interpreter Lock)** → only one thread executes Python bytecode at a time.
* Useful for **I/O-bound tasks**, e.g., network, file operations.
* **CPU-bound tasks** may require `multiprocessing` instead.

**Interview Tip:** Know difference between **threading vs multiprocessing** and when to use each.

---

### **77. What is Python multiprocessing?**

**Answer:** Run **processes concurrently** using multiple CPU cores.

```python
from multiprocessing import Process

def task(name):
    print(f"Process {name} started")

p1 = Process(target=task, args=("A",))
p2 = Process(target=task, args=("B",))
p1.start()
p2.start()
p1.join()
p2.join()
```

**Deep Explanation:**

* Each process has **its own memory space** → no GIL limitation
* Useful for **CPU-bound tasks**
* Supports **queues and pipes** for inter-process communication

**Interview Tip:** Be ready to explain **threading vs multiprocessing performance**.

---

### **78. What is Python async/await?**

```python
import asyncio

async def say_hello():
    await asyncio.sleep(1)
    print("Hello")

async def main():
    await asyncio.gather(say_hello(), say_hello())

asyncio.run(main())
```

**Deep Explanation:**

* Enables **asynchronous programming** → non-blocking I/O
* `async def` → defines a coroutine
* `await` → pauses coroutine until the awaited task completes
* Useful for **network requests, API calls, and high-concurrency programs**

**Interview Tip:** Know **difference between threading and async**; async is **single-threaded, non-blocking**.

---

### **79. What is Python serialization (pickle, json)?**

```python
import pickle, json

data = {'name':'Alice', 'age':25}

# Pickle
pkl = pickle.dumps(data)
obj = pickle.loads(pkl)

# JSON
js = json.dumps(data)
obj2 = json.loads(js)
```

**Deep Explanation:**

* **Serialization:** Convert object to byte stream or string
* **pickle** → Python-specific (supports custom objects)
* **json** → language-independent, human-readable
* Useful for **saving state, transmitting data, or caching**

**Interview Tip:** Know **security implications of pickle**; avoid untrusted data.

---

### **80. Python regular expressions (`re` module)**

```python
import re

text = "My email is test@example.com"
pattern = r'\S+@\S+'
match = re.search(pattern, text)
print(match.group())  # test@example.com

# Find all
emails = re.findall(pattern, text)
```

**Deep Explanation:**

* `re.match` → matches at start
* `re.search` → searches anywhere
* `re.findall` → returns all matches
* `re.sub` → replaces patterns
* Powerful for **validation, extraction, and text processing**

**Interview Tip:** Prepare **email, URL, or phone number pattern questions**.

---

### **81. What are Python metaclasses?**

```python
class Meta(type):
    def __new__(cls, name, bases, dct):
        dct['category'] = 'CustomClass'
        return super().__new__(cls, name, bases, dct)

class MyClass(metaclass=Meta):
    pass

print(MyClass.category)  # CustomClass
```

**Deep Explanation:**

* **Metaclasses** → class of a class
* Controls **class creation and behavior**
* Used in **ORMs, frameworks, and class validations**

**Interview Tip:** Be ready to explain **`type` vs metaclass** and custom class creation.

---

### **82. Python property decorator (`@property`)**

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def area(self):
        return 3.14 * self._radius ** 2

c = Circle(5)
print(c.area)  # 78.5
```

**Deep Explanation:**

* `@property` → create **read-only or computed attributes**
* Can also define **setter** with `@attribute.setter`
* Provides **encapsulation without changing API**

**Interview Tip:** Frequently asked with **getters/setters without explicit methods**.

---

### **83. Python `super()` function**

```python
class A:
    def greet(self):
        print("Hello from A")

class B(A):
    def greet(self):
        super().greet()
        print("Hello from B")

b = B()
b.greet()
```

**Deep Explanation:**

* `super()` → access **parent class methods or properties**
* Avoids **hardcoding parent class name**
* Important in **multiple inheritance and method resolution order (MRO)**

---

### **84. Python `__slots__` for memory optimization**

```python
class Point:
    __slots__ = ['x', 'y']
    def __init__(self, x, y):
        self.x = x
        self.y = y

p = Point(1,2)
# p.z = 3  # AttributeError
```

**Deep Explanation:**

* Limits allowed attributes → **reduces memory footprint**
* Useful for **large number of objects**
* Tradeoff → cannot add dynamic attributes

---

### **85. Python weak references (`weakref`)**

```python
import weakref

class MyClass:
    pass

obj = MyClass()
r = weakref.ref(obj)
print(r())  # <__main__.MyClass object>
del obj
print(r())  # None
```

**Deep Explanation:**

* **Weak references** → reference that **doesn’t prevent garbage collection**
* Useful in **caches or observer patterns**

---

### **86. Python memory management and garbage collection**

**Explanation:**

* Python uses **reference counting**
* **Cyclic garbage collector** handles circular references
* Functions: `gc.collect()`, `sys.getrefcount(obj)`
* Helps prevent **memory leaks**

**Interview Tip:** Expect **questions on mutable objects, circular references, and memory optimization**.

---

### **87. Python descriptors (`__get__`, `__set__`)**

```python
class Descriptor:
    def __get__(self, instance, owner):
        return instance._val
    def __set__(self, instance, value):
        instance._val = value

class MyClass:
    val = Descriptor()
    def __init__(self, v):
        self._val = v

m = MyClass(10)
print(m.val)  # 10
m.val = 20
print(m.val)  # 20
```

**Deep Explanation:**

* Descriptors control **attribute access**
* Base for `@property`, `@staticmethod`, `@classmethod`
* Used in **ORMs and frameworks**

---

### **88. Python `__call__` method**

```python
class Callable:
    def __call__(self, x):
        return x*x

obj = Callable()
print(obj(5))  # 25
```

**Deep Explanation:**

* Makes **objects callable like functions**
* Useful in **caching, function objects, or decorators**

---

### **89. Python `functools.lru_cache`**

```python
from functools import lru_cache

@lru_cache(maxsize=2)
def fib(n):
    if n < 2:
        return n
    return fib(n-1) + fib(n-2)

print(fib(10))  # 55
```

**Deep Explanation:**

* Decorator for **memoization / caching results**
* Reduces **repeated computations**
* Useful for **dynamic programming or expensive calculations**

---

### **90. Python `itertools` module**

```python
import itertools

# Infinite counter
for i in itertools.count(5):
    if i > 7:
        break
    print(i)  # 5,6,7

# Combinations
print(list(itertools.combinations([1,2,3], 2)))  # [(1,2),(1,3),(2,3)]
```

**Deep Explanation:**

* Provides **efficient iterators for combinatorics and sequences**
* Useful for **permutations, product, accumulate**
* Reduces **memory usage**

---

### **91. Python `contextlib` module**

```python
from contextlib import contextmanager

@contextmanager
def my_context():
    print("Enter")
    yield
    print("Exit")

with my_context():
    print("Inside")
```

**Deep Explanation:**

* Easier way to create **context managers**
* Wraps **resource allocation/release**
* Useful for **files, database connections, locks**

---

### **92. Python `asyncio` event loop**

```python
import asyncio

async def main():
    print("Start")
    await asyncio.sleep(1)
    print("End")

asyncio.run(main())
```

**Deep Explanation:**

* Event loop manages **asynchronous coroutines**
* Allows **non-blocking I/O**
* Often used in **web servers, API clients, and real-time apps**

---

### **93. Python `namedtuple`**

```python
from collections import namedtuple

Point = namedtuple('Point', ['x','y'])
p = Point(1,2)
print(p.x, p.y)  # 1 2
```

**Deep Explanation:**

* Lightweight, **immutable objects**
* Acts like class, but **memory-efficient**
* Useful for **structured data without full class overhead**

---

### **94. Python `dataclasses`**

```python
from dataclasses import dataclass

@dataclass
class Point:
    x: int
    y: int

p = Point(1,2)
print(p)  # Point(x=1, y=2)
```

**Deep Explanation:**

* Auto-generates `__init__`, `__repr__`, `__eq__`
* Useful for **POJOs (plain objects)**, reduces boilerplate
* Can combine with `frozen=True` for immutability

---

### **95. Python memoryview**

```python
data = bytearray(b"hello")
mv = memoryview(data)
mv[0] = 72  # H
print(data)  # b'Hello'
```

**Deep Explanation:**

* View of **memory buffer without copying**
* Useful for **large binary data**

---

### **96. Python GIL (Global Interpreter Lock)**

**Explanation:**

* Python **CPython implementation** has GIL → only one thread executes bytecode at a time
* Affects **CPU-bound multithreading**, not I/O-bound
* Multiprocessing avoids GIL

**Interview Tip:** Can be asked **why multithreading is not effective for CPU-bound tasks**.

---

### **97. Python metaprogramming**

* Modifying code **dynamically at runtime** using:

  * **Metaclasses**
  * **`type()`** to create classes dynamically
  * **`setattr` / `getattr` / `delattr`**

```python
MyClass = type('MyClass', (), {'x':5})
obj = MyClass()
print(obj.x)  # 5
```

**Deep Explanation:**

* Enables **frameworks like Django ORM**
* Dynamically create or modify classes

---

### **98. Python slots vs dataclasses**

* **`__slots__`** → memory optimization, prevents dynamic attributes
* **dataclasses** → auto-generated boilerplate, supports mutability/immutability
* Can combine for **memory-efficient structured objects**

---

### **99. Python weakref + caching**

```python
import weakref

cache = weakref.WeakValueDictionary()
class Data:
    def __init__(self, val):
        self.val = val

d = Data(10)
cache['d'] = d
print(cache['d'].val)  # 10
del d
print(list(cache.keys()))  # []
```

**Deep Explanation:**

* Weak references allow **automatic removal from cache**
* Useful in **memory-sensitive caching**

---

### **100. Python introspection**

```python
class Test:
    x = 10
    def method(self):
        pass

t = Test()
print(dir(t))          # attributes & methods
print(getattr(t,'x'))  # 10
print(hasattr(t,'y'))  # False
```

**Deep Explanation:**

* Python supports **examining objects at runtime**
* `dir()`, `getattr()`, `hasattr()`, `type()`, `isinstance()`
* Useful for **dynamic programming, frameworks, and debugging**

**Interview Tip:** Frequently asked in **dynamic frameworks or library design questions**.

---



---
## Coding Challenges
### **Challenge 1: Reverse a string**

**Problem:** Write a function that reverses a string without using the built-in `reversed()` function.

```python
def reverse_string(s):
    return s[::-1]  # slicing method

# Test
print(reverse_string("Python"))  # nohtyP
```

**Explanation:**

* `s[::-1]` → slice notation: start at end, move backwards
* Time complexity: O(n), Space complexity: O(n)

**Alternative (loop method):**

```python
def reverse_string_loop(s):
    result = ""
    for char in s:
        result = char + result
    return result

print(reverse_string_loop("Python"))  # nohtyP
```

---

### **Challenge 2: Check for palindrome**

**Problem:** Write a function to check if a string is a palindrome.

```python
def is_palindrome(s):
    s = s.lower().replace(" ", "")  # normalize string
    return s == s[::-1]

print(is_palindrome("Racecar"))  # True
print(is_palindrome("Python"))   # False
```

**Explanation:**

* Normalize string for case and spaces
* Compare with reversed string

**Alternative (two-pointer method):**

```python
def is_palindrome_two_pointer(s):
    s = s.lower().replace(" ", "")
    left, right = 0, len(s) - 1
    while left < right:
        if s[left] != s[right]:
            return False
        left += 1
        right -= 1
    return True
```

---

### **Challenge 3: Find factorial**

**Problem:** Write a function to calculate factorial of a number.

```python
def factorial(n):
    if n == 0 or n == 1:
        return 1
    return n * factorial(n - 1)

print(factorial(5))  # 120
```

**Explanation:**

* Recursive approach
* Base case: 0! = 1
* Time complexity: O(n), Space complexity: O(n) due to recursion stack

**Iterative version:**

```python
def factorial_iter(n):
    result = 1
    for i in range(2, n+1):
        result *= i
    return result
```

---

### **Challenge 4: Fibonacci sequence**

**Problem:** Generate first `n` Fibonacci numbers.

```python
def fibonacci(n):
    fib = [0, 1]
    for i in range(2, n):
        fib.append(fib[i-1] + fib[i-2])
    return fib[:n]

print(fibonacci(10))  # [0,1,1,2,3,5,8,13,21,34]
```

**Explanation:**

* Iterative solution using list
* Handles first two elements separately
* Recursive solution is less efficient (exponential time)

**Interview Tip:** Use **dynamic programming** for large n.

---

### **Challenge 5: Count vowels in a string**

**Problem:** Count the number of vowels in a string.

```python
def count_vowels(s):
    vowels = "aeiouAEIOU"
    return sum(1 for char in s if char in vowels)

print(count_vowels("Hello World"))  # 3
```

**Explanation:**

* Use generator expression with `sum()`
* Efficient and readable

---

### **Challenge 6: Find the largest element in a list**

**Problem:** Find the maximum value in a list without using `max()`.

```python
def find_max(lst):
    if not lst:
        return None
    maximum = lst[0]
    for num in lst:
        if num > maximum:
            maximum = num
    return maximum

print(find_max([3, 5, 2, 9, 1]))  # 9
```

**Explanation:**

* Initialize `maximum` with first element
* Iterate and compare each element

**Interview Tip:** Could also use **reduce()** for functional approach.

---

### **Challenge 7: Check if a number is prime**

**Problem:** Write a function to check if a number is prime.

```python
def is_prime(n):
    if n <= 1:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

print(is_prime(11))  # True
print(is_prime(15))  # False
```

**Explanation:**

* Check divisibility up to √n for efficiency
* Time complexity: O(√n)

---

### **Challenge 8: Remove duplicates from a list**

**Problem:** Remove duplicates while preserving order.

```python
def remove_duplicates(lst):
    seen = set()
    result = []
    for item in lst:
        if item not in seen:
            seen.add(item)
            result.append(item)
    return result

print(remove_duplicates([1,2,2,3,4,4,5]))  # [1,2,3,4,5]
```

**Explanation:**

* Use a set to track seen elements
* Preserve order using list

**Alternative (one-liner):**

```python
def remove_duplicates_one_liner(lst):
    return list(dict.fromkeys(lst))
```

---

### **Challenge 9: Find common elements in two lists**

**Problem:** Return the intersection of two lists.

```python
def common_elements(lst1, lst2):
    return list(set(lst1) & set(lst2))

print(common_elements([1,2,3],[2,3,4]))  # [2,3]
```

**Explanation:**

* Convert lists to sets → use `&` operator for intersection
* Time complexity: O(n + m), where n, m are list sizes

**Preserve order:**

```python
def common_elements_ordered(lst1, lst2):
    set2 = set(lst2)
    return [x for x in lst1 if x in set2]
```

---

### **Challenge 10: Flatten a nested list**

**Problem:** Flatten a list of lists into a single list.

```python
def flatten(lst):
    result = []
    for item in lst:
        if isinstance(item, list):
            result.extend(flatten(item))
        else:
            result.append(item)
    return result

nested = [1, [2, [3,4], 5], 6]
print(flatten(nested))  # [1,2,3,4,5,6]
```

**Explanation:**

* Recursive solution handles arbitrary nesting
* `isinstance(item, list)` checks for sublists
* Interviewers like **recursive list problems** to test logic



### **Challenge 11: Count the frequency of elements in a list**

**Problem:** Write a function to count how many times each element appears in a list.

```python
from collections import Counter

def count_frequency(lst):
    return dict(Counter(lst))

print(count_frequency([1,2,2,3,3,3]))  # {1:1, 2:2, 3:3}
```

**Deep Explanation:**

* `Counter` from `collections` makes counting easy and efficient
* Time complexity: O(n), space complexity: O(n)
* Useful for **word counts, voting, or element frequency**

**Alternative (manual):**

```python
def count_frequency_manual(lst):
    freq = {}
    for item in lst:
        freq[item] = freq.get(item, 0) + 1
    return freq
```

---

### **Challenge 12: Merge two dictionaries**

**Problem:** Merge two dictionaries into one.

```python
def merge_dicts(d1, d2):
    return {**d1, **d2}

dict1 = {'a': 1, 'b': 2}
dict2 = {'b': 3, 'c': 4}
print(merge_dicts(dict1, dict2))  # {'a':1, 'b':3, 'c':4}
```

**Deep Explanation:**

* `{**d1, **d2}` → dictionary unpacking (Python 3.5+)
* Later values override earlier ones
* Useful for **config merging, JSON updates, API data aggregation**

**Alternative (update method):**

```python
d1.update(d2)
```

---

### **Challenge 13: Transpose a matrix**

**Problem:** Transpose a 2D matrix (swap rows and columns).

```python
def transpose(matrix):
    return [list(row) for row in zip(*matrix)]

mat = [[1,2,3],[4,5,6]]
print(transpose(mat))  # [[1,4],[2,5],[3,6]]
```

**Deep Explanation:**

* `zip(*matrix)` → unpacks rows and zips them as columns
* Efficient and concise
* Useful in **data processing and linear algebra**

---

### **Challenge 14: Find second largest element in a list**

**Problem:** Return the second largest number.

```python
def second_largest(lst):
    unique = list(set(lst))
    if len(unique) < 2:
        return None
    unique.sort()
    return unique[-2]

print(second_largest([4,1,7,7,2]))  # 4
```

**Deep Explanation:**

* Remove duplicates first using `set()`
* Sort and pick the second last element
* Time complexity: O(n log n), space: O(n)

**Alternative (single pass):**

```python
def second_largest_single_pass(lst):
    first = second = float('-inf')
    for num in lst:
        if num > first:
            second = first
            first = num
        elif first > num > second:
            second = num
    return second
```

---

### **Challenge 15: Check if two strings are anagrams**

**Problem:** Determine if two strings have the same characters with the same counts.

```python
from collections import Counter

def are_anagrams(s1, s2):
    return Counter(s1) == Counter(s2)

print(are_anagrams("listen", "silent"))  # True
print(are_anagrams("hello", "world"))    # False
```

**Deep Explanation:**

* Use `Counter` to count character frequencies
* Efficient and readable
* Useful in **text processing, validation, and games**

---

### **Challenge 16: Remove all vowels from a string**

```python
def remove_vowels(s):
    return ''.join(c for c in s if c.lower() not in 'aeiou')

print(remove_vowels("Python Programming"))  # Pythn Prgrmmng
```

**Deep Explanation:**

* Use generator expression for efficiency
* Works for both uppercase and lowercase
* Common text-processing interview problem

---

### **Challenge 17: Find the missing number in a list of 1 to n**

**Problem:** List contains numbers from 1 to n with one missing.

```python
def find_missing_number(lst, n):
    total = n * (n + 1) // 2
    return total - sum(lst)

print(find_missing_number([1,2,4,5], 5))  # 3
```

**Deep Explanation:**

* Use **sum formula** of first n natural numbers
* O(n) time, O(1) space
* Efficient for **large datasets**

---

### **Challenge 18: Find duplicates in a list**

```python
def find_duplicates(lst):
    seen = set()
    duplicates = set()
    for item in lst:
        if item in seen:
            duplicates.add(item)
        else:
            seen.add(item)
    return list(duplicates)

print(find_duplicates([1,2,3,2,4,1]))  # [1,2]
```

**Deep Explanation:**

* Use a set to track seen elements
* Collect duplicates in another set to avoid repetition
* Common in **data cleaning**

---

### **Challenge 19: Rotate a list by k positions**

```python
def rotate_list(lst, k):
    k %= len(lst)  # handle k > len(lst)
    return lst[-k:] + lst[:-k]

print(rotate_list([1,2,3,4,5], 2))  # [4,5,1,2,3]
```

**Deep Explanation:**

* Slice notation handles rotation efficiently
* Time complexity: O(n), space: O(n)
* Useful in **queue simulation, cyclic data structures**

---

### **Challenge 20: Check if a list is sorted**

```python
def is_sorted(lst):
    return all(lst[i] <= lst[i+1] for i in range(len(lst)-1))

print(is_sorted([1,2,3,4]))  # True
print(is_sorted([1,3,2]))    # False
```

**Deep Explanation:**

* Use `all()` with generator expression for O(n) check
* Avoids creating extra lists
* Useful in **validation and optimization problems**

### **Challenge 21: Reverse words in a string**

**Problem:** Reverse the order of words in a sentence without reversing the words themselves.

```python
def reverse_words(sentence):
    words = sentence.split()
    return ' '.join(words[::-1])

print(reverse_words("Python is fun"))  # fun is Python
```

**Explanation:**

* `split()` → splits sentence into words
* `[::-1]` → reverses list
* `join()` → combines words back into a string
* Time complexity: O(n), Space complexity: O(n)

---

### **Challenge 22: Merge two sorted lists**

**Problem:** Merge two sorted lists into a single sorted list.

```python
def merge_sorted_lists(lst1, lst2):
    result = []
    i = j = 0
    while i < len(lst1) and j < len(lst2):
        if lst1[i] < lst2[j]:
            result.append(lst1[i])
            i += 1
        else:
            result.append(lst2[j])
            j += 1
    result.extend(lst1[i:])
    result.extend(lst2[j:])
    return result

print(merge_sorted_lists([1,3,5],[2,4,6]))  # [1,2,3,4,5,6]
```

**Explanation:**

* Two-pointer technique merges lists in **O(n+m) time**
* Efficient for large lists
* Classic problem for **interview sorting questions**

---

### **Challenge 23: Find the missing elements in a list**

**Problem:** Given two lists, find elements present in the first but missing in the second.

```python
def find_missing_elements(lst1, lst2):
    return list(set(lst1) - set(lst2))

print(find_missing_elements([1,2,3,4],[2,4]))  # [1,3]
```

**Explanation:**

* Convert lists to sets → difference operation
* Order is lost; if order matters, use:

```python
def find_missing_ordered(lst1, lst2):
    s2 = set(lst2)
    return [x for x in lst1 if x not in s2]
```

---

### **Challenge 24: Count words in a string**

```python
def count_words(sentence):
    words = sentence.split()
    return len(words)

print(count_words("Python is fun to learn"))  # 6
```

**Explanation:**

* `split()` separates by whitespace
* `len()` counts words
* Simple but frequently asked for **string parsing questions**

**Alternative (using regex for punctuation):**

```python
import re
def count_words_regex(sentence):
    return len(re.findall(r'\b\w+\b', sentence))
```

---

### **Challenge 25: Find all prime numbers up to n**

```python
def primes_upto_n(n):
    primes = []
    for num in range(2, n+1):
        for i in range(2, int(num**0.5)+1):
            if num % i == 0:
                break
        else:
            primes.append(num)
    return primes

print(primes_upto_n(10))  # [2,3,5,7]
```

**Explanation:**

* Check divisibility up to √num
* `else` after `for` executes if no `break` occurs
* Efficient for **small n**, for large n → Sieve of Eratosthenes

---

### **Challenge 26: Fibonacci using recursion**

```python
def fibonacci_recursive(n):
    if n <= 1:
        return n
    return fibonacci_recursive(n-1) + fibonacci_recursive(n-2)

print([fibonacci_recursive(i) for i in range(10)])  # [0,1,1,2,3,5,8,13,21,34]
```

**Explanation:**

* Classic **recursive problem**
* Time complexity: O(2^n) → inefficient for large n
* Use **memoization** for optimization

```python
from functools import lru_cache

@lru_cache(maxsize=None)
def fibonacci_memo(n):
    if n <= 1:
        return n
    return fibonacci_memo(n-1) + fibonacci_memo(n-2)
```

---

### **Challenge 27: Flatten a dictionary**

**Problem:** Convert nested dictionaries into a flat dictionary with compound keys.

```python
def flatten_dict(d, parent_key='', sep='.'):
    items = {}
    for k, v in d.items():
        new_key = f"{parent_key}{sep}{k}" if parent_key else k
        if isinstance(v, dict):
            items.update(flatten_dict(v, new_key, sep=sep))
        else:
            items[new_key] = v
    return items

nested = {'a':1, 'b':{'c':2,'d':3}}
print(flatten_dict(nested))  # {'a':1,'b.c':2,'b.d':3}
```

**Explanation:**

* Recursively traverse dictionary
* Build compound keys for nested levels
* Useful in **JSON processing and data normalization**

---

### **Challenge 28: Check balanced parentheses**

```python
def is_balanced(expr):
    stack = []
    pairs = {'(':')','[':']','{':'}'}
    for char in expr:
        if char in pairs:
            stack.append(char)
        elif char in pairs.values():
            if not stack or pairs[stack.pop()] != char:
                return False
    return not stack

print(is_balanced("({[]})"))  # True
print(is_balanced("({[})"))   # False
```

**Explanation:**

* Stack-based solution
* Push opening brackets, pop and match closing brackets
* Common in **compiler questions and expression validation**

---

### **Challenge 29: Find the most frequent element in a list**

```python
from collections import Counter

def most_frequent(lst):
    counter = Counter(lst)
    return counter.most_common(1)[0][0]

print(most_frequent([1,2,2,3,3,3]))  # 3
```

**Explanation:**

* `Counter.most_common(1)` returns **element with highest frequency**
* Time complexity: O(n)
* Useful in **analytics and data aggregation**

---

### **Challenge 30: Check if a list is a subset of another list**

```python
def is_subset(lst1, lst2):
    return set(lst1).issubset(set(lst2))

print(is_subset([1,2],[1,2,3]))  # True
print(is_subset([1,4],[1,2,3]))  # False
```

**Explanation:**

* Convert lists to sets → `issubset()`
* Efficient and readable
* Useful in **permission checks, validation, and data comparison**



### **Challenge 31: Find all subsets of a list**

**Problem:** Generate all possible subsets (power set) of a list.

```python
def subsets(lst):
    result = [[]]
    for elem in lst:
        result += [curr + [elem] for curr in result]
    return result

print(subsets([1,2,3]))
# [[], [1], [2], [1,2], [3], [1,3], [2,3], [1,2,3]]
```

**Explanation:**

* Start with empty subset
* For each element, add it to all existing subsets
* Time complexity: O(2^n), space complexity: O(2^n)
* Useful in **combinatorial problems**

---

### **Challenge 32: Implement binary search**

**Problem:** Search a number in a sorted list efficiently.

```python
def binary_search(lst, target):
    left, right = 0, len(lst)-1
    while left <= right:
        mid = (left + right) // 2
        if lst[mid] == target:
            return mid
        elif lst[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

print(binary_search([1,2,3,4,5], 3))  # 2
```

**Explanation:**

* Divide and conquer → halve search space each iteration
* Time complexity: O(log n), space: O(1)
* Classic algorithm question

---

### **Challenge 33: Find longest word in a string**

```python
def longest_word(s):
    words = s.split()
    return max(words, key=len)

print(longest_word("Python coding challenges are fun"))  # challenges
```

**Explanation:**

* `split()` separates words
* `max()` with `key=len` finds the longest
* Time complexity: O(n), where n = total characters

---

### **Challenge 34: Sum all numbers in a nested list**

```python
def sum_nested(lst):
    total = 0
    for item in lst:
        if isinstance(item, list):
            total += sum_nested(item)
        else:
            total += item
    return total

nested = [1, [2, [3,4], 5], 6]
print(sum_nested(nested))  # 21
```

**Explanation:**

* Recursive solution for arbitrary depth
* Common in **tree-like or nested data**

---

### **Challenge 35: Count occurrences of a substring**

```python
def count_substring(s, sub):
    return s.count(sub)

print(count_substring("ababa", "aba"))  # 1
```

**Explanation:**

* `str.count()` counts **non-overlapping occurrences**
* If overlapping is needed, use regex:

```python
import re
def count_overlapping(s, sub):
    return len(re.findall(f'(?={sub})', s))

print(count_overlapping("ababa", "aba"))  # 2
```

---

### **Challenge 36: Find common keys in two dictionaries**

```python
def common_keys(d1, d2):
    return list(d1.keys() & d2.keys())

d1 = {'a':1,'b':2}
d2 = {'b':3,'c':4}
print(common_keys(d1,d2))  # ['b']
```

**Explanation:**

* Set intersection on keys
* Efficient for **data comparison**

---

### **Challenge 37: Sort a dictionary by values**

```python
def sort_dict_by_value(d):
    return dict(sorted(d.items(), key=lambda item: item[1]))

d = {'a':3,'b':1,'c':2}
print(sort_dict_by_value(d))  # {'b':1,'c':2,'a':3}
```

**Explanation:**

* `sorted()` sorts items by **value** using `key`
* Convert back to dict
* Common in **ranking or analytics problems**

---

### **Challenge 38: Find first non-repeating character**

```python
from collections import Counter

def first_non_repeating(s):
    freq = Counter(s)
    for char in s:
        if freq[char] == 1:
            return char
    return None

print(first_non_repeating("swiss"))  # w
```

**Explanation:**

* Count frequencies → iterate in order → return first unique
* Time complexity: O(n)

---

### **Challenge 39: Implement a simple stack**

```python
class Stack:
    def __init__(self):
        self.items = []
    def push(self, item):
        self.items.append(item)
    def pop(self):
        return self.items.pop() if self.items else None
    def peek(self):
        return self.items[-1] if self.items else None
    def is_empty(self):
        return not self.items

stack = Stack()
stack.push(1)
stack.push(2)
print(stack.pop())  # 2
```

**Explanation:**

* Stack → LIFO (Last In First Out)
* Implemented with **list append/pop**
* Common in **algorithm and system design interviews**

---

### **Challenge 40: Implement a queue using list**

```python
class Queue:
    def __init__(self):
        self.items = []
    def enqueue(self, item):
        self.items.append(item)
    def dequeue(self):
        return self.items.pop(0) if self.items else None
    def is_empty(self):
        return not self.items

q = Queue()
q.enqueue(1)
q.enqueue(2)
print(q.dequeue())  # 1
```

**Explanation:**

* Queue → FIFO (First In First Out)
* `pop(0)` removes first element (O(n) → for large scale, use `collections.deque`)
* Common in **task scheduling and buffering**

### **Challenge 41: Remove duplicates from a string**

**Problem:** Remove duplicate characters while maintaining order.

```python
def remove_duplicates_string(s):
    seen = set()
    result = []
    for char in s:
        if char not in seen:
            seen.add(char)
            result.append(char)
    return ''.join(result)

print(remove_duplicates_string("banana"))  # "ban"
```

**Explanation:**

* `set()` tracks seen characters
* Maintain order by appending to a list
* Time complexity: O(n), space: O(n)
* Useful for **data cleaning and text normalization**

---

### **Challenge 42: Find the intersection of multiple lists**

```python
def intersect_lists(*lists):
    result = set(lists[0])
    for lst in lists[1:]:
        result &= set(lst)
    return list(result)

print(intersect_lists([1,2,3],[2,3,4],[3,5]))  # [3]
```

**Explanation:**

* Use set intersection iteratively for multiple lists
* Efficient for **finding common elements in datasets**

---

### **Challenge 43: Count the number of digits in a number**

```python
def count_digits(n):
    return len(str(abs(n)))

print(count_digits(12345))  # 5
print(count_digits(-987))   # 3
```

**Explanation:**

* Convert number to string → count characters
* `abs()` handles negative numbers
* Simple but common **basic interview question**

**Alternative (without converting to string):**

```python
def count_digits_math(n):
    n = abs(n)
    count = 0
    while n:
        n //= 10
        count += 1
    return count
```

---

### **Challenge 44: Find the missing numbers in a range**

**Problem:** Given a list and a range 1..n, find all missing numbers.

```python
def missing_numbers(lst, n):
    return [i for i in range(1, n+1) if i not in lst]

print(missing_numbers([2,3,7], 7))  # [1,4,5,6]
```

**Explanation:**

* List comprehension iterates over the full range
* Check membership with `not in`
* Time complexity: O(n*m), space: O(n)
* Can be optimized using **sets** for large n

```python
def missing_numbers_set(lst, n):
    return list(set(range(1,n+1)) - set(lst))
```

---

### **Challenge 45: Check if a string is a pangram**

**Problem:** A pangram contains all letters of the alphabet at least once.

```python
import string

def is_pangram(s):
    return set(string.ascii_lowercase).issubset(set(s.lower()))

print(is_pangram("The quick brown fox jumps over the lazy dog"))  # True
print(is_pangram("Python coding"))  # False
```

**Explanation:**

* Use `set` for uniqueness
* Check if alphabet is a subset
* Classic **text-processing interview question**

---

### **Challenge 46: Find the second most frequent element**

```python
from collections import Counter

def second_most_frequent(lst):
    counter = Counter(lst)
    most_common = counter.most_common()
    if len(most_common) < 2:
        return None
    return most_common[1][0]

print(second_most_frequent([1,2,2,3,3,3]))  # 2
```

**Explanation:**

* `Counter.most_common()` returns list sorted by frequency
* Pick second element for second highest frequency
* Useful in **analytics, ranking, and reporting**

---

### **Challenge 47: Rotate a matrix 90 degrees clockwise**

```python
def rotate_matrix(matrix):
    return [list(row)[::-1] for row in zip(*matrix)]

mat = [[1,2,3],[4,5,6],[7,8,9]]
print(rotate_matrix(mat))
# [[7,4,1],[8,5,2],[9,6,3]]
```

**Explanation:**

* `zip(*matrix)` → transposes rows and columns
* Reverse each row for clockwise rotation
* Time complexity: O(n^2), space: O(n^2)
* Classic **matrix manipulation problem**

---

### **Challenge 48: Implement a simple calculator**

```python
def calculator(a, b, operation):
    if operation == "add":
        return a + b
    elif operation == "sub":
        return a - b
    elif operation == "mul":
        return a * b
    elif operation == "div":
        return a / b if b != 0 else None
    else:
        return None

print(calculator(5,2,"add"))  # 7
print(calculator(5,0,"div"))  # None
```

**Explanation:**

* Conditional statements implement basic operations
* Handles division by zero
* Good for **OOP extension or command-based interview questions**

---

### **Challenge 49: Find the longest increasing subsequence**

```python
def longest_increasing_subseq(lst):
    if not lst:
        return 0
    dp = [1]*len(lst)
    for i in range(1,len(lst)):
        for j in range(i):
            if lst[i] > lst[j]:
                dp[i] = max(dp[i], dp[j]+1)
    return max(dp)

print(longest_increasing_subseq([10,9,2,5,3,7,101,18]))  # 4
```

**Explanation:**

* Dynamic programming solution
* `dp[i]` → length of LIS ending at i
* Time complexity: O(n^2)
* Common **algorithmic interview question**

---

### **Challenge 50: Count frequency of words in a paragraph**

```python
from collections import Counter
import re

def word_count(text):
    words = re.findall(r'\b\w+\b', text.lower())
    return dict(Counter(words))

paragraph = "Python is fun. Python is easy."
print(word_count(paragraph))
# {'python': 2, 'is': 2, 'fun': 1, 'easy': 1}
```

**Explanation:**

* Use regex to split words and ignore punctuation
* Convert to lowercase for normalization
* `Counter` for frequency counting
* Useful in **text analytics and NLP tasks**

