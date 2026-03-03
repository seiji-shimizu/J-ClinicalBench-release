# J-ClinicalBench

J-ClinicalBench is a benchmark dataset and evaluation suite for Japanese clinical NLP. 


## Overview

<img src="assets/clinicalbench_intro_v5.png" width="500">

J-ClinicalBench consists of **nine clinical NLP tasks** organized into three capability groups:

* **Reasoning** (CCA, MR, ExamQA)
* **Generation** (Summarization, Simplification)
* **Understanding** (NER, RE, ADE classification, TNM staging)

## 📋 Tasks
Datasets marked with ⋆ are newly constructed in the benchmark.

### 🧠 Clinical Reasoning Tasks

These tasks evaluate whether models can combine medical knowledge with patient context to support clinically meaningful decisions.

#### 1. Clinical Code Assignment (CCA) ⋆

**Input:** Clinical notes
**Output:** All corresponding diagnostic codes (MedDRA)

**Objective:**
Assign appropriate diagnostic codes based on patient symptoms, diseases, and conditions described in clinical text.


#### 2. Medication Recommendation (MR) ⋆

**Input:** Clinical notes
**Output:** Recommended medications

**Objective:**
Recommend all suitable medications for the patient given their clinical description.


#### 3. Exam-style Question Answering (ExamQA)

**Source:** Adapted from the IGAKU QA benchmark
**Input:** Medical exam question
**Output:** Correct answer choice

**Objective:**
Answer questions derived from the Japanese national medical board examination.


### ✍️ Clinical Generation Tasks

These tasks evaluate controlled generation and rewriting ability in clinical contexts.


#### 4. Hospitalization Summarization ⋆

**Input:** Incident report
**Output:** Concise structured summary

**Objective:**
Extract key safety information (e.g., event type, contributing factors, outcomes) and produce a summary.


#### 5. Incident Report Summarization ⋆

**Input:** Incident report
**Output:** Concise structured summary

**Objective:**
Extract key safety information (e.g., event type, contributing factors, outcomes) and produce a summary.


#### 6. Clinical Text Simplification ⋆

**Input:** Clinical note
**Output:** Plain-Japanese rewrite

**Objective:**
Rewrite clinical text into patient-friendly Japanese while preserving medical accuracy.

### 🔍 Clinical Understanding Tasks

These tasks focus on structured information extraction and document-level understanding.


#### 7. Named Entity Recognition (NER)

**Source:** MedTxt corpus (adapted)
**Input:** Clinical text
**Output:** Entity spans

**Target entities include:**

* Diseases
* Medications


#### 8. Relation Extraction (RE)

**Source:** MedTxt corpus (extended)
**Input:** Clinical text with entities
**Output:** Entity–entity and temporal relations

**Example relations:**

* Body part–disease
* Event temporal relations

#### 9. Document Classification 

##### ADE Detection
**Input:** Clinical document
**Output:** Whether the document reports an adverse drug event

##### Document Classification — TNM Classification

**Input:** Clinical document
**Output:** TNM stage labels (e.g., T2a, N0, M0)

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


### `results/`

Contains evaluation outputs for baseline or reference models.

Examples:

- Model predictions  
- Evaluation metrics  
- Benchmark comparison tables  

> ⚠️ Update with specific model names if desired.


---
## 🧪 Intended Use

J-ClinicalBench is intended for:

* Clinical NLP research
* Japanese medical language modeling
* LLM benchmarking
* Academic comparison studies

**Not intended for clinical decision making.**

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
