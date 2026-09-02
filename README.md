# AegisMind AI

**Applied Agentic AI System for Autonomous Document Intelligence, Live Web Research, Security Telemetry Analysis, and Multi-Agent Orchestration.**

---

## 1. Overview

**AegisMind AI** is an enterprise-grade agentic AI platform designed for automated security intelligence, policy compliance auditing, and multi-domain research synthesis. Built as a standalone solution for **Applied Agentic AI Coding Assignment 2**, the system orchestrates specialized autonomous agents through dynamic planning and a shared blackboard memory architecture:

1. **Document Intelligence / RAG Agent (R1)**: High-speed document ingestion (PDF/TXT), deterministic dense hash-projection vector indexing, Okapi BM25 hybrid retrieval, strict citation attribution, and LLM question answering with resilient fallback.
2. **Web Research Agent (R2)**: Multi-source search engine (DuckDuckGo + Wikipedia), secondary outbound HTTP crawler fetching full webpage text, and dynamic domain synthesis across diverse topics without static leakage.
3. **Security Analysis Agent (R3)**: Dynamic log triage engine, IOC extraction (IPs, accounts, ports, commands), MITRE ATT&CK technique mapping, internal policy compliance cross-correlation, and automated remediation playbook generation.
4. **Multi-Agent Orchestrator (R4)**: Centralized coordination engine featuring dynamic LLM/heuristic planning, stateful blackboard communication, causal inter-agent dependency propagation (Document → Security), and comprehensive 11-section Master Report generation.

---

## 2. System Architecture

```
                                  +---------------------------------------+
                                  |     Master Orchestrator Engine        |
                                  |     - Dynamic Execution Planner       |
                                  |     - Shared Blackboard State Memory  |
                                  +-------------------+-------------------+
                                                      |
              +-----------------------+---------------+---------------+-----------------------+
              |                       |                               |                       |
              v                       v                               v                       v
+---------------------------+ +---------------------------+ +---------------------------+ +---------------------------+
|    Research Agent (R2)    | |    Document Agent (R1)    | |    Security Agent (R3)    | |     Report Agent (R4)     |
| - Live Search (DDG/Wiki)  | | - PDF/TXT Text Ingestion  | | - Telemetry Stream Parser | | - Cross-Agent Synthesis   |
| - Outbound HTTP Crawler   | | - Hybrid Vector Store     | | - Rule-Based IOC Extractor| | - Executive Assessment    |
| - Dynamic Topic Synthesis | | - Grounded Citation Engine| | - Document Policy Checker | | - 11-Section Master Report|
+---------------------------+ +---------------------------+ +---------------------------+ +---------------------------+
              |                       |                               |                       |
              +-----------------------+---------------+---------------+-----------------------+
                                                      |
                                                      v
                                  +---------------------------------------+
                                  |       Configurable LLM Service        |
                                  |  (OmniRoute / OpenAI / Gemini / Groq) |
                                  +---------------------------------------+
```

---

## 3. Requirement Breakdown & Verification Status

| Requirement | Status | Runtime Proof & Verification Summary |
| :--- | :---: | :--- |
| **R1 — Document / RAG Agent** | **PARTIAL** | **Verified**: Binary PDF ingestion (`enterprise_cloud_security_controls.pdf`), 128-d hash projection indexing, hybrid Okapi BM25 retrieval (`score = 0.3196`), out-of-domain rejection (`0.25` threshold), grounded citation formatting, and OpenAI-compatible outbound HTTP client (`http://localhost:20128/v1/chat/completions`).<br>**Documented Limitation**: External round-trip LLM completion is currently blocked because upstream free reverse-proxy routes on the local OmniRoute installation returned upstream rate limits / timeouts during live verification. Resilient heuristic fallback executed seamlessly. |
| **R2 — Web Research Agent** | **FULL** | **Verified**: Live web search (DuckDuckGo + Wikipedia), secondary outbound HTTP crawler (`fetch_source_page`) extracting 2,000 characters of clean text per page across 4 distinct domains (*Tomato Gardening*, *Python Async*, *Renewable Energy*, *Zero Trust Architecture*), with **0% static cybersecurity leakage** on non-security queries. |
| **R3 — Security Analysis Agent** | **FULL** | **Verified**: Dynamic parsing of arbitrary security logs (e.g. automated SQL injection attacks from novel IPs), benign system telemetry handling, dynamic IOC extraction, MITRE ATT&CK mapping (T1190, T1046, T1078, T1059), and 7 built-in realistic threat presets. |
| **R4 — Multi-Agent Orchestration** | **FULL** | **Verified**: Sequential pipeline execution (`RESEARCH -> DOCUMENT -> SECURITY -> REPORT`), shared blackboard state passing, **proven differential Document → Security causal dependency** (injecting document findings triggers policy violations and enforcement mitigations), and dynamic generation of an 11-section Master Report. |

---

## 4. Key Features

### R1: Document Intelligence & RAG
- **Binary PDF & Text Ingestion**: Extracts text with page tracking and normalized paragraph chunking.
- **Hybrid Vector Indexing**: Combines a deterministic 128-dimensional subword/n-gram hashing projection vector with Okapi BM25 keyword scoring (60% Dense Cosine Similarity + 40% Normalized BM25).
- **Candidate Relevance Threshold**: Enforces an empirically tuned `0.25` threshold to accept in-domain cloud security queries while rejecting out-of-domain topics with an explicit "not found" response.
- **Citation Attribution**: Formats document name, page number, chunk index, similarity score, and excerpt snippet.

### R2: Web Research & Crawling
- **Dual-Engine Search Transport**: Primary DuckDuckGo HTML parser with automatic live Wikipedia Full-Text Search API fallback.
- **Outbound Source-Page Crawler**: Automatically executes a secondary HTTP GET to destination URLs, cleans HTML entities/scripts/styles, and provides up to 2,000 characters of raw webpage context to the synthesis prompt.
- **Topic-Grounded Synthesis**: Generates domain-specific key findings, strategic takeaways, and conclusions tailored to the search query.

### R3: Security Analysis & Policy Auditing
- **Multi-Vector Threat Detection**: Identifies SSH brute-force, web application attacks (SQLi, XSS, RCE), perimeter port scans, cloud IAM tampering, and ransomware staging.
- **IOC Extraction**: Dynamically extracts IPv4 addresses, hostnames, user accounts, target ports, and process commands from raw telemetry.
- **Policy Compliance Auditing**: Cross-correlates telemetry against internal document findings to flag compliance violations (e.g. password auth when key-only SSH is mandated).

### R4: Orchestration & Master Report
- **Stateful Blackboard**: Inter-agent communication channel preserving `external_research`, `document_findings`, and `security_analysis`.
- **Dynamic 11-Section Master Report**:
  1. Executive Summary
  2. Investigation Objective & Scope
  3. Internal Architecture & Policy Baseline Findings
  4. External Threat Intelligence & Research Findings
  5. Security Telemetry & Log Analysis
  6. Correlated Attack Narrative & MITRE ATT&CK Mapping
  7. Key Technical Indicators of Compromise (IOCs)
  8. Risk Impact Assessment
  9. Actionable Mitigations & Playbook
  10. Strategic Recommendations & Defensive Posture
  11. Strategic Conclusion & Next Steps

---

## 5. Technology Stack

- **Backend**: Python 3.10+, FastAPI, Uvicorn, Pydantic v2, HTTPX, PyPDF, python-dotenv
- **Frontend**: React 18, TypeScript, Vite, TailwindCSS, Lucide Icons
- **Vector Engine**: Pure Python 128-dimensional subword hash projection + Okapi BM25 (Zero heavy external C-dependencies)
- **Testing**: Pytest, Pytest-Asyncio, HTTPX TestClient

---

## 6. Installation & Setup

### Prerequisites
- Python 3.10 or higher
- Node.js 18 or higher & npm

### Backend Setup
```powershell
# Clone the repository
git clone https://github.com/Vaishnav53/AegisMind-AI.git
cd AegisMind-AI

# Install Python dependencies
pip install -r backend/requirements.txt
```

### Frontend Setup
```powershell
cd frontend
npm install
cd ..
```

---

## 7. Configuration

Copy the example configuration file to `.env`:

```powershell
copy .env.example .env
```

Configure your environment variables in `.env`:

```env
# LLM Provider Configuration
# Supported: "openai", "gemini", "groq", "ollama"
LLM_PROVIDER=openai

# OpenAI-Compatible OmniRoute or Direct Endpoint
OPENAI_BASE_URL=http://localhost:20128/v1
LLM_MODEL=auto/fast

# API Key (Paste your valid API key here - never commit .env)
OPENAI_API_KEY=your_api_key_here
GEMINI_API_KEY=
GROQ_API_KEY=

# Search Provider Configuration
SEARCH_PROVIDER=duckduckgo
```

---

## 8. Running the Application

### Start the Backend API Server
```powershell
python -m uvicorn backend.main:app --host 0.0.0.0 --port 8000 --reload
```
API Documentation will be available at `http://localhost:8000/docs`.

### Start the Frontend Web UI
```powershell
cd frontend
npm run dev
```
Web Application will be accessible at `http://localhost:5173`.

---

## 9. Automated Testing & Verification

Execute the complete backend test suite:

```powershell
python -m pytest backend/tests -v
```

### Test Suite Summary (`24/24 Passed`):
- `backend/tests/test_api_endpoints.py` (6 tests): REST endpoint contracts, health, stats, presets, upload, query, research, security, workflow.
- `backend/tests/test_document_agent.py` (3 tests): Vector generation, real binary PDF ingestion, grounded RAG Q&A, out-of-domain rejection.
- `backend/tests/test_research_agent.py` (2 tests): Research agent workflow, multi-source retrieval, history listing.
- `backend/tests/test_security_agent.py` (4 tests): Dynamic log rule engine, custom arbitrary logs, preset scenarios.
- `backend/tests/test_orchestrator.py` (3 tests): Dynamic agent planning, blackboard context passing, workflow state retrieval.
- `backend/tests/test_remediation.py` (6 tests): Strict verification of PDF RAG, OOD rejection, outbound crawler HTTP GET, multi-domain research without static leakage, Document → Security causal dependency, and 11-section Master Report.

---

## 10. Project Directory Structure

```
AegisMind-AI/
├── backend/
│   ├── agents/
│   │   ├── __init__.py
│   │   ├── document_agent.py       # Document Ingestion & RAG Agent
│   │   ├── research_agent.py       # Live Web Research & Crawler Agent
│   │   ├── security_agent.py       # Security Analyst & Policy Rule Engine
│   │   ├── orchestrator.py         # Multi-Agent Workflow Coordinator
│   │   └── report_agent.py         # 11-Section Master Report Generator
│   ├── api/
│   │   ├── __init__.py
│   │   └── routes.py               # FastAPI REST API Endpoints
│   ├── models/
│   │   ├── __init__.py
│   │   └── schemas.py              # Pydantic Request/Response Models
│   ├── rag/
│   │   ├── __init__.py
│   │   ├── embeddings.py           # 128-d Hash-Projection Vector Engine
│   │   └── vector_store.py         # Okapi BM25 + Dense Hybrid Vector Store
│   ├── services/
│   │   ├── __init__.py
│   │   ├── llm_service.py          # Configurable Multi-Provider LLM Adapter
│   │   ├── search_service.py       # DuckDuckGo + Wikipedia Search & Crawler
│   │   └── storage_service.py      # SQLite & Document File Store
│   ├── tests/
│   │   ├── test_api_endpoints.py
│   │   ├── test_document_agent.py
│   │   ├── test_orchestrator.py
│   │   ├── test_remediation.py     # Strict Assignment Remediation Tests
│   │   ├── test_research_agent.py
│   │   └── test_security_agent.py
│   ├── main.py                     # FastAPI Application Entrypoint
│   └── requirements.txt            # Python Dependencies
├── frontend/
│   ├── src/
│   │   ├── components/             # Reusable UI Components
│   │   ├── pages/                  # Document, Research, Security, Workflow Views
│   │   ├── services/               # Axios API Client
│   │   ├── App.tsx                 # Main Application Component
│   │   └── main.tsx
│   ├── package.json
│   ├── vite.config.ts
│   └── tailwind.config.js
├── sample_data/
│   ├── documents/
│   │   └── enterprise_cloud_security_controls.pdf
│   └── logs/
│       ├── ssh_brute_force.log
│       ├── web_sqli.log
│       └── ransomware_activity.log
├── .env.example                    # Sanitized Configuration Template
├── .gitignore                      # Git Ignore Rules
└── README.md                       # Project Documentation
```

---

## 11. Known Limitations

- **OmniRoute External Provider Outage**: The application integration with OpenAI-compatible gateways (including OmniRoute at `http://localhost:20128/v1`) is fully implemented with SSE stream support. During final live verification, all free public reverse-proxy routes configured in the local OmniRoute instance returned upstream rate limits or connection timeouts. The pipeline automatically activates its grounded internal fallback synthesis to ensure reliable execution. Setting a direct API key (`OPENAI_API_KEY`, `GEMINI_API_KEY`, or `GROQ_API_KEY`) in `.env` immediately enables live external model generation without code modifications.

---

## 12. License

This project is submitted as part of **Applied Agentic AI Coding Assignment 2**. All rights reserved.
