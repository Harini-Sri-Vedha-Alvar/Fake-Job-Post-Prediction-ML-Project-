# Fake Job Post Detection using NLP and Machine Learning

An NLP-based machine learning project that analyzes job-posting text and predicts whether a posting is likely legitimate or potentially fraudulent.

## Project Overview

Fraudulent job advertisements can mislead job seekers and create security and financial risks.

This project applies Natural Language Processing (NLP) and machine learning techniques to identify patterns in job postings that are associated with fraudulent listings.

The project combines multiple text fields from job postings, cleans the text, converts it into numerical features using TF-IDF, and evaluates multiple machine-learning models.

The final project also includes a reusable saved model pipeline for making predictions on new job-posting text.

## Dataset

The project uses the **Real or Fake? Fake Job Posting Prediction** dataset.

### Dataset Statistics

- 17,880 job postings
- 18 original features
- 17,014 legitimate postings
- 866 fraudulent postings
- No duplicate records were found

The target variable is:

- `0` — Legitimate
- `1` — Fraudulent

### Main Features

The dataset contains structured and text-based job-posting information including:

- Job title
- Location
- Department
- Salary range
- Company profile
- Job description
- Requirements
- Benefits
- Telecommuting
- Company logo availability
- Screening questions
- Employment type
- Required experience
- Required education
- Industry
- Function

## Project Objectives

- Analyze patterns in fraudulent and legitimate job postings
- Explore missing values and dataset structure
- Investigate relationships between job characteristics and fraud
- Apply Natural Language Processing to job-posting text
- Convert text into numerical features using TF-IDF
- Train multiple machine-learning models
- Evaluate model performance using multiple metrics
- Analyze classification errors
- Select a probability threshold without using the final test set
- Save the trained model for future predictions

## Methodology

### 1. Exploratory Data Analysis

The dataset was examined for:

- Dataset dimensions
- Data types
- Missing values
- Duplicate records
- Class distribution
- Categorical feature relationships

The analysis included fraudulent-job rates across characteristics such as:

- Company logo availability
- Screening questions
- Telecommuting
- Employment type
- Required experience

These relationships represent associations observed in the dataset and should not be interpreted as causal effects.

### 2. Text Preparation

The following text fields were combined:

- `title`
- `company_profile`
- `description`
- `requirements`
- `benefits`

The combined text was cleaned by:

- Converting text to lowercase
- Removing URLs
- Removing non-alphabetic characters
- Removing extra whitespace

### 3. Train-Test Split

The data was divided into training and testing sets using a stratified split.

This preserves the proportion of legitimate and fraudulent postings across the two sets.

### 4. TF-IDF Feature Extraction

TF-IDF was used to transform job-posting text into numerical features.

Configuration:

- Maximum 10,000 features
- English stop-word removal
- Unigrams and bigrams
- Minimum document frequency of 2
- Sublinear term-frequency scaling

The TF-IDF vectorizer was fitted only on the training data and then used to transform the test data.

This prevents information from the test set from being used during feature fitting.

### 5. Machine Learning Models

Two classification models were evaluated:

- Logistic Regression
- Random Forest

Class balancing was applied because fraudulent postings represent a minority class in the dataset.

### 6. Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC
- Confusion Matrix
- ROC Curve

### 7. Threshold Analysis

Because fraud detection can involve an imbalance between false positives and false negatives, probability thresholds were analyzed.

The final threshold was selected using out-of-fold predictions from the training data rather than tuning the threshold directly on the final test set.

### 8. Error Analysis

Incorrect predictions were examined to identify false positives and false negatives and to understand where the model may have difficulty distinguishing legitimate and fraudulent job postings.

## Project Pipeline

```text
Raw Job Postings
        ↓
Data Exploration
        ↓
Missing-Value Analysis
        ↓
Text Field Combination
        ↓
Text Cleaning
        ↓
Stratified Train-Test Split
        ↓
TF-IDF Feature Extraction
        ↓
Model Training
        ↓
Model Evaluation
        ↓
Threshold Analysis
        ↓
Error Analysis
        ↓
Model Saving
        ↓
Reusable Prediction
