# Lists

> **Lists are the most versatile and frequently used collection type in Python.**

---

# Learning Objectives

After completing this chapter, you will be able to:

- Understand what lists are
- Create and modify lists
- Access elements using indexing and slicing
- Add, remove, and update items
- Iterate through lists
- Use list methods effectively
- Understand mutability
- Compare Python lists with PHP arrays
- Apply lists in AI engineering projects
- Analyze time complexity of common operations

---

# Prerequisites

- Variables
- Data Types
- Operators
- Strings

---

# What is a List?

A **list** is an ordered, mutable collection that can store objects of different types.

Unlike strings, lists can be modified after they are created.

Example:

```python
languages = ["Python", "PHP", "Java"]
```

---

# Visual Representation

```
Index

0        1        2
┌────────┬────────┬────────┐
│Python  │ PHP    │ Java   │
└────────┴────────┴────────┘
```

---

# Why Lists Matter in AI

Lists appear everywhere in AI:

- Tokens
- Chat history
- Embedding chunks
- Search results
- Training data
- Prompt messages
- API responses

Example:

```python
messages = [
    {"role":"system","content":"You are helpful."},
    {"role":"user","content":"Explain RAG"}
]
```

---

# Creating Lists

## Empty List

```python
numbers = []
```

or

```python
numbers = list()
```

---

## List of Integers

```python
numbers = [10,20,30]
```

---

## Strings

```python
languages = [
    "Python",
    "PHP",
    "Java"
]
```

---

## Mixed Types

```python
employee = [
    "Ajit",
    50,
    True,
    62000.50
]
```

Although allowed, mixing unrelated types is generally discouraged unless there's a clear reason.

---

# List Length

```python
len(numbers)
```

Returns

```
3
```

---

# Accessing Elements

```python
languages[0]
```

Returns

```
Python
```

---

```python
languages[1]
```

Returns

```
PHP
```

---

Negative Index

```python
languages[-1]
```

Returns

```
Java
```

---

# Slicing

```python
languages[0:2]
```

Returns

```
['Python', 'PHP']
```

---

```python
languages[:2]
```

---

```python
languages[1:]
```

---

```python
languages[::-1]
```

Reverse order.

---

# Lists are Mutable

```python
languages = [
    "Python",
    "PHP",
    "Java"
]

languages[1] = "Rust"
```

Now

```
['Python', 'Rust', 'Java']
```

---

# Adding Elements

## append()

```python
languages.append("Go")
```

Result

```
Python
PHP
Java
Go
```

Time Complexity

```
O(1)
```

---

## insert()

```python
languages.insert(1, "C++")
```

Result

```
Python

C++

PHP

Java
```

Time Complexity

```
O(n)
```

---

## extend()

```python
backend = [
    "Python",
    "PHP"
]

frontend = [
    "React",
    "Vue"
]

backend.extend(frontend)
```

---

# Removing Items

## remove()

```python
languages.remove("PHP")
```

Removes by value.

---

## pop()

```python
languages.pop()
```

Removes last item.

---

```python
languages.pop(2)
```

Removes by index.

---

## del

```python
del languages[0]
```

---

## clear()

```python
languages.clear()
```

Now

```
[]
```

---

# Updating

```python
languages[0] = "Python 3"
```

---

# Searching

```python
"Python" in languages
```

Returns

```
True
```

---

```python
languages.index("Java")
```

Returns

```
2
```

---

```python
languages.count("Python")
```

---

# Sorting

```python
numbers.sort()
```

Ascending.

---

Descending

```python
numbers.sort(reverse=True)
```

---

Alphabetical

```python
languages.sort()
```

---

Reverse

```python
languages.reverse()
```

---

# Copying Lists

Wrong

```python
a = [1,2,3]

b = a
```

Both variables point to the same list.

Correct

```python
b = a.copy()
```

or

```python
b = list(a)
```

or

```python
b = a[:]
```

---

# Iteration

```python
for language in languages:
    print(language)
```

---

With Index

```python
for index, language in enumerate(languages):
    print(index, language)
```

---

# Nested Lists

```python
matrix = [
    [1,2],
    [3,4]
]
```

Access

```python
matrix[1][0]
```

Returns

```
3
```

---

# List Comprehension (Preview)

```python
numbers = [
    x*x
    for x in range(10)
]
```

We'll study comprehensions in depth later.

---

# Common List Methods

| Method | Purpose |
|----------|----------------|
| append() | Add item |
| extend() | Add collection |
| insert() | Insert |
| remove() | Remove value |
| pop() | Remove index |
| clear() | Empty list |
| sort() | Sort |
| reverse() | Reverse |
| copy() | Copy |
| index() | Find position |
| count() | Count values |

---

# Time Complexity

| Operation | Complexity |
|------------|------------|
| Index | O(1) |
| Append | O(1) |
| Insert | O(n) |
| Remove | O(n) |
| Search | O(n) |
| Sort | O(n log n) |

---

# Memory Diagram

```
languages

│

▼

┌─────────────────────────┐

Python

PHP

Java

└─────────────────────────┘
```

Variables reference list objects.

---

# AI Example

OpenAI Chat Messages

```python
messages = [
    {
        "role":"system",
        "content":"You are an AI tutor."
    },
    {
        "role":"user",
        "content":"Explain Lists."
    }
]
```

This is a list of dictionaries.

You'll see this pattern throughout AI development.

---

# PHP Comparison

PHP

```php
$users = [];
```

Python

```python
users = []
```

---

PHP

```php
$users[] = "Ajit";
```

Python

```python
users.append("Ajit")
```

---

PHP

```php
count($users);
```

Python

```python
len(users)
```

---

# Best Practices

✅ Use meaningful variable names.

✅ Prefer append() over insert() unless needed.

✅ Use enumerate() when index is required.

✅ Copy lists correctly.

---

# Common Mistakes

❌

```python
b = a
```

Thinking it creates a copy.

It doesn't.

Both variables reference the same list.

---

# Interview Questions

1. Difference between append() and extend()
2. Difference between remove() and pop()
3. Why are lists mutable?
4. Time complexity of append()
5. Difference between list and tuple
6. Explain shallow copy
7. Difference between copy() and deepcopy()

---

# Exercises

## Easy

1. Create a list of five cities.
2. Print the second city.
3. Replace one city.

---

## Medium

1. Remove duplicates.
2. Find largest number.
3. Reverse without reverse().

---

## Advanced

Create a chat history manager using a list.

Each message should contain:

- role
- content
- timestamp

Print the conversation.

---

# Mini Project

Build a simple **To-Do List Manager**.

Features:

- Add task
- Remove task
- Show tasks
- Count tasks
- Exit

---

# Summary

Lists are the foundation of Python programming.

Mastering them is essential before learning:

- Dictionaries
- Functions
- Classes
- NumPy
- Pandas
- Machine Learning
- LLMs
- RAG

You will use lists every single day as an AI Engineer.
