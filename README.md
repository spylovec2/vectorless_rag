# 🧠 Vectorless RAG

A RAG (Retrieval-Augmented Generation) system built **without any vector database or embeddings** — using **Google Gemini** + **PageIndex** instead.


---

## 📌 What is Vectorless RAG?

Traditional RAG pipelines follow this pattern:

```
Chunk documents → Embed into vectors → Store in Vector DB → Query by similarity search
```

This project challenges that assumption. Instead of embedding-based retrieval, it uses **PageIndex** to index document pages directly. At query time, **Gemini reasons over the indexed pages** to find and synthesize relevant information — no embeddings, no ANN (approximate nearest neighbor) lookup.

---

## 🗂️ Project Structure

```
vectorless_rag/
├── PageIndex_Vectorless_RAG.ipynb   # Main notebook
├── attention_all_you_need.pdf       # Sample document (Attention Is All You Need)
└── .gitignore
```

---

## ⚙️ How It Works

1. **Load** a PDF document (e.g., *Attention Is All You Need* paper)
2. **Index** pages using PageIndex — no embeddings generated
3. **Query** using natural language
4. **Gemini** reasons over the indexed pages and returns a synthesized answer

---

## ✅ Advantages

- No vector DB setup or maintenance overhead
- No embedding model needed — reduces infra cost and latency
- Simpler pipeline: fewer moving parts = easier to debug
- Works well for structured/paginated documents (PDFs, reports)
- Faster to prototype and deploy
- **Google Gemini is free to use** 😂

---

## ⚠️ Limitations

- Scales differently — retrieval is not O(log n) like ANN search
- Less effective for large unstructured corpora where semantic similarity shines
- Dependent on Gemini's reasoning quality for relevance judgment
- PageIndex is optimized for document-style inputs; less flexible for arbitrary text chunks
- Not a drop-in replacement for vector RAG in all use cases

---

## 🚀 Getting Started

### Prerequisites

- Python 3.12
- Google Gemini API key (free at [Google AI Studio](https://aistudio.google.com/))
- Jupyter Notebook

### Installation

```bash
git clone https://github.com/spylovec2/vectorless_rag.git
cd vectorless_rag
pip install -U pageindex google-generativeai python-dotenv
```

### Set your Gemini API key

```python
GEMINI_API_KEY    = os.getenv("GEMINI_API_KEY")
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Google Gemini | LLM for reasoning & answer generation |
| PageIndex | Document page indexing without vectors |
| Jupyter Notebook | Interactive development environment |
| Python | Core language |

---

## 📄 Sample Document

The repo includes the **"Attention Is All You Need"** paper (`attention_all_you_need.pdf`) as a sample document to test the RAG pipeline against.

---

## 🙏 Credits

- Inspired by **[Krish Naik](https://www.youtube.com/@krishnaik06)**'s video on RAG pipelines
- Sample document: *Attention Is All You Need* — Vaswani et al., 2017

---

## 📬 Connect

If you find this interesting or have feedback, feel free to open an issue or reach out on [LinkedIn](https://www.linkedin.com/in/spylovec2).

---

⭐ **Star this repo if you found it useful!**
