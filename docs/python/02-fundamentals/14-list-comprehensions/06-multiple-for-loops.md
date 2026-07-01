# Multiple `for` Loops in List Comprehensions

> **Multiple `for` clauses allow a single comprehension to iterate over multiple collections, generating combinations, Cartesian products, and flattened structures.**

---

# Learning Objectives

After completing this chapter, you will be able to:

- Understand multiple `for` clauses
- Understand execution order
- Generate Cartesian products
- Create coordinate systems
- Generate permutations
- Combine multiple collections
- Apply multiple loops in AI applications
- Decide when multiple loops become too complex

---

# Prerequisites

You should already know:

- Lists
- Loops
- Nested loops
- Basic list comprehensions

---

# What are Multiple `for` Loops?

A list comprehension can contain more than one `for`.

General syntax

```python
[
    expression
    for item1 in iterable1
    for item2 in iterable2
]
```

Each additional `for` behaves exactly like another nested loop.

---

# Equivalent Traditional Code

Comprehension

```python
[
    (x, y)
    for x in range(3)
    for y in range(2)
]
```

Equivalent loop

```python
result = []

for x in range(3):

    for y in range(2):

        result.append((x, y))
```

Always remember this relationship.

---

# Execution Order

```
Outer Loop

↓

Inner Loop

↓

Expression

↓

Append

↓

Repeat
```

---

# Example 1

Coordinate System

```python
coordinates = [

    (x, y)

    for x in range(3)

    for y in range(3)

]
```

Result

```python
[
(0,0),
(0,1),
(0,2),
(1,0),
(1,1),
(1,2),
(2,0),
(2,1),
(2,2)
]
```

---

# Visual Diagram

```
x = 0

↓

y = 0

↓

(0,0)

↓

y = 1

↓

(0,1)

↓

y = 2

↓

(0,2)

↓

Next x
```

---

# Example 2

Colors and Sizes

```python
colors = [

"Red",

"Blue"

]

sizes = [

"S",

"M",

"L"

]
```

```python
products = [

    (color, size)

    for color in colors

    for size in sizes

]
```

Result

```python
[
('Red','S'),
('Red','M'),
('Red','L'),
('Blue','S'),
('Blue','M'),
('Blue','L')
]
```

This is known as the **Cartesian Product**.

---

# Mathematical View

```
Colors

×

Sizes

↓

Every Possible Combination
```

---

# Example 3

User Roles

```python
users = [

"Ajit",

"Rahul"

]

roles = [

"Admin",

"Editor"

]
```

```python
permissions = [

    f"{user} - {role}"

    for user in users

    for role in roles

]
```

---

# Example 4

Board Coordinates

Chess board

```python
board = [

    (row, column)

    for row in range(8)

    for column in range(8)

]
```

Creates

64 positions.

---

# Example 5

Multiplication Table

```python
table = [

    (x, y, x * y)

    for x in range(1,6)

    for y in range(1,6)

]
```

---

# Three Loops

Possible

```python
result = [

    (x, y, z)

    for x in range(2)

    for y in range(2)

    for z in range(2)

]
```

Produces

```
2 × 2 × 2

=

8 combinations
```

---

# Four Loops?

Technically yes.

```python
[
    ...
    for a in A
    for b in B
    for c in C
    for d in D
]
```

But readability usually suffers.

---

# Combining with Filtering

```python
pairs = [

    (x, y)

    for x in range(5)

    for y in range(5)

    if x != y

]
```

Result

Identical pairs are removed.

---

# Conditional Expression

```python
result = [

    "Even"

    if x % 2 == 0

    else "Odd"

    for x in range(5)

    for _ in range(2)

]
```

---

# AI Example 1

Prompt Generation

```python
languages = [

"English",

"Hindi"

]

tasks = [

"Summarize",

"Translate"

]
```

```python
prompts = [

    f"{task} in {language}"

    for task in tasks

    for language in languages

]
```

---

# AI Example 2

Hyperparameter Search

```python
learning_rates = [

0.001,

0.01

]

batch_sizes = [

16,

32,

64

]
```

```python
experiments = [

    (lr, batch)

    for lr in learning_rates

    for batch in batch_sizes

]
```

Every combination is generated.

Very common in ML.

---

# AI Example 3

Embedding Comparisons

```python
documents = [

"A",

"B",

"C"

]

queries = [

"Q1",

"Q2"

]
```

```python
pairs = [

    (query, document)

    for query in queries

    for document in documents

]
```

Useful in retrieval evaluation.

---

# AI Example 4

Multiple Models

```python
models = [

"gpt-5",

"gpt-4"

]

temperatures = [

0.2,

0.7

]
```

```python
tests = [

    {

        "model": model,

        "temperature": temp

    }

    for model in models

    for temp in temperatures

]
```

---

# Time Complexity

One loop

```
O(n)
```

Two loops

```
O(n × m)
```

Three loops

```
O(n × m × k)
```

Always multiply the sizes.

---

# Memory Usage

Result size

```
=

Product

of

all

loop

sizes
```

Example

```
100

×

100

=

10,000 items
```

Be careful with large collections.

---

# Common Mistakes

## Assuming Parallel Iteration

This

```python
[
    (x, y)

    for x in list1

    for y in list2
]
```

creates

Every combination.

It does **not** pair matching indexes.

For parallel iteration,

use

```python
zip()
```

We'll cover `zip()` later.

---

## Too Many Loops

Avoid

```python
[
    ...
    for a in A
    for b in B
    for c in C
    for d in D
    for e in E
]
```

Almost impossible to read.

---

# Best Practices

✅ Maximum two nested loops.

✅ Keep expressions simple.

✅ Use helper functions.

✅ Prefer readability.

---

# PHP Comparison

PHP

```php
$result = [];

foreach($colors as $color){

    foreach($sizes as $size){

        $result[] = [$color,$size];

    }

}
```

Python

```python
result = [

    (color,size)

    for color in colors

    for size in sizes

]
```

---

# Debugging Tip

Convert every comprehension into ordinary loops.

Debug.

Convert back.

This is how experienced Python developers troubleshoot complex comprehensions.

---

# Interview Questions

1. Explain execution order.

2. What is a Cartesian product?

3. Difference between nested loops and multiple `for` clauses.

4. Explain complexity.

5. Difference between multiple `for` and `zip()`.

---

# Exercises

## Easy

Generate

```
(1,1)

(1,2)

(2,1)

(2,2)
```

using a comprehension.

---

Create every shirt-size combination.

---

## Medium

Generate every

```
(Student, Subject)
```

pair.

---

Create all

```
(Language, Framework)
```

pairs.

---

## Advanced

Given

```python
models = [
    "gpt-5",
    "llama-3"
]

temperatures = [
    0.2,
    0.5,
    0.8
]

datasets = [
    "news",
    "finance"
]
```

Generate every experiment configuration.

Expected

```
2 × 3 × 2

=

12 configurations
```

---

# Mini Project

Build an **AI Experiment Generator**.

Input

- Models
- Temperatures
- Prompt Templates
- Datasets

Generate every possible experiment automatically using list comprehensions.

This mirrors how ML engineers create experiment grids.

---

# Summary

Multiple `for` clauses are simply nested loops written in a compact, Pythonic style.

They are especially useful for:

- Cartesian products
- Coordinate systems
- Hyperparameter tuning
- AI experiment generation
- Data expansion

Use them wisely.

As the number of nested loops increases, readability decreases.

---

# Next Section

➡ **07-performance.md**

You'll benchmark list comprehensions against traditional loops, `map()`, generators, and NumPy, and learn why list comprehensions are often faster than manual loops.
