# How Caching is Done in Python (RAG)

## 1️⃣ Response Caching (Simple Dictionary / Redis)
Basic Example
```python
cache = {}
def get_response(query):
    if query in cache:
        return cache[query]

    response = llm.invoke(query)
    cache[query] = response
    return response
```
👉 Used for repeated identical queries.

## 2️⃣ Embedding Caching
Avoid recomputing embeddings.
```python
embedding_cache = {}

def get_embedding(text):
    if text in embedding_cache:
        return embedding_cache[text]

    vector = embedding_model.embed(text)
    embedding_cache[text] = vector
    return vector
```

## 3️⃣ Retrieval Caching
Cache retrieved documents.
```python
retrieval_cache = {}

def retrieve(query):
    if query in retrieval_cache:
        return retrieval_cache[query]

    docs = retriever.get_relevant_documents(query)
    retrieval_cache[query] = docs
    return docs
```
## 4️⃣ Using Redis (Production Style)
Instead of Python dict, use Redis:

```python
import redis
r = redis.Redis()

cached = r.get(query)
if cached:
    return cached

response = llm.invoke(query)
r.set(query, response)
```

## 5️⃣ Semantic Caching (Advanced)
- Compute embedding of query
- Compare with cached embeddings
- If similarity > threshold → reuse response

### Where caching fits in RAG
User Query
 → Embedding cache
 → Retrieval cache
 → LLM response cache

## One-liner
In production RAG, we cache embeddings, retrieval results, and LLM responses using Redis or in-memory stores to reduce cost and latency.