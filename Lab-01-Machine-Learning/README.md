# Lab 01: Sentiment Analysis Using Traditional Machine Learning

**Module:** PUSL3205 – Large Language Models and Generative AI  
**Notebook:** [Lab_Sheet_1.ipynb](Lab_Sheet_1.ipynb)
**Dataset Source:** [UCI Machine Learning Repository – Sentiment Labelled Sentences (Dataset 331)](https://archive.ics.uci.edu/dataset/331/sentiment%2Blabelled%2Bsentences)

---

## Laboratory Session
- **Module Code & Title:** PUSL3205 – Large Language Models and Generative AI
- **Laboratory Session:** Lab 01 – Sentiment Analysis Using Traditional Machine Learning
- **Environment:** Google Colab / Jupyter Notebook (`Lab_Sheet_1.ipynb`)

---

## Objective
To practise foundational Natural Language Processing (NLP) tasks—including text preprocessing, Bag-of-Words feature representation, and training and evaluating traditional machine learning classifiers (Logistic Regression and Linear SVM) on labelled sentiment sentences—to establish a baseline before working with transformer models and large language models.

---

## Tasks and Implementation

| Step | Task | Implementation Summary |
| :--- | :--- | :--- |
| 1 | Load Dataset | Downloaded and extracted the UCI Sentiment Labelled Sentences archive (`amazon`, `imdb`, `yelp`) into a `pandas` DataFrame. |
| 2 | Text Preprocessing | Lowercased text, removed non-alphabetic characters/punctuation, collapsed whitespace into `clean_text`, and removed empty rows. |
| 3 | Exploratory Data Analysis | Checked class counts, source breakdown, and top words by sentiment class. |
| 4 | Train/Test Split | Split the cleaned data into training and test sets using an 80/20 stratified split (`random_state=42`). |
| 5 | Bag-of-Words Features | Built token-count vectors using `CountVectorizer` (`4536` vocabulary size), fitting on training data and transforming test data. |
| 6 | Model Training | Trained **Logistic Regression** and **Linear SVM** (`LinearSVC`) models on the training matrix. |
| 7 | Model Evaluation | Evaluated Accuracy, Precision, Recall, and F1 Score on the test set and generated confusion matrices and metric charts. |
| 8 | New Sentence Testing | Tested unseen sentences with both trained models to compare predicted sentiment labels. |

---

## Results and Evidence

### Model Performance (Test Set)
| Model | Accuracy | Precision | Recall | F1 Score |
| :--- | :--- | :--- | :--- | :--- |
| Logistic Regression | 0.8255 | 0.8267 | 0.8267 | 0.8267 |
| Linear SVM | 0.8091 | 0.7986 | 0.8303 | 0.8142 |

### 1. Class Distribution
![Class Distribution](class_distribution%20(1).png)

### 2. Reviews by Source and Sentiment
![Source Distribution](source_distribution.png)

### 3. Top Words by Class
![Top Words by Class](top_words_by_class.png)

### 4. Confusion Matrices
![Confusion Matrices](confusion_matrices.png)

### 5. Model Performance Comparison
![Model Metrics](model_metrics.png)

---

## Observations
- On this test split (`4536` vocabulary features), **Logistic Regression** achieved higher accuracy (`0.8255`), precision (`0.8267`), and F1 score (`0.8267`) than **Linear SVM** (`0.8091` accuracy, `0.7986` precision, `0.8142` F1 score), while **Linear SVM** achieved slightly higher recall (`0.8303` vs `0.8267`).
- The dataset combines reviews from Amazon, IMDB, and Yelp with balanced sentiment classes.
- Bag-of-Words counts capture common sentiment words well, while lacking full word order and deeper context for complex phrasing, negation, or sarcasm.

---

## Learning Outcomes
- Implemented a traditional NLP sentiment classification pipeline in Python using `pandas`, `matplotlib`, `seaborn`, and `scikit-learn`.
- Practised text cleaning, stratified train/test splitting, and `CountVectorizer` feature extraction without data leakage.
- Established a baseline workflow to compare against transformer models and large language models in later labs.
