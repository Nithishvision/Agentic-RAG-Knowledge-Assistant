# Agentic RAG Knowledge Assistant

An Agentic Retrieval-Augmented Generation (RAG) application built using **LangGraph, LangChain, Hugging Face, ChromaDB, and OpenAI**. The project retrieves relevant information from technical documents, evaluates document relevance, rewrites queries when necessary, and generates context-aware answers using an LLM.

## Project Overview

Traditional LLM applications can generate incorrect answers or lack access to specific information. Retrieval-Augmented Generation (RAG) addresses this limitation by retrieving relevant information from a knowledge base before generating a response.

This project extends the RAG workflow with an agentic approach using LangGraph. The workflow can evaluate retrieved documents and rewrite a question when the retrieved information is not relevant enough.

## System Architecture

![Agentic RAG Architecture](images/rag-architecture.png)

### How It Works

1. **Document Loading:** Load technical blog posts or other supported text documents into the knowledge base.
2. **Text Chunking:** Split documents into smaller chunks with overlap to preserve context.
3. **Embedding Generation:** Convert text chunks into vector embeddings using the Hugging Face `all-MiniLM-L6-v2` model.
4. **Vector Storage:** Store document embeddings in ChromaDB for semantic similarity search.
5. **Agent Workflow:** Use LangGraph to coordinate the retrieval and response-generation process.
6. **Document Retrieval:** Retrieve relevant document chunks based on the user's question.
7. **Relevance Grading:** Use an LLM to evaluate whether the retrieved documents are relevant to the question.
8. **Query Rewriting:** If the retrieved documents are not relevant, rewrite the question to improve the next retrieval attempt.
9. **Answer Generation:** Use OpenAI GPT-4o-mini to generate an answer based on the retrieved context.
10. **Final Response:** Return a context-aware answer to the user.

## Key Features

- Agentic RAG workflow orchestrated with LangGraph.
- Semantic search using vector embeddings.
- Document storage and retrieval with ChromaDB.
- Hugging Face sentence-transformer embeddings.
- LLM-based document relevance grading.
- Query rewriting to improve retrieval.
- Context-aware answer generation using OpenAI.
- Modular workflow with conditional routing.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| LangChain | LLM and retrieval components |
| LangGraph | Agent workflow orchestration |
| Hugging Face | Text embedding model |
| `all-MiniLM-L6-v2` | Sentence embeddings |
| ChromaDB | Vector database |
| OpenAI GPT-4o-mini | Relevance grading, query rewriting, and answer generation |
| Jupyter Notebook | Development and experimentation |

## Project Structure

```text
Agentic-RAG-Knowledge-Assistant/
├── langgraph-agentic-rag-huggingface.ipynb
├── images/
│   └── rag-architecture.png
├── README.md
├── requirements.txt
├── .env.example
└── .gitignore
```

## Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/Nithishvision/Agentic-RAG-Knowledge-Assistant.git
cd Agentic-RAG-Knowledge-Assistant
```

### 2. Create a Virtual Environment

```bash
python -m venv .venv
```

Activate the environment.

**Windows:**

```bash
.venv\Scripts\activate
```

**macOS/Linux:**

```bash
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Configure the OpenAI API Key

Create a `.env` file in the project root or configure the environment variable in your development environment.

```env
OPENAI_API_KEY=your_openai_api_key
```

Replace the placeholder with your own API key. Never upload the `.env` file or expose your API key in the notebook or GitHub repository.

### 5. Run the Notebook

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open `langgraph-agentic-rag-huggingface.ipynb` and execute the cells in order.

The application requires a valid OpenAI API key and internet access for the relevant model downloads and API calls.

## Example Use Case

A user asks:

> What are the key concepts behind Retrieval-Augmented Generation?

The application retrieves relevant document chunks from ChromaDB, evaluates their relevance, and generates an answer using the retrieved context.

If the retrieved information is not relevant, the workflow can rewrite the question and attempt retrieval again.

*The example illustrates the intended workflow; actual answers depend on the indexed documents and model responses.*

## Learning Outcomes

This project demonstrates practical experience with:

- Building a Retrieval-Augmented Generation pipeline.
- Working with vector embeddings and semantic search.
- Integrating LLMs with retrieval tools.
- Designing conditional workflows with LangGraph.
- Implementing relevance grading and query rewriting.
- Managing API credentials and Python dependencies.

## Limitations and Future Improvements

Potential improvements include:

- Adding a retry limit to prevent repeated retrieval attempts.
- Evaluating retrieval quality and answer faithfulness with a test dataset.
- Adding source citations and document-level traceability.
- Supporting PDF, DOCX, and other document formats.
- Building a user interface with Streamlit.
- Adding automated evaluation metrics and error handling.
- Deploying the application through an API using FastAPI.

These are proposed improvements unless explicitly implemented in the current version.

## Security

- Store API keys in environment variables or a secrets manager.
- Do not commit `.env` files or credentials.
- Review notebook outputs before publishing the repository.

## Author

**Nithish Kumar**

- GitHub: [Nithishvision](https://github.com/Nithishvision)
- LinkedIn: [Nithish Kumar](https://www.linkedin.com/in/nithishkumar-data-analyst/)
- Kaggle: [lotusrisenithish](https://www.kaggle.com/lotusrisenithish)
