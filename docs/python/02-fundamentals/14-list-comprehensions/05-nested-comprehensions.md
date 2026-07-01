# Nested List Comprehensions

> **Nested list comprehensions allow you to iterate over multiple collections or multidimensional data structures using a single expression.**

---

# Learning Objectives

After completing this section, you will be able to:

- Understand nested comprehensions
- Work with nested lists
- Flatten lists
- Process matrices
- Read nested comprehensions confidently
- Decide when nested comprehensions should be avoided
- Apply nested comprehensions in AI and data processing

---

# Prerequisites

Before reading this chapter, you should understand:

- Lists
- Nested Lists
- List Comprehensions
- Nested Loops

---

# What is a Nested List Comprehension?

A nested comprehension contains **more than one `for` clause**.

Instead of iterating over one collection, it iterates over multiple collections.

General syntax

```python
[
    expression
    for item1 in collection1
    for item2 in collection2
]
```

Think of it as nested loops written compactly.

---

# Traditional Nested Loop

```python
result = []

for row in matrix:

    for value in row:

        result.append(value)
```

---

# Nested Comprehension

```python
result = [
    value
    for row in matrix
    for value in row
]
```

Produces exactly the same result.

---

# Visual Diagram

```
Matrix

┌──────────────┐

1 2 3

4 5 6

7 8 9

└──────────────┘

↓

Outer Loop

↓

Inner Loop

↓

Result

↓

[1,2,3,4,5,6,7,8,9]
```

---

# Reading Order

Always read left to right.

```python
[
    value
    for row in matrix
    for value in row
]
```

Read as

> Create a list containing every value for every row in the matrix.

---

# Example 1

Flatten a Matrix

```python
matrix = [

    [1,2,3],

    [4,5,6],

    [7,8,9]

]
```

Traditional

```python
flat = []

for row in matrix:

    for value in row:

        flat.append(value)
```

Comprehension

```python
flat = [

    value

    for row in matrix

    for value in row

]
```

Result

```python
[
1,2,3,4,5,6,7,8,9
]
```

---

# Example 2

Square Every Number

```python
matrix = [

    [1,2],

    [3,4]

]
```

```python
result = [

    number * number

    for row in matrix

    for number in row

]
```

Result

```python
[
1,
4,
9,
16
]
```

---

# Example 3

Extract Characters

```python
words = [

"AI",

"Python"

]
```

```python
letters = [

    letter

    for word in words

    for letter in word

]
```

Result

```python
[
'A',

'I',

'P',

'y',

't',

'h',

'o',

'n'

]
```

---

# Example 4

Cartesian Product

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

    (color,size)

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

---

# Visualizing Multiple Loops

Traditional

```
Colors

↓

Loop

↓

Sizes

↓

Loop

↓

Create Tuple
```

Comprehension

```
Tuple

↓

for Color

↓

for Size
```

---

# Example 5

Coordinates

```python
points = [

    (x,y)

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

# Nested Filtering

You can also filter.

```python
matrix = [

[1,2],

[3,4],

[5,6]

]
```

```python
result = [

    value

    for row in matrix

    for value in row

    if value % 2 == 0

]
```

Result

```python
[
2,
4,
6
]
```

---

# Nested Conditional Expression

Possible

```python
result = [

    value

    if value > 3

    else 0

    for row in matrix

    for value in row

]
```

Produces

```python
[
0,
0,
0,
4,
5,
6
]
```

---

# Matrix Transpose (Preview)

Suppose

```python
matrix = [

[1,2,3],

[4,5,6]

]
```

Transpose

```python
transpose = [

    [

        row[column]

        for row in matrix

    ]

    for column in range(len(matrix[0]))

]
```

Result

```python
[
[1,4],

[2,5],

[3,6]
]
```

We'll revisit this in the NumPy section.

---

# AI Example 1

Flatten Token Lists

```python
tokens = [

["The","cat"],

["sat","here"]

]
```

```python
all_tokens = [

    token

    for sentence in tokens

    for token in sentence

]
```

Result

```python
[
"The",

"cat",

"sat",

"here"
]
```

---

# AI Example 2

Extract Embeddings

```python
embeddings = [

[[0.1,0.2]],

[[0.5,0.8]]

]
```

Flatten

```python
values = [

    value

    for embedding in embeddings

    for vector in embedding

    for value in vector

]
```

---

# AI Example 3

Document Processing

```python
documents = [

    {

        "chunks":[

            "A",

            "B"

        ]

    },

    {

        "chunks":[

            "C"

        ]

    }

]
```

```python
chunks = [

    chunk

    for document in documents

    for chunk in document["chunks"]

]
```

---

# AI Example 4

Chat Messages

```python
conversations = [

    [

        "Hello",

        "How are you?"

    ],

    [

        "Explain RAG"

    ]

]
```

Flatten

```python
messages = [

    message

    for conversation in conversations

    for message in conversation

]
```

---

# Performance

Nested comprehensions are still loops.

Complexity depends on the nested loops.

Example

```python
for row

for value
```

Complexity

```
O(rows × columns)
```

---

# Readability

Good

```python
[
    value

    for row in matrix

    for value in row
]
```

Bad

```python
[
    complicated_function(

        value

    )

    for matrix in matrices

    for row in matrix

    for value in row

    if value > 0

    if validate(value)

    if has_permission(value)

]
```

Too difficult to read.

Prefer ordinary loops.

---

# When NOT to Use Nested Comprehensions

Avoid them when:

- More than two nested loops
- Complex business rules
- Multiple conditions
- Exception handling
- Logging
- Debugging

Use normal loops instead.

---

# PHP Comparison

PHP

```php
$result = [];

foreach($matrix as $row){

    foreach($row as $value){

        $result[] = $value;

    }

}
```

Python

```python
result = [

    value

    for row in matrix

    for value in row

]
```

---

# Best Practices

✅ Maximum two nested loops.

✅ Keep expressions simple.

✅ Break complicated logic into functions.

✅ Choose readability over cleverness.

---

# Common Mistakes

❌ Forgetting the order.

Correct

```python
expression

↓

Outer Loop

↓

Inner Loop
```

---

❌ Creating unreadable one-liners.

---

❌ Trying to debug nested comprehensions.

Convert them into loops first.

---

# Debugging Tip

Whenever a nested comprehension doesn't work,

rewrite it as nested loops.

Debug.

Then convert it back.

Professional Python developers do this frequently.

---

# Interview Questions

1. Explain nested comprehensions.

2. How are they executed?

3. What is their time complexity?

4. When should they be avoided?

5. Explain flattening a matrix.

6. Difference between nested loops and nested comprehensions.

---

# Exercises

## Easy

Flatten

```python
[
[1,2],

[3,4]
]
```

---

Create all coordinate pairs.

---

Extract all letters from

```python
["AI","ML"]
```

---

## Medium

Flatten a list of document chunks.

---

Flatten employee skills.

---

Extract all email addresses.

---

## Advanced

Given

```python
students = [

{

"name":"Ajit",

"subjects":[

"Python",

"SQL"

]

},

{

"name":"Rahul",

"subjects":[

"AI",

"ML"

]

}

]
```

Create

```python
[
"Python",

"SQL",

"AI",

"ML"
]
```

using a nested comprehension.

---

# Mini Project

Build a **Document Chunk Flattener**.

Input

```python
documents = [

{

"id":1,

"chunks":[...]

},

...

]
```

Output

One list containing every chunk from every document.

This is a common preprocessing step before generating embeddings for RAG systems.

---

# Summary

Nested list comprehensions are ideal for processing multidimensional data.

They are frequently used for:

- Matrices
- NLP token lists
- AI document chunks
- Embeddings
- CSV data
- JSON arrays

They are elegant—but only when they remain readable.

---

# Next Section

➡ **06-multiple-for-loops.md**

You'll learn how multiple `for` clauses generate combinations, permutations, and Cartesian products—techniques used in machine learning, hyperparameter tuning, and data generation.
