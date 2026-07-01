# Input and Output

---

# Output

The most common output function is:

```python
print("Hello")
```

---

# Multiple Values

```python
name = "Ajit"

age = 50

print(name, age)
```

---

# Separator

```python
print("Python","AI",sep="-")
```

Output

```
Python-AI
```

---

# End Character

```python
print("Hello", end=" ")

print("World")
```

Output

```
Hello World
```

---

# User Input

```python
name = input("Enter your name: ")
```

---

# Numeric Input

Remember:

`input()` always returns a string.

```python
age = int(input("Age: "))
```

---

# Formatted Output

```python
name = "Ajit"

age = 50

print(f"My name is {name}. I am {age} years old.")
```

---

# Multi-line String

```python
message = """
Welcome
to
Python
"""
```

---

# Best Practices

- Use f-strings for formatting.
- Convert user input to the required type.
- Keep prompts clear and concise.
