# 🧠 Research Agent | IBM Skills Build AICTE-2026

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![IBM watsonx](https://img.shields.io/badge/IBM-watsonx.ai-052FAD)
![Granite Models](https://img.shields.io/badge/Model-Granite--3.0--8B--Instruct-blue)
![LangFlow](https://img.shields.io/badge/Framework-LangFlow-FF4B4B)
![ChromaDB](https://img.shields.io/badge/VectorDB-Chroma-F9AB00)

An autonomous, multi-agent Retrieval-Augmented Generation (RAG) system designed to accelerate academic and scientific research. Built for the **IBM Skills Build for University Engagements (AICTE-2026)**, this project solves **Problem Statement No. 1: Research Agent**.

---

## 📖 Overview

Academic research often requires exhaustive literature reviews, data synthesis, and citation management—processes that are fragmented and time-consuming. This **Research Agent** leverages Agentic AI to function as an intelligent, autonomous academic assistant. 

Instead of a simple chatbot, this system utilizes a collaborative multi-agent architecture to autonomously search for literature, summarize dense papers, suggest hypotheses, and organize references with strict adherence to academic integrity.

## ✨ Key Features & Novelty

*   **Multi-Agent Intelligence:** Specialized agents (Search, Summarization, Drafting, Citation) collaborate to process complex academic queries.
*   **RAG-Based Accuracy:** Integrates real-time data retrieval from trusted repositories (e.g., ArXiv) with IBM Granite's generation capabilities to eliminate hallucinations.
*   **Agentic Reasoning Loop:** Employs a ReAct (Reason + Act) workflow, allowing the AI to dynamically decide when to fetch external data versus when to synthesize existing knowledge.
*   **Automated Citation Tracking:** Maps generated claims back to retrieved source documents, ensuring publish-ready referencing.
*   **Enterprise-Grade Infrastructure:** Powered by IBM watsonx.ai, ensuring data privacy, scalable processing, and governance over sensitive research.

---

## 🛠️ Technology Stack

This project strictly adheres to the mandatory technical requirements of the hackathon, utilizing the LangFlow + IBM watsonx.ai ecosystem.

| Component | Technology Used | Purpose |
| :--- | :--- | :--- |
| **Orchestration** | LangFlow | Visual framework managing the multi-agent routing and RAG pipelines. |
| **AI Platform** | IBM watsonx.ai | Centralized enterprise platform for API requests and embeddings. |
| **LLM Engine** | Granite-3.0-8B-Instruct | Core reasoning engine for instruction-following and text synthesis. |
| **Knowledge Base** | ChromaDB | Local vector database storing mathematical embeddings of documents. |
| **External APIs** | ArXiv / Semantic Scholar | Autonomous retrieval of scientific abstracts and metadata. |

---

## 📂 Repository Structure

```text
├── app.json                                 # LangFlow exported multi-agent workflow
├── main.py                                  # Core Python execution script (Agentic ReAct loop)
├── requirements.txt                         # Python dependencies
├── Problem_Statement_Research_Agent.pdf     # Official problem statement & solution design
├── Project_Presentation_Research_Agent.pptx # Slide deck for evaluators
└── README.md                                # Project documentation


```

```
   [ User Query / Document Upload ]
                  │
                  ▼
     ┌─────────────────────────┐
     │ LangFlow Orchestration  │◄────────────────────────┐
     └────────────┬────────────┘                         │
                  │                                      │
                  ▼                                      │
     ┌─────────────────────────┐                         │
     │   Agentic ReAct Loop    │                         │
     │ (Granite-3.0-8B-Instruct)                         │
     └────────────┬────────────┘                         │
                  │                                      │
     ┌────────────┴────────────┐                         │
     ▼                         ▼                         │ (Telemetry &

```

┌───────────┐             ┌───────────┐                   │  Refinement)
│ Tools Node│             │ RAG Node  │                   │
└─────┬─────┘             └─────┬─────┘                   │
│                         │                         │
├─► Literature Search     ├─► Vector Embeddings     │
│   (ArXiv API)           │   (watsonx.ai Engine)   │
│                         │                         │
└─► Citation Formatter    └─► Vector Store          │
(Structured Mapping)      (ChromaDB Database)   │
│                         │            │
└─────────────────────────┴────────────┘
│
▼
┌───────────────────────┐
│ Structured Output Engine│
│   (Validated Draft)   │
└───────────────────────┘

```

### Specialized Agents Breakdown

* **Literature Search Agent:** Intercepts research requirements, refines semantic search parameters, executes programmatic API calls to external open repositories, and normalizes unstructured XML/JSON payloads into clean Markdown metadata blocks.
* **Document Summarization Agent:** Takes long-form, dense text inputs and utilizes structural chunking algorithms to extract methodology data, experimental parameters, datasets used, and definitive conclusions without data loss.
* **Hypothesis & Drafting Agent:** Synthesizes historical context and raw observations to outline formal research report structures, propose logical logical continuations, and assemble technical sections.
* **Citation Management Agent:** Operates a closed dictionary matching sequence that correlates every structural section generated back to verified DOIs, author lists, and source URLs.

---

## 🛠️ Technical Stack Specification

| Architecture Layer | Technology | Selection Rationale |
| :--- | :--- | :--- |
| **Workflow Design & Low-Code Routing** | LangFlow v1.0+ | Minimizes boilerplate pipeline code, visualizes real-time token states, and structures clear directional edges between system nodes. |
| **Enterprise AI Hosting Platform** | IBM watsonx.ai | Delivers highly secure, low-latency API access to foundational model endpoints with built-in data compliance filters. |
| **Foundational Inference Engine** | IBM Granite-3.0-8B-Instruct | Optimized for multi-turn instruction compliance, complex prompt reasoning (ReAct), and resource-efficient local contextualization. |
| **Semantic Context Memory** | ChromaDB (Local Persist Store) | Provides lightweight vector indexing and distance calculations for custom uploaded documents without external network exposure. |
| **External Synthesis Interface** | Open Academic APIs (ArXiv / Crossref) | Assures real-time discovery of peer-reviewed data directly from global academic servers. |

---

## 🔄 Agentic ReAct Workflow Mechanics

The system operates on an automated **Thought → Action → Observation → Thought** cycle, granting the agent the necessary cognitive capacity to self-correct and verify its output quality prior to UI rendering.


```

[Thought]     "The user is asking about state-of-the-art energy optimization in IoT.
My internal weights lack empirical metrics from 2025/2026."

[Action]      Invoke 'Literature Search Agent' with parameter:
{"query": "IoT energy consumption optimization machine learning 2025"}

[Observation] Returned 2 papers detailing real-time clustering algorithms and cloud edge routing.

[Thought]     "I now have precise data points. I will proceed to pass this text block to the
Summarization Agent to extract mathematical variables before drafting the report."

```


---

## 🚀 Installation & Deployment Guide

To deploy the local execution module and test its algorithmic integration with your configured cloud assets, carry out the following configuration steps:

### 1. System Preparation (Ubuntu Linux Terminal)

Ensure your host environment has Python 3.8 or higher initialized:

```bash
sudo apt update
sudo apt install python3-venv python3-pip git -y

```

### 2. Environment Cloning & Workdir Isolation

```bash
git clone [https://github.com/YourUsername/IBM-SkillsBuild-Research-Agent.git](https://github.com/YourUsername/IBM-SkillsBuild-Research-Agent.git)
cd IBM-SkillsBuild-Research-Agent

```

### 3. Dependency Compilation via Isolated Environment

```bash
python3 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt

```

### 4. Credential Exporting

Create an environmental configuration file in your directory root to securely interface with IBM services:

```bash
cat <<EOF > .env
WATSONX_APIKEY="your_secure_ibm_cloud_iam_platform_key"
PROJECT_ID="your_active_watsonx_project_workspace_guid"
EOF

```

> ⚠️ **Security Policy:** The `.env` file is explicitly skipped from public repository commits to maintain system integrity. Never commit raw API keys to public source branches.

### 5. Executing Diagnostic Run

```bash
python3 main.py

```

---

## 🧩 LangFlow Integration & Execution

The visual orchestration layer is encapsulated entirely inside the versioned `app.json` file.

1. Launch your local or server-side LangFlow workspace dashboard environment (`pip install langflow && langflow run`).
2. Select **Upload/Import File** from the main dashboard workspace area.
3. Upload the structured `app.json` file provided in this repository root.
4. Locate the `WatsonxLLM` infrastructure node block in the workflow grid.
5. Provide your valid `Project ID` and credentials into the template variables text cells.
6. Connect your input stream text to execute an integrated evaluation test loop across the active Granite architecture layers.

---

## 🛡️ Enterprise Governance & Data Privacy

By routing processing operations through **IBM watsonx.ai** and utilizing open-source foundational systems like **IBM Granite**, this framework natively maintains enterprise compliance standards:

* **Data Isolation:** User uploaded manuscripts and historical evaluation prompts processed inside the local vector instance (ChromaDB) remain entirely inside the local execution memory space.
* **No Model Ingestion:** Input queries, text blocks, and research summaries processed via the watsonx.ai API gateway are never ingested into public base models for standard training purposes, ensuring intellectual property safeguards for complex research designs.

---

**Author:** Akash Aryan

*Third-Year Computer Science & Engineering | Developed for IBM Skills Build AICTE-2026*

```

```
