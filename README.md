<div align="center">

# Aryan Kumar

**AI Engineer (RAG & agentic systems) · Final-year B.S. Data Science & Applications, IIT Madras**

I build LLM systems and then measure where they break.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aryan-kumar-1969b819b/)
[![Portfolio](https://img.shields.io/badge/Portfolio-111827?style=for-the-badge&logo=vercel&logoColor=white)](https://aryan-ds-portfolio.vercel.app/)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:22f2000697@ds.study.iitm.ac.in)
[![X](https://img.shields.io/badge/X-000000?style=for-the-badge&logo=x&logoColor=white)](https://x.com/Aryanku74262338)

</div>

---

## 🧭 About

I started with copy-paste and "it works, so it's fine." Then I chose to learn *why* things work, and this GitHub is the record of that shift.

Right now I'm focused on one problem space: **RAG and agentic AI for enterprise documents**. My lead project, TenderIQ, comes from watching my own family struggle through a government e-marketplace (GeM) tender.

Looking for **AI / ML engineering roles and internships** (RAG, LLM pipelines, agentic systems). Open to relocation or remote.

---

## 🔨 Lead Project (In Progress)

### 📄 [TenderIQ](https://github.com/00-Aryan/tenderiq): RAG assistant for GeM tender PDFs

> MSMEs lose winnable government bids to preventable process mistakes: a missed EMD clause, a wrong document, a deadline buried in a table. TenderIQ lets a bidder ask questions about a tender and get cited answers.

**What's implemented**
- **Ingestion:** FastAPI upload returns `202`, a background task parses the PDF with `pymupdf4llm` (chosen over PyMuPDF after testing on real, bilingual GeM tenders), and the client polls a status endpoint.
- **Retrieval:** header-aware and recursive chunking into ChromaDB, hybrid BM25 + vector search (LangChain `EnsembleRetriever`), LLM multi-query expansion, and content-hash dedup.
- **Serving:** Streamlit UI showing page-cited answers, per-stage latency and token count; pytest suite with no live LLM calls.

**A bug worth telling you about:** the query *"deadline"* failed to find the chunk containing *"Bid End Date/Time"*. Root cause was three compounding issues: BM25 vocabulary mismatch, a 1,200-char mixed-topic chunk diluting its embedding, and two retrievers making the same mistake. Fixed with block-level chunking that preserves table structure and a query-expansion layer that maps everyday words to procurement terms.

**Evaluation (RAGAS, first run, 8 cases, so treat as directional):** context precision 1.00 · context recall 1.00 · answer relevance 0.84 · **faithfulness 0.61**. Faithfulness is the weak number, and it's the one I'm working on next.

**Not built yet:** eligibility matching against a company profile, conversation memory, OCR fallback, auth, deployment.

`Python` · `FastAPI` · `LangChain` · `ChromaDB` · `pymupdf4llm` · `Gemini` · `Streamlit` · `Pydantic` · `RAGAS` · `pytest`

---

## 🚀 Other Projects

### 🛒 [Engage2Value](https://github.com/00-Aryan/Engage2Value-From-Clicks-to-Conversions): predicting purchase value from sessions
Kaggle competition on ~116K e-commerce sessions where most sessions buy nothing, so a plain regressor collapses toward zero.
- Kaggle submission: XGBoost + LightGBM blend with target encoding, **R² 0.632**.
- Rebuilt as a **two-stage hurdle model** (will they buy → how much): on a local holdout it reached RMSLE 0.84 vs 1.88 for a predict-zero baseline.
- Caught a micros-scale target bug and used a leakage-safe split.

`Python` · `pandas` · `scikit-learn` · `XGBoost` · `LightGBM`

### 💬 [Feedback NLP](https://github.com/00-Aryan/feedback-nlp): sentiment API
3-class sentiment classifier on SBERT embeddings + Logistic Regression, served through FastAPI.

`Python` · `Sentence-BERT` · `scikit-learn` · `FastAPI`

### 🩺 [Physician Notetaker](https://github.com/00-Aryan/NLP_Physician-notetaker): clinical NLP
Turns physician-patient conversations into structured notes: symptoms, diagnoses, medications. Domain NER with scispaCy plus DistilBERT, in a modular 6-class architecture.

`Python` · `spaCy` · `scispaCy` · `HuggingFace` · `DistilBERT`

### 🏦 [Bank Term Deposit Classification](https://github.com/00-Aryan/Binary-Classification-with-a-Bank-Dataset)
Stacking ensemble tuned with Optuna. The interesting part: finding and fixing data leakage with a chronological split.

### 🤖 [Content Creation Automation](https://github.com/00-Aryan/Content-Creation-Automation) · [live](https://content-creation-automation.onrender.com)
Multi-stage agentic content pipeline on the Gemini API with Pydantic v2 schemas and a 300+ test suite. **Agent-assisted build:** I wrote the plan and specs (`AGENTS.md`), and coding agents implemented them. I'm reworking it now to understand and simplify the pipeline end to end.

### 📊 More
- [ProductivOS](https://github.com/00-Aryan/Daily-Tracker) · [live](https://daily-tracker-seven-phi.vercel.app): full-stack tracker (React, FastAPI, Supabase with row-level security) that I use to log my own applications.
- [Olist E-commerce Dashboard](https://github.com/00-Aryan/data-visualisation-olist): multi-page Plotly Dash app on 11 tables. Finding: orders delivered after 14 days see sharply lower review scores.
- [Movie Recommender](https://github.com/00-Aryan/Movie_Recommender-System-): SVD collaborative filtering on MovieLens, built to understand cold-start and sparsity.

---

## 🛠️ Stack (honest tiers)

| | |
|---|---|
| **Daily use** | Python · pandas · NumPy · scikit-learn · XGBoost / LightGBM · FastAPI · LangChain · ChromaDB · Pydantic · Streamlit · pytest · Git / GitHub Actions |
| **Working knowledge** | SQL · spaCy / HuggingFace Transformers · Flask · Plotly Dash · Gemini API · RAGAS |
| **Learning now** | LangGraph · production LLM engineering (cost, latency, scale) · retrieval evaluation |

---

## 🌱 Now

- Raising TenderIQ's faithfulness score and adding eligibility matching
- Learning LangGraph and production LLM engineering (token cost, latency, scaling)
- Strengthening SQL

---

<div align="center">

*Not an expert yet. I show up, reason through it, and ship.*

📬 **If you're building with RAG or agents, I'd like to hear about it.**

</div>
