# Conditional (if-else) List Comprehensions

> **Filtering chooses whether to keep an item. Conditional expressions choose what value to store.**

---

# Learning Objectives

After completing this section, you will be able to:

- Understand the difference between filtering and conditional expressions
- Use `if-else` inside list comprehensions
- Transform data based on conditions
- Avoid common syntax mistakes
- Apply conditional comprehensions in AI applications

---

# Prerequisites

Before reading this chapter, you should understand:

- List comprehensions
- Filtering (`if`)
- Python conditions
- Boolean expressions

---

# A Common Beginner Confusion

Many beginners confuse these two expressions.

Filtering

```python
[
    x
    for x in numbers
    if x > 5
]
```

Conditional Expression

```python
[
    x if x > 5 else 0
    for x in numbers
]
```

They are **NOT** the same.

---

# Filtering

Filtering decides

```
Should this item exist
in the new list?

YES

↓

Keep

NO

↓

Discard
```

Example

```python
numbers = [1,2,3,4,5,6]
```

```python
result = [
    x
    for x in numbers
    if x > 3
]
```

Result

```python
[4,5,6]
```

Three items disappeared completely.

---

# Conditional Expression

Instead of removing items,

we replace them.

```python
numbers = [1,2,3,4,5,6]
```

```python
result = [
    x if x > 3 else 0
    for x in numbers
]
```

Result

```python
[0,0,0,4,5,6]
```

Notice

The list length stays exactly the same.

---

# Visual Comparison

Filtering

```
1

↓

Discard

2

↓

Discard

3

↓

Discard

4

↓

Keep

5

↓

Keep
```

Result

```
[4,5]
```

---

Conditional Expression

```
1

↓

Replace with 0

2

↓

Replace with 0

3

↓

Replace with 0

4

↓

Keep

5

↓

Keep
```

Result

```
[0,0,0,4,5]
```

---

# General Syntax

```python
[
    value_if_true
    if condition
    else value_if_false
    for item in iterable
]
```

Notice carefully.

The **if-else** comes

BEFORE

the `for`.

---

# Execution Order

```
Take Item

↓

Evaluate Condition

↓

True?

↓

YES

↓

Store First Expression

↓

NO

↓

Store Second Expression

↓

Next Item
```

---

# Example 1

Positive / Negative

```python
numbers = [-2,-1,0,1,2]
```

```python
labels = [
    "Positive"
    if n > 0
    else "Not Positive"
    for n in numbers
]
```

Result

```python
[
"Not Positive",
"Not Positive",
"Not Positive",
"Positive",
"Positive"
]
```

---

# Example 2

Pass / Fail

```python
marks = [35,72,81,19,45]
```

```python
status = [
    "Pass"
    if mark >= 40
    else "Fail"
    for mark in marks
]
```

Result

```python
[
"Fail",
"Pass",
"Pass",
"Fail",
"Pass"
]
```

---

# Example 3

Even / Odd

```python
result = [
    "Even"
    if x % 2 == 0
    else "Odd"
    for x in range(10)
]
```

---

# Example 4

Uppercase / Lowercase

```python
words = [
    "Python",
    "AI",
    "RAG"
]
```

```python
result = [
    word.upper()
    if len(word) > 2
    else word.lower()
    for word in words
]
```

---

# Multiple Transformations

```python
numbers = [-5,-1,2,9]
```

```python
result = [
    abs(n)
    if n < 0
    else n * 10
    for n in numbers
]
```

Result

```python
[
5,
1,
20,
90
]
```

---

# AI Example 1

Classify Confidence

```python
scores = [
    0.92,
    0.45,
    0.81,
    0.12
]
```

```python
labels = [
    "Trusted"
    if score >= 0.90
    else "Review"
    for score in scores
]
```

---

# AI Example 2

Prompt Priority

```python
prompts = [
    {
        "text":"Summarize",
        "priority":1
    },
    {
        "text":"Translate",
        "priority":5
    }
]
```

```python
priority = [
    "High"
    if p["priority"] >= 3
    else "Low"
    for p in prompts
]
```

---

# AI Example 3

Chunk Size

```python
chunks = [
    "small",
    "large text here...",
    "tiny"
]
```

```python
labels = [
    "Large"
    if len(chunk) > 100
    else "Small"
    for chunk in chunks
]
```

---

# AI Example 4

OpenAI Messages

```python
messages = [
    {
        "role":"system"
    },
    {
        "role":"user"
    }
]
```

```python
icons = [
    "🤖"
    if m["role"] == "system"
    else "👤"
    for m in messages
]
```

---

# Combining Transformation and Filtering

You can combine both.

```python
result = [
    x * 10
    if x % 2 == 0
    else x
    for x in numbers
    if x > 0
]
```

Execution

```
Filter

↓

Transform

↓

Store
```

---

# Common Syntax Mistake

Many beginners write

❌

```python
[
    x
    for x in numbers
    if x > 5
    else 0
]
```

This is invalid.

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

Remember

```
Expression

↓

if

↓

else

↓

for
```

---

# Nested Conditional Expression

Possible

```python
[
    "A"
    if score >= 90
    else "B"
    if score >= 75
    else "C"
    for score in scores
]
```

But readability suffers.

Prefer a normal loop or function.

---

# PHP Comparison

PHP

```php
$result = [];

foreach($marks as $mark){

    $result[] =
        $mark >= 40
        ? "Pass"
        : "Fail";

}
```

Python

```python
result = [
    "Pass"
    if mark >= 40
    else "Fail"
    for mark in marks
]
```

---

# Best Practices

✅ Keep conditions short.

✅ Keep expressions simple.

✅ Use helper functions for complicated logic.

✅ Prefer readability over cleverness.

---

# Common Mistakes

❌ Confusing filtering with conditional expressions.

❌ Writing nested ternary expressions.

❌ Mixing business logic into one comprehension.

---

# Performance

Conditional expressions have the same complexity as ordinary comprehensions.

```
O(n)
```

Every element must be processed exactly once.

---

# Interview Questions

1. Difference between filtering and conditional expressions.

2. Explain the syntax.

3. Why is the `if-else` before the `for`?

4. Can filtering and conditional expressions be combined?

5. When should you avoid conditional comprehensions?

---

# Exercises

## Easy

Convert

```python
[2,5,7,8]
```

into

```python
[
"Even",
"Odd",
"Odd",
"Even"
]
```

---

## Medium

Replace negative numbers with zero.

---

Convert marks into grades.

---

## Advanced

Given

```python
employees = [

{
"name":"Ajit",
"salary":62000
},

{
"name":"Rahul",
"salary":35000
}

]
```

Create

```python
[
"Senior",
"Junior"
]
```

using a conditional comprehension.

---

# Mini Project

Build a **Risk Classification System**.

Input

```python
[
0.91,
0.22,
0.83,
0.67
]
```

Output

```python
[
"High",
"Low",
"Medium",
"Medium"
]
```

using list comprehensions.

---

# Summary

Filtering answers:

> Should this item be included?

Conditional expressions answer:

> What value should this item become?

Understanding this distinction is one of the most important steps toward mastering list comprehensions.

---

# Next Section

➡ **05-nested-comprehensions.md**

You'll learn how to work with matrices, nested lists, and multidimensional data using nested list comprehensions.
