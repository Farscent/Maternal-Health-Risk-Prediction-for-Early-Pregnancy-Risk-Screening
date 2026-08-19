# Maternal Health Risk Prediction for Early Pregnancy Risk Screening

A machine learning project developed during **BC2406: Business Analytics** at **Nanyang Technological University (NTU)** as part of the **GEM Trailblazer Summer Programme 2026**.

The project explores how routine maternal health information can be used to support **early pregnancy risk screening**, particularly in resource-limited healthcare settings. We developed interpretable machine learning models to classify patients into **low-risk** and **high-risk** groups and help healthcare workers prioritize patients who may require faster review.

## Project Overview

Maternal mortality remains a major global health challenge, particularly in low- and lower-middle-income countries. Our project investigates whether routinely collected maternal health indicators can support faster and more consistent risk prioritization.

The goal was not to create a diagnostic system, but rather an **AI-assisted clinical decision-support prototype** that could complement professional medical judgment.

## Dataset

The dataset contains maternal health records from **Kurigram General Hospital, Bangladesh**.

- **1,205 raw patient records**
- **1,169 records after cleaning**
- **11 predictor variables**
- **2 target classes:** Low Risk and High Risk

### Features

Numerical health indicators:

- Age
- Systolic Blood Pressure
- Diastolic Blood Pressure
- Blood Sugar
- Body Temperature
- Heart Rate
- BMI

Medical history and status indicators:

- Previous Complications
- Pre-existing Diabetes
- Gestational Diabetes
- Mental Health Indicator

## Data Preparation

The preprocessing workflow included:

- Auditing missing values and blank strings
- Removing records with missing target labels
- Standardizing categorical labels
- Removing duplicate records
- Validating physiologically implausible values
- Treating invalid measurements as missing values
- Mean imputation for numerical variables
- Cleaning categorical predictors
- Exploratory Data Analysis
- Correlation and multicollinearity analysis

A **70/30 stratified train-test split** was used to preserve the distribution of high- and low-risk patients.

## Exploratory Data Analysis

Several patterns were observed in the dataset.

High-risk patients tended to show higher values of:

- Blood Sugar
- Blood Pressure
- Heart Rate
- BMI

Some medical-history variables also showed strong relationships with maternal risk classification.

The analysis additionally included:

- Risk-level distributions
- Boxplots of clinical indicators
- Blood sugar vs blood pressure visualizations
- BMI analysis
- Categorical risk comparisons
- Correlation matrix
- Variance Inflation Factor (VIF) analysis

## Machine Learning Models

Two interpretable classification techniques were evaluated.

### Logistic Regression

Logistic Regression was used to estimate the probability of a patient being classified as high risk.

We also experimented with classification thresholds of **0.5** and **0.3**.

Reducing the threshold increased sensitivity toward high-risk patients, illustrating the trade-off between:

- Recall
- Precision
- False positives
- False negatives

This is particularly important in healthcare screening, where missing a high-risk patient can have greater consequences than generating an additional false alarm.

### CART Decision Tree

A Classification and Regression Tree (CART) model was developed and pruned using cross-validation.

Important variables identified by the model included:

- Blood Sugar
- BMI
- Heart Rate
- Systolic Blood Pressure
- Age

The tree structure also provides an interpretable way to understand how different health indicators contribute to the predicted risk category.

## Model Performance

| Model | Accuracy | High-Risk Recall | Precision | Specificity | F1 Score |
|---|---:|---:|---:|---:|---:|
| Logistic Regression (0.3 threshold) | 94.6% | **97.2%** | 90.1% | 92.8% | 93.5% |
| CART | **96.3%** | 95.1% | **95.7%** | **97.1%** | **95.4%** |

The Logistic Regression model using a lower threshold achieved the **highest recall**, while CART achieved stronger overall balance between accuracy, precision, specificity, and F1 score.

For a screening context, this demonstrates an important trade-off between detecting as many high-risk patients as possible and minimizing unnecessary alerts.

## Business & Healthcare Value

The prototype demonstrates how routine maternal information could potentially support:

- Earlier identification of high-risk pregnancies
- Faster patient prioritization
- Better allocation of limited healthcare resources
- More consistent screening processes
- Reduced delays in clinical review

The intended users include:

- Midwives
- Nurses
- Doctors
- Healthcare facilities performing maternal triage

## Tech Stack

- **R**
- `data.table`
- `ggplot2`
- `dplyr`
- `tidyr`
- `rpart`
- `rpart.plot`
- `car`

## Contributors

- **Farhan Adiwidya Pradana**
- **An Meihui**
- **Pan Yirui**
- **Jindal Mrinalini**

## Project Structure

```text
.
├── maternal_risk_model_updated.R
├── dataset.csv
├── BC2406-G2-Deck.pdf
└── README.md

