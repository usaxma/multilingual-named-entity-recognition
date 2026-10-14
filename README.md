# Multilingual Named Entity Recognition

Transformer NER for **English**, **Urdu**, **Roman Urdu**, and **Punjabi**. The notebook trains and compares three multilingual token classifiers on a combined BIO-tagged corpus, then reports overall and language-wise precision, recall, and F1.

## Models

| Key | Checkpoint |
|---|---|
| `xlmr` | `xlm-roberta-base` |
| `mbert` | `bert-base-multilingual-cased` |
| `distilmbert` | `distilbert-base-multilingual-cased` |

## Pipeline

1. Load English and Roman Urdu CoNLL files, Punjabi POS-NER CoNLL, and Urdu **WikiANN** (`wikiann`, `ur`)
2. Normalize Roman Urdu, Unicode, and noisy tokens
3. Language ID + BIO tag repair
4. Align labels to subword tokens
5. Fine-tune with Hugging Face `Trainer` (5 epochs, F1 as the selection metric, `seqeval`)
6. Combined and language-wise evaluation, training curves, confusion matrix, sample predictions

## Data

Urdu WikiANN is pulled from Hugging Face automatically.

Put these CoNLL files in `data/` (or keep them on Drive if you run in Colab):

- `english.txt`
- `roman_urdu.txt`
- `pos_ner.conll` (Punjabi)

See `data/README.md`.

## Run

**Colab:** open `notebooks/Multilingual_NER.ipynb` and run all cells. Drive is used if you are in Colab.

**Local:**

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/Multilingual_NER.ipynb
```

A GPU is strongly recommended for training.

## Structure

```
multilingual-named-entity-recognition/
├── notebooks/Multilingual_NER.ipynb
├── data/                 # CoNLL files (not all committed)
├── requirements.txt
└── README.md
```
