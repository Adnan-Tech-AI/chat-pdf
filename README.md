📄 chat-pdf

Chat with PDFs using LangChain and OpenAI

chat-pdf is a lightweight Python library that lets you load a PDF, ask questions about it, and optionally get source documents — all with a few lines of code.

It is built on LangChain 1.2.x, uses Chroma for vector storage, and OpenAI models for embeddings and answers.

✨ Features

✅ Simple API (functions, not heavy classes)

📄 Load and index PDFs

💬 Ask questions in natural language

📚 Retrieve source documents (pages/chunks)

🔒 Stable, version-pinned LangChain setup

🚀 Ready for local scripts, notebooks, and APIs

📦 Installation
pip install chat-pdf


Note
This package is pinned to LangChain 1.2.x for stability.

🔑 Requirements

Python 3.10+

OpenAI API key

Set your API key as an environment variable or pass it directly:

export OPENAI_API_KEY="your-api-key"

🚀 Quick Start
1️⃣ Load a PDF
from chat_pdf import load_pdf

db = load_pdf(
    "policy.pdf",
    api_key="OPENAI_API_KEY"
)


This:

Loads the PDF

Splits it into chunks

Creates embeddings

Stores them in a Chroma vector database

2️⃣ Ask a question
from chat_pdf import ask_question

answer = ask_question(
    "What is the refund policy?",
    db=db,
    api_key="OPENAI_API_KEY"
)

print(answer)

📚 Ask a question with sources
from chat_pdf import ask_question_with_sources

result = ask_question_with_sources(
    "What are the termination conditions?",
    db=db,
    api_key="OPENAI_API_KEY"
)

print("Answer:")
print(result["answer"])

print("\nSources:")
for doc in result["sources"]:
    print(doc.metadata)


Returns:

answer → generated response

sources → list of source documents used by the model

⚙️ Optional Parameters
load_pdf
load_pdf(
    pdf_path,
    api_key,
    chunk_size=1000,
    chunk_overlap=200,
    persist_directory=None
)

Parameter	Description
chunk_size	Size of text chunks
chunk_overlap	Overlap between chunks
persist_directory	Directory to persist Chroma DB
ask_question / ask_question_with_sources
ask_question(
    question,
    db,
    api_key,
    model_name="gpt-3.5-turbo",
    search_kwargs={"k": 4},
    system_prompt=None
)

Parameter	Description
model_name	OpenAI chat model
search_kwargs	Retriever settings
system_prompt	Custom system prompt
🔒 Version Compatibility

This package is intentionally pinned for stability.

chat-pdf	LangChain
1.2.0.0	1.2.x

Upgrading LangChain versions may break APIs.
New releases of chat-pdf will track newer LangChain versions explicitly.
