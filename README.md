# Enhancing Healthcare Intelligence with Retrieval-Augmented Generation (RAG)

An AI-powered Clinical Decision Support System that combines Large Language Models (LLMs) with Retrieval-Augmented Generation (RAG) to deliver accurate, evidence-based medical responses grounded in trusted healthcare literature.

![Python](https://img.shields.io/badge/Python-3.10-blue)
![LangChain](https://img.shields.io/badge/LangChain-RAG-green)
![ChromaDB](https://img.shields.io/badge/VectorDB-ChromaDB-orange)
![LLM](https://img.shields.io/badge/LLM-Llama2-red)
![License](https://img.shields.io/badge/License-MIT-yellow)

### Overview

Modern healthcare professionals face an overwhelming amount of medical literature, clinical guidelines, and research publications. While Large Language Models (LLMs) have transformed natural language understanding, they frequently produce hallucinated or outdated medical information when operating without reliable knowledge sources.

This project addresses this challenge by implementing a Retrieval-Augmented Generation (RAG) architecture that grounds every AI-generated response using authoritative medical documents before producing an answer.

Instead of relying solely on the knowledge stored inside an LLM, the system first retrieves the most relevant sections from the Merck Manual of Diagnosis & Therapy, then uses those passages as context for response generation.

The result is a significantly more reliable clinical assistant capable of providing:

- Evidence-based responses
- Context-aware reasoning
- Reduced hallucinations
- Source-grounded medical information
- Improved answer relevance and accuracy

### Project Objectives

The primary goals of this project are:

- Build a medical Question Answering system using Retrieval-Augmented Generation.
- Reduce hallucinations commonly observed in standalone LLMs.
- Enable semantic retrieval from large healthcare documents.
- Compare Prompt Engineering with RAG architecture.
- Evaluate response quality using automated metrics.
- Demonstrate how modern AI can improve clinical knowledge retrieval.

### Key Features

✅ Clinical Question Answering

✅ Retrieval-Augmented Generation (RAG)

✅ Local LLM Inference

✅ Vector Database Search

✅ Semantic Embedding Retrieval

✅ Prompt Engineering Comparison

✅ Automated Evaluation Pipeline

✅ Hallucination Reduction

✅ Evidence-Based Responses

✅ Modular Architecture

### Problem Statement

Healthcare professionals often require quick access to reliable clinical information.

Traditional search engines return thousands of unrelated documents.

Similarly, standalone LLMs may generate convincing—but incorrect—medical advice due to the absence of real-time knowledge retrieval.

This project solves that limitation by allowing the model to search trusted medical documents before generating answers, ensuring every response is grounded in authoritative evidence.

### Solution

The proposed solution integrates:

```
Medical PDF
      │
      ▼
Document Processing
      │
      ▼
Text Chunking
      │
      ▼
Embedding Generation
      │
      ▼
Chroma Vector Database
      │
      ▼
Similarity Search
      │
      ▼
Relevant Context
      │
      ▼
Llama-2 LLM
      │
      ▼
Evidence-Based Medical Answer
```

Rather than asking the LLM to answer directly, the model first retrieves the most relevant clinical passages and only then generates a response.

### Dataset

#### Primary Source

**Merck Manual of Diagnosis & Therapy**

 #### Dataset Characteristics

- 4,114+ pages
- Comprehensive medical reference
- Clinical procedures
- Disease diagnosis
- Drug information
- Treatment guidelines
- Critical care protocols
- Surgery
- Neurology
- Dermatology
- Internal Medicine

### Technologies Used

| Technology | Purpose |
|------------|----------|
| Python | Programming Language |
| LangChain | RAG Pipeline |
| ChromaDB | Vector Database |
| HuggingFace | Embedding Models |
| Sentence Transformers | Text Embeddings |
| Llama.cpp | Local LLM Inference |
| PyMuPDF | PDF Processing |
| Pandas | Data Analysis |
| NumPy | Numerical Computing |
| Regex | Text Extraction |

### AI Models

### Language Model

**Llama-2-13B Chat (GGUF)**

- Local inference
- GPU accelerated
- Quantized model
- 4096 Context Window

### Embedding Model

**sentence-transformers/all-MiniLM-L6-v2**

Features:

- 384-dimensional embeddings
- Fast inference
- Semantic similarity search
- Normalized embeddings

### Project Workflow

#### Step 1 — Environment Setup

- Install dependencies
- Configure CUDA
- Load required libraries
- Initialize models

#### Step 2 — Document Loading

Medical PDF is loaded using PyMuPDFLoader.

The loader extracts:

- Text
- Metadata
- Page numbers
- Document structure

#### Step 3 — Text Chunking

Large documents cannot be processed directly.

The document is divided into overlapping chunks using:

```
RecursiveCharacterTextSplitter
```

Configuration:

- Chunk Size: 520
- Chunk Overlap: 60

Benefits:

- Better context preservation
- Improved retrieval
- Reduced information loss

#### Step 4 — Embedding Generation

Each chunk is converted into a numerical vector using:

```
all-MiniLM-L6-v2
```

Embeddings capture semantic meaning rather than simple keyword matching.

#### Step 5 — Vector Database

Generated embeddings are stored inside **ChromaDB**.

The database enables:

- Fast similarity search
- Semantic retrieval
- Efficient indexing
- Metadata storage

#### Step 6 — Query Processing

When a user asks a question:

1. Convert query into embedding
2. Search ChromaDB
3. Retrieve top relevant chunks
4. Combine retrieved context
5. Send context to LLM

#### Step 7 — Response Generation

The LLM receives:

- User question
- Retrieved passages
- System prompt

It generates an answer strictly based on retrieved evidence.

#### Step 8 — Evaluation

The project evaluates generated responses using:

### Groundedness

Measures whether the answer is supported by retrieved documents.

### Relevance

Measures how well the response answers the question.

### Evaluation Results

| Approach | Groundedness | Relevance |
|-----------|--------------|-----------|
| Prompt Engineering | 2.67 / 5 | 3.00 / 5 |
| RAG Pipeline | 4.50 / 5 | 4.50 / 5 |

### Key Observation

The RAG-based system consistently produces:

- More accurate responses
- Better factual grounding
- Lower hallucination rates
- Improved clinical reliability

### Project Structure

```
Healthcare-RAG/
│
├── data/
│      medical_diagnosis.pdf
│
├── notebooks/
│      Enhancing Healthcare Intelligence.ipynb
│
├── vectorstore/
│      ChromaDB
│
├── models/
│      Llama2 GGUF
│
├── evaluation/
│      Results
│
├── images/
│
├── README.md
│
└── requirements.txt
```

### How to Run

### Clone Repository

```bash
git clone https://github.com/yourusername/Healthcare-RAG.git
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Launch Jupyter Notebook

```bash
jupyter notebook
```

Open:

```
Enhancing Healthcare Intelligence.ipynb
```

Execute the notebook cells sequentially.

### Applications

This project can be adapted for:

- Clinical Decision Support
- Hospital Information Systems
- Medical Education
- Healthcare Chatbots
- Telemedicine
- Drug Information Retrieval
- Medical Research Assistance
- Healthcare Knowledge Management

### Future Improvements

- Support multiple medical textbooks
- Hybrid retrieval (Dense + BM25)
- Cross-Encoder reranking
- Multi-modal document understanding
- Streaming responses
- Real-time medical guideline updates
- FHIR integration
- Electronic Health Record (EHR) integration
- Medical image retrieval
- Web application deployment

### Learning Outcomes

This project demonstrates practical implementation of:

- Retrieval-Augmented Generation
- Vector Databases
- Semantic Search
- Prompt Engineering
- LangChain
- Local LLM Deployment
- Clinical AI Systems
- AI Evaluation Metrics
- Embedding Models
- Large Document Processing
