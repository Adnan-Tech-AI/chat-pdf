# chat-pdf

Chat with PDF documents using LangChain and OpenAI.

`chat-pdf` is a lightweight Python library that allows you to load a PDF, ask questions about its content, and optionally retrieve the source passages used to generate the answers.

The library is intentionally simple and pinned to stable LangChain versions to avoid breaking changes.

---

## Features

- Load and index PDF documents
- Ask natural language questions
- Retrieve answers with or without source documents
- Minimal, function-based API
- Stable LangChain 1.2.x compatibility
- Suitable for scripts, notebooks, and APIs

---

## Installation

```bash
pip install chat-pdf

Requirements

Python 3.10 or higher

OpenAI API key

Set your API key as an environment variable or pass it directly in code:

export OPENAI_API_KEY="your-api-key"

Quick Start
Load a PDF
from chat_pdf import load_pdf

db = load_pdf(
    "document.pdf",
    api_key="OPENAI_API_KEY"
)


This will:

Load the PDF file

Split it into chunks

Generate embeddings

Store them in a Chroma vector database

