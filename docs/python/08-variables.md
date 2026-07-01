# Variables

> Variables store information that can be used later.

---

# Learning Objectives

After this chapter you will understand:

- Variables
- Assignment
- Naming rules
- Naming conventions
- Dynamic typing
- Multiple assignment

---

# What is a Variable?

Think of a variable as a labeled box.

```
+---------+
|  Ajit   |
+---------+
     ▲
     │
   name
```

The variable **name** refers to the value **Ajit**.

---

# Creating Variables

```python
name = "Ajit"
```

```python
age = 50
```

```python
salary = 62000
```

---

# Printing Variables

```python
name = "Ajit"

print(name)
```

Output

```
Ajit
```

---

# Multiple Variables

```python
first_name = "Ajit"

last_name = "Kumar"

city = "Rourkela"
```

---

# Dynamic Typing

Python automatically determines the data type.

```python
x = 10

x = "Hello"

x = 5.6
```

The same variable can hold different data types.

---

# Multiple Assignment

```python
x, y, z = 10, 20, 30
```

---

# Same Value

```python
x = y = z = 100
```

---

# Variable Naming Rules

Allowed

```python
employee_name

student1

_marks
```

Not Allowed

```python
1name

first-name

class
```

---

# Naming Convention

Good

```python
student_name

employee_salary

total_marks
```

Bad

```python
a

abc

x1

temp2
```

Choose meaningful names.

---

# Constants

Python doesn't enforce constants.

Convention:

```python
PI = 3.14159

MAX_USERS = 100
```

Uppercase indicates a value should not change.

---

# Delete Variable

```python
name = "Ajit"

del name
```

---

# Check Type

```python
name = "Ajit"

print(type(name))
```

Output

```
<class 'str'>
```

---

# Memory Model

Variables store **references** to objects.

```
name
  │
  ▼
"Ajit"
```

Understanding this is important later when learning mutability.

---

# Best Practices

✅ Use descriptive names.

✅ Prefer snake_case.

✅ Avoid single-letter variables except in short loops.

---

# Common Mistakes

❌

```python
studentName
```

Better

```python
student_name
```

---

# Mini Exercise

Create variables for:

- Name
- Age
- Country
- Occupation

Print all of them.
