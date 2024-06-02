# naive_bayesian_classifier
Sure, here's the README content for your Streamlit application:

---

# Naïve Bayes Document Classifier

This Streamlit application uses a Naïve Bayes classifier to classify documents based on their text content. The application allows you to load a dataset, train the model, and evaluate its performance in terms of accuracy, precision, and recall.

## Table of Contents
- [Naïve Bayes Document Classifier](#naïve-bayes-document-classifier)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Requirements](#requirements)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Dataset](#dataset)
  - [Code Explanation](#code-explanation)
  - [Troubleshooting](#troubleshooting)
  - [License](#license)

## Overview

This application allows you to load a CSV dataset containing text documents and their labels, train a Naïve Bayes classifier, and evaluate the model's performance. The dataset should have two columns: `text` and `label`.

## Requirements

To run this application, you need the following packages installed:

- Python 3.7 or higher
- Streamlit
- pandas
- scikit-learn

## Installation

1. Clone the repository or download the code.
2. Ensure you have Python 3.7 or higher installed.
3. Install the required packages using pip:

    ```bash
    pip install streamlit pandas scikit-learn
    ```

4. Place your dataset file `document.csv` in a directory named `week5` in the same directory as your script.

## Usage

To run the application, navigate to the directory containing the script and the `week5/document.csv` file and execute the following command:

```bash
streamlit run streamlit_app.py
```

This will start the Streamlit application, and you can view it in your web browser.

## Dataset

The dataset used in this application should be a CSV file with two columns:
- `text`: The text of the document.
- `label`: The label or category of the document.

Example of the dataset format:

| text                        | label     |
|-----------------------------|-----------|
| "The movie was fantastic!"  | positive  |
| "I did not like the film."  | negative  |
| "It was an average movie."  | neutral   |

## Code Explanation

1. **Loading the Dataset**: The dataset is loaded from a CSV file using pandas. The function `load_data` is cached to optimize performance.

    ```python
    @st.cache_data
    def load_data():
        data = pd.read_csv('week5/document.csv')
        if data.columns[0] != 'text' or data.columns[1] != 'label':
            data.columns = ['text', 'label']
        return data
    ```

2. **Training and Evaluating the Model**: The data is split into training and testing sets, vectorized, and a Naïve Bayes classifier is trained and evaluated.

    ```python
    def train_and_evaluate(data):
        X_train, X_test, y_train, y_test = train_test_split(data['text'], data['label'], test_size=0.2, random_state=42)
        vectorizer = CountVectorizer()
        X_train_vec = vectorizer.fit_transform(X_train)
        X_test_vec = vectorizer.transform(X_test)

        nb_classifier = MultinomialNB()
        nb_classifier.fit(X_train_vec, y_train)
        y_pred = nb_classifier.predict(X_test_vec)

        accuracy = accuracy_score(y_test, y_pred)
        precision = precision_score(y_test, y_pred, average='weighted')
        recall = recall_score(y_test, y_pred, average='weighted')
        
        return accuracy, precision, recall
    ```

3. **Streamlit Interface**: The Streamlit app provides an interface to load the data, display it, and train and evaluate the model.

    ```python
    st.title('Naïve Bayes Document Classifier')

    data = load_data()

    if st.checkbox('Show raw data'):
        st.write(data)

    if st.button('Train and Evaluate Model'):
        accuracy, precision, recall = train_and_evaluate(data)
        if accuracy is not None and precision is not None and recall is not None:
            st.write(f'**Accuracy:** {accuracy:.2f}')
            st.write(f'**Precision:** {precision:.2f}')
            st.write(f'**Recall:** {recall:.2f}')
    ```

## Troubleshooting

If you encounter any issues, please ensure:
- The `week5/document.csv` file is in the correct directory.
- The dataset contains the required columns: `text` and `label`.
- The required packages are installed.
- You are using the correct version of Python.

