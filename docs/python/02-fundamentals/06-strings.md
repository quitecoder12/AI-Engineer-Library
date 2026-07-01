# Strings

> Strings are immutable sequences of Unicode characters.

---

# Learning Objectives

You will learn:

- Creating strings
- Quotes
- Multiline strings
- Indexing
- Slicing
- Immutability
- Length

---

# Creating Strings

```python
name = "Ajit"
```

```python
city = 'Rourkela'
```

---

# Triple Quotes

```python
text = """
Python
AI
LLMs
"""
```

---

# Length

```python
len(name)
```

---

# Indexing

```
Python

012345
```

```python
word = "Python"

word[0]
```

Returns

```
P
```

---

```python
word[-1]
```

Returns

```
n
```

---

# Slicing

```python
word[0:3]
```

Returns

```
Pyt
```

---

```python
word[2:]
```

```
thon
```

---

```python
word[:4]
```

```
Pyth
```

---

```python
word[::-1]
```

Reverse string.

---

# Immutability

Not allowed

```python
word[0] = "J"
```

Produces

```
TypeError
```

Instead

```python
word = "J" + word[1:]
```

---

# Concatenation

```python
first = "AI"

second = "Engineer"

first + " " + second
```

---

# Repetition

```python
"-" * 20
```

---

# Membership

```python
"AI" in "AI Engineer"
```

---

# Escape Characters

```python
\n

\t

\\

\"
```

---

# Raw Strings

Useful for Windows paths.

```python
path = r"C:\Users\Ajit"
```

---

# Best Practices

- Prefer double quotes.
- Use f-strings.
- Avoid string concatenation in loops.

---

# AI Example

```python
prompt = """
Summarize the following article.
"""
```

---

# Interview Questions

1. Why are strings immutable?
2. Explain slicing.
3. Difference between indexing and slicing.

---

# Exercises

1. Reverse a string.
2. Count vowels.
3. Check palindrome.
