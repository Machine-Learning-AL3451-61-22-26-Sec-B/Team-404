# week 6
Certainly! Below is the README content for your Streamlit application that performs Bayesian Inference on COVID-19 data.

---

# COVID-19 Bayesian Inference

This Streamlit application uses a Bayesian Network to perform inference on a dataset containing COVID-19 statistics. It allows you to load a dataset, fit a Bayesian model, and perform queries based on the model to predict the likelihood of different outcomes.

## Table of Contents
- [Overview](#overview)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Dataset](#dataset)
- [Code Explanation](#code-explanation)
- [Troubleshooting](#troubleshooting)
- [License](#license)

## Overview

This application fits a Bayesian Network to a dataset of COVID-19 statistics. It then allows you to perform inference queries to predict the likelihood of different outcomes such as total confirmed cases, deaths, and recoveries based on new cases, new deaths, and new recoveries.

## Requirements

To run this application, you need the following packages installed:

- Python 3.7 or higher
- Streamlit
- pandas
- pgmpy

## Installation

1. Clone the repository or download the code.
2. Ensure you have Python 3.7 or higher installed.
3. Install the required packages using pip:

    ```bash
    pip install streamlit pandas pgmpy
    ```

4. Place your dataset file `corona.csv` in a directory named `week6` in the same directory as your script.

## Usage

To run the application, navigate to the directory containing the script and the `week6/corona.csv` file and execute the following command:

```bash
streamlit run streamlit_app.py
```

This will start the Streamlit application, and you can view it in your web browser.

## Dataset

The dataset used in this application should be a CSV file containing COVID-19 statistics. Ensure that the dataset has the following columns:
- `New cases`
- `Total Confirmed cases`
- `New deaths`
- `Death`
- `New recovered`
- `Cured/Discharged/Migrated`

Example of the dataset format:

| New cases | Total Confirmed cases | New deaths | Death | New recovered | Cured/Discharged/Migrated |
|-----------|-----------------------|------------|-------|---------------|---------------------------|
| 10        | 100                   | 1          | 10    | 5             | 50                        |
| 20        | 200                   | 2          | 20    | 10            | 100                       |
| ...       | ...                   | ...        | ...   | ...           | ...                       |

## Code Explanation

1. **Loading the Dataset**: The dataset is loaded from a CSV file using pandas. The first few rows of the dataset are displayed to ensure it is loaded correctly.

    ```python
    data_path = 'corona.csv'  # Adjust the path if necessary
    data = pd.read_csv('week6/corona.csv')
    st.write(data.head())
    ```

2. **Defining the Bayesian Model**: A simplified Bayesian Model is defined using the pgmpy library. The model structure is specified by adding edges between the nodes.

    ```python
    model = BayesianModel([
        ('New cases', 'Total Confirmed cases'),
        ('New deaths', 'Death'),
        ('New recovered', 'Cured/Discharged/Migrated')
    ])
    ```

3. **Fitting the Model**: The model is fitted to a subset of the data using Maximum Likelihood Estimation.

    ```python
    model.fit(data_subset, estimator=MaximumLikelihoodEstimator)
    ```

4. **Performing Inference**: Variable elimination is used to perform inference on the fitted model. Evidence values are provided, and the model predicts the likelihood of different outcomes.

    ```python
    infer = VariableElimination(model)
    q = infer.query(variables=['Total Confirmed cases', 'Death', 'Cured/Discharged/Migrated'], evidence={
        'New cases': new_cases,
        'New deaths': new_deaths,
        'New recovered': new_recovered
    })
    ```

5. **Displaying Results**: The results of the inference are displayed in a tabular format.

    ```python
    results_df = pd.DataFrame(results, columns=columns)
    st.write(results_df)
    ```

## Troubleshooting

If you encounter any issues, please ensure:
- The `week6/corona.csv` file is in the correct directory.
- The dataset contains the required columns.
- The required packages are installed.
- You are using the correct version of Python.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.

---

This README should provide a comprehensive guide to understanding, installing, and running your Streamlit application. Adjust the content as needed to better fit your specific project details.
