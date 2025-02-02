# Credit Card Fraud Detection using Machine Learning

## Overview
Credit card fraud poses significant challenges to financial institutions due to the rise of digital transactions and evolving fraudulent techniques. This project aims to build a robust machine learning-based fraud detection system that accurately identifies fraudulent transactions while addressing key challenges like class imbalance, feature selection, and model evaluation.

## Table of Contents
Project Summary
Dataset Overview
Methodology
Data Preprocessing
Feature Engineering
Balancing Data (SMOTE)
Machine Learning Models
Evaluation Metrics
Results & Insights
Conclusion
Future Scope
References

## Project Summary
Goal: Develop a fraud detection model that minimizes false negatives while maintaining high recall.
Techniques Used: Data preprocessing, feature selection (ANOVA & Chi-Square tests), class balancing (SMOTE), and machine learning models.
Best Model: Random Forest with SMOTE, which achieved 0.75 recall, making it the best model for fraud detection.

## Dataset Overview
Source: Kaggle - Credit Card Fraud Dataset
Total Rows: 555,719
Total Features: 22
Fraudulent Transactions: Only 0.39% of the total dataset, requiring handling for class imbalance.
Key Features:
Numerical Features: amt (Transaction Amount), trans_date_trans_time (Transaction Timestamp)
Categorical Features: merchant, category, gender
Geographical Features: city, state, zip, latitude, longitude
Target Variable: is_fraud (1 = Fraud, 0 = Not Fraud)

## Methodology

### Data Preprocessing
Removed irrelevant columns (street, dob, city) that contributed little predictive value.
Handled missing values using median imputation.
Normalized numerical features (amt) using Robust Scaler to handle outliers.
Encoded categorical variables using one-hot encoding and label encoding.
### Feature Engineering
Extracted new features:
transact_hour: Hour of transaction
transaction_weekday: Day of the week
age: Derived from dob
Geographic regions: Grouped states into broader regions (Midwest, Northeast, etc.)
Behavioral Features:
Transaction frequency
Average transaction amount per user
Applied ANOVA Test (for numerical variables) and Chi-Square Test (for categorical variables) to retain only significant predictors.

## Balancing Data (SMOTE)
The dataset had a class imbalance problem with only 0.39% fraud cases.
Synthetic Minority Oversampling Technique (SMOTE) was applied.
Different sampling strategies (30%, 50%, 70%, 100%) were tested, and 70% oversampling was found optimal.

## Machine Learning Models
Two models were implemented and evaluated:

### Logistic Regression

Good for interpretability.
Struggled with class imbalance.
SMOTE improved recall but increased false positives.

### Random Forest

Handled non-linear relationships well.
Identified key fraud predictors.
Best performing model with SMOTE, achieving 0.75 recall.

## Evaluation Metrics
Accuracy
Precision
Recall (Key metric for fraud detection)
F1-Score
AUC-ROC Curve

## Results & Insights
Random Forest with SMOTE achieved the best recall (0.75), which is crucial for fraud detection.
Logistic Regression struggled with imbalanced data but improved recall with SMOTE.
Feature importance analysis identified amt, transact_hour, and transaction_weekday as key fraud indicators.
Fraud patterns:
Higher fraud rates during specific hours of the day.
Certain transaction categories (e.g., online shopping) had higher fraud risks.

## Conclusion
Random Forest with SMOTE is the best model for fraud detection as it effectively identifies fraudulent transactions with high recall.
The study highlights the importance of class balancing, feature selection, and behavioral insights in fraud detection.

## Future Scope
To further improve fraud detection, the following enhancements can be explored:

Deep Learning: Implementing LSTMs or Autoencoders for anomaly detection.
Hybrid Models: Combining Random Forest with XGBoost for better precision-recall tradeoff.
Anomaly Detection: Using One-Class SVM or Isolation Forest for unsupervised fraud detection.
Real-time Detection: Implementing the model with Apache Kafka or Spark Streaming.
Continuous Learning: Periodic model retraining with new transaction data.

## References
Credit Card Fraud Report - Security.org
Kaggle Fraud Detection Dataset
Various machine learning papers on fraud detection.

