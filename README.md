# Acme Corp Internal RAG Knowledge Agent

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DuhranDuhran/enterprise-rag-agent/blob/main/RAG_Agent.ipynb)

An enterprise-grade Retrieval-Augmented Generation (RAG) agent designed to simulate an internal corporate knowledge assistant. The system parses internal policy documentation, generates high-dimensional vector embeddings, indexes content in ChromaDB, and delivers strictly grounded answers with anti-hallucination guardrails.

---

## 🏗 System Architecture

1. **Document Ingestion & Metadata Tagging**: Parses synthetic enterprise files (`hr_policy.txt`, `it_sop.txt`) into structural section chunks and tags each with metadata attributes (`department`, `source`).
2. **Vector Embedding**: Generates vector representations of document chunks using Gemini embeddings (`gemini-embedding-001`).
3. **Vector Database Storage**: Stores and indexes embeddings inside an in-memory **ChromaDB** collection for real-time similarity retrieval.
4. **Semantic Search**: Executes vector similarity searches against user queries to retrieve top-$k$ relevant context blocks.
5. **Strict Grounding Guardrails**: Integrates custom system instructions with `gemini-2.5-flash` to enforce zero outside knowledge usage and standardize fallback messaging when context is missing.

---

## 📋 Test Scenarios & Grounding Verification

| Scenario | User Query | Source File | Expected Agent Behavior |
| :--- | :--- | :--- | :--- |
| **HR Policy Query** | *"How many PTO days can I accrue and what's the rollover policy?"* | `hr_policy.txt` | Retrieves PTO policy section & returns structured accrual breakdown. |
| **IT Support Query** | *"What should I do if I suspect a phishing email or a security incident?"* | `it_sop.txt` | Retrieves IT SOP & provides step-by-step reporting instructions. |
| **Out-of-Context Check** | *"What is the capital of France?"* | N/A | Enforces strict grounding and returns fallback: *"I cannot provide an answer based on the provided context."* |

---

## 🚀 Environment Setup & Execution

1. Open the notebook using the **Open in Colab** badge above.
2. Configure your API key in Google Colab Secrets:
   * Click the **Key Icon (🔑 Secrets)** in the left sidebar.
   * Add Name: `Gemini_API_Key1`
   * Add Value: `[Your Gemini API Key]`
   * Toggle **Notebook access** to **ON**.
3. Execute all cells sequentially (**Runtime > Run all**).

---

## 🧰 Tech Stack

* **Language**: Python 3.10+
* **LLM**: `gemini-2.5-flash`
* **Embeddings**: `models/gemini-embedding-001`
* **Vector Store**: ChromaDB
* **SDK**: `google-generativeai` / `google-genai`
* **Environment**: Google Colab
