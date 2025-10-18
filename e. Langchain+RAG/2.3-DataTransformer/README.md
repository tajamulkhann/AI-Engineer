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

- RecursiveCharacterTextSplitter: Splits text recursively using multiple separators (\n\n, \n, space, etc.) to create more balanced chunks.

- CharacterTextSplitter: Splits text only by a single separator (like \n) without recursive fallback.

Use recursive splitter for better chunking of complex or structured documents.
