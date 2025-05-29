# Retrieval-Augmented Generation (RAG)
This repository contains practical resources for a hands-on workshop on Retrieval-Augmented Generation (RAG). It includes core concepts, architectural insights, implementation steps, and real-world examples using tools like FAISS, LangChain, and LlamaIndex to build context-aware, retrieval-powered AI systems.

# 🔍 Retrieval-Augmented Generation (RAG) Pipeline

This repository demonstrates the architecture of a RAG (Retrieval-Augmented Generation) system, which enhances the output of large language models by grounding them in external knowledge sources.

## 🖼️ Architecture Overview

![RAG Workflow](https://github.com/robaita/rag_workshop/blob/main/RAG_Workflow.png)

---

## 🧠 Pipeline Breakdown

### 🔵 Training Phase

#### 📥 Data Ingestion
Upload your raw documents into the system. These documents serve as the foundational knowledge base that the model will later retrieve from during inference.

> _Purpose: Source content for training and embedding._

#### ✂️ Data Chunking
Large documents are split into smaller, manageable chunks. This improves the granularity of information and ensures more relevant search results during retrieval.

> _Benefit: Enhanced semantic representation and retrieval precision._

#### 🧬 Data Embedding
Each chunk is converted into a dense vector using embedding models (e.g., Sentence Transformers). These vectors capture semantic meaning, enabling similarity-based retrieval.

> _Output: Vector representation of textual content._

#### 💾 Embedding Storage
The vector embeddings are stored in a vector database (like FAISS, Chroma, or Pinecone). This allows fast similarity searches using cosine or dot product measures.

> _Result: A searchable semantic index._

---

### 🟣 Testing Phase

#### ❓ Query
A user provides a natural language query, typically a question or a prompt needing document-backed context.

#### 🧮 Query Embedding
The input query is also converted into a vector using the same embedding model as in the training phase.

> _Result: Query vector for similarity comparison._

#### 🔍 Top-K Results
The query vector is compared with stored embeddings to retrieve the top-k most semantically similar document chunks.

> _Goal: Contextual document retrieval._

#### 🤖 LLM Response
The selected document chunks are passed along with the original query to an LLM (e.g., GPT, FLAN-T5). The model generates a response grounded in retrieved knowledge.

> _Outcome: Accurate, context-rich generation._

---

## 🔁 End-to-End Flow

1. **Documents → Chunked → Embedded → Stored**
2. **Query → Embedded → Top-K Retrieved → Combined with Prompt → Answer Generated**

---