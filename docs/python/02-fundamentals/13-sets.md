# Sets

> **Sets are unordered collections of unique elements.**

---

# Learning Objectives

After completing this chapter, you will be able to:

- Understand what sets are
- Create sets
- Add and remove elements
- Perform mathematical set operations
- Remove duplicates efficiently
- Understand hashing
- Compare sets with lists and dictionaries
- Apply sets in AI engineering

---

# Prerequisites

Before reading this chapter, you should know:

- Variables
- Data Types
- Lists
- Tuples
- Dictionaries

---

# What is a Set?

A **set** is an unordered collection of **unique** elements.

Unlike lists:

- Duplicate values are automatically removed.
- There is no indexing.
- Elements are stored using hash tables.

Example:

```python
languages = {"Python", "Java", "Go"}
```

---

# Visual Representation

```
           Set

 ┌─────────────────────┐
 │                     │
 │      Python         │
 │                     │
 │   Java      Go      │
 │                     │
 └─────────────────────┘
```

Notice there are **no indexes**.

---

# Why Sets Matter

Sets are extremely useful for:

- Removing duplicates
- Fast membership testing
- Comparing collections
- Finding common elements
- NLP preprocessing
- Recommendation systems
- Vector search filtering

---

# Creating Sets

```python
languages = {"Python", "PHP", "Java"}
```

---

Empty Set

❌ Wrong

```python
items = {}
```

Python creates a dictionary.

✔ Correct

```python
items = set()
```

---

# Duplicate Removal

```python
numbers = {1,2,3,3,2,1}
```

Result

```python
{1,2,3}
```

Duplicates disappear automatically.

---

# Creating from a List

```python
numbers = [1,2,3,3,2,1]

unique = set(numbers)
```

Result

```python
{1,2,3}
```

---

# Creating from a String

```python
letters = set("banana")
```

Result

```python
{'a','b','n'}
```

---

# Length

```python
len(languages)
```

---

# Membership

```python
"Python" in languages
```

Returns

```python
True
```

Membership testing in sets is typically O(1).

---

# Iteration

```python
for language in languages:
    print(language)
```

Remember:

Order is not guaranteed.

---

# Adding Elements

```python
languages.add("Rust")
```

---

Adding Multiple Elements

```python
languages.update(
    ["Go","Swift"]
)
```

---

# Removing Elements

## remove()

```python
languages.remove("PHP")
```

Raises an exception if the item is missing.

---

## discard()

```python
languages.discard("PHP")
```

No error if the item doesn't exist.

Preferred when uncertain.

---

## pop()

```python
languages.pop()
```

Removes an arbitrary element.

Do **not** assume which one.

---

## clear()

```python
languages.clear()
```

---

# Copy

```python
new_set = languages.copy()
```

---

# Set Operations

These are the real power of sets.

---

## Union

```
A ∪ B
```

```
{1,2,3}

UNION

{3,4,5}

↓

{1,2,3,4,5}
```

Python

```python
a | b
```

or

```python
a.union(b)
```

---

## Intersection

Common elements.

```
{1,2,3}

INTERSECTION

{3,4,5}

↓

{3}
```

Python

```python
a & b
```

or

```python
a.intersection(b)
```

---

## Difference

Items in A but not B.

```
{1,2,3}

DIFFERENCE

{3,4}

↓

{1,2}
```

Python

```python
a - b
```

---

## Symmetric Difference

Elements in either set, but not both.

```
{1,2,3}

^

{3,4,5}

↓

{1,2,4,5}
```

Python

```python
a ^ b
```

---

# Subset

```python
a.issubset(b)
```

Example

```
{1,2}

⊆

{1,2,3}
```

Returns

```
True
```

---

# Superset

```python
a.issuperset(b)
```

---

# Disjoint

No common elements.

```python
a.isdisjoint(b)
```

---

# Time Complexity

| Operation | Complexity |
|-----------|------------|
| Add | O(1) |
| Remove | O(1) |
| Membership | O(1) |
| Union | O(n) |
| Intersection | O(min(n,m)) |

Average case.

---

# Internal Working

Python sets are implemented using a **hash table**.

```
Value

↓

Hash

↓

Bucket

↓

Stored
```

This is why lookups are extremely fast.

---

# Mutable Elements

Not allowed

```python
{
    [1,2]
}
```

Produces

```
TypeError
```

Lists are mutable.

---

Allowed

```python
{
    (1,2)
}
```

Tuples are immutable.

---

# AI Example 1

Remove duplicate documents.

```python
documents = [
    "AI",
    "Python",
    "AI",
    "RAG"
]

unique = set(documents)
```

---

# AI Example 2

Find common keywords.

```python
query = {
    "python",
    "rag",
    "llm"
}

document = {
    "python",
    "database",
    "rag"
}

common = query & document
```

Result

```python
{"python","rag"}
```

Useful in information retrieval.

---

# AI Example 3

Vocabulary creation.

```python
words = []

for sentence in corpus:
    words.extend(sentence.split())

vocabulary = set(words)
```

Every NLP pipeline performs something similar.

---

# PHP Comparison

PHP

```php
array_unique($items);
```

Python

```python
set(items)
```

---

PHP has no native set type.

Python does.

---

# Best Practices

✅ Use sets for uniqueness.

✅ Use sets for membership testing.

✅ Convert lists to sets when removing duplicates.

✅ Use mathematical operations instead of loops where possible.

---

# Common Mistakes

❌ Expecting order.

```python
for item in my_set:
```

Order is arbitrary.

---

❌ Using {}

Thinking it creates an empty set.

Actually

```python
{}
```

Creates a dictionary.

---

# Debugging Tips

Convert to list for display.

```python
sorted(my_set)
```

Produces predictable output.

---

# Interview Questions

1. Difference between list and set.
2. Why are sets faster than lists?
3. Explain hashing.
4. Difference between remove() and discard().
5. Explain union and intersection.
6. Why can't lists be elements of a set?
7. Time complexity of membership testing.

---

# Exercises

## Easy

Create a set of five programming languages.

---

Remove duplicates from a list.

---

Find common elements between two sets.

---

## Medium

Find unique words in a paragraph.

---

Compare two student lists.

---

## Advanced

Given two recommendation lists:

- Netflix recommendations
- Amazon Prime recommendations

Find:

- Common movies
- Exclusive movies
- Total unique movies

using set operations.

---

# Mini Project

Build a **Tag Management System**.

Features:

- Add tags
- Remove tags
- Find duplicate tags
- Merge tag collections
- Display tags alphabetically

---

# Summary

Sets are one of Python's most efficient data structures.

They are ideal when:

- Order doesn't matter.
- Uniqueness matters.
- Speed matters.

You'll frequently use sets in:

- AI preprocessing
- NLP
- Search systems
- Recommendation engines
- Vector databases

---

# Cheat Sheet

```python
s = set()

s.add(x)

s.remove(x)

s.discard(x)

s.pop()

s.clear()

a | b      # Union

a & b      # Intersection

a - b      # Difference

a ^ b      # Symmetric Difference

x in s

len(s)
```

---

# Next Chapter

➡ **14-frozensets.md**

Learn about immutable sets and hashable collections.
