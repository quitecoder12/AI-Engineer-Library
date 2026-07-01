# String Formatting

Python supports several formatting techniques.

---

# f-Strings (Recommended)

```python
name = "Ajit"

print(f"Hello {name}")
```

---

# Multiple Variables

```python
age = 50

print(f"{name} is {age} years old.")
```

---

# Expressions

```python
print(f"{10+20}")
```

---

# Decimal Places

```python
pi = 3.1415926

print(f"{pi:.2f}")
```

---

# Alignment

```python
print(f"{name:<20}")

print(f"{name:^20}")

print(f"{name:>20}")
```

---

# Padding

```python
print(f"{5:05}")
```

Output

```
00005
```

---

# Thousands Separator

```python
salary = 62000

print(f"{salary:,}")
```

Output

```
62,000
```

---

# Percentage

```python
accuracy = 0.956

print(f"{accuracy:.2%}")
```

---

# Old Formatting

```python
"%s" % name
```

Avoid in new code.

---

# format()

```python
"Hello {}".format(name)
```

Still supported but f-strings are preferred.
