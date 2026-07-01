# Mini Project - AI Document Processing Pipeline

> **In this project, you'll build a simplified version of the preprocessing pipeline used in Retrieval-Augmented Generation (RAG) systems.**

---

# Project Overview

Congratulations!

You have learned:

- Basic List Comprehensions
- Filtering
- Conditional Expressions
- Nested Comprehensions
- Multiple Loops
- Performance
- Memory Considerations

Now it's time to use everything together.

---

# Project Goal

Given a collection of raw documents,

build a preprocessing pipeline that:

- Removes empty documents
- Cleans whitespace
- Converts text to lowercase
- Removes duplicate documents
- Filters small documents
- Creates metadata
- Generates prompts
- Splits into batches
- Produces statistics

Exactly this kind of processing happens before embeddings are generated in modern AI systems.

---

# Project Architecture

```
                Raw Documents
                      │
                      ▼
          Remove Empty Documents
                      │
                      ▼
              Trim Whitespace
                      │
                      ▼
             Convert to Lowercase
                      │
                      ▼
            Remove Duplicate Documents
                      │
                      ▼
          Filter Very Small Documents
                      │
                      ▼
            Generate Metadata
                      │
                      ▼
              Create AI Prompts
                      │
                      ▼
             Split into Batches
                      │
                      ▼
              Ready for Embeddings
```

---

# Input Dataset

```python
documents = [

    " Python is amazing. ",

    "",

    "Artificial Intelligence",

    "python is amazing.",

    "Machine Learning",

    None,

    "Large Language Models",

    "AI"

]
```

---

# Expected Output

```
4 Clean Documents

↓

Metadata

↓

Prompts

↓

Batches

↓

Statistics
```

---

# Step 1

## Remove Empty Documents

Ignore

- None
- Empty strings

Solution

```python
documents = [

    document

    for document in documents

    if document

]
```

Result

```python
[
" Python is amazing. ",
"Artificial Intelligence",
"python is amazing.",
"Machine Learning",
"Large Language Models",
"AI"
]
```

---

# Step 2

## Remove Leading and Trailing Spaces

```python
documents = [

    document.strip()

    for document in documents

]
```

Result

```python
[
"Python is amazing.",
"Artificial Intelligence",
"python is amazing.",
...
]
```

---

# Step 3

## Convert Everything to Lowercase

```python
documents = [

    document.lower()

    for document in documents

]
```

Result

```python
[
"python is amazing.",
"artificial intelligence",
...
]
```

---

# Step 4

## Remove Duplicate Documents

One simple approach:

```python
documents = list(
    set(documents)
)
```

> **Note:** `set()` removes duplicates but **does not preserve order**.

### Preserving Order

If preserving the original order is important (which it often is), use:

```python
documents = list(dict.fromkeys(documents))
```

This keeps the first occurrence of each document while removing duplicates.

---

# Step 5

## Remove Very Small Documents

Ignore documents shorter than 10 characters.

```python
documents = [

    document

    for document in documents

    if len(document) >= 10

]
```

---

# Current Result

```
python is amazing.

artificial intelligence

machine learning

large language models
```

---

# Step 6

## Generate Metadata

Create

```python
metadata = [

    {
        "text": document,
        "length": len(document)
    }

    for document in documents

]
```

Result

```python
[
    {
        "text":"python is amazing.",
        "length":18
    },

    ...
]
```

---

# Step 7

## Generate AI Prompts

```python
prompts = [

    f"Summarize the following document:\n\n{document}"

    for document in documents

]
```

Example

```
Summarize the following document:

python is amazing.
```

---

# Step 8

## Create Chunk Statistics

```python
statistics = [

    len(document.split())

    for document in documents

]
```

Result

```python
[
3,
2,
2,
3
]
```

This counts the number of words in each document.

---

# Step 9

## Categorize Documents

```python
categories = [

    "Large"

    if len(document) > 25

    else "Small"

    for document in documents

]
```

Result

```python
[
"Small",

"Large",

"Small",

"Large"
]
```

---

# Step 10

## Split into Batches

Suppose

```python
batch_size = 2
```

```python
batches = [

    documents[i:i+batch_size]

    for i in range(
        0,
        len(documents),
        batch_size
    )

]
```

Result

```python
[
    [
        "python is amazing.",
        "artificial intelligence"
    ],

    [
        "machine learning",
        "large language models"
    ]
]
```

---

# Step 11

## Generate Embedding Jobs

Instead of actually calling an embedding API,

prepare the requests.

```python
jobs = [

    {
        "id": index,
        "text": document
    }

    for index, document in enumerate(documents)
]
```

Result

```python
[
    {
        "id":0,
        "text":"python is amazing."
    },

    ...
]
```

---

# Step 12

## Generate Report

```python
report = {

    "documents": len(documents),

    "total_words": sum(
        len(document.split())
        for document in documents
    ),

    "average_length": sum(
        len(document)
        for document in documents
    ) / len(documents)
}
```

Example

```python
{
    "documents":4,
    "total_words":10,
    "average_length":21.5
}
```

---

# Complete Pipeline

```text
Raw Documents
        │
        ▼
Remove Empty Values
        │
        ▼
Trim Whitespace
        │
        ▼
Lowercase Text
        │
        ▼
Remove Duplicates
        │
        ▼
Filter Small Documents
        │
        ▼
Generate Metadata
        │
        ▼
Generate Prompts
        │
        ▼
Create Batches
        │
        ▼
Embedding Jobs
        │
        ▼
Final Report
```

---

# Real AI Equivalent

| This Project | Real AI System |
|--------------|----------------|
| Raw Documents | PDFs, HTML, Word Files |
| Cleaning | Text Normalization |
| Lowercase | NLP Preprocessing |
| Remove Duplicates | Deduplication |
| Metadata | Document Metadata |
| Prompt Generation | LLM Prompt Construction |
| Batching | API Batch Requests |
| Embedding Jobs | Vector Database Pipeline |

---

# Improvements

Enhance the pipeline by adding:

- Language detection
- Stop-word removal
- Stemming
- Lemmatization
- Sentence splitting
- Token counting
- Duplicate detection using hashes
- Logging
- Error handling
- Progress bars

---

# Challenge Tasks

## Challenge 1

Sort documents by length.

---

## Challenge 2

Generate unique IDs using `uuid`.

---

## Challenge 3

Extract the first sentence from each document.

---

## Challenge 4

Calculate reading time.

Hint

```
Average reading speed

≈ 200 words/minute
```

---

## Challenge 5

Create a JSON file containing

- Metadata
- Prompts
- Statistics

---

# What You've Practiced

✅ Basic comprehensions

✅ Filtering

✅ Conditional expressions

✅ Dictionary comprehensions

✅ Nested comprehensions

✅ Batching

✅ Data transformation

✅ AI preprocessing

---

# Key Takeaways

This project demonstrates how list comprehensions fit into a real AI workflow.

Although production systems include additional concerns such as validation, logging, retries, and exception handling, the core data transformations are very similar to what you've built here.

As an AI Engineer, you'll use patterns like these regularly when preparing data for:

- Embedding models
- Vector databases
- RAG systems
- Machine learning pipelines
- LLM applications

---

# Next File

➡ **CHEATSHEET.md**

A quick-reference guide containing:

- Complete syntax
- Common patterns
- Performance comparison
- Decision tree
- Do's and Don'ts
- Interview revision
- AI coding patterns
