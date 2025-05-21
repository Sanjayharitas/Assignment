# Final Assignment - Security Threat Explanation Assistant

is an AI-powered assistant that helps users understand software vulnerabilities (CVEs) using simple language. It combines:

🧠 Semantic search via Sentence Transformers + FAISS

🤖 Large Language Model (LLM) via OpenRouter (e.g., GPT-4o-mini)

🖼️ Gradio web interface for easy interaction

Users can ask natural questions about potential threats (e.g., “Is CVE-2024-5678 a problem for my Windows server?”), and the system provides an explanation, relevant risks, and actionable advice.

# Installation
 - Clone the repository
 - Install dependencies (The first cell)
 - Set your OpenRouter API key
 - Run the rest of the cell and you are ready to go!

# Architecture
```
                            ┌────────────────────────────┐
                            │  Load CVE dataset          │
                            │                            │
                            └────────────┬───────────────┘
                                         │
                      ┌──────────────────▼──────────────────┐
                      │ Embed descriptions using            │
                      │ SentenceTransformer                 │
                      └──────────────────┬──────────────────┘
                                         │
                               ┌─────────▼──────────┐
                               │   FAISS Index      │
                               └─────────┬──────────┘
                                         │
                                         ▼
                          ┌────────────────────────────┐
                          │  Embed user query          │
                          │  using SentenceTransformer │
                          └──────────┬─────────────────┘
                                     │
                          ┌──────────▼────────────┐
                          │ Search for top-k CVEs │
                          └──────────┬────────────┘
                                     │
                         ┌───────────▼────────────┐
                         │ Generate context-rich  │
                         │ LLM prompt             │
                         └───────────┬────────────┘
                                     │
                         ┌───────────▼─────────────┐
                         │ Query OpenRouter LLM    │
                         └───────────┬─────────────┘
                                     │
                         ┌───────────▼─────────────┐
                         │ Generate response and   │
                         │ related CVE links       │
                         └───────────┬─────────────┘
                                     │
                         ┌───────────▼────────────┐
                         │      Gradio UI         │
                         │ Shows explanation +    │
                         │ links to references    │
                         └────────────────────────┘

User enters query + optional context → Embed query → Search top-k → LLM → Gradio UI.
```


# Sample Input/Output
Input - CVE + Context(Optional)

# Colab- 
https://colab.research.google.com/drive/11Jfk_4g_R67usUIQWoKJpiwkE3awQYbV?usp=sharing


![FinalProject](https://github.com/user-attachments/assets/131081b6-6896-4679-b1f8-ed517b16219c)




