# Operators

> Operators are symbols that perform operations on values and variables.

---

# Learning Objectives

After this chapter you will understand:

- Arithmetic operators
- Assignment operators
- Comparison operators
- Logical operators
- Membership operators
- Identity operators
- Bitwise operators
- Operator precedence

---

# Operator Categories

| Category | Example |
|----------|---------|
| Arithmetic | + - * / |
| Assignment | = += -= |
| Comparison | == != < > |
| Logical | and or not |
| Membership | in |
| Identity | is |
| Bitwise | & \| ^ << >> |

---

# Arithmetic Operators

```python
a = 10
b = 3

print(a + b)
print(a - b)
print(a * b)
print(a / b)
print(a // b)
print(a % b)
print(a ** b)
```

Output

```
13
7
30
3.3333
3
1
1000
```

---

# Floor Division

```python
10 // 3
```

Returns

```
3
```

---

# Modulus

```python
10 % 3
```

Returns

```
1
```

Useful for:

- Even/Odd
- Cyclic operations
- Pagination

---

# Exponent

```python
2 ** 10
```

Returns

```
1024
```

---

# Assignment

```python
x = 10
```

---

# Compound Assignment

```python
x += 5

x -= 2

x *= 3

x /= 2
```

Equivalent to

```python
x = x + 5
```

---

# Comparison

```python
10 == 10

10 != 5

10 > 5

10 >= 10

10 < 20

10 <= 15
```

Return values are Boolean.

---

# Logical Operators

## and

```python
age = 20
citizen = True

age >= 18 and citizen
```

---

## or

```python
is_admin or is_manager
```

---

## not

```python
not logged_in
```

---

# Membership

```python
"Python" in ["Python","PHP"]
```

Returns

```
True
```

---

```python
"AI" not in skills
```

---

# Identity

```python
a = None

a is None
```

Preferred over

```python
a == None
```

---

# Identity vs Equality

```python
a = [1,2]
b = [1,2]

a == b
```

Returns

```
True
```

But

```python
a is b
```

Returns

```
False
```

---

# Operator Precedence

```python
2 + 3 * 4
```

Returns

```
14
```

Use parentheses

```python
(2 + 3) * 4
```

Returns

```
20
```

---

# Best Practices

✅ Use parentheses for readability.

✅ Use `is None`.

✅ Avoid unnecessary complexity.

---

# Common Mistakes

❌

```python
if x == None:
```

✔

```python
if x is None:
```

---

# AI Example

```python
if embedding is None:
    raise ValueError("Embedding not generated.")
```

---

# PHP Comparison

PHP

```php
$a === $b;
```

Python

```python
a is b
```

Be careful—they are **not exactly equivalent**.

---

# Interview Questions

1. Difference between `/` and `//`
2. Difference between `==` and `is`
3. Explain operator precedence.
4. When should `is None` be used?

---

# Exercises

1. Find if a number is even.
2. Find the largest of three numbers.
3. Calculate compound interest using `**`.
