# Common Mistakes with List Comprehensions

> **List comprehensions are simple to learn but surprisingly easy to misuse. This chapter covers the mistakes you'll encounter most often and shows how to avoid them.**

---

# Learning Objectives

After completing this chapter, you will be able to:

- Identify common list comprehension mistakes
- Understand why they occur
- Write more readable comprehensions
- Debug broken comprehensions
- Know when to use a normal loop instead
- Follow Pythonic best practices

---

# Why This Chapter Matters

Many beginners think:

> "If I can write it as a list comprehension, I should."

This is **not** true.

The goal is:

> Write the clearest code.

Sometimes that's a comprehension.

Sometimes it's a normal loop.

Professional Python developers make this decision constantly.

---

# Mistake 1

## Trying to Do Too Much

❌ Bad

```python
result = [
    complicated_function(x)
    for x in numbers
    if validate(x)
    if has_permission(x)
    if x > 100
    if x % 5 == 0
]
```

This is difficult to read.

---

✅ Better

```python
result = []

for number in numbers:

    if not validate(number):
        continue

    if not has_permission(number):
        continue

    if number <= 100:
        continue

    if number % 5 != 0:
        continue

    result.append(
        complicated_function(number)
    )
```

---

# Rule

If explaining the comprehension takes longer than reading it...

...use a loop.

---

# Mistake 2

## Confusing Filtering and if-else

Incorrect

```python
[
    x
    for x in numbers
    if x > 5
    else 0
]
```

Produces

```
SyntaxError
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

Filtering

```python
[
    x
    for x in numbers
    if x > 5
]
```

Conditional

```python
[
    x if x > 5 else 0
    for x in numbers
]
```

Different concepts.

---

# Mistake 3

## Forgetting the Expression

Incorrect

```python
[
    for x in numbers
]
```

Every comprehension starts with

```
Expression
```

---

Correct

```python
[
    x
    for x in numbers
]
```

---

# Mistake 4

## Wrong Order

Incorrect

```python
[
    for x in numbers
    x*x
]
```

Correct

```python
[
    x*x
    for x in numbers
]
```

---

# Mental Model

Always read

```
Expression

↓

for

↓

if
```

---

# Mistake 5

## Using append()

Some beginners try

```python
[
    result.append(x)
    for x in numbers
]
```

This is incorrect.

List comprehensions already create the list.

Instead

```python
[
    x
    for x in numbers
]
```

---

# Mistake 6

## Ignoring Return Values

Consider

```python
names = []

result = [
    names.append(x)
    for x in users
]
```

Result

```python
[
None,
None,
None
]
```

Why?

Because

```python
append()
```

returns

```python
None
```

Always understand what your expression returns.

---

# Mistake 7

## Creating Side Effects

Avoid

```python
[
    print(x)
    for x in numbers
]
```

Result

```
[None, None, None...]
```

Comprehensions should create data.

Not perform actions.

---

Better

```python
for number in numbers:
    print(number)
```

---

# Mistake 8

## Nesting Too Many Loops

Possible

```python
[
    ...
    for a in A
    for b in B
    for c in C
    for d in D
]
```

Readable?

Usually not.

---

Recommendation

Maximum

```
2

Nested Loops
```

---

# Mistake 9

## Long Expressions

Bad

```python
[
    calculate_salary_after_tax_and_bonus(employee)
    for employee in employees
]
```

Better

```python
def final_salary(employee):
    ...

result = [
    final_salary(employee)
    for employee in employees
]
```

The comprehension becomes much easier to read.

---

# Mistake 10

## Forgetting That a New List is Created

```python
numbers = [1,2,3]

new_numbers = [
    x*2
    for x in numbers
]
```

Original list

```
[1,2,3]
```

remains unchanged.

---

# Mistake 11

## Using List Comprehensions for Huge Data

Bad

```python
rows = [
    row
    for row in csv_reader
]
```

If

```
10 Million Rows
```

Memory usage can become enormous.

Better

```python
for row in csv_reader:
    process(row)
```

or

Use a generator.

---

# Mistake 12

## Expecting Lazy Evaluation

List

```python
[
    expensive_function(x)
    for x in numbers
]
```

Every function executes immediately.

Generators

```python
(
    expensive_function(x)
    for x in numbers
)
```

execute lazily.

---

# Mistake 13

## Using Comprehensions for Exception Handling

Avoid

```python
[
    process(item)
    for item in items
]
```

if

```
process()
```

may raise exceptions that require handling.

Use

```python
result = []

for item in items:

    try:
        result.append(
            process(item)
        )

    except Exception:
        ...
```

Much clearer.

---

# Mistake 14

## Forgetting Readability

Bad

```python
[
    (
        x+y
        if x>5
        else x-y
    )

    for x in numbers

    for y in values

    if x%2==0

    if y<100
]
```

Can you understand it quickly?

Probably not.

---

Professional developers often rewrite code like this as loops.

---

# AI Example

Bad

```python
embeddings = [

model.embed(

clean(

translate(

document

)

)

)

for document in documents

if validate(document)

]
```

Better

```python
embeddings = []

for document in documents:

    if not validate(document):
        continue

    translated = translate(document)

    cleaned = clean(translated)

    embedding = model.embed(cleaned)

    embeddings.append(embedding)
```

This version is much easier to debug.

---

# Debugging Strategy

When a comprehension doesn't work

Don't stare at it.

Rewrite it.

```python
result = []

for item in items:

    ...

    result.append(...)
```

Debug.

Convert back if appropriate.

Professional developers do this frequently.

---

# Readability Checklist

Before using a comprehension ask yourself

✅ Can another developer understand it in 10 seconds?

✅ Does it express one idea?

✅ Is it shorter **and** clearer?

✅ Does it avoid side effects?

If the answer is "No"

Use a loop.

---

# Performance Myth

Some developers write unreadable comprehensions because they think they're faster.

Example

```python
[
    huge_expression(...)
    for ...
]
```

The tiny performance gain is rarely worth the loss of readability.

---

# AI Engineer Tip

Production AI systems spend far more time:

- Waiting for APIs
- Reading databases
- Performing inference
- Accessing vector databases

than executing list comprehensions.

Optimize the bottlenecks.

Not the syntax.

---

# Summary Table

| Mistake | Better Approach |
|----------|-----------------|
| Too many conditions | Use loops |
| Side effects | Use loops |
| append() inside comprehension | Return values directly |
| Huge datasets | Use generators |
| Long expressions | Helper functions |
| Exception handling | Use loops |
| Complex business logic | Use loops |

---

# Interview Questions

1. What are common mistakes with list comprehensions?
2. Why should side effects be avoided?
3. When should a loop replace a comprehension?
4. Why is readability important?
5. Explain lazy evaluation.

---

# Exercises

## Easy

Find five syntax errors in intentionally broken comprehensions.

---

## Medium

Rewrite five complex comprehensions as ordinary loops.

---

## Advanced

Take an existing Python script and refactor it:

- Replace loops with comprehensions where appropriate.
- Replace unreadable comprehensions with loops.

Explain every decision.

---

# Mini Project

Review a Python file containing **20 intentionally bad list comprehensions**.

For each one:

- Explain the problem.
- Rewrite it.
- Justify your solution.

This is excellent practice for code reviews.

---

# Key Takeaways

✔ List comprehensions are tools—not goals.

✔ Readability is more important than cleverness.

✔ One responsibility per comprehension.

✔ Avoid side effects.

✔ Use loops when logic becomes complex.

✔ Write code that your future self can understand.

---

# Next Section

➡ **11-best-practices.md**

You'll learn the coding standards, style guidelines, and conventions used by professional Python developers and open-source AI projects when writing list comprehensions.
