# ConsultAdd Agentic Workflows - RFP Automation System

An intelligent AI-powered system that automates and simplifies the Request for Proposal (RFP) analysis process using Generative AI, Retrieval-Augmented Generation (RAG), and multi-agent workflows.

## 🚀 Overview

This project leverages advanced AI agents to help ConsultAdd efficiently analyze government RFPs by automating key tasks such as eligibility checking, checklist generation, risk analysis, and market research. The system uses FAISS vector databases for document retrieval and LangChain with Groq's LLM for intelligent analysis.

## ✨ Features

### 🤖 AI Agents

1. **Eligibility Agent** - Evaluates whether ConsultAdd meets RFP eligibility criteria
   - Verifies legal requirements and qualifications
   - Compares company profile against RFP requirements
   - Provides detailed eligibility assessment with percentage match

2. **Checklist Agent** - Generates comprehensive submission checklists
   - Extracts document formatting requirements
   - Lists required attachments and forms
   - Provides submission method and deadline information

3. **Risk Analysis Agent** - Identifies and assesses contract risks
   - Analyzes legal, financial, and operational risks
   - Classifies risks by severity (High/Moderate/Low)
   - Suggests balanced modifications to mitigate risks

4. **Market Search Agent** - Conducts market analysis and competitive research
   - Identifies industry trends
   - Analyzes competition
   - Suggests positioning strategies for ConsultAdd

## 🏗️ Architecture

```
ConsultAdd-Agentic-Workflows/
├── app.py                          # FastAPI backend with REST endpoints
├── UI.py                           # Streamlit frontend interface
├── EligiblityAgent.py             # Eligibility checking agent
├── checklistAgent.py              # Submission checklist generator
├── riskAgent.py                   # Risk analysis agent
├── marketSearchAgent.py           # Market research agent
├── extractEligibityCriteria.py    # Eligibility criteria extraction
├── new_RAG.py                     # RAG implementation for document embedding
├── requirements.txt               # Python dependencies
├── Data/                          # Data directory
├── Downloaded/                    # Temporary storage for uploaded PDFs
└── VectorDB/                      # FAISS vector databases
    ├── Company_Uploaded/          # Company profile embeddings
    └── RPF_Uploadded/             # RFP document embeddings
```

## 🛠️ Technology Stack

- **Framework**: FastAPI (Backend), Streamlit (Frontend)
- **LLM**: DeepSeek-R1-Distill-Llama-70B via Groq
- **Vector Store**: FAISS
- **Embeddings**: HuggingFace Sentence Transformers (all-MiniLM-L6-v2)
- **Orchestration**: LangChain
- **Search**: DuckDuckGo Search API
- **Python**: 3.x

## 📦 Installation

1. **Clone the repository**
```powershell
git clone https://github.com/Sahil1694/ConsultAdd-Agentic-Workflows.git
cd ConsultAdd-Agentic-Workflows
```

2. **Create a virtual environment** (recommended)
```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

3. **Install dependencies**
```powershell
pip install -r requirements.txt
```

4. **Set up environment variables**

Create a `.env` file in the root directory and add your API keys:
```
GROQ_API_KEY=your_groq_api_key_here
```

## 🚀 Usage

### Running the Backend (FastAPI)

```powershell
uvicorn app:app --reload
```

The API will be available at `http://localhost:8000`

### Running the Frontend (Streamlit)

```powershell
streamlit run UI.py
```

The UI will open in your browser at `http://localhost:8501`

### Using the System

1. **Upload Documents**
   - Upload RFP PDF document
   - Upload Company profile PDF
   - Click "Process and Embed PDFs" to save files
   - Click "Generate FAISS Vector DBs" to create embeddings

2. **Run Agents**
   - **Eligibility Check**: Analyzes if ConsultAdd meets RFP criteria
   - **Generate Checklist**: Creates submission requirements checklist
   - **Risk Analysis**: Identifies and assesses contract risks
   - **Market Report**: Generates market analysis and competitive insights

## 📡 API Endpoints

### Base URL: `http://localhost:8000`

- `GET /` - Welcome message
- `POST /eligibility` - Run eligibility check agent
- `POST /checklist` - Generate submission checklist
- `POST /risks` - Analyze contract risks
- `POST /generate-market-report` - Generate market research report

### Example Request

```python
import requests

response = requests.post("http://localhost:8000/eligibility")
print(response.json())
```

## 🔧 Configuration

### Vector Database Paths
- RFP Documents: `./VectorDB/RPF_Uploadded`
- Company Data: `./VectorDB/Company_Uploaded`

### LLM Settings
- Model: `deepseek-r1-distill-llama-70b`
- Temperature: 0.7 (configurable per agent)
- Retrieval: MultiQuery with k=4-8 documents

## 📊 Key Components

### RAG Pipeline
- Document chunking and embedding using HuggingFace transformers
- FAISS vector store for efficient similarity search
- Multi-query retrieval for comprehensive context gathering

### Agent Workflow
1. Document upload and preprocessing
2. Embedding generation and vector storage
3. Query-based retrieval with MultiQuery
4. LLM-powered analysis and generation
5. Structured output formatting

