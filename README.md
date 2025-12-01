# 🤖 Karl Marx RAG Chatbot: Bilingual Retrieval Agent

**A robust Question-Answering (QA) application designed to provide accurate, source-grounded answers based on the complete English works of Karl Marx (e.g., Das Kapital, Grundrisse).**

---

## 💡 Project Overview & Architecture

This project solves the challenge of creating a highly accurate, domain-specific chatbot that operates seamlessly for a non-English speaking audience (Turkish) while leveraging the stability of the global NLP ecosystem.

The core design utilizes a **Retrieval-Augmented Generation (RAG)** architecture with a critical **bilingual abstraction layer**. 

### Key Components

| Component | Technology | Role |
| :--- | :--- | :--- |
| **Data Source** | English `Das Kapital` (Word/DOCX) | Provides the foundational corpus for grounding. |
| **Embedding Model** | `all-mpnet-base-v2` | Converts textual queries/chunks into dense, high-performance vectors. |
| **Vector Index** | **FAISS (CPU/GPU)** | Enables efficient nearest-neighbor search across millions of vectors. |
| **Translation Layer** | `Helsinki-NLP/opus-mt-en-tr` | Handles real-time conversion between Turkish and English. |
| **Generator (LLM)** | `google/flan-t5-base` / `google/mt5-small` | Generates context-aware, concise English answers. |

### Bilingual RAG Flow

1.  **Turkish Input (User):** User asks a question in Turkish.
2.  **Translate to English:** The query is immediately translated (TR → EN).
3.  **Retrieval (EN Core):** The English query is embedded and matched against the English FAISS index.
4.  **Generation (EN Output):** The English LLM generates an answer based on the retrieved English context.
5.  **Translate to Turkish:** The final English answer is translated back to Turkish.
6.  **Turkish Output (User):** The Turkish answer is presented to the user.

---
