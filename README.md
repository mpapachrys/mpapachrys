<h1 align="center">Hi, I'm Manos 👋</h1>
<h3 align="center">AI Engineer</h3>

<p align="center">
I like figuring out how to connect LLMs to real data and real systems —
RAG, MCP, agents, knowledge graphs — through projects I build end to end.
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/epapachrysanthou/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
  <a href="https://www.credential.net/profile/emmanouilpapachrysanthou136156/wallet"><img src="https://img.shields.io/badge/Credentials-4B4B4B?style=for-the-badge&logo=readdotcv&logoColor=white" /></a>
</p>

---

### 🔍 What I focus on

Most of my projects sit at the point where an LLM has to touch real systems — a database, a document store, a calendar, another team's service — and stop being just a chatbot. In practice that's meant:

- **Grounding models in real data** so they answer from retrieved facts, not memory (RAG, hybrid retrieval with knowledge graphs when relationships matter more than similarity)
- **Decoupling agent reasoning from tool execution** using MCP, so tools can change without touching agent logic
- **Building the parts around the model that make it production-usable** — auth, data modeling, role boundaries, fallback behavior when the LLM call fails or an API key is missing
- **Making retrieval and agent behavior testable**, not just "it looked right in one run"

---

### 🚀 Projects

**[matchify-ai-hiring-platform](https://github.com/mpapachrys/matchify-ai-hiring-platform)** — `Next.js 15 · FastAPI · MongoDB · MinIO`
A hiring platform for a single company: post roles, review applicants, move them through a pipeline.
- **Problem:** resume parsing needed an LLM, but the platform had to run and be testable without an API key, and a bad/expensive model call couldn't be allowed to block the core product.
- **Approach:** the parser sits behind a `Protocol` interface — a regex-only stub is the default, a real model via OpenRouter is one env var away. Nothing outside that module knows which one is running.
- **Also handles:** two-layer role gating (UX-level cookie check + server-side enforcement that's the only one that actually matters for security), a documented read-only export boundary with a separate Neo4j-based matching service, and a MongoDB schema where a few explicit design calls (snapshotting job data at apply-time, a hard uniqueness constraint instead of an app-level check) prevent real race conditions and data-integrity bugs.
- **Tested:** concurrent duplicate-application race, role boundaries, full auth flow — against a real database, not mocks.

**[agentic-rag-mcp-system](https://github.com/mpapachrys/agentic-rag-mcp-system)** — `Python · LangChain · ChromaDB · MCP`
Automates classifying and acting on incoming customer-order emails.
- **Problem:** an agent that both reasons and executes tools directly becomes impossible to extend — every new capability means touching the agent's core logic.
- **Approach:** MCP separates the two. The LLM classifies emails and decides intent; separate MCP servers own execution (checking real-time inventory in PostgreSQL, generating PDF invoices). A RAG layer feeds product context into the agent so it doesn't invent details about products it hasn't seen.
- **Result:** adding a new tool (e.g. Slack, Jira) means registering it in a config file, not editing the agent.

**[cuad-rag-knowledge_graph-assistant](https://github.com/mpapachrys/cuad-rag-knowledge_graph-assistant)** — `Python · Neo4j · RAG`
A question-answering assistant over contract data.
- **Problem:** vector similarity search is good at "find similar text," bad at "find everything connected to this clause across contracts" — that's a graph traversal problem, not a similarity one.
- **Approach:** routes each question to whichever retrieval method actually answers it — RAG for semantic lookup, a Neo4j knowledge graph for relational/structural queries — instead of forcing every question through one pipeline.

**[nlp_text_classification](https://github.com/mpapachrys/nlp_text_classification)** — `Python · scikit-learn`
Binary classifier for human- vs AI-generated text using BGE-M3 embeddings — the non-LLM ML fundamentals underneath the agent work above.

*(Full list: [Repositories →](https://github.com/mpapachrys?tab=repositories))*

---

### ⚙️ Stack

| Area | Tools |
|---|---|
| **LLM / Agents** | LangChain, MCP, OpenAI, OpenRouter, RAG pipelines |
| **Retrieval / Data** | ChromaDB, Neo4j (knowledge graphs), PostgreSQL, MongoDB |
| **Backend** | Python, FastAPI |
| **Infra** | Docker, CI/CD (GitLab), Azure |
| **ML** | PyTorch, scikit-learn, embeddings/NLP |

---

### 🎓 Certifications
*Big Blue Data Academy*

`AI Engineering Bootcamp` · `Chatbots & AI Agents (MCP/RAG/KAG)` · `Deep Learning & NLP` · `Machine Learning` · `Docker` · `Data Science Bootcamp` · `SQL` · `Python` · `Git`

→ [Full credentials with issue dates](https://www.credential.net/profile/emmanouilpapachrysanthou136156/wallet)

---

### 📫 Contact

[LinkedIn](https://www.linkedin.com/in/epapachrysanthou/) · [Credentials](https://www.credential.net/profile/emmanouilpapachrysanthou136156/wallet) · Athens, Greece
