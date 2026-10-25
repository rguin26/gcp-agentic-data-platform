# Enterprise Agentic Data & GenAI Platform on GCP

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![GCP](https://img.shields.io/badge/Google%20Cloud-Platform-4285F4?logo=googlecloud&logoColor=white)](https://cloud.google.com/)
[![Gemini](https://img.shields.io/badge/Vertex%20AI-Gemini%202.5-8E75B2?logo=google&logoColor=white)](https://cloud.google.com/vertex-ai)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

An end-to-end, security-first Cloud Data & AI platform built on **Google Cloud Platform (GCP)**. This project demonstrates the convergence of **Data Engineering**, **Generative AI**, **Agentic AI workflows**, and the **Model Context Protocol (MCP)**—built entirely with zero hardcoded credentials using Python.

---

## 🏗️ Architecture Overview

The system establishes an autonomous AI agent loop capable of querying enterprise operational data in BigQuery via standard Model Context Protocol tool bindings.

+-----------------------------------------------------------------------------------+
|                                GCP ENVIRONMENT                                   |
|                                                                                   |
|  +------------------+         +-------------------+         +------------------+  |
|  |   BigQuery Data  | <=> |   MCP Tool Layer  | <=> |  Vertex AI Agent |  |
|  |   Pipeline Logs  |         | (JSON-RPC Schema) |         |   (Gemini 2.5)   |  |
|  +------------------+         +-------------------+         +------------------+  |
|           ^                             ^                            ^            |
|           |                             |                            |            |
+-----------|-----------------------------|----------------------------|------------+
|                             |                            |
+-----------------------------+----------------------------+
|
+---------------------------------------+
| Application Default Credentials (ADC) |
|    (Zero-Hardcoding / IAM Security)   |
+---------------------------------------+

### Key Workflow Steps
1. **Data Ingestion**: Operational logs are structured and loaded into Google BigQuery using `google-cloud-bigquery`.
2. **AI Data Engineering**: Data schemas and metadata are formatted into semantic analytical views for safe LLM evaluation.
3. **Agentic Reasoning Loop**: Gemini 2.5 on Vertex AI acts as an autonomous infrastructure agent.
4. **Model Context Protocol (MCP)**: Custom Python functions act as MCP tools, letting Gemini query BigQuery context dynamically at runtime.
5. **Security & DevOps**: Project IDs and credentials are strictly resolved at runtime via Google ADC (`google.auth`).

---

## 🚀 Getting Started

### Prerequisites

* **Google Cloud Project** with an active billing account.
* **gcloud CLI** installed and authenticated ([Installation Guide](https://cloud.google.com/sdk/docs/install)).
* **Python 3.10+** installed locally or running in Google Cloud Vertex AI Workbench.

### 1. Enable Required GCP APIs

Run the following command in your terminal to enable the necessary Google Cloud APIs:

```bash
gcloud services enable \
    bigquery.googleapis.com \
    storage.googleapis.com \
    aiplatform.googleapis.com \
    secretmanager.googleapis.com
```

### 2. Authenticate GCP Credentials
Log in with your Google Account and set your default application credentials:

```bash
gcloud auth login
gcloud auth application-default login
gcloud config set project YOUR_PROJECT_ID
```

## 🔒 Cloud Security & DevOps Best Practices
Zero Hardcoding Policy: Project IDs, service account keys, and region variables are dynamically identified at runtime.

Least Privilege Access: Requires only BigQuery Data Editor and Vertex AI User roles for execution.

Secret Management: Built to integrate seamlessly with Google Cloud Secret Manager for sensitive environment secrets.

## 🛠️ Tech Stack
Cloud Platform: Google Cloud Platform (GCP)

Data Services: BigQuery, Cloud Storage

AI & LLMs: Vertex AI, Gemini 2.5

Agentic Standard: Model Context Protocol (MCP)

Language & Tools: Python 3.10+, Jupyter Notebooks, google-cloud-sdk
