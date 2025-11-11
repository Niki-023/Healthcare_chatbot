<div align="center">

# 🩺 Healthcare Chatbot  
**RAG-based Clinical Reference Assistant**

*A context-aware AI chatbot that answers medical questions using real documents instead of guessing.*

</div>

---

## 🧠 Overview

**Healthcare Chatbot** is an intelligent **Retrieval-Augmented Generation (RAG)** system that provides accurate, reference-based answers to medical queries.  
It uses **FAISS vector search** to retrieve relevant information from a **local medical knowledge base (PDFs)** and generates responses with **LLMs** (Groq-hosted or HuggingFace models).

Unlike traditional chatbots, it avoids hallucinations by grounding every answer in real medical sources.

---

## ✨ Key Highlights

- 🧩 **Retrieval-Augmented Generation (RAG)** pipeline for factual responses  
- ⚡ **FAISS** for fast and efficient vector similarity search  
- 🧠 **SentenceTransformer embeddings** (`all-MiniLM-L6-v2`) for text understanding  
- 🤖 Supports **Groq** and **HuggingFace** language models  
- 📘 **Source traceability** — every answer shows which document it came from  
- 💬 Web chat UI built with **Streamlit** + Command-line mode for testing  

---

## 🏗️ System Architecture

```
PDF(s) --> Text Splitter --> Embeddings --> FAISS Index (vectorstore/db_faiss)
								│
User Query --> Retriever (top-k) ---------------┘
			    │
		    Prompt Assembly
			    │
		    LLM Generation (HF or Groq)
			    │
		    Answer + Source Chunks
```

### Main Components
| File | Role |
|------|------|
| `create_memory_for_llm.py` | Builds FAISS index from PDFs (embedding + persist) |
| `connect_memory_with_llm.py` | CLI RAG query using HuggingFaceEndpoint |
| `medibot.py` | Streamlit chat interface using Groq Chat model + FAISS retrieval |
| `vectorstore/db_faiss` | Persisted FAISS index (created beforehand) |
| `data/` | PDF source documents |



---

## 📁 Project Structure

| File / Folder | Description |
|----------------|--------------|
| `create_memory_for_llm.py` | Builds FAISS index from PDFs |
| `connect_memory_with_llm.py` | Command-line chatbot using HuggingFace model |
| `medibot.py` | Streamlit web chat interface using Groq LLM |
| `vectorstore/db_faiss` | Stored FAISS vector database |
| `data/` | PDF source files (medical references) |

---

## ⚖️ Disclaimer
This tool is for educational and reference purposes only. It does **not** provide medical advice, diagnosis, or treatment recommendations. Always consult a licensed healthcare professional for medical decisions.


