## Alvin Nataputra

Data Scientist / ML Engineer at XLSmart — customer value & experience management: churn modeling, LTV forecasting, data pipelines at telco scale.

Interested in reliable ML systems and agentic AI: how models behave under distribution shift, how agents stay grounded when operating autonomously over long horizons, and what it takes to deploy these systems responsibly.

[Portfolio](https://apricitea.github.io) · [Email](mailto:alvincnataputra@gmail.com) · [LinkedIn](https://linkedin.com/in/alvincnataputra) · [HuggingFace](https://huggingface.co/apricitea) · [Medium](https://medium.com/@apricitea)

---

### Research

**[Ensemble ML for Signal Generation in Indonesian Equity Markets](https://github.com/apricitea/aurum-paper)** — working draft, not submitted; reports a negative result

- Walk-forward study on the IDX: LightGBM + XGBoost ensemble with purged and embargoed cross-validation, ATR-scaled triple-barrier labeling, average-uniqueness sample weights, and a meta-labeler that scales position size by signal confidence
- **Result: the model does not beat buy-and-hold.** Equal-weight over 16 IDX large caps, 2025 out-of-sample, net of IDX costs: signal model +0.12% (Sharpe 0.05) with the meta-labeler filter, +7.62% (0.88) without it, +4.73% (1.38) on technical features only — against +14.17% (0.74) for buy-and-hold and +20.71% (1.12) for the IHSG
- Walk-forward accuracy inside the training period is 0.341–0.361 against a majority-class baseline of 0.532 on three-class labels; the model is worse than always predicting the most frequent label
- The earlier 195.6% / 2.70 Sharpe claim is withdrawn. Four evaluation defects account for it: the final model was trained on rows inside the test window, early stopping used the fold's own test set, the scaler was fitted on the whole series, and the 5-day calendar embargo was shorter than the 10-bar label horizon with no purge
- Code, run manifests (data SHA-256s), per-fold metrics, trade ledgers and figures: [`project-aurum/research/`](https://github.com/apricitea/project-aurum/tree/main/research)

![2025 out-of-sample: signal model vs buy-and-hold vs IHSG](https://raw.githubusercontent.com/apricitea/project-aurum/main/research/out/20260928T102521Z-f552679/fig_equity_curve.png)

![Walk-forward accuracy against the majority-class baseline, per ticker](https://raw.githubusercontent.com/apricitea/project-aurum/main/research/out/20260928T102521Z-f552679/fig_fold_accuracy.png)

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

- Ensemble signal model: LightGBM + XGBoost with purged and embargoed walk-forward cross-validation; SHAP-based explainability on every signal
- FastAPI backend, React + TypeScript frontend, real-time Telegram alerts, PostgreSQL + Redis
- A committed, reproducible re-evaluation lives in [`research/`](https://github.com/apricitea/project-aurum/tree/main/research): it fixes four leakage defects in the original pipeline and finds that the model does not beat buy-and-hold. Details in the Research section above
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