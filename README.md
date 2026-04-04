# 🚀 MLflow Deployment of a RAG Pipeline

Deploy a production-ready **Retrieval-Augmented Generation (RAG)** pipeline 
using MLflow as the MLOps framework, with LlamaIndex and LangChain as 
orchestrators and Ollama/HuggingFace LLMs as backends.

---

## 🧠 Project Goal

To build, evaluate, and deploy a fully tracked RAG pipeline using MLflow — 
enabling experiment tracking, model versioning, and one-command deployment 
of LLM-powered retrieval systems.

---

## 🏗️ Technical Architecture
User Query
↓
Frontend (React)
↓
app.py (Flask API)
↓
MLflow Model Server  ←→  MLflow Tracking UI
↓
RAG Pipeline
┌─────────────────────────────────────┐
│  LlamaIndex / LangChain             │
│  ┌──────────┐    ┌───────────────┐  │
│  │ Retriever│───▶│  LLM (Ollama/ │  │
│  │ (Vector  │    │  HuggingFace/ │  │
│  │  Index)  │    │  Groq)        │  │
│  └──────────┘    └───────────────┘  │
└─────────────────────────────────────┘
↓
Generated Answer

---

## 🔄 Pipeline Workflow

1. **Data Prep** — Put your documents in `data/` folder
2. **Index Generation** — Notebook generates vector index + QA evaluation dataset
3. **RAG Tuning** — `tune_rag.py` runs experiments tracked by MLflow
4. **Deployment** — `workflow.py` logs the model, MLflow serves it on port 5001
5. **Frontend** — React UI connects to the served model via `app.py`

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| MLOps | MLflow | Experiment tracking, model registry, deployment |
| Orchestration | LlamaIndex + LangChain | RAG pipeline construction |
| LLM Backend | Ollama / HuggingFace / Groq | Language model inference |
| Evaluation | BERT Score + custom metrics | RAG quality assessment |
| Backend API | Python / Flask | Model serving bridge |
| Frontend | React (Node.js) | Chat interface |
| Data | JSON eval datasets | QA evaluation |

---

## 📁 Project Structure
mlflow-rag-pipeline/
│
├── data/                        # Your input documents
├── deployement/
│   └── workflow.py              # MLflow experiment + model logging
├── frontend/                    # React chat interface
├── images/                      # Architecture diagrams
├── app.py                       # Flask API server
├── tune_rag.py                  # RAG hyperparameter tuning
├── generating_qa_dataset.ipynb  # QA dataset generation notebook
├── pg_eval_dataset_index.json   # Evaluation dataset
├── Modelfile                    # Ollama model configuration
└── requirements.txt             # Python dependencies

---

## 🚀 Getting Started

### Prerequisites
- Python 3.9+
- Node.js (for frontend)
- Ollama installed locally (or HuggingFace API key)
- MLflow installed

### Step 1 — Install dependencies
```bash
git clone https://github.com/Shubhamharanale7/mlflow-rag-pipeline.git
cd mlflow-rag-pipeline
pip install -r requirements.txt
```

### Step 2 — Configure API keys
Rename `example.env` to `.env` and add your API keys:
HUGGINGFACE_API_KEY=your_key_here
GROQ_API_KEY=your_key_here

### Step 3 — Prepare data and generate index
- Put your documents in `data/` folder
- Run `generating_qa_dataset.ipynb` notebook
- Download the output JSON file

### Step 4 — Run MLflow experiment
```bash
cd deployement
python workflow.py
```

### Step 5 — Serve the model
Get the Run ID from MLflow UI, then:
```bash
mlflow models serve -m runs:/<run_id>/rag_deployment -p 5001
```

### Step 6 — Start the API server
```bash
python app.py
```

### Step 7 — Launch frontend
```bash
cd frontend
npm start
```

Now open your browser — the chat interface is live! 🎉

---

## 📊 MLflow Tracking

MLflow tracks every experiment run including:
- Retrieval parameters (chunk size, overlap, top-k)
- Evaluation metrics (BERT Score, faithfulness, relevancy)
- Model artifacts and versions
- Deployment history

---

## ⚠️ Notes
- If you don't have a GPU, run the notebook on **Google Colab**
- Download the output JSON from Colab before proceeding
- Check `requirements.txt` for any missing dependencies on errors

---

## 📜 License
MIT License

---

## 🙌 Feedback Welcome

Thank you for exploring my MLflow RAG Pipeline project!
I'm always open to suggestions, improvements, or collaboration ideas.

📩 Connect with me on [LinkedIn](https://www.linkedin.com/in/shubhamharanale7)  
📧 Email: **shubhaminfosoft7@gmail.com**

Your feedback helps me grow. Let's connect and build something great!
