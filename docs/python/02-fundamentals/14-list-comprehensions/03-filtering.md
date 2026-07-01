
# Filtering

> **One of the biggest advantages of list comprehensions is the ability to filter data while creating a new list.**

---

# Learning Objectives

After completing this section you will be able to:

- Filter elements using `if`
- Combine transformation and filtering
- Understand execution order
- Build efficient filtering pipelines
- Apply filtering in AI applications
- Avoid common mistakes

---

# Prerequisites

You should already understand:

- List comprehensions
- for loops
- if statements
- Comparison operators

---

# What is Filtering?

Filtering means **keeping only the elements that satisfy a condition**.

Suppose you have

```python
numbers = [1,2,3,4,5,6,7,8,9,10]
```

You only want even numbers.

Result

```python
[2,4,6,8,10]
```

---

# Traditional Approach

```python
even_numbers = []

for number in numbers:

    if number % 2 == 0:
        even_numbers.append(number)
```

---

# List Comprehension

```python
even_numbers = [
    number
    for number in numbers
    if number % 2 == 0
]
```

Much shorter.

Much more readable.

---

# General Syntax

```python
[
    expression
    for item in iterable
    if condition
]
```

Notice the order.

```
Expression

↓

Loop

↓

Filter
```

---

# Execution Flow

```
numbers

↓

Take First Number

↓

Condition?

↓

YES

↓

Evaluate Expression

↓

Append

↓

Next Number

↓

Repeat
```

Only items satisfying the condition are included.

---

# Example 1

Keep Positive Numbers

```python
numbers = [-5,-2,0,2,4,8]
```

```python
positive = [
    n
    for n in numbers
    if n > 0
]
```

Result

```python
[2,4,8]
```

---

# Example 2

Odd Numbers

```python
odd = [
    x
    for x in range(20)
    if x % 2 == 1
]
```

---

# Example 3

Numbers Greater Than 50

```python
scores = [
    12,
    45,
    88,
    61,
    92
]

passed = [
    score
    for score in scores
    if score >= 50
]
```

Result

```python
[88,61,92]
```

---

# Example 4

Long Words

```python
words = [
    "AI",
    "Python",
    "Engineering",
    "ML"
]
```

```python
long_words = [
    word
    for word in words
    if len(word) > 5
]
```

Result

```python
[
"Python",
"Engineering"
]
```

---

# Filtering Strings

```python
languages = [

"Python",

"PHP",

"Java",

"Rust"

]
```

Keep only words beginning with P.

```python
result = [

language

for language in languages

if language.startswith("P")

]
```

Result

```python
["Python","PHP"]
```

---

# Filtering Dictionaries

Very common.

```python
employees = [

{
    "name":"Ajit",
    "salary":62000
},

{
    "name":"Rahul",
    "salary":45000
},

{
    "name":"John",
    "salary":72000
}

]
```

Employees earning more than 60,000.

```python
high_salary = [

employee

for employee in employees

if employee["salary"] > 60000

]
```

---

# Filtering Object Attributes

```python
premium_users = [

user

for user in users

if user.is_premium

]
```

Very common in Django, FastAPI and AI projects.

---

# Combining Transformation and Filtering

Suppose we want

- only even numbers
- multiplied by 10

Traditional

```python
result = []

for number in numbers:

    if number % 2 == 0:
        result.append(number * 10)
```

Comprehension

```python
result = [

number * 10

for number in numbers

if number % 2 == 0

]
```

Result

```python
[20,40,60,80,100]
```

---

# Important Rule

Filtering always happens **before** adding the item to the new list.

Think of it like

```
Take Item

↓

Check Condition

↓

Pass?

↓

YES

↓

Evaluate Expression

↓

Append

↓

NO

↓

Discard
```

---

# Multiple Conditions

```python
eligible = [

student

for student in students

if student.age >= 18

if student.passed

]
```

Equivalent to

```python
if student.age >=18 and student.passed
```

---

# Using Logical Operators

```python
result = [

x

for x in numbers

if x > 10 and x < 50

]
```

---

# Membership Filtering

```python
languages = [

"Python",

"PHP",

"Rust",

"Go"

]
```

```python
result = [

language

for language in languages

if "P" in language

]
```

Result

```python
[
"Python",
"PHP"
]
```

---

# Filtering Empty Strings

Very useful.

```python
names = [

"Ajit",

"",

"Rahul",

"",

"John"

]
```

```python
clean = [

name

for name in names

if name

]
```

Result

```python
[
"Ajit",
"Rahul",
"John"
]
```

---

# AI Example 1

Remove Empty Chunks

```python
chunks = [

"Python",

"",

"AI",

""

]
```

```python
chunks = [

chunk

for chunk in chunks

if chunk

]
```

---

# AI Example 2

High Confidence Predictions

```python
predictions = [

{
"label":"Cat",
"score":0.97
},

{
"label":"Dog",
"score":0.42
}

]
```

```python
trusted = [

prediction

for prediction in predictions

if prediction["score"] > 0.90

]
```

---

# AI Example 3

OpenAI Messages

Keep only user messages.

```python
messages = [

message

for message in history

if message["role"] == "user"

]
```

---

# AI Example 4

Large Documents

```python
documents = [

doc

for doc in documents

if len(doc.page_content) > 500

]
```

---

# Performance

Filtering using comprehensions is usually slightly faster than:

```python
for

append()
```

because CPython optimizes the execution.

Complexity remains

```
O(n)
```

Every item must still be examined.

---

# Common Mistakes

## Wrong Order

Incorrect

```python
[

x

if x > 5

for x in numbers

]
```

This syntax is invalid.

Correct

```python
[

x

for x in numbers

if x > 5

]
```

---

## Modifying Original List

This

```python
filtered = [

x

for x in numbers

if x > 10

]
```

creates a **new list**.

It does **not** modify

```
numbers
```

---

## Complex Conditions

Avoid

```python
result = [

employee

for employee in employees

if employee.active

and employee.salary > 50000

and employee.country == "India"

and employee.department == "AI"

and employee.experience > 10

]
```

Consider a normal loop if readability suffers.

---

# PHP Comparison

PHP

```php
$result = [];

foreach($numbers as $n){

    if($n>10){

        $result[] = $n;

    }

}
```

Python

```python
result = [

n

for n in numbers

if n > 10

]
```

---

# Best Practices

✅ Keep filter conditions simple.

✅ Use descriptive variable names.

✅ Break complex logic into functions.

✅ Prefer readability over cleverness.

---

# Interview Questions

1. Explain filtering in list comprehensions.

2. What is the execution order?

3. Can multiple `if` conditions be used?

4. What is the time complexity?

5. Does filtering modify the original list?

---

# Exercises

## Easy

Create a list containing only odd numbers.

---

Create a list of names longer than four characters.

---

Keep numbers greater than 100.

---

## Medium

Given

```python
employees
```

Return only employees earning more than ₹60,000.

---

Filter all PDF files.

Hint

```
endswith(".pdf")
```

---

## Advanced

Given a collection of AI documents

Return only documents

- larger than 1000 characters
- language = English
- score > 0.90

using one comprehension.

---

# Mini Project

Create a **Student Filter System**.

Each student contains

- name
- marks
- branch

Generate:

- Passed students
- Failed students
- Top scorers
- Computer Science students

using list comprehensions.

---

# Summary

Filtering makes list comprehensions dramatically more powerful.

Instead of:

1. Creating a list
2. Looping
3. Testing
4. Appending

you can express the same logic in a single, readable expression.

Filtering is one of the most common patterns you'll encounter in production Python, AI frameworks, and data processing pipelines.

---

# Next Section

➡ **04-if-else-comprehensions.md**

You'll learn how to choose **between two values** while building a list—a feature that is often confused with filtering but serves a different purpose.
