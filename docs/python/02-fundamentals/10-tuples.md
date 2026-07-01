# Tuples

> Immutable ordered collections for fixed data.

---

# Learning Objectives

After this chapter you will understand:

- What tuples are
- Why tuples exist
- Tuple packing
- Tuple unpacking
- Immutability
- Performance differences
- When to use tuples instead of lists
- AI use cases

---

# What is a Tuple?

A tuple is an **ordered, immutable collection**.

Unlike lists, tuples **cannot be modified** after creation.

```
List
↓

Mutable

Can Change

Tuple
↓

Immutable

Cannot Change
```

---

# Why Tuples?

Suppose you want to store GPS coordinates.

```
Latitude

Longitude
```

Those values shouldn't accidentally change.

Tuples are perfect.

```python
location = (22.2604, 84.8536)
```

---

# Creating Tuples

```python
numbers = (1,2,3)
```

---

Single element

Wrong

```python
x = (5)
```

Python thinks this is an integer.

Correct

```python
x = (5,)
```

Notice the comma.

---

Without Parentheses

Python automatically creates tuples.

```python
point = 10,20
```

Equivalent to

```python
point = (10,20)
```

---

# Access Elements

```python
languages = (
    "Python",
    "PHP",
    "Java"
)

languages[0]
```

Returns

```
Python
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
("Python","PHP")
```

---

# Immutability

This is NOT allowed

```python
languages[0] = "Rust"
```

Produces

```
TypeError
```

---

# Why Immutable?

Imagine an AI model configuration.

```python
MODEL = (
    "gpt-5",
    4096,
    0.7
)
```

You don't want someone accidentally changing these values.

---

# Tuple Packing

```python
user = (
    "Ajit",
    50,
    "India"
)
```

---

# Tuple Unpacking

```python
name, age, country = user
```

Now

```
name

↓

Ajit

age

↓

50

country

↓

India
```

---

# Swapping Variables

Without temporary variables

```python
a = 10
b = 20

a, b = b, a
```

Result

```
a = 20

b = 10
```

Elegant and Pythonic.

---

# Returning Multiple Values

Functions often return tuples.

```python
def get_user():
    return "Ajit",50
```

Usage

```python
name, age = get_user()
```

---

# Tuple Methods

Only two methods exist.

```python
count()

index()
```

Example

```python
numbers = (1,2,3,2)

numbers.count(2)
```

Returns

```
2
```

---

# Nested Tuples

```python
matrix = (
    (1,2),
    (3,4)
)
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

# Tuple vs List

| Feature | List | Tuple |
|-----------|------|--------|
| Mutable | ✅ | ❌ |
| Ordered | ✅ | ✅ |
| Faster | ❌ | ✅ |
| Memory | More | Less |
| Hashable | ❌ | Usually |

---

# Memory

Tuples generally consume less memory than lists because they don't support modification.

---

# Performance

Reading

```
O(1)
```

Searching

```
O(n)
```

Creation is slightly faster than lists.

---

# AI Example

Embedding dimensions

```python
embedding_shape = (
    1536,
)
```

Tensor dimensions

```python
shape = (
    128,
    768
)
```

Coordinate

```python
point = (
    x,
    y
)
```

---

# PHP Comparison

PHP

```php
$user = [
    "Ajit",
    50
];
```

Python

```python
user = (
    "Ajit",
    50
)
```

PHP has no true tuple type.

---

# Best Practices

✅ Use tuples for fixed data.

✅ Return tuples from functions.

✅ Use unpacking whenever possible.

---

# Common Mistakes

❌

```python
single = (5)
```

✔

```python
single = (5,)
```

---

# Interview Questions

1. Why are tuples immutable?
2. Difference between tuple and list.
3. Explain tuple unpacking.
4. Can tuples contain mutable objects?

---

# Exercises

1. Swap two numbers.
2. Return three values from a function.
3. Store GPS coordinates.
4. Create nested tuples.

---

# Mini Project

Create a Student Record System where each student record is stored as a tuple:

- Roll Number
- Name
- Branch
- CGPA

Display all records.
