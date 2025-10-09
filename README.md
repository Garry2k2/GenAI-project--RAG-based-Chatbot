# 🤖 RAG-based Chatbot (LangChain + HF + FAISS)

[![Made with Python](https://img.shields.io/badge/Made%20with-Python-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/Powered%20by-LangChain-1C3C3C)](https://python.langchain.com)
[![HF Models](https://img.shields.io/badge/Models-Hugging%20Face-F9A03C?logo=huggingface&logoColor=white)](https://huggingface.co/models)
[![FAISS](https://img.shields.io/badge/Vector%20DB-FAISS-009688)](https://github.com/facebookresearch/faiss)
[![Gradio](https://img.shields.io/badge/UI-Gradio-00B4AB)](https://gradio.app)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Production-ready Retrieval-Augmented Generation (RAG) chatbot that answers questions grounded in your documents using LangChain, sentence-transformer embeddings, FAISS vector search, and open-source Hugging Face models. Runs locally and in Google Colab with a simple Gradio UI—no paid APIs required.

---

## Overview
- Ingest PDFs into chunks, embed with MiniLM, store/retrieve via FAISS
- Generate grounded answers with attributions using an open LLM (e.g., FLAN-T5 or Llama-family)
- Works offline (local) or in Colab; customizable pipeline and components

<p align="center">
  <img alt="RAG pipeline" src="docs/diagram/rag-pipeline.png" width="640" />
</p>

---

## Features
- Document loaders for PDF; easy to extend to DOCX/HTML/URLs
- Robust text chunking with overlap to preserve context
- Sentence-Transformer embeddings: all-MiniLM-L6-v2 (lightweight, fast)
- FAISS IndexFlatIP for efficient similarity search
- LangChain RetrievalQA chain with source citations
- Gradio chat UI + CLI mode
- Deterministic, fully open-source stack

---

## Datasets / Sources
This demo ships with an example: data/NLP_with_Transformers.pdf. Replace or add your own PDFs under data/ and re-run indexing.

- Example source: NLP with Transformers (O’Reilly) excerpt used for demonstration only
- Bring-your-own data: place PDFs into data/ and rebuild the index

---

## Project Structure
```
.
├── data/
│   └── NLP_with_Transformers.pdf        # Example document
├── notebooks/
│   └── colab_rag_demo.ipynb             # Optional Colab notebook
├── scripts/
│   ├── ingest.py                        # Build/refresh FAISS index from PDFs
│   ├── qa_chat.py                       # CLI chatbot
│   └── ui.py                            # Gradio web UI
├── docs/
│   └── diagram/rag-pipeline.png         # Architecture diagram
├── requirements.txt                     # Python dependencies
├── README.md                            # You are here
└── .gitignore
```

---

## Environment and Requirements
- Python 3.9+
- pip or uv/poetry
- CPU-only works; GPU speeds up embedding/LLM inference

Install dependencies:
```
python -m venv .venv && source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

requirements.txt (referenced):
- langchain, sentence-transformers, faiss-cpu, transformers, accelerate, gradio, pypdf, python-dotenv

---

## Installation
Clone and set up:
```
git clone https://github.com/Garry2k2/GenAI-project--RAG-based-Chatbot.git
cd GenAI-project--RAG-based-Chatbot
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
```

---

## Indexing Your Documents
Place PDFs in data/ then build the index:
```
python scripts/ingest.py --data_dir data --index_dir .cache/index
```
Options:
- --chunk_size 800 --chunk_overlap 120
- --model all-MiniLM-L6-v2

---

## Run the Chatbot
CLI mode:
```
python scripts/qa_chat.py --index_dir .cache/index
```
Gradio UI:
```
python scripts/ui.py --index_dir .cache/index --host 0.0.0.0 --port 7860
```
Colab: open notebooks/colab_rag_demo.ipynb and run all cells.

---

## Usage Examples
Query:
```
What is the role of transformers in NLP?
```
Answer (example):
```
Transformers enable sequence-to-sequence learning with attention, capturing long-range dependencies efficiently.
[Source: NLP_with_Transformers.pdf]
```

---

## Configuration
- Model: set via env or flags (e.g., HF model id for generator)
- Embeddings: sentence-transformers/all-MiniLM-L6-v2
- Top-k retrieval, similarity threshold, and max tokens are configurable
- .env supported for optional keys (e.g., HF token) but not required

---

## Contributing
Contributions welcome! Please:
- Open an issue describing change
- Use feature branches and descriptive PRs
- Run lint/format and basic tests before submitting

---

## License
This repository is licensed under the MIT License. See LICENSE for details.

---

## References
- LangChain docs: https://python.langchain.com
- Sentence-Transformers: https://www.sbert.net/
- FAISS: https://github.com/facebookresearch/faiss
- Gradio: https://gradio.app
- Transformers: https://huggingface.co/docs/transformers

---

## Credits
- Author: Garry2k2
- Thanks to the open-source community for components used in this stack

---

## Call to Action
- Star the repo if this helped you
- Open issues for ideas/bugs
- Share improvements via PRs
