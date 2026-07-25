## Alvin Nataputra

Data Scientist / ML Engineer at XLSmart — customer value & experience management: churn modeling, LTV forecasting, data pipelines at telco scale.

Interested in reliable ML systems and agentic AI: how models behave under distribution shift, how agents stay grounded when operating autonomously over long horizons, and what it takes to deploy these systems responsibly.

[Email](mailto:alvincnataputra@gmail.com) · [LinkedIn](https://linkedin.com/in/alvincnataputra)

---

### Projects

**[Project Aurum](https://github.com/apricitea/project-aurum)** — quantitative trading system for the Indonesian Stock Exchange (IDX)

- Ensemble signal model: LightGBM + XGBoost with walk-forward cross-validation and embargo to prevent lookahead bias
- SHAP-based feature explainability; signals ranked by confidence
- Backtested on 2025 IDX data: Sharpe 2.70 · 195% return · 44% win rate · -17% max drawdown · 509 trades
- FastAPI backend, React + TypeScript frontend, real-time Telegram alerts, PostgreSQL + Redis
- Stack: Python, LightGBM, XGBoost, scikit-learn, statsmodels, LangGraph, FastAPI, React

**[Autonomous Agent Orchestrator](https://github.com/apricitea/orchestrator-system)** — self-hosted autonomous coding agent running on a schedule

- Priority queue with RAG-based context retrieval (Qdrant hybrid dense + sparse) — each task is enriched with relevant knowledge before execution
- LLM-as-judge scoring of outputs; failure memory stores past errors and retrieves them to avoid repeating mistakes
- Reversibility classification before executing destructive operations; immutable policy governance
- Automatic branch + PR workflow for team repos; direct commit for solo repos
- Stack: Python, Claude API, Qdrant, Redis, PostgreSQL, systemd

**[LapScout](https://lapscout.mahirdev.my.id/)** — Indonesian laptop recommendation platform

- 800+ models scraped from Tokopedia and other Indonesian retailers via Puppeteer-Stealth + ScrapingBee fallback
- Three-layer medallion pipeline (Bronze → Silver → Gold): raw scrape → normalized specs → 80-column fact table with market percentiles and SOTA scores
- AI chat advisor (Maki) using GLM-4.5 with function calling — natural language queries translate to live database lookups
- Quiz-based recommendation engine: archetype matching → budget filter → must-have feature conditions → cascading fallback
- Stack: Next.js 15, TypeScript, Tailwind, Supabase (PostgreSQL), Node.js

**[project-helios](https://github.com/apricitea/project-helios)** — telco CVM analytics & ML lab, built on public and synthetic data only

- Idempotent DuckDB warehouse pipeline with a data-quality gate that aborts on critical failures before touching downstream tables
- Two independently-calibrated risk models (churn, late payment) instead of one shared multiclass model — avoids the miscalibration that comes from conflating distinct risk types; churn AUC 0.823, late-payment AUC 0.628 on real data
- Forward-looking label construction with a leakage check enforced by test, not just eyeballed
- LLM-generated report narrative with explicit graceful degradation (missing key, API error, refusal, bad JSON all fall back safely)
- Documentation-first repo structure (architecture doc, table registry, runbook, agent dispatch doc) designed for AI-assisted development
- Stack: Python, DuckDB, scikit-learn, Claude API, GitHub Actions

---

### Focus areas

ML systems engineering · LLM agents and orchestration · Applied forecasting and signal generation · AI for financial markets

---

### Stack

Python · JavaScript · PostgreSQL · MySQL · DuckDB  
scikit-learn · LightGBM · XGBoost · SHAP · BERT · statsmodels  
LangChain · LangGraph · FastAPI · Docker · Redis

---

### Open science & community

Contributing compute and data to the broader research and open-internet community from a personal homelab server:

**Volunteer computing (BOINC)** — 223,000+ credits across:
- [Einstein@Home](https://einsteinathome.org/) — gravitational wave and pulsar signal analysis (LIGO/Arecibo data)
- [MilkyWay@Home](https://milkyway.cs.rpi.edu/) — Milky Way galaxy structure modeling
- [World Community Grid](https://www.worldcommunitygrid.org/) — cancer, COVID, and clean energy research

**Privacy infrastructure** — running a Tor relay and [Tor Snowflake](https://snowflake.torproject.org/) proxy to support censorship-circumvention for users in restricted regions.

**Indonesian NLP** — building and maintaining a Bahasa Indonesia token dataset pipeline, contributing to the underrepresented Indonesian language in open NLP resources.

---

