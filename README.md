# Agentic-Roadmap-Generator
<div align="center">

# 🔬 Agentic Research Assistant

**An LLM-powered multi-agent system that builds you a personalized research onboarding plan.**

[![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![LangGraph](https://img.shields.io/badge/LangGraph-0.2-green?style=flat)](https://github.com/langchain-ai/langgraph)
[![LangChain](https://img.shields.io/badge/LangChain-latest-blue?style=flat)](https://langchain.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

</div>

---

Tell it your background and the field you want to break into. It will fetch recent papers, mine trends, surface relevant courses, and hand you a structured knowledge roadmap — all in one run.

## ✨ Features

- 📚 **Knowledge plan** — maps the concepts and skills you need to acquire
- 🎓 **Course recommendations** — matches IISc courses to your learning path
- 📈 **Trend analysis** — identifies hot topics from recent arXiv & bioRxiv papers
- 📄 **Paper recommendations** — ranks the most relevant papers using semantic similarity

---

## 🗂 Project Structure

```
.
├── main.py               # Entry point
├── config.py             # Global settings and paths
├── requirements.txt
│
├── agents/               # Individual LangGraph agents
├── graph/                # LangGraph workflow (node wiring)
├── tools/                # Tool implementations (search, embeddings, etc.)
│
├── data/
│   └── iisc_courses.json # Course catalog
└── output/
    └── roadmap.txt       # Generated knowledge roadmap
```

---

## 🚀 Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/your-username/agentic-research-assistant.git
cd agentic-research-assistant
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure

Edit `config.py` to set your LLM and adjust any search parameters:

```python
LLM_MODEL = "gpt-4o-mini"   # or a local Ollama model e.g. "llama3"
LLM_TEMPERATURE = 0.2
```

If using OpenAI, set your key:

```bash
export OPENAI_API_KEY=your_key_here
```

If using Ollama locally, make sure it's running:

```bash
ollama serve
ollama pull llama3
```

### 4. Run

```bash
python main.py
```

You'll be prompted for two inputs:

```
Enter your background: MSc in Computer Science, experience in NLP
Enter target research field: Computational Biology
```

---

## 📤 Output

After the pipeline completes, results are printed to the console and the roadmap is saved to `output/roadmap.txt`.

```
===== Knowledge Plan =====
...

===== Courses =====
...

===== Research Trends =====
...

===== Papers =====
...
```

---

## ⚙️ Configuration Reference

All settings live in `config.py`:

| Key | Default | Description |
|-----|---------|-------------|
| `LLM_MODEL` | `gpt-4o-mini` | LLM used by all agents |
| `LLM_TEMPERATURE` | `0.2` | Sampling temperature |
| `ARXIV_MAX_RESULTS` | `40` | Papers fetched from arXiv |
| `BIORXIV_MAX_RESULTS` | `40` | Papers fetched from bioRxiv |
| `PAPER_START_YEAR` | `2023-01-01` | Earliest paper date to consider |
| `TOP_PAPER_RECOMMENDATIONS` | `5` | Number of papers returned |
| `EMBEDDING_MODEL` | `all-MiniLM-L6-v2` | Sentence-transformers model |
| `MAX_TREND_KEYWORDS` | `15` | Keywords extracted for trend analysis |
| `DEBUG_MODE` | `True` | Verbose agent step logging |

---

## 🛠 Tech Stack

| Layer | Library |
|-------|---------|
| Agent orchestration | [LangGraph](https://github.com/langchain-ai/langgraph) |
| LLM integration | [LangChain](https://langchain.com/), [langchain-ollama](https://pypi.org/project/langchain-ollama/) |
| Observability | [LangSmith](https://smith.langchain.com/) |
| Paper search | arXiv API, bioRxiv RSS via [feedparser](https://pypi.org/project/feedparser/) |
| Semantic similarity | [sentence-transformers](https://www.sbert.net/) |
| Data handling | pandas, numpy, scikit-learn |
| CLI output | [rich](https://github.com/Textualize/rich) |

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

---

## 📄 License

[MIT](LICENSE)
