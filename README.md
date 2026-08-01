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

**[project-helios](https://github.com/apricitea/project-helios)** — telco CVM analytics & ML lab, built on the IBM Telco Customer Churn dataset and synthetic usage data at ~1M-row scale

- Idempotent DuckDB warehouse pipeline with a data-quality gate that aborts on critical failures before touching downstream tables
- Two independently-calibrated risk models (churn, late payment) — avoids miscalibration from conflating distinct risk types; churn AUC 0.823, late-payment AUC 0.628
- Forward-looking label construction with a leakage check enforced by test
- LLM-generated report narrative with explicit graceful degradation (missing key, API error, bad JSON all fall back safely)
- Stack: Python, DuckDB, scikit-learn, Claude API, GitHub Actions

**[MLBB Draft](https://github.com/apricitea/mlbb-draft)** — Mobile Legends: Bang Bang draft assistant

- Hero recommendations scored across counter-matchups (40%), team synergy (35%), and meta strength (25%)
- Role gap detection — filters candidates by unfilled team roles before scoring
- Stack: Next.js 15, TypeScript, Tailwind

**[speech-event](https://github.com/apricitea/speech-event)** — event study on BBRI stock reaction to CEO-speech news

- Market-model regression (BBRI return ~ IHSG return) flags abnormal-return days, joined against scraped news by publish date
- Local LLM (Ollama, llama3) scores article sentiment, topic, and summary — no API dependency
- Streamlit dashboard for interactive price, article, event-study, and sentiment views
- Stack: Python, statsmodels, yfinance, Streamlit, PostgreSQL, Ollama

**[churn-project](https://github.com/apricitea/churn-project)** — telco churn prediction with a causal-inference layer

- XGBoost churn classifier with SHAP explainability, plus IPTW propensity-score estimation of the causal effect of product adoption on churn, revenue, and CLTV
- Distinguishes correlation from causation — flags which adoption pushes are worth doing vs. which need product fixes first
- Stack: Python, XGBoost, SHAP, scikit-learn, Streamlit

**[brimo-sentiment](https://github.com/apricitea/brimo-sentiment)** — sentiment analysis on public BRImo Play Store reviews

- Local LLM (Ollama, llama3) extracts topic, sentiment, and explanation per review — no per-request API cost at corpus scale
- Playwright-based Twitter scraper as a secondary text source
- Stack: Python, google-play-scraper, Playwright, Ollama

**[turning-point-analysis](https://github.com/apricitea/turning-point-analysis)** — bull/bear market phase dating for IDX stocks

- Censored local-extrema algorithm (Pagan-Sossounov style) — no arbitrary fixed lookback window, phases must clear minimum duration and amplitude thresholds
- Correctly isolates the 2020 COVID crash as a distinct bear phase on BBRI, unsupervised
- Stack: Python, pandas, scipy, matplotlib

**[text-suicide-ideation-detection](https://github.com/apricitea/text-suicide-ideation-detection)** — Indonesian-language text classification, undergraduate thesis + transformer follow-up

- Original thesis: FastText embeddings + LSTM, F1 0.79 on the positive class
- Added a fine-tuned IndoBERT comparison on the identical train/val split: F1 0.90 — contextual embeddings resolve sarcasm and negation that static vectors miss
- Deployed on HuggingFace; full write-up on Medium
- Stack: Python, TensorFlow/Keras, PyTorch, Transformers, FastText, IndoBERT

---

### Research

**[Ensemble ML for Signal Generation in Indonesian Equity Markets](https://github.com/apricitea/aurum-paper)** — Preprint, 2026

- Walk-forward study on the IDX: LightGBM + XGBoost ensemble with embargo-safe CV and SHAP explainability
- MetaLabeler for signal confidence filtering; backtested on 2020–2024 LQ45 data
- Sharpe 2.70 · 195% return · 44% win rate · -17% max drawdown · 509 trades (2025 OOS)

---

### Focus areas

ML systems engineering · LLM agents and orchestration · Applied forecasting and signal generation · AI for financial markets

---

### Stack

**Data & cloud platforms** BigQuery · Snowflake · Databricks · AWS Bedrock · Tencent WeData  
**Languages** Python · JavaScript  
**Databases** PostgreSQL · MySQL · DuckDB  
**ML/DS** scikit-learn · LightGBM · XGBoost · CatBoost · SHAP · BERT · statsmodels · PySpark  
**Tools** LangChain · LangGraph · FastAPI · Docker · Redis · GitLab CI

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

