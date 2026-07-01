# List Comprehensions in AI Engineering

> **List comprehensions are one of the most frequently used Python features in AI, Machine Learning, Data Science, and LLM applications.**

---

# Learning Objectives

After completing this chapter, you will be able to:

- Recognize list comprehensions in production AI code
- Understand common AI patterns
- Write cleaner AI pipelines
- Process LLM responses
- Work with embeddings
- Transform datasets efficiently
- Prepare data for Machine Learning
- Understand when NOT to use comprehensions

---

# Introduction

If you browse the source code of:

- OpenAI SDK
- LangChain
- LlamaIndex
- Hugging Face
- FastAPI
- Streamlit
- Pandas examples

you'll quickly notice one thing...

List comprehensions are everywhere.

They make code:

- shorter
- cleaner
- easier to review
- easier to maintain

---

# Example 1
## Extracting User Messages

Imagine an OpenAI conversation.

```python
messages = [
    {
        "role": "system",
        "content": "You are a helpful AI."
    },
    {
        "role": "user",
        "content": "Explain RAG."
    },
    {
        "role": "assistant",
        "content": "RAG stands for..."
    },
    {
        "role": "user",
        "content": "Explain Vector Databases."
    }
]
```

Extract only user messages.

Traditional

```python
user_messages = []

for message in messages:

    if message["role"] == "user":

        user_messages.append(
            message["content"]
        )
```

Pythonic

```python
user_messages = [
    message["content"]
    for message in messages
    if message["role"] == "user"
]
```

Result

```python
[
    "Explain RAG.",
    "Explain Vector Databases."
]
```

---

# Example 2
## Extracting Assistant Responses

```python
assistant_answers = [
    message["content"]
    for message in messages
    if message["role"] == "assistant"
]
```

Very common.

---

# Example 3
## Embedding Dimensions

Suppose

```python
embeddings = [

    [0.21,0.18,0.11],

    [0.91,0.22,0.41],

    [0.73,0.52,0.61]

]
```

Find the length of every embedding.

```python
dimensions = [
    len(vector)
    for vector in embeddings
]
```

Result

```python
[
3,
3,
3
]
```

---

# Example 4
## Chunk Sizes

```python
chunks = [

"Introduction...",

"Python Basics...",

"Vector Databases..."

]
```

```python
sizes = [
    len(chunk)
    for chunk in chunks
]
```

Useful before creating embeddings.

---

# Example 5
## Remove Empty Chunks

```python
chunks = [

"Python",

"",

"AI",

"",

"LLMs"

]
```

```python
clean_chunks = [
    chunk
    for chunk in chunks
    if chunk
]
```

Result

```python
[
"Python",

"AI",

"LLMs"
]
```

---

# Example 6
## Extract Metadata

```python
documents = [

{
"title":"Python",
"pages":400
},

{
"title":"AI",
"pages":520
}

]
```

```python
titles = [
    document["title"]
    for document in documents
]
```

Result

```python
[
"Python",

"AI"
]
```

---

# Example 7
## LangChain Documents

LangChain documents look like

```python
document.page_content

document.metadata
```

Extract text.

```python
texts = [
    document.page_content
    for document in documents
]
```

---

Extract source.

```python
sources = [
    document.metadata["source"]
    for document in documents
]
```

---

# Example 8
## Hugging Face Predictions

Suppose

```python
predictions = [

{
"label":"POSITIVE",
"score":0.98
},

{
"label":"NEGATIVE",
"score":0.11
}

]
```

Extract labels.

```python
labels = [
    prediction["label"]
    for prediction in predictions
]
```

---

High confidence predictions.

```python
trusted = [
    prediction
    for prediction in predictions
    if prediction["score"] > 0.90
]
```

---

# Example 9
## Chat History

```python
history = [

{
"role":"user",
"content":"Hello"
},

{
"role":"assistant",
"content":"Hi!"
}

]
```

Conversation

```python
conversation = [
    message["content"]
    for message in history
]
```

---

# Example 10
## Building Prompt Lists

```python
topics = [

"Python",

"RAG",

"Prompt Engineering"

]
```

```python
prompts = [

f"Explain {topic}"

for topic in topics

]
```

Result

```python
[
"Explain Python",

"Explain RAG",

"Explain Prompt Engineering"
]
```

---

# Example 11
## Prompt Variations

```python
styles = [

"Simple",

"Advanced",

"Interview"

]

topics = [

"Python",

"AI"

]
```

```python
prompts = [

f"{style}: {topic}"

for style in styles

for topic in topics

]
```

---

# Example 12
## Extract File Names

```python
files = [

"python.pdf",

"rag.pdf",

"notes.txt"

]
```

Only PDF

```python
pdfs = [

file

for file in files

if file.endswith(".pdf")

]
```

---

# Example 13
## Confidence Labels

```python
scores = [

0.92,

0.44,

0.81,

0.12

]
```

```python
labels = [

"Trusted"

if score >= 0.90

else "Review"

for score in scores

]
```

---

# Example 14
## Token Lengths

```python
sentences = [

"Python",

"Artificial Intelligence",

"RAG"

]
```

```python
lengths = [

len(sentence.split())

for sentence in sentences

]
```

---

# Example 15
## Lowercase Vocabulary

```python
words = [

"Python",

"AI",

"Machine",

"Learning"

]
```

```python
vocabulary = [

word.lower()

for word in words

]
```

Useful before tokenization.

---

# Example 16
## Remove Stop Words

```python
stop_words = {

"a",

"an",

"the",

"is"

}

tokens = [

"this",

"is",

"python",

"the",

"future"

]
```

```python
filtered = [

token

for token in tokens

if token not in stop_words

]
```

Result

```python
[
"this",

"python",

"future"
]
```

---

# Example 17
## Batch Processing

Split documents into batches.

```python
batch_size = 100

batches = [

documents[i:i+batch_size]

for i in range(
    0,
    len(documents),
    batch_size
)

]
```

This pattern appears frequently in:

- OpenAI APIs
- Embedding APIs
- Database inserts

---

# Example 18
## FastAPI Response

Suppose

```python
users = [

User(...),

User(...),

User(...)

]
```

Return names.

```python
return [

user.name

for user in users

]
```

---

# Example 19
## Feature Engineering

```python
ages = [

18,

25,

41,

63

]
```

Normalize

```python
normalized = [

age / 100

for age in ages

]
```

---

# Example 20
## Building a RAG Pipeline

Documents

↓

Chunks

↓

Embeddings

↓

Store

```python
embeddings = [

embedding_model.embed(chunk)

for chunk in chunks

]
```

One of the most common AI patterns.

---

# Common AI Patterns

| Task | Comprehension |
|--------|---------------|
| Extract metadata | ✅ |
| Build prompts | ✅ |
| Remove duplicates | ✅ |
| Filter documents | ✅ |
| Build embeddings | ✅ |
| Extract labels | ✅ |
| Batch processing | ✅ |
| Dataset cleaning | ✅ |

---

# When NOT to Use Comprehensions

Avoid

```python
results = [

very_complicated_function(

a,

b,

c,

d,

e

)

for item in collection

if complicated_condition(item)

]
```

Instead

```python
results = []

for item in collection:

    if complicated_condition(item):

        results.append(

            very_complicated_function(

                item

            )

        )
```

Readable code always wins.

---

# Best Practices

✅ Keep comprehensions short.

✅ Prefer readability.

✅ One responsibility per comprehension.

✅ Use helper functions.

✅ Profile before optimizing.

---

# Interview Questions

1. Why are comprehensions common in AI?
2. Give examples from LLM applications.
3. How are embeddings commonly processed?
4. Explain batching with comprehensions.
5. Difference between filtering and transformation.

---

# Mini Project

Build a simple **Document Preprocessing Pipeline**.

Input

```
Raw Documents
```

Steps

- Remove empty documents
- Trim whitespace
- Convert to lowercase
- Generate prompts
- Calculate chunk sizes
- Group into batches

Try to implement each step using list comprehensions where appropriate.

---

# Summary

List comprehensions are a fundamental part of modern AI Python code.

Whether you're building:

- Chatbots
- RAG Systems
- Agents
- FastAPI APIs
- Data Pipelines
- Embedding Pipelines
- ML Models

you'll use list comprehensions every day.

Learning to read and write them fluently is an essential skill for every AI Engineer.

---

# Next Section

➡ **10-common-mistakes.md**

In the next section, we'll examine the most common mistakes developers make with list comprehensions, why they happen, and how to avoid them.
