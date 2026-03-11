# 🤖 Autonomous Blog Generation System

> A multi-agent AI system that automatically generates structured, research-backed technical blog posts using LangGraph, LangChain, and Google Gemini.

---

## 📌 Overview

Traditional single-prompt blog generation often produces shallow, unstructured content. This system solves that by orchestrating **specialized AI agents**, each responsible for a distinct stage of the pipeline — from research and planning to parallel section writing and diagram generation.

Built with **LangGraph** and **LangChain**, it delivers publication-ready Markdown blogs with optional AI-generated diagrams through an interactive **Streamlit** frontend.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🧠 Multi-Agent Architecture | Specialized agents handle research, planning, writing, and assembly |
| 🔀 Intelligent Research Routing | Router agent decides if LLM knowledge suffices or web research is needed |
| 🌐 Automated Web Research | Collects and synthesizes sources via Tavily Search API |
| 📋 Structured Blog Planning | Orchestrator creates outlines with sections, goals, and word targets |
| ⚡ Parallel Section Generation | Worker agents write sections simultaneously for faster output |
| 🔗 Content Aggregation | Reducer pipeline merges sections into one cohesive article |
| 🖼️ AI Diagram Generation | Auto-generates and embeds technical diagrams |
| 📝 Markdown Output | Clean Markdown ready for GitHub, Medium, or Dev.to |
| 🖥️ Streamlit UI | Interactive frontend with preview, download, and history |
| 💾 Blog Persistence | Blogs saved locally and accessible through the interface |

---

## 🏗️ System Architecture

```
User Topic
    │
    ▼
Router Agent
    │
    ├── Closed-book ──────────────────────┐
    │                                     │
    └── Research Needed                   │
            │                             │
            ▼                             │
        Research Agent                    │
            │                             │
            ▼                             ▼
        Orchestrator Agent ◄──────────────┘
            │
            ▼
        Worker Agents (Parallel)
            │
            ▼
        Reducer Pipeline
            ├── Merge Sections
            ├── Decide Images
            └── Generate Diagrams
            │
            ▼
        Final Blog (Markdown)
```

---

## 🤖 Agents Overview

### 🔀 Router Agent
Determines whether the topic requires internet research.
- **Outputs:** research mode, search queries

### 🔍 Research Agent
Collects and synthesizes evidence from the web using Tavily Search.
- Runs search queries
- Extracts relevant sources
- Deduplicates evidence

### 📋 Orchestrator Agent
Creates the full blog structure.
- **Outputs:** blog title, audience, tone, section tasks, word targets

### ✍️ Worker Agents
Generate individual blog sections in parallel.
- Each worker receives one section task
- Writes structured Markdown
- Optionally includes code examples or citations

### 🔗 Reducer Pipeline
Post-processing stage that:
- Merges all generated sections
- Determines whether images are needed
- Generates diagrams
- Produces the final Markdown file

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Agent Orchestration | LangGraph |
| LLM Framework | LangChain |
| LLM Model | Google Gemini 2.5 Flash |
| Web Search | Tavily Search API |
| Frontend | Streamlit |
| Data Modeling | Pydantic |
| Language | Python |

---

## 📁 Project Structure

```
project-root/
│
├── backend.py          # Multi-agent LangGraph pipeline
├── frontend.py         # Streamlit UI for blog generation
├── images/             # Generated diagrams
├── *.md                # Generated blog files
├── .env                # API keys
└── README.md
```

---

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/agentic-blog-writer.git
cd agentic-blog-writer
```

### 2. Create a Virtual Environment

```bash
python -m venv venv

# macOS/Linux
source venv/bin/activate

# Windows
venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

Key dependencies:
```
langchain
langgraph
streamlit
pydantic
python-dotenv
langchain-google-genai
langchain-community
langchain-huggingface
tavily-python
pandas
```

### 4. Set Environment Variables

Create a `.env` file in the project root:

```env
GOOGLE_API_KEY=your_gemini_api_key
TAVILY_API_KEY=your_tavily_api_key
```

---

## ▶️ Running the Application

```bash
streamlit run frontend.py
```

Then open your browser at:

```
http://localhost:8501
```

---

## 📖 Usage

1. Enter a blog topic in the sidebar
2. Click **Generate Blog**
3. The system will:
   - Analyze the topic
   - Perform research if needed
   - Generate a blog outline
   - Write sections in parallel
   - Assemble the final blog
   - Generate diagrams (if required)
4. Preview the blog in the **Markdown Preview** tab
5. Download as:
   - 📄 Markdown file
   - 📦 ZIP bundle (Markdown + images)

---

## 💡 Example Topics

```
Understanding Transformer Architecture
Vector Databases Explained for Developers
How Retrieval-Augmented Generation Works
Latest Developments in Open Source LLMs
```

---

## 🔮 Future Improvements

- [ ] Vector database for long-term research memory
- [ ] Support for multiple LLM providers
- [ ] Image model customization
- [ ] Blog publishing integrations (Medium, Dev.to, Ghost)
- [ ] Collaborative editing
- [ ] SEO optimization

---

## 🌟 Why This Project Matters

This system demonstrates how **agentic workflows** can:

- Break complex tasks into specialized roles
- Incorporate real-time research
- Generate structured, high-quality content
- Improve factual accuracy

It showcases the power of **multi-agent orchestration using LangGraph** for complex AI pipelines — a significant step beyond single-prompt generation.

---

## 📄 License

This project is open source. See [LICENSE](LICENSE) for details.
