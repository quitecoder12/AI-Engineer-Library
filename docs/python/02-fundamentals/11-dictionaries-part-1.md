# Dictionaries

> The most important data structure for AI Engineers.

---

# Learning Objectives

After completing this chapter you will understand:

- What dictionaries are
- Hash tables
- Keys
- Values
- Dictionary operations
- Performance
- AI use cases
- JSON relationship
- API responses
- Nested dictionaries

---

# Why Dictionaries Matter

If Lists are the heart of Python,

**Dictionaries are the brain.**

Almost every AI framework returns dictionaries.

Examples include:

- OpenAI Responses
- Hugging Face
- LangChain
- FastAPI
- Streamlit
- JSON APIs
- Configuration files

If you master dictionaries,

you master Python.

---

# Visual Representation

```
Dictionary

┌──────────────┐

name

↓

Ajit

age

↓

50

country

↓

India

└──────────────┘
```

Unlike lists,

dictionaries use **keys** instead of indexes.

---

# Creating Dictionaries

```python
user = {
    "name": "Ajit",
    "age": 50,
    "country": "India"
}
```

---

# Access Values

```python
user["name"]
```

Returns

```
Ajit
```

---

# Using get()

Preferred

```python
user.get("name")
```

If the key doesn't exist:

```python
user.get("salary")
```

Returns

```
None
```

Instead of raising an exception.

---

# Adding New Keys

```python
user["city"] = "Rourkela"
```

---

# Updating

```python
user["age"] = 51
```

---

# Removing

```python
del user["country"]
```

---

Or

```python
user.pop("country")
```

---

# Checking Keys

```python
"name" in user
```

Returns

```
True
```

---

# Length

```python
len(user)
```

---

# Iteration

```python
for key in user:
    print(key)
```

---

Values

```python
for value in user.values():
    print(value)
```

---

Both

```python
for key, value in user.items():
    print(key, value)
```

---

# AI Example

OpenAI Response

```python
response = {
    "model": "gpt-5",
    "usage": {
        "input_tokens": 120,
        "output_tokens": 350
    }
}
```

Access

```python
response["usage"]["output_tokens"]
```

Returns

```
350
```

---

# Time Complexity

| Operation | Complexity |
|------------|------------|
| Lookup | O(1) |
| Insert | O(1) |
| Delete | O(1) |
| Search by Key | O(1) |

Average case.

This speed is possible because dictionaries are implemented using **hash tables**.

---

**To be continued in Part 2:** Internal hash tables, nested dictionaries, dictionary methods, comprehensions, merging, copying, JSON, performance, debugging, interview questions, AI case studies, and exercises.
