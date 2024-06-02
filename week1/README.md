# Locally Weighted Regression with Streamlit

This repository contains an implementation of Locally Weighted Regression (LWR) using Streamlit for interactive visualization. 

## Algorithm

Locally Weighted Regression (LWR) is a type of non-parametric regression that performs a weighted linear regression around each query point. The weights are determined by a kernel function, which assigns higher weights to points closer to the query point.

### Key Components:
1. **Kernel Function**: The kernel function used here is the Gaussian kernel:
   \[
   w(i) = \exp\left(-\frac{(x_i - x_0)^2}{2\tau^2}\right)
   \]
   where \( x_0 \) is the query point, \( x_i \) are the training points, and \( \tau \) is the bandwidth parameter that determines the width of the kernel.

2. **Weighted Linear Regression**: For each query point \( x_0 \), we solve the weighted least squares problem:
   \[
   \theta = (X^T W X)^{-1} X^T W y
   \]
   where \( X \) is the design matrix, \( W \) is the diagonal matrix of weights, and \( y \) is the vector of target values.

## Code Overview

### `local_weighted_regression` Function
This function returns a prediction function for LWR given the training data \( X \) and \( y \), and the bandwidth parameter \( \tau \).

### `generate_data` Function
This function generates synthetic data for demonstrating the LWR. It creates a sine wave and adds noise to simulate real-world data.

### `plot_data` Function
This function plots the training data and the fitted LWR curve using Matplotlib and Streamlit.

### `main` Function
This is the entry point of the Streamlit application. It sets up the Streamlit interface, generates the data, and visualizes the LWR fit.

## Running the Application

1. Ensure you have the necessary packages installed. You can do this by running:
   ```bash
   pip install -r requirements.txt

