# J-ClinicalBench

J-ClinicalBench is a benchmark dataset and evaluation suite for Japanese clinical NLP.

## Overview

<img src="assets/clinicalbench_intro_v5.png" width="500">

J-ClinicalBench consists of **nine clinical NLP tasks** organized into three capability groups:

- **Reasoning** (CCA, MR, ExamQA)
- **Generation** (Hospitalization Summarization, Incident Report Summarization, Clinical Text Simplification)
- **Understanding** (NER, RE, ADE classification, TNM staging)

## 📂 Folder Structure

```text
J-ClinicalBench-release/
├── assets/
├── data/
│   ├── benchmarks/        # Task-ready benchmark datasets/prompts
│   ├── raw/               # Normalized source documents (.txt)
│   ├── _raw_downloaded/   # Original downloaded files (xml/csv/xlsx/docx...)
│   └── _org/              # Original resources/metadata
├── results/
└── README.md
```

## 🗂️ `data/raw` Document Types

All documents in `data/raw` are normalized text files for consistent downstream processing.

- `CR/`: Case report text converted from XML (`id.txt`, tags removed).
- `NR/`: Nursing records (`SOAP`) converted to `## S`, `## O`, `## A`, `## P` style text.
- `RR/`: Radiology report text converted from XML and additional txt corpora.
- `DS/`: Discharge summaries converted from DOCX tables.
- `PN/`: Problem/note-style mixed discharge/nursing documents (from `DS_PN_mixed`).
- `IR/`: Incident reports converted from CSV to sectioned text (`## 項目名`).
- `MH/`: Pharmaceutical care records converted from CSV rows to sectioned text.
- `RN/`: Pre-round chart notes from XLSX (`退院サマリのファイル名_作成者ID.txt`).
- `abbreviations.txt`: Abbreviation list used for normalization/reference.

## 📋 Tasks

Datasets marked with `⋆` are newly constructed in this benchmark.

### 🧠 Clinical Reasoning Tasks

#### 1. Clinical Code Assignment (CCA) ⋆

- Input: Clinical note
- Output: All corresponding diagnostic codes (MedDRA)

#### 2. Medication Recommendation (MR) ⋆

- Input: Clinical note
- Output: Recommended medications

#### 3. Exam-style Question Answering (ExamQA)

- Source: Adapted from IGAKU QA benchmark
- Input: Medical exam question
- Output: Correct answer choice

### ✍️ Clinical Generation Tasks

#### 4. Hospitalization Summarization ⋆

- Input: Hospitalization/discharge record
- Output: Concise clinical summary

#### 5. Incident Report Summarization ⋆

- Input: Incident report
- Output: Concise structured summary

#### 6. Clinical Text Simplification ⋆

- Input: Clinical text
- Output: Plain-Japanese rewrite

### 🔍 Clinical Understanding Tasks

#### 7. Named Entity Recognition (NER)

- Input: Clinical text
- Output: Entity spans and labels

#### 8. Relation Extraction (RE)

- Input: Clinical text with entities
- Output: Entity/temporal relations

#### 9. Document Classification

- ADE Detection: classify adverse drug event mention (`有/無`)
- TNM Classification: predict TNM labels (`T`, `N`, `M`)

## 🧪 `data/benchmarks` Mock Input/Output

The following are **mock examples** aligned with each dataset format.

### CLR (Clinical Reasoning)

#### `CLR/CCA/data.csv`

- Mock input (`text`):

```text
腹痛と発熱が持続。画像検査で虫垂腫大を認め、急性虫垂炎と診断。
```

- Mock output (`medra_list`):

```text
["虫垂炎", "腹痛", "発熱"]
```

#### `CLR/MR/data.csv`

- Mock input (`text`):

```text
術後疼痛あり。便秘傾向もある。
```

- Mock output (`medications`):

```text
["ロキソプロフェン", "酸化マグネシウム"]
```

#### `CLR/MCQA/igakuqa_clinical_*.jsonl`

- Mock input (`question`, `options`):

```text
question: 70歳男性。突然の動悸。最初に行うべき対応はどれか。
options: ["A", "B", "C", "D", "E"]
```

- Mock output (`answer_idx`):

```text
3
```

### CLG (Clinical Generation)

#### `CLG/HS_DS/*`

- Mock input (`data_ds.csv` text + doctor profile):

```text
患者は腹痛で入院し、急性虫垂炎に対して腹腔鏡下虫垂切除術を施行。
```

- Mock output (`data_summary.csv` summary):

```text
急性虫垂炎術後。術後経過良好で退院。
```

#### `CLG/HS_PN/data.json`

- Mock input (`notes`):

```text
[S] 食欲低下。 [O] 高Ca血症。 [A] 脱水併存。 [P] 補液開始。
```

- Mock output (`summary`):

```text
高Ca血症による意識障害に対し補液治療を実施し改善。
```

#### `CLG/IRS/data.csv`

- Mock input (`incident_description`, `action_token`):

```text
食前血糖測定前に患者が食事を開始。
```

- Mock output (`summary`):

```text
食前血糖測定のタイミング逸脱。
```

#### `CLG/CTS/*.csv`

- Mock input (`input_text`):

```text
術後炎症反応は改善傾向で、全身状態は安定している。
```

- Mock output (`simplified_text`):

```text
手術後の炎症は良くなっており、体調は安定しています。
```

### CLU (Clinical Understanding)

#### `CLU/NER_Disease/*.json` (JSONL format)

- Mock input (`text`):

```text
右下腹部痛と発熱を認め、急性虫垂炎と診断した。
```

- Mock output (`entities`):

```text
[{"name":"急性虫垂炎","type":"d_positive","span":[...]}]
```

#### `CLU/NER_Medication/*.json` (JSONL format)

- Mock input (`text`):

```text
疼痛時にロキソプロフェンを内服。
```

- Mock output (`entities`):

```text
[{"name":"ロキソプロフェン","type":"m-key","span":[...]}]
```

#### `CLU/RE_Ent/rel_data.json`

- Mock input (`text`):

```text
<e1 type=a>肝</e1>に<e2 type=d>転移</e2>を認める。
```

- Mock output (`relation`):

```text
region
```

#### `CLU/RE_Time/rel_data.json`

- Mock input (`text`):

```text
<e2 type=TIMEX3>術後3日</e2>に<e1 type=t-val>CRP低下</e1>。
```

- Mock output (`relation`):

```text
on
```

#### `CLU/DC_ADE/data.csv`

- Mock input (`text`, `medication`):

```text
薬剤開始後に皮疹が出現。
```

- Mock output (`label`):

```text
有
```

#### `CLU/DC_TMN/data.csv`

- Mock input (`text`):

```text
右上葉肺腫瘤。縦隔リンパ節腫大なし。遠隔転移なし。
```

- Mock output (`t`, `n`, `m`):

```text
T2a, N0, M0
```

## 🧪 Intended Use

J-ClinicalBench is intended for:

- Clinical NLP research
- Japanese medical language modeling
- LLM benchmarking
- Academic comparison studies

Not intended for direct clinical decision making.

## 📝 Citation

If you use J-ClinicalBench in your research, please cite:

```bibtex
@dataset{jclinicalbench,
  title={J-ClinicalBench: Japanese Clinical NLP Benchmark},
  author={Shimizu, Seiji},
  year={2025},
}
```

## 🤝 Contributing

Contributions are welcome via issues and pull requests.

## 📧 Contact

Maintainer: **Seiji Shimizu**
