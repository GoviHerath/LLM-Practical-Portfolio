import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.svm import SVC
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score
import string

# 1. Load the dataset (Using Amazon reviews from UCI Sentiment Labelled Sentences)
url = "https://raw.githubusercontent.com/javedsha/text-classification/master/Sentiment%20Labelled%20Sentences/amazon_cells_labelled.txt"
df = pd.read_csv(url, sep='\t', header=None, names=['text', 'label'])

# 2. Text Preprocessing
def preprocess_text(text):
    text = text.lower() # Convert to lowercase
    text = "".join([char for char in text if char not in string.punctuation]) # Remove punctuation
    text = " ".join(text.split()) # Remove extra whitespace
    return text

df['clean_text'] = df['text'].apply(preprocess_text)

# 4. Split the dataset
X_train, X_test, y_train, y_test = train_test_split(df['clean_text'], df['label'], test_size=0.2, random_state=42)

# 5. Create BOW representation
vectorizer = CountVectorizer()
X_train_bow = vectorizer.fit_transform(X_train)
X_test_bow = vectorizer.transform(X_test)

# 6. Train a ML model (SVM)
model = SVC(kernel='linear')
model.fit(X_train_bow, y_train)

# 7. Evaluate the model
y_pred = model.predict(X_test_bow)
print("--- Model Evaluation ---")
print("Accuracy:", accuracy_score(y_test, y_pred))
print("Precision:", precision_score(y_test, y_pred))
print("Recall:", recall_score(y_test, y_pred))
print("F1 Score:", f1_score(y_test, y_pred))

# 8. Test with a new sentence
new_sentence = ["The battery life is amazing and I love this phone!"]
new_sentence_clean = [preprocess_text(new_sentence[0])]
new_sentence_bow = vectorizer.transform(new_sentence_clean)
prediction = model.predict(new_sentence_bow)
print("\n--- Testing New Sentence ---")
print("Sentence:", new_sentence[0])
print("Prediction (1=Positive, 0=Negative):", prediction[0])
