# RAG Retrieval Techniques

This folder contains a structured, hands-on exploration of **retrieval strategies used in Retrieval-Augmented Generation (RAG)** systems.

The goal of this work is to understand **why naive similarity search is often insufficient**, and how advanced retrieval techniques improve:
- relevance
- diversity
- context quality
- answer faithfulness

Each notebook focuses on **one retrieval technique**, explains the problem it solves, and demonstrates how it behaves in practice.

---

## Why Retrieval Matters in RAG

In RAG pipelines, **retrieval quality directly controls generation quality**.

Common challenges:
- Redundant chunks
- Loss of document-level context
- Query ambiguity
- Stale or time-sensitive information
- Overly long or noisy context

The techniques implemented here address these challenges step by step.

---

## Techniques Implemented

### 1️.Similarity Search
**Notebook:** `Similarity_Search.ipynb`

- Baseline retrieval using vector similarity
- Fast and simple
- Suffers from redundancy and lack of diversity

**Best used when:** documents are short and queries are specific.

---

### 2️.Maximum Marginal Relevance (MMR)
**Notebook:** `Maximum_Mariginal_Relevance.ipynb`

- Balances relevance and diversity
- Reduces repetitive chunks
- Improves coverage of different subtopics

**Tradeoff:** slightly less relevance per chunk, but better overall context.

---

### 3️.Multi-Query Retrieval
**Notebook:** `Multi_Query_Retrieval.ipynb`

- Uses an LLM to generate multiple query variations
- Retrieves documents for each variation
- Combines results for broader coverage

**Best used when:** user queries are vague or underspecified.

---

### 4️.Parent Document Retrieval
**Notebook:** `Parent_Retrieval.ipynb`

- Embeds small chunks for accuracy
- Retrieves larger parent documents for context
- Solves the “lost context” problem

**Best used when:** documents are long (PDFs, reports, manuals).

---

### 5️.Contextual Compression
**Notebook:** `Contextual_Compression.ipynb`

- Retrieves documents first
- Then compresses them using an LLM
- Removes irrelevant sentences before generation

**Benefit:** lower token usage with higher signal-to-noise ratio.

---

### 6️.Time-Weighted Retrieval
**Notebook:** `Time_Weighted_Retrieval_.ipynb`

- Prioritizes more recent documents
- Combines semantic relevance with recency
- Useful for evolving knowledge bases

**Best used when:** information freshness matters.

---

### 7️.Self-Query Retrieval
**Notebook:** `Self_Query.ipynb`

- LLM converts natural language queries into structured filters
- Enables metadata-aware retrieval
- Supports constraints like date, author, category

**Example:** “papers after 2022 about transformers”

---

##  Learning Outcomes

Through these experiments, this work demonstrates:
- Why retrieval is the bottleneck in RAG systems
- How different strategies trade off relevance vs diversity
- When LLMs appear **inside retrieval**, not just generation
- Practical decision-making for real-world RAG pipelines

---

## Tech Stack
- Python
- Vector databases
- Embeddings
- LLM-assisted retrievers
- Jupyter Notebooks

---

##  Next Steps
- Add quantitative evaluation (precision@k, recall@k)
- Compare latency across retrievers
- Integrate retrieval strategies into a single configurable RAG pipeline
