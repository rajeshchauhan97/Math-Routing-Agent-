# 🧮 Math Routing Agent – Human-in-the-Loop AI Tutor

## Overview
The **Math Routing Agent** is an AI-powered tutor designed to replicate a math professor.  
It provides **step-by-step solutions** to mathematical problems using a **Knowledge Base (KB)** first approach, and falls back to **web/MCP search** when needed.  
With **human-in-the-loop feedback**, the system continuously learns and improves over time.

---

## ✨ Features
- 📘 **Knowledge Base First** → Solves questions from stored data.
- 🌐 **Web/MCP Search Fallback** → Retrieves answers when KB lacks a solution.
- 🔄 **Feedback Loop** → Human-in-the-loop rating & validation improves accuracy.
- 🛡 **Guardrails** → Input/output validation for safety & clarity.
- 📊 **Benchmarking Ready** → JEE Math dataset integration (optional).
- 🎨 **React Frontend** → Interactive UI for solving and feedback.

---

## 🏗️ Architecture
```

math-routing-agent/
├── app/                        # Backend
│   ├── main.py                 # FastAPI entrypoint
│   ├── agents/                 # Agent logic
│   │   ├── routing\_agent.py
│   │   └── feedback\_agent.py
│   ├── knowledge\_base/         # KB data & retriever
│   │   ├── kb\_retriever.py
│   │   └── data/math\_questions.json
│   ├── search/                 # MCP/Web search
│   │   └── mcp\_client.py
│   ├── guardrails/             # Input/output validation
│   │   └── io\_guardrails.py
│   └── models/                 # Embedding & vector logic
│       └── embeddings.py
├── frontend/                   # React UI
│   ├── src/
│   │   ├── App.js
│   │   └── components/MathSolver.js
├── benchmarks/                 # Optional evaluation
│   ├── jee\_bench\_complete.py
│   └── results/
├── tests/                      # Unit tests
├── Dockerfile                  # Containerization
├── requirements.txt            # Python deps
└── README.md

````

---

## ⚙️ Setup Instructions

### Backend (FastAPI)
```bash
# Create virtual env
python -m venv venv
source venv/bin/activate   # Mac/Linux
venv\Scripts\activate      # Windows

# Install deps
pip install -r requirements.txt

# Run backend
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
````

### Frontend (React)

```bash
cd frontend
npm install
npm start
```

---

## 🔌 API Endpoints

### Solve Math Question

**POST** `/api/solve`

```json
{
  "question": "Solve for x: 2x + 5 = 15"
}
```

Response:

```json
{
  "solution": "Step 1: Subtract 5 → 2x = 10\nStep 2: Divide by 2 → x = 5",
  "source": "knowledge_base",
  "confidence": 1.0
}
```

### Submit Feedback

**POST** `/api/feedback`

```json
{
  "question": "Solve for x: 2x + 5 = 15",
  "answer": "x = 5",
  "rating": 5,
  "comments": "Clear explanation"
}
```

---

## 🛠️ Tech Stack

* **Backend:** FastAPI, Python 3.10+
* **Frontend:** React.js
* **Agent Logic:** LangChain, CrewAI, Autogen
* **Vector DB:** Qdrant / Weaviate
* **Search APIs:** MCP, Tavily, Exa
* **Feedback:** DSPy
* **Deployment:** Docker

---

## 📊 Benchmarking (Optional)

* Run: `python benchmarks/jee_bench_complete.py`
* Results stored in: `benchmarks/results/jee_bench_results.json`

---

## 🚀 Demo Workflow

1. Enter a math problem in frontend.
2. Backend routes → KB first, else Web/MCP.
3. Step-by-step solution generated.
4. User submits feedback → system learns.

---

## 📌 Author

**Raju Sabhavath**
🔗 [LinkedIn](https://linkedin.com/) | [GitHub](https://github.com/)

----


⚡ Question: Do you want me to make a **shorter `README.md` summary version** for GitHub repo landing page (1–2 sections only), or keep this **full detailed professional one**?
```
