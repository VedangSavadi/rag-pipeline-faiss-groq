# 🔍 RAG Pipeline with FAISS & Groq LLM  
### Case Study: Tech Mahindra – Integrated Energy Major Transitions to Multi-Cloud Access

This project implements a **Retrieval-Augmented Generation (RAG)** pipeline using **FAISS vector store** and **Groq-hosted LLMs (LLaMA 3)** to enable intelligent question answering and summarization over enterprise case study documents.  

The use case is based on **Tech Mahindra case study PDFs**, focusing on:
> *Integrated Energy Major Transitions to Multi-Cloud Access, Accelerating Data Access and Enhancing Decision-Making*

---

## 🚀 Project Overview

Enterprises generate massive volumes of unstructured data (PDFs, reports, case studies). Manually extracting insights is slow and inefficient.

This project solves that by:
- Converting documents into embeddings using **SentenceTransformers**
- Storing them in **FAISS** for fast similarity search
- Using **Groq LLM (LLaMA 3)** to generate grounded, context-aware answers

The result is a **production-style RAG system** capable of answering complex business and technical queries from enterprise documents.

---

## 🧠 Key Features

- 📄 **Multi-PDF ingestion** (Tech Mahindra case studies)
- ✂️ **Intelligent text chunking** with overlap
- 🧬 **Embeddings using all-MiniLM-L6-v2**
- ⚡ **FAISS vector store** for high-speed retrieval
- 🤖 **Groq LLM (LLaMA 3)** for generation
- 🔐 **Secure API key handling using .env**
- 📌 **Source-aware retrieval design**
- 🏗 **Production-ready architecture (clean separation of concerns)**

---

## 🏗 System Architecture

This project follows a **modular, production-style RAG architecture** where each component has a clear responsibility. The design ensures scalability, maintainability, and clean separation of concerns.

### 🔹 High-Level Architecture Diagram

```text
                         ┌─────────────────────────────┐
                         │        User / Client         │
                         │   (Query / Question Input)   │
                         └───────────────┬─────────────┘
                                         │
                                         ▼
                         ┌─────────────────────────────┐
                         │           app.py             │
                         │   (Application Entry Point)  │
                         └───────────────┬─────────────┘
                                         │
                                         ▼
                         ┌─────────────────────────────┐
                         │         RAGSearch            │
                         │  (Orchestration Layer)       │
                         └───────────────┬─────────────┘
                                         │
             ┌───────────────────────────┴───────────────────────────┐
             │                                                       │
             ▼                                                       ▼
┌─────────────────────────────┐                       ┌─────────────────────────────┐
│        FAISS Vector Store   │                       │         Groq LLM             │
│  (Semantic Retrieval Layer) │                       │   (LLaMA 3 – Generation)     │
└───────────────┬─────────────┘                       └───────────────┬─────────────┘
                │                                                       │
                ▼                                                       ▼
┌─────────────────────────────┐                       ┌─────────────────────────────┐
│   Embedding Pipeline        │                       │     Answer / Summary         │
│  (Chunking + Embeddings)    │                       │   (Final Output to User)     │
└───────────────┬─────────────┘                       └─────────────────────────────┘
                │
                ▼
┌─────────────────────────────┐
│     Tech Mahindra PDFs       │
│   (Case Study Documents)     │
└─────────────────────────────┘

