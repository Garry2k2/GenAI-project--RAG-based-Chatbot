```markdown
# 📚 RAG-based Chatbot (Colab + Hugging Face + FAISS)

This project implements a **Retrieval-Augmented Generation (RAG) chatbot** using **LangChain, Hugging Face models, FAISS, and Google Colab** — **completely free** (no OpenAI API key required).

The chatbot answers questions based on the document:
```

data/NLP_with_Transformers.pdf

```

This PDF was used to demonstrate the chatbot's ability to ingest, index, and answer questions from a single reference source.

---

## 🚀 Features
- Document ingestion (PDFs in this case) using LangChain loaders  
- Chunking & semantic embeddings using **MiniLM (sentence-transformers)**  
- Vector database using **FAISS** (fully local, free)  
- LLM-based answer generation using **Flan-T5** (Hugging Face)  
- Incremental ingestion: add new PDFs without rebuilding everything  
- Simple **Gradio UI** for chat interface  
- Works entirely in **Google Colab**  

---

## 🛠️ Tech Stack
- **LangChain** (document loading, RAG pipeline)  
- **Sentence-Transformers** (`all-MiniLM-L6-v2`) for embeddings  
- **FAISS** for vector similarity search  
- **Hugging Face Transformers** (`flan-t5-base`) for answer generation  
- **Gradio** for chatbot UI  
- **Google Colab** runtime  

---

## 📂 Project Structure
```

rag-chatbot/
│── data/
│   └── NLP_with_Transformers.pdf   # Knowledge source
│
│── notebooks/
│   └── colab_rag_demo.ipynb        # Main Colab notebook
│
│── src/
│   ├── ingest.py                   # Build FAISS index from PDF
│   ├── qa_chat.py                  # CLI-based chatbot
│   ├── ui.py                       # Gradio UI for chatbot
│
│── requirements.txt                # Dependencies
│── README.md                       # Project description
│── .gitignore                      # Ignore unnecessary files

````

---

## ⚡ Quick Start (Colab)

1. Clone the repo:
```bash
git clone https://github.com/<your-username>/rag-chatbot.git
cd rag-chatbot
````

2. Open `notebooks/colab_rag_demo.ipynb` in **Google Colab**.

3. Ensure your `data/` folder contains the PDF (`NLP_with_Transformers.pdf`).

4. Run all cells → chatbot will be ready in Colab with a Gradio link.

---

## 🧪 Example Usage

**Query:**

```
What is the role of transformers in NLP?
```

**Output:**

```
Transformers enable sequence-to-sequence learning with attention mechanisms, allowing efficient handling of long-range dependencies in NLP tasks.
(Source: NLP_with_Transformers.pdf)
```


## 🔮 Future Improvements

* Extend ingestion to multiple PDFs or DOCX files
* Experiment with larger LLMs (Falcon, Llama 2)
* Deploy outside Colab with Streamlit or FastAPI

---
