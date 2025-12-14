# 📂 Dataset Documentation: Restaurant Sentiment Analysis & NER

This repository utilizes public datasets to train two **Deep Learning** models: **Sentiment Analysis (SA)** and **Named Entity Recognition (NER)** within the restaurant review domain.

## 🔗 Data Sources (Credits)

The datasets collected and used in this project are sourced from the following repositories:

- **For Named Entity Recognition (NER):**
  - Dataset: **MIT Restaurant Corpus**
  - Source: [Kaggle - MIT Restaurant Corpus CRF Dataset](https://www.kaggle.com/datasets/marusagar/mit-restaurant-corpus-crf-dataset)
- **For Sentiment Analysis (SA):**
  - Dataset: **Restaurant Reviews**
  - Source: [GitHub - Restaurant Reviews Sentiment Analysis](https://github.com/aadimangla/Restaurant-Reviews-Sentiment-Analysis/blob/master/Dataset/Restaurant_Reviews.tsv)

---

## 🗂️ Directory Structure

Ensure your dataset files are stored using the folder structure below to match the training notebooks:

```text
dataset/
├── ner/
│   ├── label_test.txt      # Entity labels (BIO tags) for testing
│   ├── label_train.txt     # Entity labels (BIO tags) for training
│   ├── sent_test.txt       # Sentence text for testing
│   └── sent_train.txt      # Sentence text for training
│
└── sa/
    ├── Restaurant_Reviews.csv  # Reviews dataset with sentiment labels (CSV Format)
    └── Restaurant_Reviews.tsv  # Reviews dataset with sentiment labels (TSV Format)

1. Sentiment Analysis (SA) Dataset
This dataset contains customer reviews for restaurants along with their sentiment polarity (Positive/Negative).

File Location: dataset/sa/

Format: CSV & TSV

Columns:

Review: The text of the customer review.

Liked: Binary label (0 = Negative, 1 = Positive).

2. Named Entity Recognition (NER) Dataset
This dataset is used to extract specific entities such as Food, Price, Location, etc. The data is separated into two types of files: one containing the sentences and another containing the labels that correspond line-by-line.

File Location: dataset/ner/

Format: Plain Text (.txt)

Tagging Scheme: BIO Tagging (Beginning, Inside, Outside)
```
