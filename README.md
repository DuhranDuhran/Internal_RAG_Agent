# Internal RAG Knowledge Agent

An enterprise-grade Retrieval-Augmented Generation (RAG) assistant that grounds AI responses directly on internal company policies (HR & IT SOPs) using **ChromaDB** for vector retrieval and **Gemini 3.6 Flash** with strict anti-hallucination guardrails.

---

## 🛠 Repository Overview

This repository demonstrates how to build an end-to-end internal knowledge assistant using Python, vector databases, and modern Gemini embeddings. The interactive notebook runs directly in Google Colab using `Gemini_API_Key1` stored securely in Colab Secrets.

### Featured Modules & Capabilities

| Module / Scenario | Key Capabilities | Interactive Notebook |
| :--- | :--- | :--- |
| **HR Policy Assistant** | Parses PTO accrual, equipment stipends, and rollover policies from synthetic HR documents. | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DuhranDuhran/Internal_RAG_Agent/blob/main/RAG_Agent.ipynb) |
| **IT Support SOPs** | Extracts security protocols, VPN rules, PhishAlarm reporting steps, and Slack incident handles. | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DuhranDuhran/Internal_RAG_Agent/blob/main/RAG_Agent.ipynb) |
| **Strict Guardrails & Fallbacks** | Restricts model answers strictly to retrieved context, automatically triggering safe fallbacks for out-of-context queries. | [Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DuhranDuhran/Internal_RAG_Agent/blob/main/RAG_Agent.ipynb) |

---

## 🚀 Key Architectural Patterns

1. **Document Ingestion & Metadata Tagging:** Parses multi-department text files (`hr_policy.txt`, `it_sop.txt`), splits text by section breaks (`\n\n`), and tags chunks with department and source metadata.
2. **Vector Indexing & Semantic Search:** Generates dense vector representations using `models/gemini-embedding-001` and indexes them in **ChromaDB** for fast distance-based similarity lookups.
3. **Grounded Generation & Guardrails:** Passes top retrieved context blocks ($k=2$) to `gemini-3.6-flash` wrapped in strict system instructions to refuse queries missing from internal context.

---

## 💻 Environment & Setup

1. Open `RAG_AgentV1.ipynb` in Google Colab using the **Open in Colab** badges above.
2. Store your API key in Google Colab:
   * Click the **Key Icon (🔑 Secrets)** in the left sidebar.
   * Add Name: `Gemini_API_Key1`
   * Add Value: `[Your Google AI Studio API Key]`
   * Toggle **Notebook access** to **ON**.
3. Run the notebook cells sequentially (`Ctrl + F9`).

---

## 🧰 Tech Stack

* **Language:** Python 3.10+
* **SDK:** `google-generativeai` / `google-genai`
* **Model:** `gemini-3.6-flash`
* **Embedding Model:** `models/gemini-embedding-001`
* **Vector Store:** ChromaDB
* **Environment:** Google Colab
