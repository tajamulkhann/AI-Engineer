## Document Loading & Text Splitting

```python
# Load PDF or Text files
from langchain_community.document_loaders import TextLoader, PyPDFLoader

loader = PyPDFLoader('syllabus.pdf')
docs = loader.load()
print(f"Number of pages loaded: {len(docs)}")  # e.g., 34

# Recursive Character Text Splitter
from langchain_text_splitters import RecursiveCharacterTextSplitter

recursive_splitter = RecursiveCharacterTextSplitter(
    chunk_size=1000, chunk_overlap=200
)
recursive_docs = recursive_splitter.split_documents(docs)
print(f"Chunks after recursive split: {len(recursive_docs)}")  # e.g., 53

# Character Text Splitter (simpler, splits by separator)
from langchain_text_splitters import CharacterTextSplitter

char_splitter = CharacterTextSplitter(
    separator="\n", chunk_size=1000, chunk_overlap=200
)
char_docs = char_splitter.split_documents(docs)
print(f"Chunks after character split: {len(char_docs)}")
# By default, splits by '\n\n'
```

### Notes

- Recursive Character Text Splitter: It splits text hierarchically. First, it tries to split by paragraphs. If a paragraph is too long, it splits by sentences. If a sentence is still too long, it splits by words. It preserves whole words and avoids cutting text mid-word.

- Regular Text Splitter (like CharacterTextSplitter): It splits text purely based on character count, ignoring paragraphs, sentences, or word boundaries. This can result in cutting a word in half.

Use recursive splitter for better chunking of complex or structured documents.

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/7283af28-4ba3-46d5-913c-8d1c42f29465" />



