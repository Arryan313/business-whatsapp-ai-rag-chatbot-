# Business WhatsApp AI RAG Chatbot

An AI-powered WhatsApp chatbot built with **n8n**, **OpenAI**, **Qdrant**, and **Google Drive**.  
It uses Retrieval-Augmented Generation (RAG) to answer customer questions from your own business documents.

This workflow is ideal for:

- Electronics stores
- Customer support teams
- Product FAQ automation
- Internal knowledge base assistants
- Any business that wants a WhatsApp AI assistant

## Features

- WhatsApp webhook integration with Meta
- Receives and replies to WhatsApp messages
- Uses Google Drive as a document source
- Chunks and embeds documents into Qdrant
- RAG-powered AI Agent with OpenAI
- Conversation memory with Window Buffer Memory
- Sends responses back to WhatsApp
- Supports text-only message handling

## Architecture

```mermaid
flowchart TD
    A[Google Drive Folder] --> B[Download Files]
    B --> C[Token Splitter]
    C --> D[OpenAI Embeddings]
    D --> E[Qdrant Vector Store]

    F[WhatsApp User] --> G[Webhook: Respond]
    G --> H{Is Message?}
    H -->|Yes| I[AI Agent]
    I --> J[OpenAI Chat Model]
    I --> K[Qdrant Vector Store]
    I --> L[Window Buffer Memory]
    I --> M[Send WhatsApp Reply]
    H -->|No| N[Only message response]
