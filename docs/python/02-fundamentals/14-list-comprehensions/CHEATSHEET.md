# List Comprehensions Cheat Sheet

> **A quick reference guide for Python developers and AI Engineers.**

---

# Syntax

## Basic Syntax

```python
[
    expression
    for item in iterable
]
```

Example

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

# Filtering

```python
[
    expression
    for item in iterable
    if condition
]
```

Example

```python
evens = [
    x
    for x in range(10)
    if x % 2 == 0
]
```

Result

```python
[0,2,4,6,8]
```

---

# Conditional Expression

```python
[
    value_if_true
    if condition
    else value_if_false
    for item in iterable
]
```

Example

```python
labels = [
    "Even"
    if x % 2 == 0
    else "Odd"
    for x in range(5)
]
```

Result

```python
[
"Even",
"Odd",
"Even",
"Odd",
"Even"
]
```

---

# Nested Loops

```python
[
    expression
    for item1 in iterable1
    for item2 in iterable2
]
```

Example

```python
pairs = [
    (x,y)
    for x in range(2)
    for y in range(2)
]
```

Result

```python
[
(0,0),
(0,1),
(1,0),
(1,1)
]
```

---

# Nested Loop + Filter

```python
[
    value
    for row in matrix
    for value in row
    if value > 0
]
```

---

# Execution Order

Basic

```
Expression

↓

for

↓

if
```

Conditional Expression

```
Expression

↓

if

↓

else

↓

for
```

Nested

```
Expression

↓

Outer Loop

↓

Inner Loop

↓

Filter
```

---

# Translation Guide

## Traditional Loop

```python
result = []

for item in items:

    result.append(item)
```

↓

```python
result = [
    item
    for item in items
]
```

---

Traditional

```python
result = []

for item in items:

    result.append(item.upper())
```

↓

```python
result = [
    item.upper()
    for item in items
]
```

---

Traditional

```python
result = []

for item in items:

    if item.active:

        result.append(item)
```

↓

```python
result = [
    item
    for item in items
    if item.active
]
```

---

Traditional

```python
result = []

for item in items:

    if item.active:

        result.append(item.name)
```

↓

```python
result = [
    item.name
    for item in items
    if item.active
]
```

---

# Most Common Patterns

Uppercase

```python
[
    word.upper()
    for word in words
]
```

---

Lowercase

```python
[
    word.lower()
    for word in words
]
```

---

Lengths

```python
[
    len(word)
    for word in words
]
```

---

Squares

```python
[
    x*x
    for x in numbers
]
```

---

Cubes

```python
[
    x**3
    for x in numbers
]
```

---

Even Numbers

```python
[
    x
    for x in numbers
    if x % 2 == 0
]
```

---

Odd Numbers

```python
[
    x
    for x in numbers
    if x % 2
]
```

---

Positive Numbers

```python
[
    x
    for x in numbers
    if x > 0
]
```

---

Negative Numbers

```python
[
    x
    for x in numbers
    if x < 0
]
```

---

Replace Negatives

```python
[
    x
    if x > 0
    else 0
    for x in numbers
]
```

---

Flatten Matrix

```python
[
    value
    for row in matrix
    for value in row
]
```

---

Coordinates

```python
[
    (x,y)
    for x in range(5)
    for y in range(5)
]
```

---

Cartesian Product

```python
[
    (color,size)
    for color in colors
    for size in sizes
]
```

---

# AI Patterns

Extract User Messages

```python
[
    message["content"]
    for message in history
    if message["role"] == "user"
]
```

---

Extract Assistant Messages

```python
[
    message["content"]
    for message in history
    if message["role"] == "assistant"
]
```

---

Extract Metadata

```python
[
    document.metadata
    for document in documents
]
```

---

Extract Page Content

```python
[
    document.page_content
    for document in documents
]
```

---

Embedding Lengths

```python
[
    len(vector)
    for vector in embeddings
]
```

---

Generate Prompts

```python
[
    f"Explain {topic}"
    for topic in topics
]
```

---

Batch Processing

```python
[
    items[i:i+100]
    for i in range(
        0,
        len(items),
        100
    )
]
```

---

Remove Empty Strings

```python
[
    text
    for text in texts
    if text
]
```

---

Normalize Values

```python
[
    value / 100
    for value in values
]
```

---

# Performance Comparison

| Method | Speed | Memory | Readability |
|----------|--------|---------|------------|
| Loop | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| List Comprehension | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Generator | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| map() | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |

---

# Time Complexity

| Operation | Complexity |
|-----------|------------|
| Basic | O(n) |
| Filtering | O(n) |
| Conditional | O(n) |
| Nested Loops | O(n × m) |
| Triple Loops | O(n × m × k) |

---

# Memory Comparison

List

```
Entire Collection

↓

RAM
```

Generator

```
One Value

↓

Next Value

↓

Next Value
```

---

# Decision Tree

```
Need a List?

│

├── No

│      ↓

│   Use Generator

│

└── Yes

      │

      ├── Simple Transformation?

      │

      │      ↓

      │   List Comprehension

      │

      ├── Complex Logic?

      │

      │      ↓

      │   Normal Loop

      │

      ├── Huge Dataset?

      │

      │      ↓

      │   Generator

      │

      └── Numeric Arrays?

             ↓

           NumPy
```

---

# Do's

✅ Keep comprehensions short.

✅ Use descriptive variable names.

✅ Use helper functions.

✅ Prefer readability.

✅ Use filtering for selection.

✅ Use conditional expressions for transformation.

---

# Don'ts

❌ Don't use append()

❌ Don't create side effects

❌ Don't perform logging

❌ Don't write huge expressions

❌ Don't nest many loops

❌ Don't sacrifice readability

---

# Common Mistakes

Wrong

```python
[
    print(x)
    for x in numbers
]
```

---

Wrong

```python
[
    x
    for x in numbers
    if x > 5
    else 0
]
```

---

Wrong

```python
[
    result.append(x)
    for x in numbers
]
```

---

Correct

```python
[
    x
    if x > 5
    else 0
    for x in numbers
]
```

---

# Interview Questions

Can you answer?

✅ Why are list comprehensions faster?

✅ Difference between filtering and transformation?

✅ Difference between list and generator?

✅ Explain nested comprehensions.

✅ Explain execution order.

✅ When should they be avoided?

---

# Quick Revision

Basic

```python
[
    expression
    for item in iterable
]
```

Filter

```python
[
    expression
    for item in iterable
    if condition
]
```

Conditional

```python
[
    a if condition else b
    for item in iterable
]
```

Nested

```python
[
    expression
    for x in A
    for y in B
]
```

Flatten

```python
[
    value
    for row in matrix
    for value in row
]
```

---

# Professional Tips

✔ Prefer readability over cleverness.

✔ One transformation per comprehension.

✔ If you need comments inside a comprehension, it's probably too complex.

✔ If debugging becomes difficult, rewrite it as a normal loop.

✔ Benchmark before optimizing.

---

# Related Topics

After mastering list comprehensions, continue with:

- Dictionary Comprehensions
- Set Comprehensions
- Generator Expressions
- Generator Functions (`yield`)
- Iterators
- Functional Programming (`map`, `filter`, `reduce`)

These topics build directly on the concepts you've learned here.

---

# Congratulations! 🎉

You have completed one of the most important Python topics.

List comprehensions are used extensively in:

- Python Standard Library
- FastAPI
- Django
- Pandas
- NumPy
- OpenAI SDK
- Hugging Face
- LangChain
- LlamaIndex
- Streamlit
- Production AI systems

Mastering them is a major step toward becoming a proficient Python developer and AI Engineer.
