# WEEK-4_Naive_Bayesian_Algorithm
# Play Tennis Predictor

This repository contains a Streamlit application that uses a Naïve Bayes classifier to predict whether you can play tennis based on weather conditions. The model is trained on a small dataset with weather features such as Outlook, Temperature, Humidity, and Windy.

## Dataset

The dataset used in this project is a small sample containing the following features:
- **Outlook**: Sunny, Overcast, Rainy
- **Temperature**: Hot, Mild, Cool
- **Humidity**: High, Normal
- **Windy**: True, False
- **PlayTennis**: Yes, No (target variable)

### Sample Data
| Outlook  | Temperature | Humidity | Windy | PlayTennis |
|----------|-------------|----------|-------|------------|
| Sunny    | Hot         | High     | False | No         |
| Sunny    | Hot         | High     | True  | No         |
| Overcast | Hot         | High     | False | Yes        |
| Rainy    | Mild        | High     | False | Yes        |
| Rainy    | Cool        | Normal   | False | Yes        |

## Algorithm

The model uses the Naïve Bayes classifier, which is based on Bayes' theorem with the assumption of independence between every pair of features. The classifier is particularly suited for this problem due to its simplicity and effectiveness on small datasets.

## Code Overview

### Data Preprocessing

The categorical features are converted to numerical codes to be used by the Naïve Bayes classifier:
- **Outlook**: Sunny = 0, Overcast = 1, Rainy = 2
- **Temperature**: Hot = 0, Mild = 1, Cool = 2
- **Humidity**: High = 0, Normal = 1
- **Windy**: False = 0, True = 1

### Training the Model

The data is split into training and test sets. The model is then trained using the training set.

### Streamlit Application

The Streamlit app provides an interface for users to input weather conditions and get a prediction on whether they can play tennis.

## Running the Application

1. **Install the Required Packages:**
   Ensure you have the necessary packages installed by running:
   ```bash
   pip install -r requirements.txt
