# week2-ID3-algo
# Decision Tree Classifier with Streamlit

This repository contains an implementation of a Decision Tree Classifier using Streamlit for interactive visualization.

## Algorithm

A Decision Tree is a non-parametric supervised learning method used for classification and regression. The goal is to create a model that predicts the value of a target variable by learning simple decision rules inferred from the data features.

### Key Components:
1. **Nodes**: Internal nodes represent a feature and a threshold, and leaf nodes represent a predicted class.
2. **Splitting**: The dataset is split into subsets based on the feature that results in the most homogeneous subgroups.
3. **Gini Impurity**: A measure of how often a randomly chosen element would be incorrectly labeled if it was randomly labeled according to the distribution of labels in the subset.

### Gini Impurity Calculation:
\[
Gini = 1 - \sum_{i=1}^{n} p_i^2
\]
where \( p_i \) is the probability of an element being classified into a particular class.

## Code Overview

### `Node` Class
Represents a single node in the decision tree. Each node stores information about the feature index, threshold, left child, right child, and predicted value if it's a leaf node.

### `DecisionTree` Class
Implements the decision tree algorithm with methods to fit the model to data, find the best split, calculate Gini impurity, make predictions, and visualize the tree.

### Streamlit Application
- **File Upload**: Users can upload a CSV file containing the dataset.
- **Feature Sliders**: Users can input sample features to classify using sliders.
- **Tree Visualization**: The structure of the decision tree is displayed.

## Running the Application

1. **Install the Required Packages:**
   Ensure you have the necessary packages installed by running:
   ```bash
   pip install -r requirements.txt
