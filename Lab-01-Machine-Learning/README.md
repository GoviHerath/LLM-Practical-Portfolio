# Lab 01: Sentiment Analysis Using Traditional Machine Learning

**Module:** PUSL3205 – Large Language Models and Generative AI  
**Notebook:** [Lab_Sheet_1.ipynb](Lab_Sheet_1.ipynb)[cite: 33]  
**Dataset Source:** [UCI Machine Learning Repository – Sentiment Labelled Sentences (Dataset 331)](https://archive.ics.uci.edu/dataset/331/sentiment%2Blabelled%2Bsentences)[cite: 5]

---

## Laboratory Session
- **Module Code & Title:** PUSL3205 – Large Language Models and Generative AI[cite: 4, 5]
- **Laboratory Session:** Lab 01 – Sentiment Analysis Using Traditional Machine Learning
- **Environment:** Google Colab / Jupyter Notebook (`Lab_Sheet_1.ipynb`)[cite: 31, 33]

---

## Objective
To practise foundational Natural Language Processing (NLP) tasks—including text preprocessing, Bag-of-Words feature representation, and training/evaluating traditional machine learning classifiers (Logistic Regression and Linear SVM) on labelled sentiment text—to establish a baseline before studying transformer architectures and large language models[cite: 4, 5].

---

## Tasks and Implementation

| Step | Task | Implementation Summary |
| :--- | :--- | :--- |
| 1 | Load Dataset | Downloaded the archived dataset zip file from the UCI source, extracted the Amazon, IMDB, and Yelp review files, and merged them into a `pandas` DataFrame. |
| 2 | Text Preprocessing | Lowercased text, removed punctuation and non-letter characters via regular expressions, collapsed extra whitespace into `clean_text`, and dropped rows that became empty after cleaning[cite: 5]. |
| 3 | Exploratory Data Analysis | Checked sentiment class counts, source breakdown (Amazon, IMDB, Yelp), and top frequent words per sentiment class[cite: 5]. |
| 4 | Train/Test Split | Split the cleaned text and labels into training and test sets using an 80/20 stratified split (`random_state=42`)[cite: 5]. |
| 5 | Bag-of-Words Features | Generated token-count feature vectors using `CountVectorizer`, fitting on training data and transforming test data[cite: 5]. |
| 6 | Model Training | Trained **Logistic Regression** (`max_iter=1000`, `random_state=42`) and **Linear SVM** (`LinearSVC`, `random_state=42`) classifiers on the training features[cite: 5]. |
| 7 | Model Evaluation | Computed Accuracy, Precision, Recall, and F1 Score on the test set and visualised confusion matrices and model comparisons[cite: 5, 34]. |
| 8 | New Sentence Testing | Passed unseen test sentences (including negation and tricky phrasing) through the trained models to observe predictions[cite: 5, 17]. |

### Key Preprocessing & Modelling Code
```python
def clean_text(raw):
  if pd.isna(raw):
    return ""
  txt = str(raw).lower()
  txt = re_non_alpha.sub(" ", txt)
  txt = re_multi_space.sub(" ", txt).strip()
  return txt


X_train, X_test, y_train, y_test = train_test_split(
    data["clean_text"],
    data["label"],
    test_size=0.2,
    random_state=42,
    stratify=data["label"],
)

bow = CountVectorizer()
X_train_vec = bow.fit_transform(X_train)
X_test_vec = bow.transform(X_test)
