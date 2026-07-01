# Exercises

> **The best way to master list comprehensions is to write them yourself. Reading code helps you recognize patterns, but writing code builds real skill.**

---

# Learning Objectives

After completing these exercises, you will be able to:

- Write list comprehensions naturally
- Convert loops into comprehensions
- Use filtering confidently
- Use conditional expressions
- Write nested comprehensions
- Solve real-world AI problems

---

# Difficulty Levels

| Level | Description |
|--------|-------------|
| 🟢 Beginner | Basic syntax |
| 🔵 Intermediate | Filtering & transformations |
| 🟠 Advanced | Nested comprehensions |
| 🔴 Expert | Real-world AI problems |

---

# Part 1 – Beginner Exercises

## Exercise 1

Create the following list.

```
[1,2,3,4,5]
```

Use only a list comprehension.

---

## Exercise 2

Create

```
[10,20,30,40,50]
```

using

```python
range()
```

---

## Exercise 3

Create

```
[0,1,4,9,16,25]
```

---

## Exercise 4

Create cubes

```
[1,8,27,64,125]
```

---

## Exercise 5

Convert

```python
["python","ai","rag"]
```

to uppercase.

Expected

```python
[
"PYTHON",
"AI",
"RAG"
]
```

---

## Exercise 6

Find the length of every word.

Input

```python
[
"Python",
"Programming",
"AI"
]
```

Expected

```python
[
6,
11,
2
]
```

---

## Exercise 7

Convert

```python
["APPLE","BANANA"]
```

to lowercase.

---

## Exercise 8

Create a list of booleans indicating whether each number is even.

Input

```python
[1,2,3,4]
```

Expected

```python
[
False,
True,
False,
True
]
```

---

## Exercise 9

Create

```python
[
"Hello Ajit",
"Hello Rahul",
"Hello John"
]
```

from

```python
names = [
"Ajit",
"Rahul",
"John"
]
```

---

## Exercise 10

Extract the first character of every word.

---

# Part 2 – Filtering

## Exercise 11

Keep only even numbers.

Input

```python
range(20)
```

---

## Exercise 12

Keep only odd numbers.

---

## Exercise 13

Keep numbers greater than 50.

---

## Exercise 14

Keep words longer than five characters.

---

## Exercise 15

Keep only PDF files.

Input

```python
[
"a.pdf",
"b.txt",
"c.pdf"
]
```

---

## Exercise 16

Remove empty strings.

Input

```python
[
"",
"Python",
"",
"AI"
]
```

---

## Exercise 17

Remove None values.

Input

```python
[
1,
None,
3,
None,
5
]
```

---

## Exercise 18

Keep only positive numbers.

---

## Exercise 19

Keep numbers divisible by both

```
3

and

5
```

---

## Exercise 20

Keep words beginning with

```
P
```

---

# Part 3 – Conditional Expressions

## Exercise 21

Convert

```python
[
10,
55,
90
]
```

to

```python
[
"Fail",
"Pass",
"Pass"
]
```

---

## Exercise 22

Replace negative numbers with zero.

---

## Exercise 23

Convert

```python
[
2,
3,
4,
5
]
```

to

```python
[
"Even",
"Odd",
"Even",
"Odd"
]
```

---

## Exercise 24

Convert confidence scores into

```
High

Medium

Low
```

---

## Exercise 25

Replace empty strings with

```
Unknown
```

---

# Part 4 – Nested Comprehensions

## Exercise 26

Flatten

```python
[
[1,2],
[3,4],
[5,6]
]
```

---

## Exercise 27

Extract every character.

Input

```python
[
"AI",
"ML"
]
```

Expected

```python
[
"A",
"I",
"M",
"L"
]
```

---

## Exercise 28

Generate all coordinate pairs.

```
0-2

×

0-2
```

---

## Exercise 29

Generate every

```
Color

×

Size
```

combination.

---

## Exercise 30

Create a multiplication table.

Output

```
(x,y,x*y)
```

---

# Part 5 – Dictionaries

## Exercise 31

Extract all employee names.

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

---

## Exercise 32

Extract salaries.

---

## Exercise 33

Return employees earning more than ₹60,000.

---

## Exercise 34

Return employee emails.

---

## Exercise 35

Return active users only.

---

# Part 6 – AI Exercises

## Exercise 36

Extract all user prompts.

---

## Exercise 37

Extract assistant replies.

---

## Exercise 38

Extract document titles.

---

## Exercise 39

Extract embedding lengths.

---

## Exercise 40

Generate prompts.

Input

```python
[
"Python",
"AI",
"RAG"
]
```

Output

```
Explain Python

Explain AI

Explain RAG
```

---

# Part 7 – Real-World Problems

## Exercise 41

Batch a list into groups of 100.

---

## Exercise 42

Remove duplicate words using

```
set()
```

inside a comprehension where appropriate.

---

## Exercise 43

Normalize ages.

Input

```python
[
18,
25,
40
]
```

Output

```
Age / 100
```

---

## Exercise 44

Generate experiment configurations.

Models

×

Temperatures

×

Datasets

---

## Exercise 45

Generate chatbot greetings.

Example

```
Hello Ajit

Hello Rahul

Hello John
```

---

# Part 8 – Code Conversion

Rewrite each loop as a list comprehension.

---

## Exercise 46

```python
result = []

for number in numbers:

    result.append(number*2)
```

---

## Exercise 47

```python
names = []

for employee in employees:

    names.append(employee.name)
```

---

## Exercise 48

```python
result = []

for word in words:

    if len(word)>5:

        result.append(word)
```

---

## Exercise 49

```python
emails=[]

for user in users:

    if user.active:

        emails.append(user.email)
```

---

## Exercise 50

```python
titles=[]

for document in documents:

    titles.append(document["title"])
```

---

# Bonus Challenges

## Challenge 1

Generate a chessboard.

Output

```
64

Coordinates
```

---

## Challenge 2

Generate every possible password consisting of

```
2 letters

+

2 digits
```

(Hint: use nested loops.)

---

## Challenge 3

Generate all possible API test combinations.

Input

- Models
- Temperatures
- Languages
- Prompt Styles

---

## Challenge 4

Flatten a nested JSON response.

---

## Challenge 5

Create a document preprocessing pipeline using only list comprehensions where appropriate.

---

# AI Mini Project

## Build a Prompt Generator

Input

```python
topics = [
    "Python",
    "AI",
    "RAG"
]

styles = [
    "Beginner",
    "Advanced",
    "Interview"
]
```

Generate

```
Beginner : Python

Beginner : AI

...

Interview : RAG
```

using list comprehensions.

---

# Self-Assessment Checklist

Can you confidently:

☐ Write a basic list comprehension?

☐ Filter values?

☐ Use conditional expressions?

☐ Flatten nested lists?

☐ Process dictionaries?

☐ Read complex comprehensions?

☐ Decide when NOT to use one?

☐ Apply comprehensions in AI projects?

If you answered **Yes** to every question, you've mastered one of Python's most important features.

---

# Next Chapter

➡ **14-mini-project.md**

You'll build a complete **AI Document Processing Pipeline** using everything you've learned in this chapter:

- Cleaning
- Filtering
- Transforming
- Prompt generation
- Batch creation
- Embedding preparation
- Metadata extraction
- Reporting

This project ties together all list comprehension concepts in a realistic AI workflow.
