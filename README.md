# MultiAgent-RAG-Workflow

This repository contains a **Multi-Agent Retrieval-Augmented Generation (RAG) workflow** built with **LangGraph** and **LangChain**.

The system models the pipeline as a graph of independent agents (nodes). Each agent performs a focused responsibility and contributes to generating a final, grounded response to a user query.

## Workflow Overview

When a user submits a query, the workflow proceeds through the following agents:

1. **Relevance Checker Agent**
   - Checks whether the query is relevant to the documents already stored in the vector database.
   - If relevant, it triggers retrieval of matching documents from the vector store.

2. **Research Agent**
   - Receives the user query and the retrieved context.
   - Produces a draft response based on the supplied documents.

3. **Verifier Agent**
   - Validates whether the draft is relevant, accurate, and grounded in the retrieved evidence.
   - If the draft passes verification, it is returned to the user.
   - If not, it is sent back to the Research Agent for revision.

This verification loop continues until the draft is sufficiently grounded and reliable.

## Core Idea

Instead of relying on a single generation step, this architecture separates retrieval, drafting, and validation into specialized agents. This improves response quality, factual grounding, and robustness for knowledge-based question answering.