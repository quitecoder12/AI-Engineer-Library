# Dictionaries (Part 2)

> Understanding how dictionaries work internally is one of the biggest steps toward becoming an advanced Python programmer.

---

# Recap

A dictionary stores information as:

```
Key  →  Value
```

Example

```python
student = {
    "name": "Ajit",
    "age": 50,
    "city": "Rourkela"
}
```

---

# How Dictionaries Work

Most people think dictionaries search one key after another.

They don't.

Python dictionaries are implemented using a **Hash Table**.

```
                Hash Function

"name"
   │
   ▼
Hash Value
   │
   ▼
Bucket
   │
   ▼
"Ajit"
```

Lookup is extremely fast.

Average complexity

```
O(1)
```

---

# Why Dictionaries are Fast

Imagine searching for

```
"name"
```

inside

```
10 Million Records
```

A list would need to scan items.

Dictionary

↓

Calculate hash

↓

Jump directly

↓

Done

This is why dictionaries are used everywhere.

---

# Valid Keys

Keys must be immutable.

Allowed

```python
{
    "name":"Ajit"
}
```

```python
{
    10:"Ten"
}
```

```python
{
    (1,2):"Point"
}
```

---

Not Allowed

```python
{
    [1,2]:"Hello"
}
```

Produces

```
TypeError

unhashable type: list
```

---

# Why?

Lists can change.

Dictionary keys must never change.

---

# Nested Dictionaries

```python
employee = {

    "id":101,

    "personal":{

        "name":"Ajit",

        "age":50

    },

    "office":{

        "department":"IT",

        "salary":62000

    }

}
```

---

Access

```python
employee["office"]["salary"]
```

Returns

```
62000
```

---

# Dictionary of Lists

Very common.

```python
student = {

    "subjects":[

        "Python",

        "SQL",

        "AI"

    ]

}
```

Access

```python
student["subjects"][1]
```

---

# List of Dictionaries

Even more common.

```python
employees = [

    {
        "name":"Ajit",
        "salary":62000
    },

    {
        "name":"Rahul",
        "salary":45000
    }

]
```

Access

```python
employees[0]["name"]
```

---

This pattern appears everywhere in AI.

---

# Dictionary Methods

## keys()

```python
user.keys()
```

Returns

```
dict_keys(...)
```

---

## values()

```python
user.values()
```

---

## items()

```python
user.items()
```

Returns

```
(key,value)
```

pairs.

---

## update()

```python
user.update({

    "city":"Rourkela"

})
```

---

## pop()

```python
user.pop("age")
```

---

## popitem()

Removes the last inserted key.

```python
user.popitem()
```

---

## clear()

```python
user.clear()
```

---

## copy()

```python
new_user = user.copy()
```

---

# Dictionary Comprehension

Create

```python
squares = {

    x:x*x

    for x in range(5)

}
```

Result

```
{

0:0,

1:1,

2:4,

3:9,

4:16

}
```

---

Filter

```python
even = {

    x:x

    for x in range(10)

    if x%2==0

}
```

---

# Merge Dictionaries

Python 3.9+

```python
a = {"x":1}

b = {"y":2}

c = a | b
```

Result

```python
{

"x":1,

"y":2

}
```

---

Older Method

```python
a.update(b)
```

---

# Shallow Copy

```python
a = {

    "numbers":[1,2]

}

b = a.copy()
```

Now

```python
b["numbers"].append(3)
```

Both dictionaries change.

Why?

Only the outer dictionary was copied.

The list is shared.

---

# Deep Copy

```python
import copy

b = copy.deepcopy(a)
```

Now both are independent.

---

# Dictionary vs JSON

JSON

```json
{
    "name":"Ajit"
}
```

Python

```python
{

"name":"Ajit"

}
```

Almost identical.

---

Convert

```python
import json

text = json.dumps(user)
```

Back

```python
json.loads(text)
```

---

# AI Example

OpenAI Response

```python
response = {

    "id":"abc",

    "model":"gpt-5",

    "usage":{

        "input_tokens":140,

        "output_tokens":380

    }

}
```

Access

```python
response["usage"]["input_tokens"]
```

---

# FastAPI

Request Body

```python
@app.post("/chat")

def chat(request:dict):

    ...
```

---

# Streamlit

```python
st.session_state["username"]
```

Dictionary.

---

# LangChain

Most chains return dictionaries.

```python
{

"answer":"...",

"sources":[...]

}
```

---

# Performance Table

| Operation | Complexity |
|------------|------------|
| Lookup | O(1) |
| Insert | O(1) |
| Delete | O(1) |
| Iterate | O(n) |

---

# Common Mistakes

## KeyError

```python
user["salary"]
```

If missing

↓

KeyError

Better

```python
user.get("salary")
```

---

## Mutable Keys

Never use

```python
{

[]:"Hello"

}
```

---

## Assuming Order

Modern Python preserves insertion order.

Older versions did not.

---

# Debugging Tips

Pretty Print

```python
from pprint import pprint

pprint(user)
```

Much easier to read.

---

# PHP Comparison

PHP

```php
$user["name"];
```

Python

```python
user["name"]
```

---

PHP

```php
isset($user["salary"]);
```

Python

```python
"salary" in user
```

or

```python
user.get("salary")
```

---

# Interview Questions

1. Explain hash tables.

2. Why are dictionaries fast?

3. Difference between get() and [].

4. Explain shallow copy.

5. Explain deep copy.

6. Why can't lists be keys?

7. Difference between dictionary and JSON.

8. Explain dictionary comprehension.

9. Time complexity of lookup.

10. Difference between update() and merge operator.

---

# Exercises

## Easy

Create

```python
book = {

"title":"Python",

"pages":500

}
```

Print title.

---

## Medium

Count word frequency.

Hint

Use dictionary.

---

## Advanced

Read a text file.

Count every word.

Sort by frequency.

Display top 20 words.

---

# AI Project

Create a Prompt Manager.

Each prompt should contain

```python
{

"id":1,

"name":"Summarizer",

"prompt":"...",

"temperature":0.3,

"model":"gpt-5"

}
```

Store multiple prompts inside a dictionary.

Implement

- Add
- Update
- Delete
- Search
- List

---

# Summary

If Lists are the heart of Python,

Dictionaries are the brain.

Nearly every AI framework uses dictionaries as its primary data structure.

Master dictionaries before moving to APIs, JSON, FastAPI, LangChain, or RAG.

This is one of the most important chapters in the entire handbook.
