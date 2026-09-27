<p align="center">
  <img src="docs/img/aura_logo.svg" width="110" height="110" alt="Aura Logo" />
</p>

<h1 align="center">⚡ Aura — High-Performance RAG & LLM Orchestration Framework</h1>

<p align="center">
  <strong>Advanced LLM orchestration and high-performance Retrieval-Augmented Generation (RAG) pipeline architecture.</strong>
</p>

<p align="center">
  <a href="https://www.python.org"><img src="https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" /></a>
  <a href="https://pytorch.org"><img src="https://img.shields.io/badge/PyTorch-2.0+-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch" /></a>
  <a href="https://fastapi.tiangolo.com"><img src="https://img.shields.io/badge/FastAPI-Production%20Ready-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI" /></a>
  <a href="https://opentelemetry.io"><img src="https://img.shields.io/badge/OpenTelemetry-Native%20Tracing-4A154B?style=for-the-badge&logo=opentelemetry&logoColor=white" alt="OpenTelemetry" /></a>
  <a href="https://github.com/SHAZAAN25/Aura/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg?style=for-the-badge" alt="License" /></a>
  <a href="https://github.com/SHAZAAN25/Aura"><img src="https://img.shields.io/badge/Status-Active%20Maintained-success?style=for-the-badge" alt="Status" /></a>
</p>

<p align="center">
  <em>"Connect models, vector databases, and document transformers into resilient, production-grade intelligence pipelines."</em>
</p>

---

## 👨‍💼 Leadership & Credits

> **Project Architected and Maintained by [Mohammed Shazaan Aarish](https://github.com/SHAZAAN25)**  
> *Engineered to deliver modular, transparent, and scalable LLM orchestration, hybrid retrieval-augmented generation (RAG), and deterministic graph pipeline execution for production AI systems.*

---

## ⚡ Core Engineering Philosophy & Architectural Tenets

Modern generative AI applications require more than chained prompt strings. Production-grade systems demand deterministic data flow, type validation, fault tolerance, and deep observability across every inference step.

**Aura is built on five core architectural tenets:**

1. **Explicit Directed Graph (DAG) Pipelines**: Aura models workflows as deterministic directed acyclic graphs. Components declare strict input and output type contracts (`@component.output_types`), preventing runtime type mismatches and silent prompt leakage.
2. **Provider & Vendor Agnostic Orchestration**: Zero proprietary lock-in. Seamlessly swap between OpenAI, Anthropic Claude, Google Gemini, Cohere, Hugging Face, or local inference engines (Ollama, vLLM, TensorRT-LLM) by updating a single pipeline node.
3. **Multi-Stage Hybrid RAG & Re-Ranking**: Overcomes traditional semantic retrieval pitfalls by combining dense vector embeddings with sparse BM25 lexical search, dynamic reciprocate rank fusion (RRF), and cross-encoder similarity rankers.
4. **Autonomous Agentic Loops with Schema Enforcement**: Multi-step reasoning loops featuring deterministic JSON Schema validation, tool function calling, dynamic short/long-term memory buffers, and graceful error recovery.
5. **Production Observability & Declarative Serialization**: Native OpenTelemetry distributed tracing across all pipeline steps, structured logging, and instant pipeline export/import using declarative YAML/JSON specifications.

---

## 🏛️ System Architecture

<p align="center">
  <img src="docs/img/aura_architecture.svg" width="100%" alt="Aura System Architecture" />
</p>

---

## 🌟 Key Framework Capabilities

### 🧠 Multi-Provider LLM Generators
- Native interfaces for **OpenAI** (`OpenAIGenerator`, `OpenAIChatGenerator`), **Anthropic**, **Cohere**, and **Google Gemini**.
- First-class support for open-source self-hosted models via **Hugging Face**, **Ollama**, and **vLLM**.
- Deterministic response formatting via JSON Schema validation and structured outputs.

### 🔍 Hybrid Vector Search & Storage Engines
- Plug-and-play integrations with industry-standard vector databases:
  - **Qdrant**, **Pinecone**, **Chroma**, **OpenSearch**, **Milvus**, **Weaviate**, **pgvector (PostgreSQL)**, and **In-Memory Store**.
- Hybrid search fusing dense embedding vectors with sparse BM25 lexical matching to achieve peak retrieval accuracy.

### 📄 Enterprise Document Ingestion & Parsers
- Native converters for diverse formats: **PDF** (PyPDF, PDFMiner, Azure Form Recognizer OCR), **DOCX**, **PPTX**, **HTML** (Trafilatura), **XLSX**, **Markdown**, and **JSON**.
- Granular text chunking via **Character**, **Word**, **Sentence**, **NLTK**, and **Recursive Token** splitters.

### 🤖 Autonomous Agents & Function Calling
- Dynamic agentic execution with schema-enforced tool execution.
- Auto-generate tool definitions directly from standard Python functions or **OpenAPI** service specifications.
- Memory management and context window optimization for continuous multi-turn dialogue.

### 📊 Evaluation & Guardrails Engine
- Quantitative evaluation metrics: **Context Recall**, **Context Precision**, **Faithfulness**, and **Semantic Answer Similarity**.
- Automated validation gates preventing hallucinations before answers reach downstream users.

### 🚀 REST API Deployment via Hayhooks
- Wrap any Aura pipeline into a production-ready **FastAPI** REST microservice in seconds.
- Fully compatible with OpenAI-compatible API schemas and front-end chat interfaces.

---

## ⚙️ Component & Pipeline Engine Specifications

| Component Category | Supported Technologies / Providers | Primary Engineering Function |
| :--- | :--- | :--- |
| **Generators** | OpenAI, Anthropic, Gemini, Cohere, HuggingFace, Ollama | Multi-model text and chat completion with streaming |
| **Embedders** | SentenceTransformers, OpenAI, HuggingFace Hub, Cohere | Dense vector embedding generation for text and documents |
| **Document Stores** | In-Memory, Qdrant, Chroma, Pinecone, OpenSearch, pgvector | Vector indexing, hybrid search, document persistence |
| **Retrievers** | Dense Embedding Retrievers, BM25 Keyword Retrievers | Candidate document retrieval with metadata filtering |
| **Rankers** | SentenceTransformers, Cohere Re-ranker, Diversity Ranker | Cross-encoder contextual re-scoring and redundancy filtering |
| **Converters & Splitters** | PyPDF, Trafilatura, python-docx, NLTK, Tiktoken | Raw file ingestion, text extraction, semantic chunking |
| **Agents & Tools** | ReAct Agent, Tool, OpenAPIServiceConnector | Autonomous multi-step problem solving & tool calling |
| **Observability** | OpenTelemetry, Datadog, Structlog | End-to-end distributed tracing, latency profiling, metrics |

---

## 📂 Repository Structure

```
Aura/
├── haystack/                    # Core Aura Engine Framework
│   ├── components/              # Modular Pipeline Components
│   │   ├── builders/            # PromptBuilder, ChatPromptBuilder, AnswerBuilder
│   │   ├── converters/          # PyPDF, DOCX, HTML, Markdown, Tika, OCR
│   │   ├── embedders/           # OpenAI, SentenceTransformers text & doc embedders
│   │   ├── generators/          # LLM interfaces (OpenAI, HuggingFace, Chat)
│   │   ├── rankers/             # TransformersSimilarityRanker, DiversityRanker
│   │   ├── retrievers/          # In-Memory, Dense, BM25, and Vector retrievers
│   │   ├── routers/             # Conditional branching & language routers
│   │   ├── splitters/           # NLTK, Recursive, and Character text splitters
│   │   └── tools/               # Agent Tool wrappers & OpenAPI connectors
│   ├── core/                    # Core Directed Graph Pipeline Engine
│   │   ├── pipeline/            # Pipeline DAG graph execution & validation
│   │   └── serialization/       # Declarative YAML & JSON export/import
│   ├── dataclasses/             # Document, ChatMessage, Tool, ByteStream
│   └── tracing/                 # OpenTelemetry and Datadog telemetry hooks
├── docs/                        # Technical Documentation & Architectural Guides
│   └── img/                     # High-resolution logos, banners, diagrams
├── examples/                    # End-to-end reference implementations & notebooks
├── test/                        # Rigorous unit, integration, and e2e test suites
├── pyproject.toml               # Build system, dependencies, and package metadata
├── CITATION.cff                 # Academic citation and metadata
├── CONTRIBUTING.md              # Engineering guidelines and pull request standards
├── LICENSE                      # Apache License 2.0
└── README.md                    # Project documentation
```

---

## 🚀 Quickstart & Setup

### Prerequisites
- Python 3.9, 3.10, 3.11, or 3.12
- `pip` or [`uv`](https://github.com/astral-sh/uv) package manager
- (Optional) Docker for containerized vector store deployment

### 1. Installation

Install the package directly:
```bash
pip install haystack-ai
```

Or install in editable mode for local development:
```bash
git clone https://github.com/SHAZAAN25/Aura.git
cd Aura
pip install -e ".[test]"
```

### 2. Building Your First Hybrid RAG Pipeline

Here is a complete, runnable example demonstrating how to index documents and query them using an end-to-end RAG pipeline:

```python
from haystack import Pipeline, Document
from haystack.document_stores.in_memory import InMemoryDocumentStore
from haystack.components.embedders import OpenAITextEmbedder, OpenAIDocumentEmbedder
from haystack.components.retrievers.in_memory import InMemoryEmbeddingRetriever
from haystack.components.builders import PromptBuilder
from haystack.components.generators import OpenAIGenerator

# 1. Initialize Document Store & Ingest Knowledge
document_store = InMemoryDocumentStore()
docs = [
    Document(content="Aura is a high-performance LLM orchestration and RAG framework architected by Mohammed Shazaan Aarish."),
    Document(content="Aura features explicit directed graph pipelines, hybrid search, and native OpenTelemetry distributed tracing."),
    Document(content="Aura allows zero-friction model swapping across OpenAI, Anthropic, Gemini, Cohere, and local vLLM instances.")
]

# 2. Embed and Write Documents
doc_embedder = OpenAIDocumentEmbedder(model="text-embedding-3-small")
docs_with_embeddings = doc_embedder.run(documents=docs)["documents"]
document_store.write_documents(docs_with_embeddings)

# 3. Construct the RAG Pipeline Graph
rag_pipeline = Pipeline()
rag_pipeline.add_component("text_embedder", OpenAITextEmbedder(model="text-embedding-3-small"))
rag_pipeline.add_component("retriever", InMemoryEmbeddingRetriever(document_store=document_store, top_k=2))

template = """
Answer the question based strictly on the provided context:
Context:
{% for doc in documents %}
  {{ doc.content }}
{% endfor %}

Question: {{ query }}
Answer:
"""
rag_pipeline.add_component("prompt_builder", PromptBuilder(template=template))
rag_pipeline.add_component("llm", OpenAIGenerator(model="gpt-4o-mini"))

# 4. Connect the Pipeline Sockets
rag_pipeline.connect("text_embedder.embedding", "retriever.query_embedding")
rag_pipeline.connect("retriever.documents", "prompt_builder.documents")
rag_pipeline.connect("prompt_builder.prompt", "llm.prompt")

# 5. Execute Pipeline Query
query = "Who architected Aura and what are its key capabilities?"
results = rag_pipeline.run({
    "text_embedder": {"text": query},
    "prompt_builder": {"query": query}
})

print("⚡ Answer:", results["llm"]["replies"][0])
```

### 3. Declarative Pipeline Serialization (YAML)

Aura pipelines can be serialized into declarative YAML configurations for clean version-controlled deployments:

```python
# Export pipeline to YAML
yaml_pipeline = rag_pipeline.dumps()

# Save to disk or load on a remote cluster
with open("rag_pipeline.yaml", "w") as f:
    f.write(yaml_pipeline)

# Load pipeline anywhere with zero code recreation
loaded_pipeline = Pipeline.loads(yaml_pipeline)
```

---

## 🧪 Testing & Verification

Aura maintains comprehensive test coverage across unit components, integration pipelines, and end-to-end workflows:

```bash
# Run Unit Tests
pytest test/core/pipeline/

# Run Component Tests
pytest test/components/

# Verify Static Types
mypy haystack

# Run Code Formatting and Linting Check
ruff check .
ruff format --check .
```

---

## 🤝 Contributing

We welcome contributions from engineers, researchers, and builders worldwide!

1. **Fork the Repository** on GitHub: `https://github.com/SHAZAAN25/Aura`
2. **Create a Feature Branch**: `git checkout -b feature/amazing-component`
3. **Commit Your Changes**: Follow clear conventional commit conventions
4. **Push to Your Branch**: `git push origin feature/amazing-component`
5. **Open a Pull Request**: Detail your changes, test results, and motivation

For comprehensive contribution guidelines, code formatting standards, and testing procedures, please refer to [CONTRIBUTING.md](CONTRIBUTING.md).

---

## 📜 License & Acknowledgments

- Distributed under the **Apache License 2.0**. See [`LICENSE`](LICENSE) for complete terms.
- Built with respect for foundational open-source components and the broader AI ecosystem.

---

<p align="center">
  <b>⚡ Aura — High-Performance RAG & LLM Orchestration Framework</b><br>
  Architected & Maintained with precision by <b><a href="https://github.com/SHAZAAN25">Mohammed Shazaan Aarish</a></b>
</p>
