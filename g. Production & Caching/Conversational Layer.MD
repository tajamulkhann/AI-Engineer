# Conversational Layer in RAG

To maintain conversation in a RAG chatbot, you:
- Store chat history
- Rewrite follow-up questions into standalone queries
- Retrieve context using the rewritten query
- Pass recent history + retrieved context to the LLM

```python
chat_history = []

def rewrite_query(user_input, chat_history):
    prompt = f"""
    Given the conversation:
    {chat_history}
    Rewrite the user question into a standalone query:
    {user_input}
    """
    return llm.invoke(prompt)

def rag_chat(user_input):
    # 1️⃣ Rewrite query for better retrieval
    standalone_query = rewrite_query(user_input, chat_history)

    # 2️⃣ Retrieve relevant documents
    docs = retriever.get_relevant_documents(standalone_query)

    # 3️⃣ Build final prompt
    final_prompt = f"""
    Conversation:
    {chat_history}

    Context:
    {docs}

    Question:
    {user_input}
    """

    response = llm.invoke(final_prompt)

    # 4️⃣ Update memory
    chat_history.append({"role": "user", "content": user_input})
    chat_history.append({"role": "assistant", "content": response})

    return response
```

## Key Idea
Always rewrite follow-up questions before retrieval and limit chat history to avoid token explosion.

## Interview One-Liner
In conversational RAG, we maintain chat memory, rewrite follow-up queries, and pass summarized history with retrieved context to the LLM.