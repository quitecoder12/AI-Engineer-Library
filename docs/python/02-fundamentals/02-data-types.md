# Data Types

Everything in Python is an object.

---

# Built-in Types

| Type | Example |
|------|---------|
| int | 10 |
| float | 5.5 |
| complex | 2+3j |
| bool | True |
| str | "Python" |
| list | [1,2,3] |
| tuple | (1,2) |
| set | {1,2} |
| dict | {"name":"Ajit"} |
| NoneType | None |

---

# Integer

```python
age = 50
```

---

# Float

```python
price = 99.95
```

---

# Boolean

```python
is_admin = True

is_logged_in = False
```

---

# String

```python
name = "Ajit"
```

---

# List

```python
numbers = [10,20,30]
```

---

# Tuple

```python
point = (5,10)
```

---

# Set

```python
languages = {"Python","PHP","Java"}
```

---

# Dictionary

```python
user = {
    "name":"Ajit",
    "age":50
}
```

---

# None

```python
result = None
```

---

# Type Checking

```python
print(type(10))
```

```python
print(type(True))
```

```python
print(type({}))
```

---

# isinstance()

Preferred over comparing type directly.

```python
age = 50

isinstance(age, int)
```

Returns

```
True
```

---

# Summary Table

| Mutable | Immutable |
|----------|-----------|
| list | int |
| dict | float |
| set | bool |
| | tuple |
| | string |
