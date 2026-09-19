# Enterprise RAG Knowledge Agent

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DuhranDuhran/enterprise-rag-agent/blob/main/RAG_AgentV1.ipynb)

An internal corporate knowledge assistant that answers employee policy questions using semantic vector search in **ChromaDB** and strict anti-hallucination guardrails powered by **Gemini**.

---

## 🛠 Architecture & Workflow

```text
[ Synthetic Docs (HR/IT) ] ➔ [ Line-Break Chunking ] ➔ [ Gemini Embeddings ]
                                                              │
                                                              ▼
[ User Query ] ➔ [ Semantic Search ] ◄───────────── [ ChromaDB Vector Store ]
       │                │
       ▼                ▼
[ Strict Prompt ] ➔ [ Gemini 3.6 Flash ] ➔ [ Grounded Response ]
