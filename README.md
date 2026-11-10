# 🔎 Text Search Engine using TF-IDF

A simple **Information Retrieval** system that ranks documents by their relevance to a user's query using **TF-IDF** and **Cosine Similarity**.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HaithamHD/tfidf-search-engine/blob/main/TFIDF_Search_Engine.ipynb)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![NLTK](https://img.shields.io/badge/NLTK-154F5B?style=flat)

## 📌 How It Works

```text
User query ─┐
            ├─► Preprocessing ─► TF-IDF vectors ─► Cosine similarity ─► Top 5 documents
Documents ──┘
```

1. **Load data** – the first 30 documents of the [20 Newsgroups](https://scikit-learn.org/stable/datasets/real_world.html#newsgroups-dataset) dataset (via `sklearn.datasets`).
2. **Preprocess** documents and query with the same pipeline:
   - Tokenization (NLTK `word_tokenize`)
   - Lowercasing
   - Stop-word removal (NLTK English stop words)
   - Removing punctuation, digits and words containing digits
   - Removing special characters
   - Stemming (Porter Stemmer)
   - Joining tokens and trimming white space
3. **Vectorize** with scikit-learn's `TfidfVectorizer` → a 30 × 2,128 TF-IDF matrix.
4. **Rank** documents by cosine similarity to the query vector and return the **top 5**.

### Preprocessing example

```text
Before: "Machine Learning is #1 in 2025!"
After:  "machine learn"
```

## 🧪 Example Query

```text
Input:      football championship results fd5s 165 aedd1 is are is @#
Processed:  footbal championship result
```

Noise such as numbers, mixed letter-digit tokens, stop words and symbols is removed, and the remaining words are reduced to their stems before searching. The system then prints the five documents with the highest similarity scores.

## 📄 Report

The written report with the analysis and discussion (why the top document ranks first, which terms contribute most, and the effect of removing stop words) is in [`report/Report.pdf`](report/Report.pdf).

## 🚀 How to Run

**Easiest:** click **Open in Colab** above, then *Runtime → Run all*. The notebook asks for a search query when it reaches the *User input* cell.

**Locally:**

```bash
git clone https://github.com/HaithamHD/tfidf-search-engine.git
cd tfidf-search-engine
pip install -r requirements.txt
jupyter notebook TFIDF_Search_Engine.ipynb
```

The dataset and NLTK resources are downloaded automatically the first time the notebook runs.

## 👤 Author

**Haitham Hani Dalloul**
*Information Retrieval (ITAP3312) – Al-Aqsa University, First Semester 2025–2026*
Instructor: Mohammed Jamil Altahrawi
