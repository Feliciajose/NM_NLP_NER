# Financial Named Entity Recognition (NER) Model

## Problem Statement

Financial documents like annual reports, audit summaries, and regulatory filings contain critical insights about organizations. However, extracting structured data from these unstructured texts is challenging due to:

- Domain-specific jargon
- Similar-looking financial terms (e.g., net profit vs. gross margin)
- Volume and complexity of data

Manual analysis is time-consuming, error-prone, and inconsistent. General-purpose NER tools often fail to detect financial entities accurately.

This project develops a **domain-specific Named Entity Recognition (NER) model** to automate the extraction of key financial entities such as:

- Organization names
- Asset values
- Transaction dates
- Stock tickers
- Legal codes
- Financial metrics

The goal is to enable fast, accurate, and scalable analysis across thousands of financial documents to support investment analysis, risk assessment, and fraud detection.

---

## Features

- Fine-tuned NER model for financial text
- High precision and recall on financial terms
- Handles ambiguous and similar-looking terms
- Hybrid approach: Transformers + Regex + Domain heuristics
- Outputs structured data in CSV/JSON formats
- Easy to integrate with downstream analytics pipelines

---

## Tech Stack

- Python
- Hugging Face Transformers (RoBERTa, FinBERT)
- Regex for pattern-based extraction
- PyMuPDF (PDF parsing)
- SpaCy (tokenization & preprocessing)

---

## Installation

### Clone the Repository

```bash
git clone https://github.com/yourusername/financial-ner.git
cd financial-ner/backend
````

### Set up Virtual Environment & Install Dependencies

```bash
python -m venv venv
source venv/bin/activate 
pip install -r requirements.txt
```

### Run the Model (for inference or API)

```bash
python app.py  
```

---

## Folder Structure

```
financial-ner/
│
├── backend/
│   ├── app.py                     
│   ├── model/
│   │   ├── roberta_finetuned/    
│   │   ├── finbert/              
│   │   └── regex_rules.py        
│   ├── utils/
│   │   ├── pdf_parser.py         │   │   └── entity_postprocess.py # Entity grouping, cleaning
│   └── requirements.txt
```

---

## Model Overview

NER pipeline combines three approaches:

* **Fine-tuned RoBERTa**: For general-purpose contextual entity recognition.
* **FinBERT**: Specialized BERT model trained on financial corpora for improved domain understanding.
* **Regex-based Matching**: Rule-based system to catch entities not well captured by ML models (e.g., legal codes, currency formats).

These methods are ensemble-combined to improve precision and recall.

---

## Output Format

* **CSV or JSON** files with columns like:

  * Entity
  * Type (Organization, Date, Value, Code, etc.)

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for more information.

---

## Acknowledgments

* Hugging Face Transformers
* FinBERT by Prosus AI
* SpaCy
* PyMuPDF

```
