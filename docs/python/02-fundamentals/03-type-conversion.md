# Type Conversion

Python allows converting one data type into another.

---

# int()

```python
age = int("50")
```

---

# float()

```python
price = float("99.95")
```

---

# str()

```python
text = str(100)
```

---

# bool()

```python
bool(1)

bool(0)

bool("")
```

---

# list()

```python
list("Python")
```

Result

```
['P','y','t','h','o','n']
```

---

# tuple()

```python
tuple([1,2,3])
```

---

# set()

```python
set([1,2,2,3])
```

Duplicates are removed.

---

# dict()

```python
dict(name="Ajit", age=50)
```

---

# Common Errors

```python
int("Hello")
```

Produces

```
ValueError
```

Always validate input before converting.
