# Lab 01: Sentiment Analysis Using Traditional Machine Learning

## Laboratory Session
- **Module:** PUSL3205 – Large Language Models and Generative AI[cite: 4, 5]
- **Lab:** Lab 01 – Sentiment Analysis Using Traditional Machine Learning[cite: 5]
- **Notebook:** `Lab_Sheet_1.ipynb`[cite: 32]

## Objective
To practice basic Natural Language Processing (NLP) tasks—including text preprocessing, Bag-of-Words representation, and training/evaluating traditional machine learning classifiers (Logistic Regression and Linear SVM)—on labelled sentiment sentences, establishing a baseline before moving to contextual transformer and LLM approaches[cite: 5].

## Tasks and Implementation
1. **Loaded Dataset:** Loaded the UCI Sentiment Labelled Sentences dataset (Amazon, IMDB, and Yelp reviews) in Python using `pandas`[cite: 5].
2. **Text Preprocessing:** Converted text to lowercase, removed non-alphabetic characters/punctuation, collapsed extra whitespace, and removed any rows that became empty after cleaning[cite: 5].
3. **Exploratory Data Analysis (EDA):** Checked class balance between negative (`0`) and positive (`1`) sentiment labels[cite: 5].
4. **Train/Test Split:** Split the cleaned dataset into training and testing sets (80/20 split, stratified by label)[cite: 5].
5. **Feature Representation:** Converted text into a Bag-of-Words matrix using `CountVectorizer` (fitted on training data to avoid data leakage)[cite: 5].
6. **Model Training & Evaluation:** Trained **Logistic Regression** and **Linear SVM** models and evaluated them using confusion matrices and classification metrics[cite: 5].
7. **Testing on New Sentences:** Tested both trained models on new sample sentences to observe how they classify sentiment[cite: 5].

## Results and Evidence
- **Notebook:** `Lab_Sheet_1.ipynb` contains the full execution and outputs[cite: 32].

### Class Distribution
![Class Distribution](class_distribution.png)[cite: 32]

### Confusion Matrices
![Confusion Matrices](confusion_matrices.png)[cite: 32]

## Observations
- The dataset classes are balanced across positive and negative labels[cite: 5].
- Traditional Bag-of-Words models rely on token counts rather than deeper context or word order, which can limit performance on nuanced phrasing, negation, or sarcasm.
- Loading the dataset via the archived zip file ensured reliable access when a direct file URL returned a 404 error.

## Learning Outcomes
- Gained practical experience building a traditional text classification pipeline in Python (`pandas`, `matplotlib`, `seaborn`, `scikit-learn`)[cite: 5].
- Learned how text cleaning, train/test splitting, and `CountVectorizer` work together for baseline sentiment classification[cite: 5].
- Built a clear baseline for comparing traditional ML models against modern LLMs in later labs[cite: 5].
