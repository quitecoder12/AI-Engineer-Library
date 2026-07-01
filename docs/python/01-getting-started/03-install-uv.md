# Installing uv

> Modern Python package and project manager

---

# Learning Objectives

After completing this chapter you will be able to:

- Understand what uv is
- Install uv
- Create virtual environments
- Install packages
- Run Python programs
- Replace pip with uv

---

# What is uv?

uv is a modern Python package manager developed by Astral.

It is designed to replace tools like:

- pip
- virtualenv
- pip-tools
- pyenv (partially)

It is significantly faster than pip because it is written in Rust.

---

# Why We Use uv

Throughout this library we use **uv** instead of **pip** whenever possible.

Benefits:

- Extremely fast
- Modern dependency resolution
- Built-in virtual environments
- Better project management
- Cross-platform

---

# Installation

## Windows

Open PowerShell

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

---

## macOS / Linux

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

---

# Verify Installation

```bash
uv --version
```

Example

```
uv 0.8.x
```

---

# Create a Project

```bash
mkdir myproject

cd myproject
```

---

# Create Virtual Environment

```bash
uv venv
```

Result

```
.venv/
```

---

# Activate

Windows

```bash
.venv\Scripts\activate
```

Linux/macOS

```bash
source .venv/bin/activate
```

---

# Install Packages

```bash
uv add pandas
```

```bash
uv add numpy
```

```bash
uv add openai
```

Install multiple packages

```bash
uv add pandas numpy matplotlib
```

---

# Remove Package

```bash
uv remove pandas
```

---

# Upgrade Package

```bash
uv add pandas --upgrade
```

---

# Run Python

```bash
uv run app.py
```

---

# Install Requirements

```bash
uv pip install -r requirements.txt
```

---

# Best Practices

✔ One virtual environment per project

✔ Keep dependencies updated

✔ Commit `uv.lock`

✔ Ignore `.venv`

---

# Common Mistakes

❌ Installing packages globally

❌ Forgetting to activate the environment

❌ Mixing pip and uv unnecessarily

---

# Summary

uv is the preferred package manager for this handbook because it simplifies environment management and dependency installation while being significantly faster than traditional tooling.
