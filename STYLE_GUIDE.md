# Style Guide

## Purpose

This guide ensures every page in the AI Engineer Library has a consistent structure, writing style, and quality.

---

# Page Structure

Every chapter must follow this order:

```text
Title

Learning Objectives

Prerequisites

Overview

Why This Matters

Core Concepts

Syntax

Examples

AI Engineering Examples

PHP Comparison

Best Practices

Common Mistakes

Performance Notes

Interview Questions

Exercises

Mini Project

Summary

Cheat Sheet

Further Reading
```

---

# Writing Principles

## Explain before showing code

Bad

```python
x = 10
```

Good

Explain what a variable is before introducing syntax.

---

## Prefer practical examples

Instead of:

```python
print("Hello")
```

Use:

```python
import pandas as pd

df = pd.read_csv("employees.csv")
```

---

## Code Standards

- Python 3.13+
- Type hints where appropriate
- pathlib instead of os.path
- uv instead of pip where practical
- PEP 8 compliant

---

## Headings

Use sentence case.

Correct:

```
# Variables
```

Avoid:

```
# VARIABLES
```

---

## Notes

Use MkDocs admonitions:

```markdown
!!! note

    Helpful information.
```

```markdown
!!! warning

    Avoid this common mistake.
```

```markdown
!!! tip

    Recommended approach.
```

---

## Diagrams

Use Mermaid whenever a visual explanation improves understanding.

---

## Goal

Every page should be understandable by a beginner while remaining useful to an experienced developer.
