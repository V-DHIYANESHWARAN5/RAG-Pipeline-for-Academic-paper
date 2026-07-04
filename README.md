# 📚 RAG on Academic Papers – Retrieval-Augmented Generation

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

## 🧠 What is RAG?

**Retrieval-Augmented Generation (RAG)** combines a **retriever** (vector search) with a **generator** (LLM) to answer questions grounded in your own private data. Instead of relying solely on the LLM's internal knowledge (which may be outdated or hallucinated), RAG first searches a knowledge base, retrieves relevant documents, and then asks the LLM to answer based *only* on those documents.

This approach is:
- **Fact‑grounded** – reduces hallucinations.
- **Up‑to‑date** – no need to retrain the model.
- **Secure** – your data stays private.

---

## 🚀 Project Overview

This project builds a **RAG pipeline** for a dataset of **academic papers** (AI/ML research 2023–2026). It allows you to:

- Upload a CSV of papers (with metadata like title, authors, citations, etc.)
- Convert each paper into a text chunk.
- Generate embeddings using a free, open‑source model (`all-MiniLM-L6-v2`).
- Index the embeddings with **FAISS** for fast similarity search.
- Query the system and retrieve the top‑3 most relevant papers.
- Generate a grounded answer using:
  - **DeepSeek API** (primary, high quality)
  - **Local T5 model** (fallback, free, no API key)

---

## 📂 Dataset Format

The CSV **must** have the following columns (exact names):

| Column | Description |
| :--- | :--- |
| `title` | Paper title |
| `doi` | Digital Object Identifier |
| `publication_date` | Date published (YYYY‑MM‑DD) |
| `cited_by_count` | Number of citations |
| `authors` | Author names |
| `journal` | Journal / conference name |
| `open_access` | `True` or `False` |
| `type` | `preprint`, `article`, `review`, `book`, etc. |
| `topic` | Research topic (e.g., LLMs, RAG, Diffusion Models) |

---

## 🛠️ Setup & Installation

### Option 1: Run in Google Colab (Recommended)
Click the badge above or go to [Colab](https://colab.research.google.com/) and upload the `rag_academic_papers.ipynb` notebook. Run all cells – it will install dependencies automatically.

### Option 2: Run Locally

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/rag-academic-papers.git
   cd rag-academic-papers