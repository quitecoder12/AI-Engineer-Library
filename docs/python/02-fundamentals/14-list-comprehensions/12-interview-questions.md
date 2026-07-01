# List Comprehensions Interview Questions

> **This chapter contains interview questions ranging from beginner to senior AI Engineer level. Understanding *why* an answer is correct is far more important than memorizing it.**

---

# Learning Objectives

After completing this chapter, you will be able to:

- Answer common Python interview questions
- Explain the advantages and disadvantages of list comprehensions
- Write list comprehensions confidently
- Recognize poor coding practices
- Understand performance trade-offs
- Solve coding interview problems

---

# Interview Difficulty Levels

| Level | Experience |
|---------|------------|
| 🟢 Beginner | 0–1 Year |
| 🔵 Intermediate | 1–3 Years |
| 🟠 Advanced | 3–5 Years |
| 🔴 Senior | 5+ Years |

---

# Beginner Questions

---

## Question 1

### What is a list comprehension?

### Answer

A list comprehension is a concise way of creating a new list by applying an expression to every item in an iterable.

Example

```python
numbers = [
    x
    for x in range(5)
]
```

Equivalent to

```python
numbers = []

for x in range(5):
    numbers.append(x)
```

---

## Question 2

### Why use list comprehensions?

Expected points

- Less code
- More readable
- Pythonic
- Usually faster
- Easier to maintain

---

## Question 3

Write a list comprehension that creates

```
[1,4,9,16,25]
```

Answer

```python
squares = [
    x * x
    for x in range(1,6)
]
```

---

## Question 4

Convert

```python
names = []

for employee in employees:
    names.append(employee.name)
```

into a list comprehension.

Answer

```python
names = [
    employee.name
    for employee in employees
]
```

---

## Question 5

How do you filter values?

Answer

```python
[
    x
    for x in numbers
    if x % 2 == 0
]
```

---

# Intermediate Questions

---

## Question 6

Explain the difference between

```python
[
    x
    for x in numbers
    if x > 5
]
```

and

```python
[
    x if x > 5 else 0
    for x in numbers
]
```

Expected Answer

First

↓

Filters

Second

↓

Transforms

---

## Question 7

What is wrong with

```python
[
    print(x)
    for x in numbers
]
```

Answer

List comprehensions should create data.

Not produce side effects.

---

## Question 8

Why are list comprehensions often faster?

Expected Answer

CPython optimizes them using specialized bytecode.

Less overhead.

---

## Question 9

What is the complexity?

Answer

```
O(n)
```

Every item must still be processed.

---

## Question 10

When should you avoid list comprehensions?

Expected Answer

- Complex business logic
- Exception handling
- Logging
- Deep nesting
- Poor readability

---

# Advanced Questions

---

## Question 11

Difference between

```python
[
    x*x
    for x in numbers
]
```

and

```python
(
    x*x
    for x in numbers
)
```

Answer

List

↓

Entire collection

Generator

↓

Lazy evaluation

---

## Question 12

Why are generators memory efficient?

Answer

They generate one value at a time instead of storing the entire collection.

---

## Question 13

Can list comprehensions modify the original list?

Answer

No.

They create a new list.

Unless the objects themselves are mutable and modified.

---

## Question 14

What happens internally?

Expected Answer

Conceptually

```
Create List

↓

Iterate

↓

Evaluate Expression

↓

Append Result

↓

Return List
```

Internally,

CPython uses optimized bytecode such as

```
LIST_APPEND
```

---

## Question 15

Explain nested list comprehensions.

Answer

They represent nested loops.

Example

```python
[
    value
    for row in matrix
    for value in row
]
```

---

# Senior-Level Questions

---

## Question 16

Would you always replace loops with list comprehensions?

Expected Answer

No.

Readability is more important.

Sometimes a loop is the better solution.

---

## Question 17

Review this code

```python
[
    calculate(
        clean(
            translate(doc)
        )
    )
    for doc in documents
    if validate(doc)
]
```

Expected Answer

Readable?

No.

Better

Use ordinary loops.

---

## Question 18

Explain the memory implications of

```python
[
    x
    for x in range(100_000_000)
]
```

Expected Points

- Entire list stored
- Huge RAM usage
- Generator preferred

---

## Question 19

When would NumPy outperform list comprehensions?

Expected Answer

Numeric arrays.

Vectorized operations.

Native C implementation.

---

## Question 20

How would you benchmark

Loop

vs

Comprehension

Answer

Use

```python
timeit
```

Not

```python
time.time()
```

---

# Coding Questions

---

## Question 21

Return even numbers.

Input

```python
[1,2,3,4,5,6]
```

Expected

```python
[
2,
4,
6
]
```

Solution

```python
[
    x
    for x in numbers
    if x % 2 == 0
]
```

---

## Question 22

Uppercase all strings.

Input

```python
[
"python",

"ai"
]
```

Solution

```python
[
    word.upper()
    for word in words
]
```

---

## Question 23

Extract employee names.

Input

```python
employees = [

{
"name":"Ajit"
},

{
"name":"Rahul"
}

]
```

Solution

```python
[
    employee["name"]
    for employee in employees
]
```

---

## Question 24

Flatten

```python
[
[1,2],

[3,4]
]
```

Solution

```python
[
    value
    for row in matrix
    for value in row
]
```

---

## Question 25

Create coordinate pairs.

Expected

```
(0,0)

(0,1)

...

(2,2)
```

Solution

```python
[
    (x,y)
    for x in range(3)
    for y in range(3)
]
```

---

# AI Engineer Questions

---

## Question 26

Extract all user prompts.

```python
history = [
    {
        "role":"user",
        "content":"Hello"
    },
    {
        "role":"assistant",
        "content":"Hi"
    }
]
```

Solution

```python
[
    message["content"]
    for message in history
    if message["role"] == "user"
]
```

---

## Question 27

Generate prompts.

Input

```python
topics = [

"Python",

"RAG"

]
```

Output

```
Explain Python

Explain RAG
```

Solution

```python
[
    f"Explain {topic}"
    for topic in topics
]
```

---

## Question 28

Remove empty chunks.

Solution

```python
[
    chunk
    for chunk in chunks
    if chunk
]
```

---

## Question 29

Generate embedding lengths.

Solution

```python
[
    len(vector)
    for vector in embeddings
]
```

---

## Question 30

Create experiment combinations.

Input

- Models
- Temperatures

Output

Every combination.

Solution

```python
[
    (model,temp)
    for model in models
    for temp in temperatures
]
```

---

# Code Review Exercise

Which version is better?

A

```python
[
    x*x
    for x in numbers
]
```

B

```python
result = []

for x in numbers:

    result.append(
        x*x
    )
```

Expected Answer

Both are correct.

Version A is preferred because it is shorter and equally readable.

---

# Trick Questions

---

## Does a list comprehension modify the original list?

No.

---

## Can it return None?

Yes.

If the expression returns None.

Example

```python
[
    print(x)
    for x in numbers
]
```

Produces

```python
[
None,
None,
None
]
```

---

## Can it contain try/except?

No.

Use a normal loop.

---

## Can it contain break?

No.

---

## Can it contain continue?

No.

---

## Can it contain multiple if statements?

Yes.

```python
[
    x
    for x in numbers
    if x > 10
    if x % 2 == 0
]
```

---

# Interview Tips

When answering:

Don't simply say

> "Because it's Pythonic."

Explain

- readability
- maintainability
- performance
- memory
- trade-offs

Interviewers value reasoning more than memorization.

---

# Practice Challenge

Without looking at previous chapters,

write list comprehensions for

- Squares
- Cubes
- Even numbers
- Odd numbers
- Filtering
- Conditional expressions
- Nested loops
- Flattening
- Prompt generation
- Embedding processing

If you can solve all of these comfortably,

you've mastered list comprehensions.

---

# Summary

You should now be able to answer:

✅ Beginner interview questions

✅ Intermediate coding questions

✅ Senior design discussions

✅ AI engineering scenarios

Mastering these concepts will prepare you for technical interviews involving Python, Data Science, Machine Learning, and AI Engineering.

---

# Next Section

➡ **13-exercises.md**

The next chapter contains **50 progressively challenging exercises**, from beginner to interview-level and real-world AI applications, to help reinforce everything you've learned about list comprehensions.
