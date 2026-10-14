# Data

Expected local files (UTF-8 CoNLL-style token + NER tag):

| File | Language |
|---|---|
| `english.txt` | English |
| `roman_urdu.txt` | Roman Urdu |
| `pos_ner.conll` | Punjabi |

Urdu is loaded in the notebook with:

```python
load_dataset("wikiann", "ur")
```

If these files are missing, the notebook still creates the workspace folders; training on English / Roman Urdu / Punjabi will fail until the files are present.
