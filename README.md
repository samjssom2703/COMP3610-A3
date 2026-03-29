# COMP 3610 — Assignment 3: Big Data Analytics

## Overview

This project implements a complete big data analytics pipeline combining Apache Spark for distributed data processing with a Retrieval-Augmented Generation (RAG) system for document-based question answering. The two systems are integrated through an LLM-powered query router into a unified analytics application for NYC transportation data.

## Components


**Part 1** - Spark Distributed Processing — loading, cleaning, SQL analytics, and optimization of 2.9M+ NYC taxi trip records
**Part 2** - RAG Pipeline — PDF ingestion, chunking, embedding, vector storage, and LLM-powered Q&A over transportation policy documents
**Part 3** - Integrated Application — LLM query router, NL-to-SQL data handler, and end-to-end hybrid analytics
**Part 4** - Documentation and reproducibility

## Tech Stack

- **Apache Spark (PySpark)** — distributed data processing and SQL analytics
- **ChromaDB** — vector database for document embeddings
- **sentence-transformers** — all-MiniLM-L6-v2 for embedding generation
- **LangChain** — PDF loading and text chunking
- **OpenAI-compatible LLM** — llama3-8b-instruct for generation, routing, and evaluation
- **Pandas / Matplotlib / Seaborn** — data analysis and visualization

## Prerequisites

- Python 3.10+
- Java 21 (required for PySpark — set `JAVA_HOME`)
- Internet access (data downloads + LLM API)

## Quick Start

```bash
# Clone and setup
git clone <repository-url>
cd COMP3610-A3

# Create virtual environment
python -m venv .venv
.venv\Scripts\activate          # Windows
# source .venv/bin/activate     # Linux/Mac

# Install dependencies
pip install -r requirements.txt
```

## Running

1. Open `assignment3.ipynb` in VS Code or Jupyter
2. Select the `.venv` Python kernel
3. **Run all cells sequentially** — each cell depends on previous outputs
4. Expected runtime: ~15-25 minutes

## Project Structure

```
COMP3610-A3/
├── assignment3.ipynb      # Main notebook with all code, outputs, and analysis
├── requirements.txt       # Python package dependencies
├── README.md              # This file
├── .gitignore             # Git ignore rules
├── docs/                  # NYC transportation policy PDFs (5 documents)
├── data/                  # Downloaded taxi data (gitignored)
├── chroma_db/             # ChromaDB persistent vector store (gitignored)
└── partitioned_trips/     # Partitioned parquet output (gitignored)
```

## Data Sources

- **NYC Yellow Taxi Trip Records** (January 2024) — ~2.96M trip records from the NYC TLC
- **NYC Transportation Policy PDFs** — 5 public documents covering Vision Zero, congestion pricing, bus improvements, cycling, and strategic planning

## Key Features

- Full data cleaning pipeline with 4-stage filtering and 5 derived columns
- 5 Spark SQL analytical queries with window functions and CTEs
- Performance optimization: caching benchmarks, partitioned Parquet, partition pruning
- RAG pipeline with chunking experiment (500/1000/2000 chars) and ChromaDB
- LLM-based query routing with 15-query test suite
- NL-to-SQL translation with retry mechanism
- HYBRID query handling combining structured data + document retrieval
- Comprehensive RAG evaluation with 10 ground-truth Q&A pairs

## AI Tool Disclosure

AI Tools were used as a coding assistant during the development of this project. (ChatGPT and Copilot)

- The AI tool assisted with code debugging, and documentation assistance.
- Assistance with the LLM key usage and recommendations on where to place the generated key.
- README was done by GitHub Copilot.
- AI was also used to run and check the assignment3.ipynb file against the assignment 3 pdf to see if there were any errors and to verify the validity and correctness of the code.
