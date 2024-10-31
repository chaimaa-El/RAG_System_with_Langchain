# Retrieval-Augmented Generation (RAG) System with Langchain

This code implements a Retrieval-Augmented Generation (RAG) system using a large language model (LLM) and the Langchain framework. It allows users to ask questions and receive detailed answers by retrieving relevant information from a collection of documents.

## Structure

### 1. Document Retrieval Setup
   - **Vector Store and Embedding Model**: We use Langchain’s retrieval mechanisms, specifically using vector stores to store document embeddings, which enables efficient retrieval of relevant information based on a user query.
   - **Retriever**: A custom `retrieve_with_confidence` function is implemented to search for the most relevant passages across documents using cosine similarity. This helps the system find content most closely related to the user’s query.

### 2. LLM Integration
   - **LLM Model**: We integrate a large language model to handle response generation, using Langchain’s `LLMChain` interface to format retrieved document content as context and combine it with the user’s question to produce a coherent answer.
   - **Prompt Engineering**: A prompt template is designed to format the retrieved context and question for the LLM, ensuring responses are generated in line with information found in the documents.

### 3. Retrieval-Augmented Generation (RAG) Architecture
   - **Combining Retrieval and Generation**: The system follows the RAG architecture, first retrieving relevant document passages and then using these passages as context to generate responses.
   - **Confidence Filtering**: In `retrieve_with_confidence`, confidence scores are filtered to ensure only high-confidence results are passed to the LLM, reducing the chance of generating answers based on irrelevant information.
   - **Caching Mechanism**: Frequently asked queries and their responses are stored in a cache to enhance response speed and reduce computation for repeated questions.

## Files and Code
   - **Notebook**: `RAG_System_with_Langchain.ipynb` contains the entire workflow, from document indexing and retrieval to response generation.
   - **Key Functions**:
      - `generate_answer`: Uses the `LLMChain` with context retrieved from the documents to generate an answer.
      - `generate_answer2`: An alternative function using `RetrievalQA` for retrieving and generating answers in a single step.

## Installation and Requirements

The following dependencies are required to run this project:

```bash
pip install langchain langchain_community langchain-chroma faiss-gpu pymupdf sentence-transformers

