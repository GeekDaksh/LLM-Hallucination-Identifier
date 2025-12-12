# 🚨 Identifying Hallucinations in LLM Outputs

A sentence-level verification system that identifies factual hallucinations in Large Language Model (LLM) responses by cross-checking claims against real-world web evidence.

---

## 🔍 Overview

Large Language Models often generate confident statements that may not be factually correct.  
This project analyzes generated text by breaking it into individual claims and verifying each claim using web search and Natural Language Inference (NLI).

Each claim is evaluated for factual consistency and highlighted for easy interpretation.

---

## 🟢🟡🔴 Claim Classification

- 🟢 **Verified** — Claim is supported by online evidence  
- 🔴 **Hallucinated** — Claim is contradicted or likely false  
- 🟡 **Uncertain** — Evidence is missing or inconclusive  

---

## 🧩 Verification Pipeline

1. **Claim Extraction**  
   Text is segmented into individual factual claims using spaCy.

2. **Search Query Construction**  
   Queries are refined using:
   - Named entities from a BERT-based NER model
   - Noun phrases extracted via spaCy
   - Heuristic keywords (e.g., invented, founded, discovered)

3. **Evidence Retrieval**  
   Claims are searched on the web using DuckDuckGo and relevant snippets are collected.

4. **Natural Language Inference (NLI)**  
   Each claim is compared against retrieved snippets using RoBERTa-large-MNLI:
   - ENTAILMENT → supports the claim  
   - CONTRADICTION → refutes the claim  
   - NEUTRAL → insufficient or irrelevant evidence  

5. **Decision Logic**
if contradiction_score >= 0.80 → Hallucinated
elif entailment_score >= 0.75 → Verified
else → Uncertain


6. **Visualization**  
Results are displayed using Streamlit with color-coded highlights.

---

## 🧠 Models Used

- RoBERTa-large-MNLI — Natural Language Inference  
- dslim/bert-base-NER — Named Entity Recognition  
- all-MiniLM-L6-v2 — Semantic similarity  
- spaCy (en_core_web_sm) — NLP processing  

---

## 📁 Project Structure
LLM-Hallucination-Indentifier/
├── app.py # Streamlit interface
├── verifier.py # Verification logic
├── requirements.txt # Dependencies
└── README.md # Documentation


---

## ▶️ Getting Started

### Clone the repository

### Install dependencies

### Run the application


---

## 🎯 Use Cases

- Evaluating factual reliability of LLM outputs  
- AI safety and trustworthiness research  
- Fact-checking assistants  
- Educational demonstrations of LLM hallucinations  

---

## ⚠️ Disclaimer

This system assists in hallucination detection but does not replace human fact-checking.  
Results depend on available web evidence and model confidence.
