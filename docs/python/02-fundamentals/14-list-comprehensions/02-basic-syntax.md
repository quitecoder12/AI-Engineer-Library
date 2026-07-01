# File: docs/python/02-fundamentals/14-list-comprehensions/02-basic-syntax.md

# Basic Syntax

> "Once you understand the syntax, you'll begin seeing opportunities to use list comprehensions everywhere."

---

# Learning Objectives

After completing this section you will be able to:

- Understand the anatomy of a list comprehension
- Read any basic list comprehension
- Convert loops into comprehensions
- Build lists from ranges
- Build lists from existing collections
- Apply transformations
- Read comprehensions written by other developers

---

# Prerequisites

- Variables
- Lists
- for loops
- range()

---

# The General Syntax

A list comprehension has the following structure.

```python
[
    expression
    for item in iterable
]
```

Let's break it apart.

```
expression

↓

What should go into the list?

↓

for item

↓

Iterate through every item

↓

in iterable

↓

Source collection
```

---

# Visual Diagram

```
            List Comprehension

┌───────────────────────────────────────┐

Expression

↓

For each item

↓

Store result

↓

Return List

└───────────────────────────────────────┘
```

---

# Smallest Example

Traditional

```python
numbers = []

for x in range(5):
    numbers.append(x)
```

Comprehension

```python
numbers = [
    x
    for x in range(5)
]
```

Result

```python
[0,1,2,3,4]
```

---

# Reading a Comprehension

Read this:

```python
[x for x in range(5)]
```

As English:

> Create a list containing every value x from range(5).

---

# Another Example

```python
[
    number
    for number in range(10)
]
```

Read as:

> Build a list using every number from 0 to 9.

---

# Expression Position

Notice the expression comes first.

```python
[
    x*x
    for x in range(5)
]
```

Many beginners expect

```python
for x in range(5):
```

first.

Python intentionally puts

```
What

↓

before

↓

How
```

You first describe

"What do I want?"

Then

"Where does it come from?"

---

# Building Squares

Traditional

```python
squares = []

for x in range(5):
    squares.append(x*x)
```

Comprehension

```python
squares = [
    x*x
    for x in range(5)
]
```

Result

```python
[0,1,4,9,16]
```

---

# Building Cubes

```python
[
    x**3
    for x in range(6)
]
```

Result

```python
[0,1,8,27,64,125]
```

---

# Using Variables

```python
numbers = [1,2,3,4]
```

Multiply by 10

```python
[
    number*10
    for number in numbers
]
```

Result

```python
[10,20,30,40]
```

---

# Working with Strings

```python
languages = [
    "python",
    "php",
    "java"
]
```

Uppercase

```python
[
    language.upper()
    for language in languages
]
```

Result

```python
[
'PYTHON',
'PHP',
'JAVA'
]
```

---

# String Length

```python
[
    len(word)
    for word in languages
]
```

Returns

```python
[
6,
3,
4
]
```

---

# Using Functions

```python
def square(x):
    return x*x
```

```python
[
    square(x)
    for x in range(5)
]
```

---

# Method Calls

```python
[
    word.title()
    for word in words
]
```

---

# Object Attributes

```python
employees = [
    employee1,
    employee2,
    employee3
]
```

```python
[
    employee.name
    for employee in employees
]
```

Very common.

---

# Dictionary Values

```python
users = [

    {
        "name":"Ajit"
    },

    {
        "name":"Rahul"
    }

]
```

Extract names.

```python
[
    user["name"]
    for user in users
]
```

Result

```python
[
"Ajit",
"Rahul"
]
```

---

# Multiple Expressions?

Only one expression is allowed.

Correct

```python
[
    x*x
    for x in numbers
]
```

Incorrect

```python
[
    print(x)
    x*x
    for x in numbers
]
```

If your logic becomes complicated,

use a normal loop.

---

# Comprehension Execution

Python conceptually performs

```
Create Empty List

↓

Loop

↓

Evaluate Expression

↓

Append Result

↓

Repeat

↓

Return List
```

Although internally CPython uses optimized bytecode.

---

# Equivalent Loop

This

```python
[
    expression
    for item in iterable
]
```

is conceptually similar to

```python
result = []

for item in iterable:

    result.append(expression)
```

Understanding this relationship makes comprehensions much easier.

---

# AI Example 1

Extract prompts.

```python
prompts = [

    {
        "prompt":"Hello"
    },

    {
        "prompt":"Explain AI"
    }

]
```

```python
[
    item["prompt"]
    for item in prompts
]
```

---

# AI Example 2

Embedding Dimensions

```python
[
    len(vector)
    for vector in embeddings
]
```

---

# AI Example 3

Chunk Sizes

```python
[
    len(chunk)
    for chunk in chunks
]
```

---

# AI Example 4

FastAPI Models

```python
[
    user.email
    for user in users
]
```

---

# AI Example 5

LangChain Documents

```python
[
    document.page_content
    for document in documents
]
```

---

# PHP Comparison

PHP

```php
$names = [];

foreach($users as $user){

    $names[] = $user["name"];

}
```

Python

```python
names = [
    user["name"]
    for user in users
]
```

Notice how the Python version focuses on

"What"

rather than

"How."

---

# Memory Diagram

Traditional

```
Create List

↓

Append

↓

Append

↓

Append
```

Comprehension

```
Create List

↓

Populate

↓

Return
```

Internally,

Python optimizes this process.

---

# Readability Tips

Good

```python
[
    x*x
    for x in numbers
]
```

Bad

```python
[
    calculate_square_after_checking_permissions(x)
    for x in numbers
]
```

Long expressions reduce readability.

---

# Common Mistakes

## Forgetting the Expression

Wrong

```python
[
    for x in numbers
]
```

---

## Wrong Order

Wrong

```python
[
    for x in numbers
    x*x
]
```

Remember

```
Expression

↓

for

↓

Iterable
```

---

## Confusing List with Generator

List

```python
[
    x
    for x in numbers
]
```

Generator

```python
(
    x
    for x in numbers
)
```

Different topic.

---

# Best Practices

✅ Keep comprehensions short.

✅ Use descriptive variable names.

✅ One transformation per comprehension.

✅ Prefer readability over cleverness.

---

# Interview Questions

1. Explain the syntax of a list comprehension.

2. Why does the expression appear before the loop?

3. Convert a traditional loop into a comprehension.

4. Explain how Python executes a comprehension.

5. Difference between comprehension and generator expression.

---

# Exercises

## Easy

Create

```python
[1,2,3,4,5]
```

using a comprehension.

---

Create

```python
[
10,
20,
30,
40
]
```

using

```
range()
```

---

Convert every string to uppercase.

---

## Medium

Extract all employee names.

---

Create squares from

1–100.

---

Create list of filename lengths.

---

## Challenge

Given

```python
employees = [

{
"name":"Ajit",
"salary":62000
},

{
"name":"Rahul",
"salary":45000
},

{
"name":"John",
"salary":70000
}

]
```

Create a list containing only salaries.

Expected

```python
[
62000,
45000,
70000
]
```

---

# Summary

You have learned:

- The anatomy of a list comprehension
- Expression placement
- Iteration
- Transformations
- Object access
- Dictionary access
- AI use cases

In the next section, you'll learn how to **filter** data while building lists using the `if` clause.
