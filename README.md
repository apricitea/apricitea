## Alvin Nataputra

Data Scientist / ML Engineer at XLSmart — customer value & experience management: churn modeling, LTV forecasting, data pipelines at telco scale.

Interested in reliable ML systems and agentic AI: how models behave under distribution shift, how agents stay grounded when operating autonomously over long horizons, and what it takes to deploy these systems responsibly.

[Portfolio](https://apricitea.github.io) · [CV](https://apricitea.github.io/cv.pdf) · [Email](mailto:alvincnataputra@gmail.com) · [LinkedIn](https://linkedin.com/in/alvincnataputra) · [HuggingFace](https://huggingface.co/apricitea) · [Medium](https://medium.com/@apricitea)

---

### Research

**[Ensemble ML for Signal Generation in Indonesian Equity Markets](https://github.com/apricitea/aurum-paper)** — working draft, not submitted; reports a negative result

- Walk-forward study on the IDX: LightGBM + XGBoost ensemble with purged and embargoed cross-validation, ATR-scaled triple-barrier labeling, average-uniqueness sample weights, and a meta-labeler that scales position size by signal confidence
- **Result: the model does not beat buy-and-hold.** Equal-weight over 16 IDX large caps, 2025 out-of-sample, net of IDX costs: signal model +0.12% (Sharpe 0.05) with the meta-labeler filter, +7.62% (0.88) without it, +4.73% (1.38) on technical features only — against +14.17% (0.74) for buy-and-hold and +20.71% (1.12) for the IHSG
- Walk-forward accuracy is below the majority-class baseline on **0 of 16 tickers** (sign-test p = 3e-5). Per-ticker return vs buy-and-hold is 8/16 (p = 1) — not distinguishable from chance. Median time in market is 3% of test days, so raw-return "wins" are sitting in cash on falling names, not timing skill
- The earlier 195.6% / 2.70 Sharpe claim is withdrawn. Four evaluation defects account for it: the final model was trained on rows inside the test window, early stopping used the fold's own test set, the scaler was fitted on the whole series, and the 5-day calendar embargo was shorter than the 10-bar label horizon with no purge
- Code, run manifests (data SHA-256s), per-fold metrics, trade ledgers and figures: [`project-aurum/research/`](https://github.com/apricitea/project-aurum/tree/main/research)

![2025 out-of-sample: signal model vs buy-and-hold vs IHSG](https://raw.githubusercontent.com/apricitea/project-aurum/main/research/out/20260928T102521Z-f552679/fig_equity_curve.png)

![Walk-forward accuracy against the majority-class baseline, per ticker](https://raw.githubusercontent.com/apricitea/project-aurum/main/research/out/20260928T102521Z-f552679/fig_fold_accuracy.png)

**[Turning-Point Analysis](https://github.com/apricitea/turning-point-analysis)** — bull/bear market phase dating for IDX stocks

- Censored local-extrema algorithm in the style of Pagan & Sossounov (2003) — no arbitrary fixed lookback window; phases must clear minimum duration and amplitude thresholds
- Isolates the 2020 COVID crash as a distinct bear phase on BBRI, unsupervised; properties enforced by a test suite

**[What a 0.91 F1 actually measures](https://github.com/apricitea/text-suicide-ideation-detection)** — leakage audit of the undergraduate thesis corpus

- The 10,128-post Indonesian suicide-ideation corpus is a scraped X sample. A random 80/20 split without deduplication put **739 of 2,026 validation posts (36.5%)** in both halves
- On the 1,287 genuinely unseen rows, fine-tuned IndoBERT falls from F1 **0.910 → 0.877** [0.845, 0.904]. A character n-gram logistic regression reaches 0.787; the remaining transformer advantage is **+0.090** [+0.049, +0.131], McNemar p = 6.3e-4
- The probabilities are close to honest (ECE 0.046). Catching 90% of ideation-positive posts means reviewing **21.8% of the corpus at 83.6% precision**
- The FastText + LSTM thesis arm (reported F1 0.79) cannot be recomputed: tokenizer and vectors were never saved. Recorded, not hidden
- [Paper (PDF)](https://github.com/apricitea/text-suicide-ideation-detection/blob/main/paper/main.pdf) · [evaluation code](https://github.com/apricitea/text-suicide-ideation-detection/tree/main/eval) · [serving demo](https://github.com/apricitea/text-suicide-ideation-detection/tree/main/demo) (container built and smoke-tested in CI; no public URL)

![Positive-class F1 by protocol](https://raw.githubusercontent.com/apricitea/text-suicide-ideation-detection/main/eval/out/20261025-full/fig_scores.png)

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

**[speech-event](https://github.com/apricitea/speech-event)** — do BRI CEO-speech news days move the stock?

- The original pipeline picked days by abnormal return and then looked for news on them. The merged table it read had 32 news rows and **zero** labelled abnormal, so its implied "match" was structurally empty
- Rebuilt with news as the event and abnormal return as the outcome: 26 events, market model on [-130,-11], CAR over [-1,+1]. **Patell Z −2.84 (p = 0.0045), BMP t −3.24 (p = 0.0034)**; 1 of 26 survives Benjamini–Hochberg
- Mean CAR −1.23%, and the pre-publication component (−0.39% at t−1) argues against a clean "repriced on publication" story — reported rather than smoothed over
- 3 tests, committed runs with reports and figures; original notebooks kept so the correction is legible against what they did

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

Contributing idle compute and data from a personal homelab server:

**Volunteer computing (BOINC)** — 247,311 credits across [Einstein@Home](https://einsteinathome.org/) (gravitational-wave and pulsar signal analysis), [MilkyWay@Home](https://milkyway.cs.rpi.edu/) (galaxy structure modelling), and [World Community Grid](https://www.worldcommunitygrid.org/) (cancer, COVID, and clean-energy research).

**Indonesian NLP** — a weekly pipeline collecting Bahasa Indonesia text (Indonesian Wikipedia extracts plus Indonesian news sites). The public release is deliberately restricted to records that carry full attribution, so every published record is traceable to the exact source revision: currently 552 Wikipedia extracts (~39k tokens) released under [CC BY-SA 4.0 on HuggingFace](https://huggingface.co/datasets/apricitea/bahasa-indonesia-corpus), growing each week. Scraped news text and records collected before provenance was recorded are excluded from the release rather than published without a licence — 2,221 news-derived and ~30,000 unattributed records stay local.

**Privacy infrastructure** — a [Tor Snowflake](https://snowflake.torproject.org/) proxy supporting censorship circumvention.

---