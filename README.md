# KyrgyzNER: Human-Annotated NER Dataset for Kyrgyz

[![Paper](https://img.shields.io/badge/arXiv-Preprint-red)](https://arxiv.org/abs/2509.19109)  
[![Model](https://img.shields.io/badge/HuggingFace-Model-blue)](https://huggingface.co/TTimur/xlm-roberta-base-kyrgyzNER)

## Overview
**KyrgyzNER** is the first **manually annotated Named-Entity Recognition (NER) dataset** for the Kyrgyz language.  
It consists of **1,499 news articles** (10,900 sentences, 140k tokens) from the [24.kg](https://24.kg) news portal, annotated with **39,075 entity mentions across 27 classes**.  

This project provides both the dataset and baseline models, aiming to advance NLP research for low-resource Turkic languages.

---

## Key Features
- 📑 **Dataset**:  
  - 1,499 Kyrgyz news articles (2017–2022)  
  - 10,900 sentences, 39,075 entity mentions  
  - 27 entity categories (Person, Location, Institution, Period, etc.)  
  - Format: **CoNLL-2003**  

- 🛠 **Annotation**:  
  - Annotated by 59 trained Kyrgyz linguists and students  
  - Guidelines adapted from **GROBID-NER**  
  - High-quality dataset with **κ = 0.89 inter-annotator agreement**  

- 🤖 **Models**:  
  - Baselines: CRF, BiLSTM+CRF, multilingual BERT, mT5  
  - Best results: **XLM-RoBERTa-base** (F1 ≈ 0.73)  
  - [HuggingFace Model](https://huggingface.co/TTimur/xlm-roberta-base-kyrgyzNER) ready to use  

---

## Usage
You can directly load and use our fine-tuned model from HuggingFace:

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification
from transformers import pipeline

model_name = "TTimur/xlm-roberta-base-kyrgyzNER"

tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForTokenClassification.from_pretrained(model_name)

ner_pipeline = pipeline("ner", model=model, tokenizer=tokenizer)

text = "Президент Садыр Жапаров бүгүн Бишкекте сүйлөө жасады."
print(ner_pipeline(text))
```

---

## Dataset Statistics
| Split       | Docs | Sentences | Tokens | Mentions |
|-------------|------|-----------|--------|----------|
| Train (999) | 999  | 7,033     | 89,248 | 24,949   |
| Test (500)  | 500  | 3,867     | 51,118 | 14,126   |
| **Total**   |1499  | 10,900    |140,366 | 39,075   |

- Most frequent classes: **Person, Location, Institution, Measure**  
- Rare classes (few samples): **Award, Animal, Substance, Identifier**  

---

## Baseline Results
| Model            | Precision | Recall | F1   |
|------------------|-----------|--------|------|
| CRF              | 0.70      | 0.55   | 0.62 |
| BERT+CRF         | 0.67      | 0.63   | 0.65 |
| mBERT (cased)    | 0.68      | 0.68   | 0.68 |
| mT5-small        | 0.70      | 0.68   | 0.69 |
| **XLM-RoBERTa**  | **0.74**  | **0.71** | **0.73** |

---

## Contribution
We are grateful to:
- **59 volunteers** (mainly students of KSTU) who annotated the dataset  
- Dr. Gulnara Kabaeva and Dr. Gulira Zhumalieva for academic support  
- [List of contributors](volunteers.md)  

We welcome contributions from the **NLP community**. Please open issues or pull requests if you’d like to improve the dataset, guidelines, or models.

---

## Citation
If you use this dataset or model in your research, please cite:

```bibtex
@inproceedings{turatali2025kyrgyzner,
  title     = {Human-Annotated NER Dataset for the Kyrgyz Language},
  author    = {Turatali, Timur and Alekseev, Anton and Jumalieva, Gulira and Kabaeva, Gulnara and Nikolenko, Sergey},
  booktitle = {Proceedings of TurkLang 2025},
  year      = {2025}
}
```

---

## License
- Dataset: **CC BY-NC-SA 4.0**  
- Code & Models: **MIT license**  

---

👉 Full details are available in our [paper](link-to-arxiv).
