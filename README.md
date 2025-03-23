# Document Similarity Search API

## Overview
This API provides a document similarity search service using sentence embeddings and FAISS for vector search. It is built with FastAPI and supports multiple similarity metrics, including L2, Cosine, and Dot Product.

## Features
- Compute embeddings for a dataset of documents.
- Search for similar documents using FAISS.
- Supports multiple similarity metrics (L2, Cosine, Dot Product).
- Allows adding new documents dynamically.
- FastAPI-based REST API.

## Installation
 Python installed, then installed the required dependencies:

```bash
pip install faiss-cpu fastapi uvicorn sentence-transformers pandas numpy
```

## Running the API
Command to start the FastAPI server:

```bash
python app.py
```

## API Endpoints
### Home
**GET `/`**
- Returns a welcome message.

### Search Documents
**POST `/api/search`**
- Searches for similar documents based on the given query.

**Request Body:**
```json
{
  "q": "query text here",
  "metric": "cosine"  // Options: "l2", "cosine", "dot"
}
```

**Response:**
```json
{
  "query": "query text here",
  "metric": "cosine",
  "results": ["Similar document 1", "Similar document 2", ...]
}
```

### Add Document
**POST `/api/add_document`**
- Adds a new document to the FAISS index.

**Request Body:**
```json
{
  "text": "New document content here"
}
```

**Response:**
```json
{
  "message": "Document added successfully!",
  "total_documents": 101
}
```

## Notes
- The model used for embeddings is `all-MiniLM-L6-v2` from Sentence Transformers.
- The document dataset is loaded from `Articles.csv`.
- FAISS is used for efficient similarity search.

## License
This project is open-source. Feel free to use and modify it as needed.

