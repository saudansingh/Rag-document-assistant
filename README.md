#  Advanced RAG Document Assistant

A high-accuracy RAG (Retrieval-Augmented Generation) document assistant that supports multiple document formats.

## Features

- **Multi-Document Support**: PDF, Word (.docx), and Text files
- **Advanced Chunking**: Intelligent text splitting with metadata
- **High-Accuracy Retrieval**: Similarity search with score thresholds
- **Gemini AI Integration**: Powered by Google's Gemini for accurate responses
- **Real-time Metrics**: Processing statistics and document information
- **Accuracy**: Optimized for precise answers
- **Modern Chat Interface**: ChatGPT-like user experience
- **Rich Metadata**: UUID-based chunk identification and tracking

## Tech Stack

- **Frontend**: Streamlit
- **Document Processing**: 
  - PyMuPDF (PDF extraction)
  - python-docx (Word documents)
  - LangChain Text Loader
- **Embeddings**: Sentence Transformers (all-MiniLM-L6-v2)
- **Vector Database**: FAISS
- **LLM**: Google Gemini Pro
- **Chunking**: LangChain RecursiveCharacterTextSplitter
- **Metadata**: UUID for unique chunk identification

## Prerequisites

- Python 3.8+
- Google Gemini API key
- Git

## Quick Start

### 1. Clone and Setup

```bash
git clone <repository-url>
cd rag-document-assistant
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure API Key

```bash
# Copy environment file
cp .env.example .env

# Edit .env and add your Gemini API key
GOOGLE_API_KEY=your_gemini_api_key_here
```

### 4. Run the Application

```bash
streamlit run app.py
```

The application will be available at `http://localhost:8501`

##  Configuration

### Document Processing Parameters

The system uses optimized parameters for high accuracy:

- **Chunk Size**: 1000 characters
- **Chunk Overlap**: 200 characters
- **Retrieval**: Top 5 most relevant chunks
- **Similarity Threshold**: 0.3 (minimum relevance score)
- **LLM Temperature**: 0.1 (for consistent, accurate responses)

### Embedding Model

Uses `sentence-transformers/all-MiniLM-L6-v2` for:
- Fast processing
- High-quality embeddings
- CPU compatibility
- Multilingual support

##  Usage Guide

### 1. Upload Documents
- Click "Choose documents" in the sidebar
- Select PDF, Word, or Text files
- Click "Process Documents"

### 2. View Processing Metrics
- Number of documents processed
- Total chunks created
- Character count
- Document information

### 3. Ask Questions
- Type questions in the chat interface
- Get accurate answers based on document content
- Chat history is maintained

### 4. Get Results
- Responses include source information
- Page/paragraph references
- High accuracy with context

##  Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Document      │───▶│  Text Extraction │───▶│  Chunking with  │
│   Upload        │    │  (PyMuPDF/Docx)  │    │   Metadata     │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                                                        │
                                                        ▼
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   User Query    │───▶│ Vector Search    │───▶│  Embeddings     │
│   (Streamlit)   │    │   (FAISS)        │    │ (Sentence-T)    │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                                                        │
                                                        ▼
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Answer Display│◀───│  Gemini LLM      │◀───│ Context Retrieval│
│   (Streamlit)   │    │  (Gemini Pro)    │    │   (LangChain)   │
└─────────────────┘    └──────────────────┘    └─────────────────┘
```

##  Accuracy Features

### Enhanced Retrieval
- **Similarity Score Threshold**: Filters irrelevant chunks
- **Multiple Document Retrieval**: Uses top 5 relevant chunks
- **Metadata Enrichment**: Tracks source, page, and chunk IDs

### Optimized Prompting
- **Context-Aware Prompts**: Structured for accuracy
- **Source Attribution**: References document sources
- **Confidence Scoring**: Only answers when confident

### Quality Assurance
- **Chunk Overlap**: Ensures context continuity
- **Intelligent Splitting**: Preserves sentence boundaries
- **UUID Tracking**: Unique identification for debugging

##  Document Types Supported

| Format | Extraction Method | Metadata |
|--------|------------------|----------|
| PDF | PyMuPDF | Page numbers, total pages |
| Word (.docx) | python-docx | Paragraph numbers |
| Text (.txt) | Text Loader | File information |


### Project Structure

```
rag-assistant/
├── app.py                 # Main application
├── requirements.txt       # Dependencies
├── .env.example          # Environment template
├── README.md             # Documentation
└── Dockerfile            # Container config
```

### Key Classes

- **DocumentProcessor**: Handles document extraction and chunking
- **RAGAssistant**: Manages RAG pipeline and querying
- **Metadata**: UUID-based tracking system

## Acknowledgments

- Google Gemini for powerful language understanding
- LangChain for RAG framework
- Sentence Transformers for quality embeddings
- FAISS for efficient vector search
- Streamlit for beautiful UI

---

**Built for accuracy, speed, and reliability in document Q&A!**
