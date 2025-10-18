# 🚀 LangChain + RAG (Retrieval-Augmented Generation)

## 🔹 What is RAG?
RAG combines **retrieval** (from a knowledge base/vector DB) with **generation** (using an LLM).  
It helps LLMs answer queries using **external knowledge**, instead of relying only on their training data.

---

## 🔹 LangChain + RAG Workflow

### 1️⃣ Data Ingestion
- Load documents (PDFs, CSVs, text, etc.)  
- Split into smaller chunks using `RecursiveCharacterTextSplitter` or similar  

### 2️⃣ Embedding & Storage
- Convert text chunks into **vector embeddings** (OpenAI, Hugging Face, or custom models)  
- Store in a **Vector Database** (FAISS, Pinecone, Weaviate, etc.)  

#### Index Types
| Index Type | Description | Use Case |
|------------|-------------|----------|
| **Flat**   | Linear scan of all vectors | Small datasets, exact search |
| **HNSW**   | Hierarchical Navigable Small World graph | Fast approximate search for large datasets |
| **IVF**    | Inverted File + clustering | Approximate search, huge datasets |

#### VectorDB Example
```python
from vectordb import VectorDB
from embeddings import OpenAIEmbeddings

# Initialize embeddings
embed_model = OpenAIEmbeddings(model="text-embedding-3-large")

# Create vector DB
db = VectorDB(
    embedding_model=embed_model,
    index_type="HNSW",
    dimension=1536,
    id_key="doc_id"
)

# Add vectors
db.add(data=[{"doc_id": 1, "text": "Sample document"}])
```

## 🔹 Visuals

### 1. High-Level LangChain + RAG Flow
![LangChain + RAG Architecture](LLM+RAG.png)

---

### 2. Basic RAG Pipeline
![RAG Pipeline](RAGPipeline.png)

---

## 🔹 Why LangChain + RAG?
- ✅ Overcomes LLM hallucination  
- ✅ Allows **domain-specific knowledge** injection  
- ✅ Scales with custom/private datasets  
- ✅ Provides explainability (retrieved sources)

---
