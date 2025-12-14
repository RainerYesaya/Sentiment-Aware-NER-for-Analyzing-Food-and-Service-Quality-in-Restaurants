# Restaurant Review NLP Models

This repository contains a **Deep Learning project** focused on Natural Language Processing (NLP) in the restaurant domain. The project implements and evaluates two transformer-based models:

- **Sentiment Analysis (SA)** – to classify restaurant reviews as positive or negative
- **Named Entity Recognition (NER)** – to extract structured entities such as food items, prices, and locations from restaurant-related text

Both models are built using **DistilBERT** and the **Hugging Face Transformers** ecosystem.

---

## Project Overview

The goal of this project is to demonstrate the application of modern transformer-based architectures for text understanding tasks commonly used in real-world restaurant and review analysis systems.

Key objectives:

- Perform **binary sentiment classification** on restaurant reviews
- Perform **token-level entity recognition** using BIO tagging
- Apply best practices such as **early stopping**, **model checkpointing**, and **conditional training/loading**
- Provide reproducible experiments and clear dataset organization

---

## Models

### 1. Sentiment Analysis (SA)

- **Task Type:** Text Classification
- **Model Architecture:** DistilBERT (`distilbert-base-uncased`)
- **Labels:**

  - `0` → Negative
  - `1` → Positive

- **Evaluation Metrics:** Accuracy (optionally Precision, Recall, F1)

The Sentiment Analysis model predicts whether a restaurant review expresses a positive or negative sentiment.

---

### 2. Named Entity Recognition (NER)

- **Task Type:** Token Classification
- **Model Architecture:** DistilBERT (`distilbert-base-uncased`)
- **Tagging Scheme:** BIO (Beginning, Inside, Outside)
- **Evaluation Metrics:** Precision, Recall, F1-score (SeqEval)

The NER model extracts structured entities from text, such as:

- Food items
- Prices
- Locations
- Restaurant-related attributes

---

## Project Structure

```
DEEP_LEARNING-FINAL_PROJECT/
├── app/                # Application / inference interface (optional)
├── dataset/            # Training and evaluation datasets
├── report/             # Project report and documentation
├── src/                # Model training notebooks / scripts
│   ├── NER_Model.ipynb
│   └── Sentiment_Model.ipynb
├── trained_models/     # Saved trained models
│   ├── ner/
│   └── sa/
└── README.md
```

---

## Training Strategy

- Conditional training: models are **loaded if already trained**, otherwise trained from scratch
- Early stopping is applied to prevent overfitting
- Best model is automatically loaded based on validation metrics

---

## Evaluation Results & Discussion

### Named Entity Recognition (NER)

**Final Evaluation Metrics (Test Set):**

| Metric    | Score     |
| --------- | --------- |
| Precision | **0.792** |
| Recall    | **0.826** |
| F1-score  | **0.809** |
| Accuracy  | 0.064     |

During training, the NER model shows a consistent decrease in both training and validation loss across epochs, indicating stable convergence. The F1-score improves from **0.746 (Epoch 1)** to **0.790 (Epoch 3)** on the validation set, demonstrating effective learning of entity boundaries.

The final evaluation achieves a balanced precision and recall, suggesting that the model is capable of both correctly identifying entities and minimizing false positives. The relatively low accuracy value is expected in token-level NER tasks due to class imbalance and the dominance of the `O` (Outside) label. Therefore, **F1-score is considered the primary performance metric** for this task.

---

### Sentiment Analysis (SA)

**Final Evaluation Metrics (Test Set):**

| Metric    | Score     |
| --------- | --------- |
| Accuracy  | **0.920** |
| Precision | 0.921     |
| Recall    | 0.920     |
| F1-score  | 0.920     |

The Sentiment Analysis model achieves strong performance, with a peak accuracy of **92%** on the test set. The training loss decreases significantly across epochs, while the validation loss remains stable, indicating good generalization without severe overfitting.

The balanced precision and recall values show that the model performs consistently across both positive and negative sentiment classes. These results demonstrate that DistilBERT is effective for binary sentiment classification in the restaurant review domain, even with a relatively small number of training epochs.

---

## Requirements

Main libraries used:

- Python 3.8+
- PyTorch
- Transformers (Hugging Face)
- Datasets
- Evaluate
- Scikit-learn
- NumPy
- Matplotlib

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Usage

1. Prepare datasets following the required directory structure
2. Open the notebooks:

   - `src/Sentiment_Model.ipynb`
   - `src/NER_Model.ipynb`

3. Run all cells to train or load existing models
4. Trained models will be saved under `trained_models/`
