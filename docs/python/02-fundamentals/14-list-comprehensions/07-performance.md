# File: docs/python/02-fundamentals/14-list-comprehensions/07-performance.md

# Performance of List Comprehensions

> **List comprehensions are not only elegant—they are often faster than traditional loops. Understanding why will help you write better Python code.**

---

# Learning Objectives

After completing this chapter, you will be able to:

- Understand why list comprehensions are fast
- Compare list comprehensions with traditional loops
- Compare list comprehensions with `map()`
- Compare list comprehensions with generator expressions
- Understand memory usage
- Benchmark Python code
- Decide when performance matters
- Apply these concepts in AI projects

---

# Does Performance Matter?

Many beginners ask:

> "Should I use a list comprehension because it is faster?"

The better question is:

> "Should I use the most readable solution?"

Performance is important.

Readability is usually **more** important.

However...

List comprehensions are often **both** readable **and** faster.

---

# The Competitors

We'll compare four approaches.

1. Traditional Loop
2. List Comprehension
3. map()
4. Generator Expression

---

# Example Problem

Create squares from

```
0 → 999999
```

---

## Method 1

Traditional Loop

```python
result = []

for x in range(1_000_000):
    result.append(x * x)
```

---

## Method 2

List Comprehension

```python
result = [
    x * x
    for x in range(1_000_000)
]
```

---

## Method 3

map()

```python
result = list(
    map(
        lambda x: x*x,
        range(1_000_000)
    )
)
```

---

## Method 4

Generator

```python
result = (
    x*x
    for x in range(1_000_000)
)
```

Notice

Generator

↓

No list is created.

---

# Typical Performance

Actual numbers depend on

- CPU
- Python Version
- Operating System

Typical ranking

| Method | Speed |
|---------|------|
| List Comprehension | ⭐⭐⭐⭐⭐ |
| map() | ⭐⭐⭐⭐ |
| Loop | ⭐⭐⭐ |
| Generator | Different Goal |

---

# Why are List Comprehensions Faster?

Consider this loop.

```python
result = []

for x in numbers:

    result.append(x*x)
```

Each iteration

- Finds append()
- Calls append()
- Executes Python bytecode

There is overhead.

---

List comprehension

```python
[
    x*x
    for x in numbers
]
```

is optimized internally.

Python uses a dedicated bytecode instruction.

Less overhead.

Fewer operations.

---

# Conceptual Execution

Traditional

```
Loop

↓

Find append()

↓

Call append()

↓

Repeat
```

Comprehension

```
Loop

↓

Store Value

↓

Repeat
```

Fewer steps.

---

# CPython Optimization

Internally,

CPython generates specialized bytecode for list comprehensions.

One important instruction is

```
LIST_APPEND
```

instead of repeatedly performing method lookups.

You don't need to memorize the opcode.

Just understand

Python recognizes list comprehensions as a common pattern and optimizes them.

---

# Measuring Performance

Python provides

```python
timeit
```

---

Example

```python
import timeit

time = timeit.timeit(
    "[x*x for x in range(1000)]",
    number=1000
)

print(time)
```

---

# Timing a Loop

```python
import timeit

code = """

result=[]

for x in range(1000):
    result.append(x*x)

"""

print(
    timeit.timeit(
        code,
        number=1000
    )
)
```

---

# Don't Use `time.time()`

Bad

```python
import time

start = time.time()

# code

print(time.time()-start)
```

Use

```python
timeit
```

instead.

It is more accurate.

---

# Memory Usage

Traditional Loop

```
Memory

↓

List

↓

Append

↓

Append

↓

Append
```

---

List Comprehension

```
Memory

↓

Optimized List Construction
```

---

Generator

```
Memory

↓

One Value

↓

Next Value

↓

Next Value
```

Almost constant memory.

---

# Benchmark Example

Suppose

```
10 Million Numbers
```

Traditional loop

```
Fast
```

List comprehension

```
Faster
```

Generator

```
Much Less Memory
```

---

# Big-O Complexity

Traditional

```
O(n)
```

List Comprehension

```
O(n)
```

Both visit every element.

The difference is

**constant factors**

not algorithm complexity.

---

# Performance vs Readability

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
    complicated_business_logic(
        x,
        y,
        z
    )
    for ...
]
```

Performance gains are not worth losing readability.

---

# map() vs List Comprehension

Example

```python
list(
    map(
        str.upper,
        words
    )
)
```

Equivalent

```python
[
    word.upper()
    for word in words
]
```

Most Python developers prefer

List Comprehensions

because

- easier to read
- easier to debug
- more flexible

---

# Generator vs List Comprehension

List

```python
[
    x*x
    for x in numbers
]
```

Generator

```python
(
    x*x
    for x in numbers
)
```

Difference

List

```
Entire list

↓

Memory
```

Generator

```
One value

↓

Next value

↓

Next value
```

Generators are covered in a later chapter.

---

# AI Example 1

Embedding Lengths

```python
lengths = [
    len(vector)
    for vector in embeddings
]
```

Fast.

Readable.

---

# AI Example 2

Document Titles

```python
titles = [
    doc.metadata["title"]
    for doc in documents
]
```

---

# AI Example 3

Chunk Sizes

```python
sizes = [
    len(chunk)
    for chunk in chunks
]
```

---

# AI Example 4

Extract User Messages

```python
messages = [
    m["content"]
    for m in history
]
```

Exactly the style used in many production AI applications.

---

# NumPy Note

If your data consists entirely of numbers,

NumPy is often **much faster** than Python lists.

Example

Python

```python
[
    x*x
    for x in numbers
]
```

NumPy

```python
array * array
```

NumPy performs vectorized operations written in optimized native code.

We'll study this later.

---

# Common Mistakes

## Optimizing Too Early

Don't rewrite readable code

just because

a benchmark shows a tiny improvement.

Follow

> Make it work.

↓

Make it readable.

↓

Then optimize.

---

## Ignoring Memory

Creating

```
100 Million

Items
```

inside a list comprehension

still creates

```
100 Million

Objects
```

Generators may be a better choice.

---

# Best Practices

✅ Prefer readability.

✅ Benchmark before optimizing.

✅ Use `timeit`.

✅ Use list comprehensions for simple transformations.

✅ Use generators for large streams.

---

# Debugging Tip

When performance matters,

measure.

Never guess.

---

# Interview Questions

1. Why are list comprehensions faster?

2. Difference between complexity and constant factors.

3. Explain LIST_APPEND.

4. Difference between comprehension and generator.

5. Why use `timeit`?

6. When should generators be preferred?

7. When is NumPy faster?

---

# Exercises

## Easy

Benchmark

Loop

vs

List Comprehension

---

Benchmark

List

vs

Generator

---

## Medium

Create

1 Million Squares

using

- loop
- comprehension
- map

Measure execution time.

---

## Advanced

Read a CSV file containing

100,000 rows.

Extract

- Names
- Emails
- Salaries

using

1. Loop

2. Comprehension

Compare timings.

---

# Mini Project

Build a **Python Benchmark Tool**.

The program should compare

- Loop
- List Comprehension
- map()
- Generator

Display

- Execution Time
- Memory Usage
- Recommendation

for each method.

---

# Summary

List comprehensions are usually:

- More readable
- Slightly faster
- Optimized by CPython
- Widely used in production code

However,

performance should never come at the cost of readability.

Measure first.

Optimize second.

---

# Next Section

➡ **08-memory-usage.md**

You'll learn how Python stores list comprehensions in memory, why generators are memory-efficient, and how to choose the right data structure for large AI workloads.
