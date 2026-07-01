# String Methods

Python provides dozens of built-in methods.

---

# Case Conversion

```python
text.upper()

text.lower()

text.title()

text.capitalize()

text.swapcase()
```

---

# Remove Spaces

```python
text.strip()

text.lstrip()

text.rstrip()
```

---

# Search

```python
text.find("AI")

text.index("AI")
```

Difference:

- `find()` returns `-1`
- `index()` raises an exception

---

# Replace

```python
text.replace("AI","Python")
```

---

# Split

```python
text.split(",")
```

---

# Join

```python
",".join(names)
```

---

# Startswith

```python
text.startswith("Hello")
```

---

# Endswith

```python
text.endswith(".pdf")
```

---

# Count

```python
text.count("AI")
```

---

# Check Methods

```python
isalpha()

isdigit()

isalnum()

isspace()

islower()

isupper()

istitle()
```

---

# Common Chain

```python
text.strip().lower()
```

---

# AI Example

```python
prompt = prompt.strip()
```

Always clean user input.
