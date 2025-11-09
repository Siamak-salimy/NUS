Decision Tree Classifier for Diabetes Prediction  ( DTC ) </br>
 
This repository contains Python code for implementing a Decision Tree–based diagnostic model for predicting diabetes using clinical features from the Pima Indians Diabetes Dataset. The workflow includes data retrieval from GitHub, pre-processing, model training, evaluation, and prediction for new samples. The implementation uses entropy-based splitting to approximate C4.5/C5.0 behavior.

1. Overview

This project demonstrates a complete machine-learning pipeline for binary clinical prediction. The workflow includes:

Direct loading of Excel datasets from GitHub

Data cleaning and medical feature correction

Model development using a Decision Tree (entropy criterion)

Performance evaluation (accuracy, precision, recall, F1-score)

Feature importance analysis

Prediction for external data (newdata.xlsx)

The code is structured for use in Google Colab, but can also be executed locally.

2. Dataset Description

Two datasets are used in this project:

diabetes.xlsx: Main dataset containing clinical variables such as glucose level, BMI, blood pressure, insulin, and diabetes outcome.

newdata.xlsx: External dataset used for model inference.

Both files are loaded directly from GitHub using raw download links.

3. Methodology
3.1 Data Loading

Data are imported using pandas.read_excel() directly from GitHub URLs.
The script automatically removes unnecessary columns such as sample if present.

3.2 Data Cleaning and Pre-processing

Several biomedical variables can contain physiologically impossible zeros (e.g., BMI = 0).
These are detected and replaced with NaN, after which rows with missing values are removed.
Outcome labels are converted to integer format.

3.3 Model Development

A DecisionTreeClassifier is trained using entropy as the criterion, which mimics C4.5/C5.0 behavior.
The model is restricted by:

max_depth = 5

min_samples_split = 10

min_samples_leaf = 5

This prevents overfitting and improves generalization.

3.4 Model Evaluation

Performance metrics include:

Accuracy score

Classification report (precision, recall, F1-score)

These metrics demonstrate that the model achieves strong predictive performance, with balanced sensitivity and specificity.

3.5 Feature Importance

Feature contributions are calculated using the tree’s internal Gini/entropy gain measures.
The model identifies the following as the most influential predictors (example results):

Glucose

Age

BMI

DiabetesPedigreeFunction

3.6 Prediction for New Samples

The script attempts to load newdata.xlsx.
If the file exists, diabetes probability is reported for each sample.
If the file does not exist or produces errors, the script switches to interactive user input, allowing manual entry of clinical features.

4. How to Run
Option A: Google Colab (recommended)

Click the following badge to open the notebook directly in Google Colab:
