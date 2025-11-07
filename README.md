# 👩‍🔬🧑‍💻💆‍♂️ LeWiDi Repository Data. Shared Task — Editions 1–3

This repository hosts material for all **three editions** of the LeWiDi shared task.

### Aim (in brief)
- **Embrace interpretative variation:** model and analyze disagreement rather than collapsing it away.  
- **Unified benchmarking:** offer a shared, comparable framework to train and evaluate systems on disagreement-aware data.  
- **From hard to soft labels:** encourage use of distributions/soft labels and perspectivist evaluation instead of single “gold” labels.  

## Editions & Datasets
### 2025 — 3rd Edition @ NLPerspectives (EMNLP 2025)
**Scope:** NLP; soft-label + perspectivist evaluation.  
**Datasets:**  
- **Conversational Sarcasm Corpus (CSC)** — sarcasm ratings (Likert 1–6)  
- **MultiPico (MP)** — multilingual irony detection in context  
- **Paraphrase Detection (Par)** — question-pair paraphrase judgments (Likert)  
- **VariErrNLI** — NLI with variation vs. error distinctions  

### 2023 — SemEval-2023 Task 11 (2nd Edition)
**Scope:** NLP, subjective tasks.  
**Datasets:**  
- **MD-Agreement** — offensiveness in English tweets  
- **ConvAbuse** — abusiveness in human–bot dialogues  
- **HS-Brexit** — hate speech/offensiveness around Brexit  
- **ArMIS** — Arabic misogyny/sexism  

### 2021 — SemEval-2021 Task 12 (1st Edition)
**Scope:** NLP + Computer Vision.  
**Datasets:**  
- **Twitter POS** (Gimpel et al.) — crowd-labeled POS tagging  
- **Phrase Detectives (PDIS)** — information status (Discourse New/Old)  
- **Humour** — pairwise funniness preference learning  
- **LabelMe** — 8-way image classification with crowd labels  
- **CIFAR-10H** — CIFAR-10 with human label distributions  
See the task paper for details.

## Repository Structure & Data Format
- Each top-level folder corresponds to an edition (**2021**, **2023**, **2025**) and contains that edition’s **datasets and materials**.  
- **Data format note:** the datasets from the **second (2023)** and **third (2025)** editions are provided in the **same harmonized JSON format** (schema aligned across tasks).
