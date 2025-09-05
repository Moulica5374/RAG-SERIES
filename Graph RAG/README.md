#  Financial RAG with Knowledge Graphs

## Overview
This project implements a **Retrieval-Augmented Generation (RAG)** pipeline tailored for the **financial domain**, enhanced with **Knowledge Graphs** for structured reasoning.  
Instead of relying only on vector search, it extracts **entities and relationships** from financial filings (e.g., SEC 10-K/10-Q reports) and builds a **knowledge graph** to enable **multi-hop, explainable queries**.

---

##  Features
-  **Document Parsing**: Load and process SEC filings or other financial documents (JSON, HTML, TXT).  
-  **Entity & Relation Extraction**: Identify companies, executives, risks, financial metrics, etc.  
-  **Knowledge Graph Construction**: Build graphs capturing entity relationships.  
-  **Hybrid Retrieval**: Combine semantic search with graph traversal.  
-  **LLM Integration**: Use large language models for context-aware answers.  
-  **Explainability**: Provide reasoning paths along with answers.

---

##  Tech Stack
- **Language Models**: OpenAI GPT / Hugging Face Transformers  
- **Graph Libraries**: NetworkX / Neo4j  
- **Vector Store**: FAISS / Chroma  
- **NLP**: spaCy, NLTK  
- **Environment**: Jupyter Notebook (Python 3.8+)  

---

##  Project Structure
-- **Financial_Rag(Knowledge_Graphs).ipynb
-- **data.json
-- 



---

## How It Works
1. **Load Data** → Parse SEC filings (10-K/10-Q).  
2. **Preprocess** → Extract sections (Business, Risk Factors, etc.).  
3. **Entity Recognition** → Detect companies, executives, and financial concepts.  
4. **Graph Construction** → Build a knowledge graph of entities & relationships.  
5. **Hybrid Retrieval** → Combine vector similarity + graph traversal.  
6. **Answer Generation** → Pass retrieved context into the LLM.  

---

##  Example Use Cases
- “What risks did NetApp highlight in their 2023 10-K?”  
- “Which executives are tied to cybersecurity initiatives?”  
- “Compare how two companies describe competition.”  
- “Summarize R&D investment trends across filings.”  

---

## Getting Started

### Prerequisites
- Python 3.8+  
- Jupyter Notebook  

### Installation
```bash
git clone <your-repo-url>
cd <your-repo>
pip install -r requirements.txt
```

### Example Input & Output:

Summarize NetApp’s competitive risks in 2023.



