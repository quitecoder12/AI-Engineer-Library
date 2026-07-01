# List Comprehensions

> *One of Python's most elegant and powerful features.*

---

## Overview

List comprehensions provide a concise, readable, and Pythonic way to create lists.

Instead of writing several lines of code with loops and `append()`, you can often express the same logic in a single readable statement.

They are used extensively throughout:

- Python Standard Library
- NumPy
- Pandas
- FastAPI
- LangChain
- Hugging Face
- OpenAI SDK
- Streamlit

If you read professional Python code, you'll encounter list comprehensions everywhere.

Mastering them is essential.

---

## Learning Objectives

After completing this chapter you will be able to:

- Understand why list comprehensions exist
- Write basic comprehensions
- Filter data
- Use conditional expressions
- Create nested comprehensions
- Read complex comprehensions
- Convert loops into comprehensions
- Understand performance implications
- Decide when **not** to use comprehensions
- Use comprehensions in AI projects

---

## Prerequisites

Before reading this chapter you should understand:

- Variables
- Lists
- Loops
- Conditions
- Functions

---

## Why This Chapter Matters

Suppose you have:

```python
numbers = []

for i in range(10):
    numbers.append(i)
```

Most Python developers would instead write

```python
numbers = [i for i in range(10)]
```

Same result.

Less code.

Better readability.

---

## Where You'll See Them

Professional Python code

```python
files = [
    file
    for file in directory.iterdir()
]
```

Machine Learning

```python
features = [
    x.age
    for x in customers
]
```

OpenAI

```python
messages = [
    message["content"]
    for message in history
]
```

Pandas

```python
columns = [
    col.lower()
    for col in df.columns
]
```

LangChain

```python
documents = [
    doc.page_content
    for doc in docs
]
```

These examples appear throughout modern AI development.

---

## Chapter Structure

This chapter is divided into multiple sections.

1. Why List Comprehensions
2. Basic Syntax
3. Filtering
4. Conditional Expressions
5. Nested Comprehensions
6. Multiple Loops
7. Performance
8. Memory Usage
9. AI Examples
10. Common Mistakes
11. Best Practices
12. Interview Questions
13. Exercises
14. Mini Project

---

## Learning Tips

Don't memorize syntax.

Instead:

1. Write the loop normally.
2. Understand the logic.
3. Convert it into a comprehension.
4. Compare both versions.

With practice, comprehensions become natural.

---

## Next

➡ **01-why-list-comprehensions.md**
