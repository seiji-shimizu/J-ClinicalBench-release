# J-ClinicalBench

J-ClinicalBench is a benchmark dataset and evaluation suite for Japanese clinical NLP. It is designed to support research on large language models (LLMs) and traditional NLP systems in the clinical domain.

---

## 📌 Overview

J-ClinicalBench provides curated clinical text data and evaluation outputs to facilitate:

- Benchmarking Japanese clinical language understanding  
- Evaluating LLM performance on clinical tasks  
- Supporting reproducible clinical NLP research  
- Enabling comparison across models and methods  

The repository contains processed datasets and corresponding evaluation results.

---

## 📂 Repository Structure

```

J-ClinicalBench-release/
├── data/        # Benchmark datasets
├── results/     # Model evaluation outputs
└── README.md

````

### `data/`

Contains the released benchmark datasets used for evaluation.  
Typical contents may include:

- Train/dev/test splits  
- Task-specific annotations  
- Preprocessed clinical text  

> ⚠️ Update this section with exact dataset details if needed.

---

### `results/`

Contains evaluation outputs for baseline or reference models.

Examples:

- Model predictions  
- Evaluation metrics  
- Benchmark comparison tables  

> ⚠️ Update with specific model names if desired.

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/seiji-shimizu/J-ClinicalBench-release.git
cd J-ClinicalBench-release
````

### 2. Inspect the data

```bash
ls data/
```

### 3. Review benchmark results

```bash
ls results/
```

---

## 🧪 Intended Use

J-ClinicalBench is intended for:

* Clinical NLP research
* Japanese medical language modeling
* LLM benchmarking
* Academic comparison studies

**Not intended for clinical decision making.**

---

## 📊 Tasks (Example — edit as needed)

The benchmark may include tasks such as:

* Named Entity Recognition (NER)
* Clinical classification
* Information extraction
* Adverse event detection

> ⚠️ Please update with the actual tasks in your dataset.

---

## 🔒 Data Usage & Ethics

* Ensure compliance with institutional and legal requirements when using clinical text.
* Do not attempt to re-identify individuals.
* Use the dataset strictly for research purposes.

---

## 📝 Citation

If you use J-ClinicalBench in your research, please cite:

```bibtex
@dataset{jclinicalbench,
  title={J-ClinicalBench: Japanese Clinical NLP Benchmark},
  author={Shimizu, Seiji},
  year={2025},
}
```

> ⚠️ Replace with your official citation.

---

## 🤝 Contributing

Contributions are welcome. Please open an issue or pull request for:

* Bug reports
* Benchmark improvements
* Additional baselines
* Documentation fixes

---

## 📧 Contact

Maintainer: **Seiji Shimizu**

For questions or collaboration inquiries, please open a GitHub issue.

```

---

If you want the **paper-ready polished README**, I can next add:

- ✅ Table-1 task table (properly formatted)  
- ✅ dataset statistics  
- ✅ leaderboard  
- ✅ badges (HF, license, paper)

Just say the word.
::contentReference[oaicite:0]{index=0}
```

## 📋 Task Overview

J-ClinicalBench consists of **nine clinical NLP tasks** organized into three capability groups:

* 🧠 Clinical Reasoning (3 tasks)
* ✍️ Clinical Generation (2 tasks)
* 🔍 Clinical Understanding (4 tasks)

Datasets marked with ⋆ are newly constructed in the benchmark.

---

### 🧠 Clinical Reasoning Tasks

These tasks evaluate whether models can combine medical knowledge with patient context to support clinically meaningful decisions.

#### 1. Clinical Code Assignment (CCA) ⋆

**Input:** Clinical notes
**Output:** All corresponding diagnostic codes (MedDRA)

**Objective:**
Assign appropriate diagnostic codes based on patient symptoms, diseases, and conditions described in clinical text.

**Clinical relevance:**

* Medical billing
* Epidemiological studies
* Secondary use of clinical data

**Key challenge:** multi-label medical reasoning over free text.

---

#### 2. Medication Recommendation (MR) ⋆

**Input:** Clinical notes
**Output:** Recommended medications

**Objective:**
Recommend all suitable medications for the patient given their clinical description.

**Clinical relevance:**

* Decision support
* Treatment planning
* Prescription assistance

**Key challenge:** context-aware therapeutic reasoning.

---

#### 3. Exam-style Question Answering (ExamQA)

**Source:** Adapted from the IGAKU QA benchmark
**Input:** Medical exam question
**Output:** Correct answer choice

**Objective:**
Answer questions derived from the Japanese national medical board examination.

**Clinical relevance:**

* Medical knowledge assessment
* Clinical reasoning ability

**Key challenge:** high-level medical reasoning under exam conditions.

---

### ✍️ Clinical Generation Tasks

These tasks evaluate controlled generation and rewriting ability in clinical contexts.

---

#### 4. Incident Report Summarization ⋆

**Input:** Incident report
**Output:** Concise structured summary

**Objective:**
Extract key safety information (e.g., event type, contributing factors, outcomes) and produce a summary.

**Clinical relevance:**

* Patient safety monitoring
* Risk detection
* Quality improvement

**Key challenge:** faithful information compression from noisy reports.

---

#### 5. Clinical Text Simplification ⋆

**Input:** Clinical note
**Output:** Plain-Japanese rewrite

**Objective:**
Rewrite clinical text into patient-friendly Japanese while preserving medical accuracy.

**Clinical relevance:**

* Patient communication
* Health literacy
* Accessibility

**Key challenge:** balance between simplification and factual fidelity.

---

### 🔍 Clinical Understanding Tasks

These tasks focus on structured information extraction and document-level understanding.

---

#### 6. Named Entity Recognition (NER)

**Source:** MedTxt corpus (adapted)
**Input:** Clinical text
**Output:** Entity spans and types

**Target entities include:**

* Diseases
* Medications
* Other clinical concepts

**Clinical relevance:**

* Knowledge base construction
* Cohort identification
* Downstream IE tasks

**Key challenge:** fine-grained span detection in Japanese clinical text.

---

#### 7. Relation Extraction (RE)

**Source:** MedTxt corpus (extended)
**Input:** Clinical text with entities
**Output:** Entity–entity and temporal relations

**Example relations:**

* Body part–disease
* Event temporal relations

**Clinical relevance:**

* Structured patient history
* Clinical timeline construction
* Decision support

**Key challenge:** contextual relation reasoning.

---

#### 8. Document Classification — ADE Detection

**Input:** Clinical document
**Output:** Whether the document reports an adverse drug event

**Clinical relevance:**

* Pharmacovigilance
* Drug safety monitoring

**Key challenge:** document-level safety signal detection.

---

#### 9. Document Classification — TNM Staging

**Input:** Clinical document
**Output:** TNM stage labels (e.g., T2a, N0, M0)

**Clinical relevance:**

* Cancer prognosis
* Treatment planning
* Oncology workflows

**Key challenge:** clinically precise multi-axis classification.

---

## 📊 Benchmark Coverage

J-ClinicalBench evaluates models across:

* **Reasoning** (CCA, MR, ExamQA)
* **Generation** (Summarization, Simplification)
* **Understanding** (NER, RE, ADE classification, TNM staging)

This design enables comprehensive assessment of Japanese clinical language models from low-level extraction to high-level clinical decision support.

---

✅ If you want the README to look **conference-ready**, I can next add:

* a compact Table-1 style summary table
* dataset statistics
* evaluation metrics per task
* leaderboard template

Just say the word.
