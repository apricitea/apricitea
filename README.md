## Alvin Nataputra

Data Scientist / ML Engineer at XLSmart — customer value & experience management: churn modeling, LTV forecasting, data pipelines at telco scale.

Interested in reliable ML systems and agentic AI: how models behave under distribution shift, how agents stay grounded when operating autonomously over long horizons, and what it takes to deploy these systems responsibly.

[Portfolio](https://apricitea.github.io) · [Email](mailto:alvincnataputra@gmail.com) · [LinkedIn](https://linkedin.com/in/alvincnataputra) · [HuggingFace](https://huggingface.co/apricitea) · [Medium](https://medium.com/@apricitea)

---

### Research

**[Ensemble ML for Signal Generation in Indonesian Equity Markets](https://github.com/apricitea/aurum-paper)** — methods write-up, working draft, not submitted

- Walk-forward study on the IDX: LightGBM + XGBoost ensemble with embargo-safe cross-validation, ATR-scaled triple-barrier labeling, and a MetaLabeler that scales position size by signal confidence
- **Status: evaluation incomplete, and the draft says so.** The committed backtest artifact covers 16 tickers with mean return −2.01% and mean Sharpe −0.04, against out-of-sample fold accuracy of 0.27–0.33 while training accuracy was 1.0. That is not a reportable result. An earlier headline figure (195.6% return / 2.70 Sharpe / 509 trades) had no linked run artifact in the checkout and is withdrawn.
- Next: purge- and embargo-corrected folds, a buy-and-hold benchmark under identical costs, archived run manifests, and reporting whatever the corrected numbers turn out to be

**[Turning-Point Analysis](https://github.com/apricitea/turning-point-analysis)** — bull/bear market phase dating for IDX stocks

- Censored local-extrema algorithm in the style of Pagan & Sossounov (2003) — no arbitrary fixed lookback window; phases must clear minimum duration and amplitude thresholds
- Isolates the 2020 COVID crash as a distinct bear phase on BBRI, unsupervised; properties enforced by a test suite

**[Indonesian suicide-ideation text classification](https://github.com/apricitea/text-suicide-ideation-detection)** — undergraduate thesis + transformer follow-up

- FastText + LSTM (thesis) against a fine-tuned IndoBERT on the identical train/val split: positive-class F1 0.79 → 0.90
- Class-imbalance treatment (class weighting, ADASYN) *reduced* F1 in the thesis arm — reported rather than dropped
- [Deployed on HuggingFace](https://huggingface.co/spaces/apricitea/suicide-detection) · [write-up on Medium](https://medium.com/@apricitea)

---

### Projects

**[Project Aurum](https://github.com/apricitea/project-aurum)** — quantitative trading system for the Indonesian Stock Exchange (IDX), 4-person team

- Ensemble signal model: LightGBM + XGBoost with walk-forward cross-validation and embargo to prevent lookahead bias; SHAP-based explainability on every signal
- FastAPI backend, React + TypeScript frontend, real-time Telegram alerts, PostgreSQL + Redis
- See the Research section above for current evaluation status — the pipeline is the contribution; the performance claim is not yet supported
- Stack: Python, LightGBM, XGBoost, scikit-learn, statsmodels, LangGraph, FastAPI, React

**[Autonomous Agent Orchestrator](https://github.com/apricitea/orchestrator-system)** — self-hosted autonomous coding agent running on a schedule

- Priority queue with RAG-based context retrieval (Qdrant hybrid dense + sparse) — each task is enriched with relevant knowledge before execution
- LLM-as-judge scoring of outputs; failure memory stores past errors and retrieves them to avoid repeating mistakes
- Reversibility classification before executing destructive operations; immutable policy governance
- Automatic branch + PR workflow for team repos; direct commit for solo repos
- Stack: Python, Claude API, Qdrant, Redis, PostgreSQL, systemd

**[project-helios](https://github.com/apricitea/project-helios)** — telco CVM analytics & ML lab, built on the IBM Telco Customer Churn dataset and synthetic usage data at ~1M-row scale

- Idempotent DuckDB warehouse pipeline with a data-quality gate that aborts on critical failures before touching downstream tables
- Two independently-calibrated risk models (churn, late payment) — avoids miscalibration from conflating distinct risk types; churn AUC 0.823, late-payment AUC 0.628
- Forward-looking label construction with a leakage check enforced by test
- LLM-generated report narrative with explicit graceful degradation (missing key, API error, bad JSON all fall back safely)
- Stack: Python, DuckDB, scikit-learn, Claude API, GitHub Actions

**[MLBB Draft](https://github.com/apricitea/mlbb-draft)** — Mobile Legends: Bang Bang draft assistant

- Hero recommendations scored across counter-matchups (40%), team synergy (35%), and meta strength (25%)
- Role gap detection — filters candidates by unfilled team roles before scoring
- Stack: Next.js, TypeScript, Tailwind

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

**LapScout** — Indonesian laptop recommendation platform (private repo, team project)

- 800+ models scraped from Indonesian retailers via Puppeteer-Stealth + ScrapingBee fallback
- Three-layer medallion pipeline (Bronze → Silver → Gold): raw scrape → normalized specs → fact table with market percentiles and SOTA scores
- AI chat advisor with function calling — natural language queries translate to live database lookups
- Stack: Next.js, TypeScript, Tailwind, PostgreSQL, Node.js

---

### Focus areas

ML systems engineering · LLM agents and orchestration · Applied forecasting and signal generation · Validity and leakage control in time-series ML

---

### Stack

**Data & cloud platforms** BigQuery · Snowflake · Databricks · AWS Bedrock · Tencent WeData  
**Languages** Python · JavaScript  
**Databases** PostgreSQL · MySQL · DuckDB  
**ML/DS** scikit-learn · LightGBM · XGBoost · CatBoost · SHAP · BERT · statsmodels · PySpark  
**Tools** LangChain · LangGraph · FastAPI · Docker · Redis · GitLab CI

---

### Open science & homelab

Contributing idle compute and services from a personal homelab server:

**Volunteer computing (BOINC)** — [Einstein@Home](https://einsteinathome.org/) (gravitational-wave and pulsar signal analysis), [MilkyWay@Home](https://milkyway.cs.rpi.edu/) (galaxy structure modelling), and [World Community Grid](https://www.worldcommunitygrid.org/) (cancer, COVID, and clean-energy research).

**Privacy infrastructure** — a Tor relay and [Tor Snowflake](https://snowflake.torproject.org/) proxy supporting censorship circumvention.

---