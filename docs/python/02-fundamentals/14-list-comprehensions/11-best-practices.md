# Best Practices for List Comprehensions

> **Writing a list comprehension is easy. Writing one that is readable, maintainable, and Pythonic is a professional skill.**

---

# Learning Objectives

After completing this chapter you will be able to:

- Write Pythonic list comprehensions
- Follow PEP 8 recommendations
- Improve readability
- Decide when not to use a comprehension
- Write production-quality code
- Review other developers' code confidently

---

# What Makes a Good List Comprehension?

A good list comprehension should be:

- Easy to read
- Easy to understand
- Easy to maintain
- Easy to debug

The shortest code is **not** always the best code.

---

# The Golden Rule

> **Readability counts.**

This comes directly from **The Zen of Python**.

Run this command anytime:

```python
import this
```

One of its most famous principles is:

```
Readability counts.
```

This principle should guide every list comprehension you write.

---

# Rule 1
## One Purpose Per Comprehension

Good

```python
names = [
    user.name
    for user in users
]
```

Bad

```python
results = [
    complicated_function(user)
    for user in users
    if validate(user)
    if has_permission(user)
    if user.active
]
```

Every comprehension should solve **one problem**.

---

# Rule 2
## Keep Expressions Simple

Good

```python
prices = [
    product.price
    for product in products
]
```

Bad

```python
prices = [
    calculate_discounted_price(product)
    for product in products
]
```

Better

```python
def discounted_price(product):
    ...

prices = [
    discounted_price(product)
    for product in products
]
```

---

# Rule 3
## Use Meaningful Variable Names

Bad

```python
[
    x.name
    for x in users
]
```

Better

```python
[
    user.name
    for user in users
]
```

Even better

```python
[
    employee.name
    for employee in employees
]
```

Readable names improve code quality.

---

# Rule 4
## Avoid Side Effects

Never write

```python
[
    print(item)
    for item in items
]
```

or

```python
[
    database.save(item)
    for item in items
]
```

List comprehensions should create lists.

Not perform actions.

---

# Rule 5
## Maximum Two Nested Loops

Good

```python
[
    value
    for row in matrix
    for value in row
]
```

Avoid

```python
[
    value
    for a in A
    for b in B
    for c in C
    for d in D
]
```

When nesting becomes deep,

use normal loops.

---

# Rule 6
## Keep Conditions Small

Good

```python
[
    employee
    for employee in employees
    if employee.active
]
```

Avoid

```python
[
    employee
    for employee in employees
    if employee.active
    and employee.salary > 70000
    and employee.department == "AI"
    and employee.country == "India"
]
```

Break large conditions into helper functions.

---

# Rule 7
## Prefer Helper Functions

Instead of

```python
[
    complicated_transformation(document)
    for document in documents
]
```

Use

```python
def clean_document(document):
    ...

clean_documents = [
    clean_document(document)
    for document in documents
]
```

Now the comprehension clearly communicates its intent.

---

# Rule 8
## Keep One Line When Possible

Good

```python
squares = [x*x for x in numbers]
```

If the line becomes too long,

split it.

Good

```python
embeddings = [
    embedding_model.embed(text)
    for text in documents
]
```

---

# Rule 9
## Follow PEP 8

Long comprehensions should be formatted vertically.

Recommended

```python
results = [
    employee.name
    for employee in employees
    if employee.active
]
```

Avoid

```python
results = [employee.name for employee in employees if employee.active]
```

when the line becomes difficult to read.

---

# Rule 10
## Don't Optimize Prematurely

Bad mindset

> List comprehensions are faster, so I'll use them everywhere.

Better mindset

> I'll choose the clearest solution first.

Performance comes later.

---

# Rule 11
## Prefer Comprehensions Over map()

Most Python developers prefer

```python
[
    word.upper()
    for word in words
]
```

instead of

```python
list(
    map(
        str.upper,
        words
    )
)
```

Both work.

The comprehension is often easier to read.

---

# Rule 12
## Don't Fear Normal Loops

There is nothing wrong with

```python
results = []

for item in items:

    if valid(item):

        results.append(
            process(item)
        )
```

Sometimes this is the best solution.

---

# Production Example

Instead of

```python
embeddings = [
    model.embed(clean(translate(document)))
    for document in documents
]
```

Professional code often looks like

```python
embeddings = []

for document in documents:

    translated = translate(document)

    cleaned = clean(translated)

    embedding = model.embed(cleaned)

    embeddings.append(embedding)
```

This version is:

- easier to debug
- easier to log
- easier to test
- easier to maintain

---

# AI Engineering Best Practices

## Prompt Generation

Good

```python
prompts = [
    f"Summarize: {text}"
    for text in documents
]
```

---

## Message Extraction

Good

```python
user_messages = [
    message["content"]
    for message in history
    if message["role"] == "user"
]
```

---

## Embedding Pipeline

Good

```python
vectors = [
    model.embed(chunk)
    for chunk in chunks
]
```

---

## Batch Creation

Good

```python
batches = [
    items[i:i+100]
    for i in range(0, len(items), 100)
]
```

---

# Code Review Checklist

Ask yourself:

- Is the purpose obvious?
- Is the variable name meaningful?
- Is there only one transformation?
- Is the expression short?
- Would a loop be clearer?
- Can another developer understand it quickly?

If any answer is "No",

consider rewriting.

---

# Readability Scale

★★★★★

```python
[
    x*x
    for x in numbers
]
```

★★★★☆

```python
[
    user.name
    for user in users
]
```

★★★☆☆

```python
[
    user.name.upper()
    for user in users
    if user.active
]
```

★★☆☆☆

```python
[
    complicated(user)
    for user in users
    if validate(user)
]
```

★☆☆☆☆

```python
[
    process(a,b,c,d)
    for ...
    for ...
    if ...
    if ...
]
```

---

# Comparison

Readable

```python
active_users = [
    user
    for user in users
    if user.active
]
```

Unreadable

```python
active_users = [
    process(user)
    if validate(user)
    else default(user)
    for user in users
    if user.active
    if user.salary > 70000
]
```

---

# Common Advice from Python Core Developers

Python's philosophy is not

> "Use comprehensions everywhere."

Instead

> "Use the simplest solution that communicates intent."

---

# Interview Questions

1. When should you avoid list comprehensions?
2. Why are helper functions useful?
3. Why should side effects be avoided?
4. What does PEP 8 recommend?
5. Why are meaningful variable names important?

---

# Exercises

## Easy

Rewrite five loops as list comprehensions.

---

## Medium

Take five unreadable comprehensions.

Rewrite them as readable comprehensions.

---

## Advanced

Review an open-source Python project.

Identify:

- Good comprehensions
- Poor comprehensions

Explain your reasoning.

---

# Mini Project

Perform a code review on a Python file containing 30 list comprehensions.

For each one:

- Rate readability (1–5 stars)
- Explain improvements
- Rewrite if necessary

---

# Professional Guidelines

When writing production Python:

✔ Prefer clarity.

✔ Keep comprehensions short.

✔ One responsibility per comprehension.

✔ Avoid side effects.

✔ Don't fear ordinary loops.

✔ Write code that your teammates will thank you for.

---

# Summary

List comprehensions are one of Python's best features—but only when used wisely.

Professional developers value:

- Readability
- Maintainability
- Simplicity
- Explicitness

A good comprehension should make the code easier to understand, not harder.

---

# Next Section

➡ **12-interview-questions.md**

In the next chapter, we'll cover beginner, intermediate, and senior-level interview questions on list comprehensions, including coding exercises and real interview scenarios from top technology companies.
