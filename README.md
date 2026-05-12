Project Title: Medical RAG Chatbot (End-to-End LLMOps)
Project Overview
This project is a specialized Medical Information System that uses Retrieval-Augmented Generation (RAG) to provide accurate answers from medical documents. Unlike standard chatbots that might hallucinate, this system "consults" a trusted medical PDF database before generating a response, ensuring the information is grounded in real medical literature.

Technical Architecture
The project is built using a modular LLMOps pipeline, divided into several key stages:

Data Ingestion: Loads and processes medical PDFs using PyPDFLoader.

Text Processing: Uses RecursiveCharacterTextSplitter to break down large medical texts into manageable chunks for better context retrieval.

Vector Embedding: Converts text chunks into high-dimensional vectors using HuggingFace Embeddings (sentence-transformers).

Vector Store: Uses FAISS (Facebook AI Similarity Search) to store and perform lightning-fast similarity searches on the embeddings.

LLM Integration: Leverages specialized Large Language Models (via HuggingFace Hub or Groq) to generate human-like answers based on the retrieved context.

Web Interface: A user-friendly Flask application with a clean HTML/CSS frontend to interact with the chatbot in real-time.

Key Features
Context-Aware Responses: The bot only answers based on the provided medical data, reducing "hallucinations."

Local Vector Storage: FAISS allows for efficient local indexing without needing expensive cloud databases.

Modular Codebase: Organized into separate components for logging, exceptions, configuration, and core logic for better maintainability.

LLMOps & Deployment Stack
This project focuses heavily on the "Ops" side of AI:

Containerization: Uses Docker to ensure the app runs identically across all environments.

CI/CD Pipeline: Integrated with Jenkins for automated building and testing.

Security: Scanned with Aqua Trivy for vulnerabilities before deployment.

Cloud Deployment: Deployed to AWS (using ECR and an AWS Runner) to handle real-world traffic.

How it Works
User asks a medical question via the Flask web interface.

The system converts the query into a vector embedding.

FAISS searches the local vector store for the top-k most relevant text chunks from the medical PDF.

The LLM receives the question + the relevant chunks as "context."

The LLM generates a precise answer, which is displayed back to the user.
