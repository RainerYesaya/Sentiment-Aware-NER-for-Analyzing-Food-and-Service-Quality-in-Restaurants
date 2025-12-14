# Main Application – Restaurant NLP System

This application serves as the **main interface** for demonstrating the trained **Restaurant NLP models**, integrating both **Sentiment Analysis (SA)** and **Named Entity Recognition (NER)** into a single end-to-end system.

The application is designed to load pre-trained models when available and perform inference on user-provided restaurant reviews or queries.

---

## Application Overview

The main application is built using **Gradio** and provides an interactive web-based interface for analyzing restaurant reviews using the trained **Sentiment Analysis (SA)** and **Named Entity Recognition (NER)** models.

The interface is organized into **two main pages**:

- **Home** – General introduction and overview of the system
- **Analysis Dashboard** – Core analysis features and visual insights

This design allows users to easily explore model capabilities, analyze review datasets, and interpret results through visualizations and structured outputs.

---

## Application Pages & Features

### 1. Home Page

The Home page serves as an entry point to the application and provides:

- Brief explanation of the system
- Overview of Sentiment Analysis and NER tasks
- Guidance on how to use the Analysis Dashboard

---

### 2. Analysis Dashboard

The Analysis Dashboard is the main analytical workspace of the application. It supports batch analysis of restaurant reviews and presents the results in multiple interpretable formats.

#### a. Input Data

Users can upload restaurant review data in **CSV format**.

- The CSV file should contain a column with review text
- Uploaded data will be processed automatically by both SA and NER models

#### b. Use Sample Data

For demonstration purposes, users can choose to analyze a predefined sample dataset:

- **File:** `sample_reviews.csv`
- Allows users to quickly observe model behavior and output without providing custom data

#### c. Conclusion

This section provides an automatically generated **summary and conclusion** based on the analysis results, including:

- Overall sentiment tendency of the reviews
- High-level interpretation of customer opinions
- General insights derived from sentiment distribution and extracted entities

---

#### d. Data Visualization

The dashboard includes visual analytics to help users better understand the review data.

##### i. Sentiment Distribution

- Displayed as a **pie chart**
- Shows the percentage of **positive** and **negative** reviews
- Helps identify the overall customer sentiment trend

##### ii. Top 10 Menu / Services

- Displays the **top 10 most frequently mentioned entities**
- Focuses on menu items and services extracted by the NER model
- Highlights key aspects that customers frequently discuss

---

#### e. Extraction Details

This section presents a detailed table containing token- and segment-level extraction results.

**Table Columns:**

| Column Name | Description                                     |
| ----------- | ----------------------------------------------- |
| Review      | Original review text                            |
| Segment     | Text segment or token extracted from the review |
| Entity      | Entity label predicted by the NER model         |
| Sentiment   | Sentiment polarity associated with the review   |

This table enables fine-grained inspection of how entities and sentiments are identified within each review.

---

## Features

- Unified inference pipeline for **SA and NER**
- Automatic loading of trained models from disk
- Conditional training (train only if model files are not found)
- Support for transformer-based models using Hugging Face
- Reproducible and modular code structure

---

## Model Integration

### Sentiment Analysis (SA)

- **Model:** DistilBERT for Sequence Classification
- **Output:** Binary sentiment prediction

  - `0` → Negative
  - `1` → Positive

### Named Entity Recognition (NER)

- **Model:** DistilBERT for Token Classification
- **Output:** Token-level entity labels using BIO tagging

---

## File Description

```
app/
└── main_app.ipynb   # Main application notebook for model inference
```
The `main_app.ipynb` notebook handles model loading, data preparation, prediction, and result visualization.

---

## How It Works

1. The application checks whether trained models exist in the `trained_models/` directory
2. If models are found, they are loaded directly for inference
3. If not found, the application can trigger model training (optional)
4. User input text is tokenized using the corresponding tokenizer
5. Predictions are generated using the trained models
6. Results are displayed for both sentiment and entity recognition

---

## Usage Instructions

1. Make sure all required dependencies are installed correctly
2. Ensure that the trained models are available in the `trained_models/`directory
3. Open the following notebook and run **Run All Cells**:

```text
app/main_app.ipynb
```

After all cells have finished running, the Gradio interface will appear automatically.

4. Open the Gradio URL shown in the notebook output
5. Use the navigation menu to switch between the **Home** and **Analysis Dashboard**
6. Upload a CSV file or use the provided sample data to start the analysis

---

## Input Example

```
The sushi was delicious but the service was slow.
```

### Example Output

- **Sentiment:** Positive
- **Entities:**

  - `B-FOOD`: sushi
  - `B-SERVICE`: service

---

## Requirements

The application requires the following dependencies:

- Python 3.8+
- PyTorch
- Transformers (Hugging Face)
- Datasets
- Evaluate
- NumPy
- Scikit-learn
- **Gradio**
- Matplotlib

Install all dependencies in your Terminal using:

```bash
pip install -r requirements.txt
```
