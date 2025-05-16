# Credit Card Fraud Detection

**Author:** Lokesh Saroj  
**Supervisors:** Prof. Sumona Mondal, Naveen Reddy  
**Department:** Data Science  
**University:** Clarkson University  

## Table of Contents
1. [Abstract](#abstract)
2. [Introduction](#introduction)
3. [Objective](#objective)
4. [Dataset Overview](#dataset-overview)
5. [Methods](#methods)
   - [Data Preprocessing](#data-preprocessing)
   - [Feature Engineering](#feature-engineering)
   - [ANOVA Test for Numerical Variables](#anova-test-for-numerical-variables)
   - [Chi-Square Test on Categorical Variables](#chi-square-test-on-categorical-variables)
   - [Addressing Class Imbalance](#addressing-class-imbalance)
   - [Model Selection](#model-selection)
6. [Model Evaluation](#model-evaluation)
   - [Logistic Regression](#logistic-regression)
   - [Random Forest](#random-forest)
7. [Conclusion](#conclusion)
8. [Future Scope](#future-scope)
9. [Acknowledgments](#acknowledgments)
10. [References](#references)

## Abstract

Credit card fraud is an ongoing challenge in financial institutions, exacerbated by the increased reliance on digital transactions and constantly evolving fraudulent techniques. This project focuses on developing a machine learning-based system to detect fraudulent transactions accurately while addressing challenges such as class imbalance and feature optimization. Using the Credit Card Fraud Detection Dataset, which includes only 0.39% fraudulent transactions, the study emphasizes data preprocessing, feature engineering, and advanced modeling techniques. The goal is to build a robust system that can effectively identify fraud, minimize false positives, and improve detection accuracy.

## Introduction

In the modern digital era, the increasing use of credit cards has led to a rise in fraud activities. This project applies machine learning to detect fraudulent credit card transactions, leveraging historical transaction data to identify anomalous patterns. Traditional fraud detection systems often fall short in dealing with these evolving fraud schemes. Thus, this project seeks to build an effective system using models such as Logistic Regression and Random Forest, comparing their performance in terms of precision, recall, F1-score, and AUC-ROC.

## Objective

The main objectives of this project are:
1. **Accurate Fraud Detection:** Minimizing false negatives and ensuring high precision and recall for fraud detection.
2. **Handling Class Imbalance:** Using techniques like SMOTE to balance the dataset and prevent model bias.
3. **Feature Engineering:** Enhancing the dataset with meaningful features such as transaction patterns, demographic information, and transaction locations.
4. **Model Evaluation and Selection:** Comparing various models to choose the best one for fraud detection.

## Dataset Overview

The dataset for this project is sourced from Kaggle and contains 555,719 rows and 22 columns, with only 0.39% of the transactions labeled as fraudulent. The dataset includes transactional data such as transaction amount, merchant details, and customer demographics, which serve as the basis for building a fraud detection model.
![image](https://github.com/user-attachments/assets/a96824eb-e3f2-4474-97fa-487b0c702f91)


## Methods

### Data Preprocessing
- **Cleaning:** Irrelevant columns (like street and city) were removed after feature engineering.
- **Normalization:** Transaction amounts were normalized using robust scaling to mitigate outliers.
- **Encoding:** Categorical variables (e.g., transaction categories, gender) were encoded using one-hot and label encoding.

### Feature Engineering
- **Temporal Features:** Extracted transaction hour and weekday from the transaction date and time.
- **Geographic Features:** Analyzed customer and merchant geographic data to identify location-based fraud patterns.
- **Demographic Features:** Categorized customer age into age bands and analyzed gender data.

### Statistical Testing
- **ANOVA Test for Numerical Variables:** Identified significant predictors of fraud such as transaction amount and transaction hour.
  #### ANOVA Results
| Feature        | F-Statistic     | p-Value        |
|----------------|----------------|----------------|
| amt            | 5430.460084    | 0.000000e+00   |
| transact_hour  | 75.894770      | 2.999880e-18   |
| merch_lat      | 18.774903      | 1.471158e-05   |
| merch_long     | 0.624331       | 4.294427e-01   |
| distance_km    | 0.030178       | 8.620877e-01   |

- **Chi-Square Test for Categorical Variables:** Evaluated the relationship between categorical variables (e.g., transaction category) and fraud detection.
#### Chi-Squared Test Results
| Feature                  | Chi² Score     | p-Value         |
|--------------------------|----------------|------------------|
| category_shopping_net    | 739.826033     | 6.540460e-163    |
| category_grocery_pos     | 393.983415     | 1.123813e-87     |
| category_misc_net        | 247.462989     | 9.279874e-56     |
| category_home            | 90.612221      | 1.747775e-21     |
| transaction_weekday      | 84.837022      | 3.240005e-20     |
| category_kids_pets       | 80.736188      | 2.579547e-19     |
| category_food_dining     | 63.051268      | 2.013956e-15     |
| category_health_fitness  | 56.878100      | 4.636807e-14     |
| category_personal_care   | 44.247655      | 2.893508e-11     |
| category_misc_pos        | 28.406330      | 9.834324e-08     |
| category_gas_transport   | 18.651259      | 1.569436e-05     |
| category_grocery_net     | 15.460196      | 8.426113e-05     |
| category_travel          | 11.150035      | 8.403010e-04     |
| Region                   | 8.086196       | 4.460368e-03     |
| age_group                | 6.731766       | 9.471077e-03     |
| category_shopping_pos    | 2.262802       | 1.325141e-01     |
| gender_M                 | 0.170375       | 6.797788e-01     |

### Addressing Class Imbalance
- **SMOTE (Synthetic Minority Oversampling Technique):** Generated synthetic samples to balance the dataset, testing different oversampling levels and optimizing the model’s recall and precision balance.
![image](https://github.com/user-attachments/assets/791f202c-d06d-4fd4-862c-d54fd4a93ffa)


### Model Selection
Two models were evaluated:
- **Logistic Regression:** Used as a baseline, effective for linear relationships but struggled with class imbalance.
- **Random Forest:** An ensemble model that performed better with SMOTE, providing higher recall and feature importance insights.

## Model Evaluation

![image](https://github.com/user-attachments/assets/e414031e-1c90-441b-970d-3e410e476446)

### Logistic Regression
- **Without SMOTE:** High precision, but low recall for fraud detection.
- **With SMOTE:** Improved recall at the cost of slightly reduced precision.
  ![image](https://github.com/user-attachments/assets/7e4cfd00-8f08-4b04-bc59-5ba9a3ac0666)


### Random Forest
- **Without SMOTE:** Better precision but lower recall due to class imbalance.
- **With SMOTE:** Significant improvement in recall, offering a balanced performance with high F1-scores.
  ![image](https://github.com/user-attachments/assets/87cd8fbb-6823-441b-9e6a-b0bcd736dba9)

## Conclusion

The project demonstrated the effectiveness of using machine learning, specifically Random Forest with SMOTE, to detect credit card fraud. Random Forest outperformed Logistic Regression, achieving higher recall and identifying significant fraud predictors. This approach has shown promise in minimizing false negatives and improving the detection of fraudulent transactions. However, the system can be further improved through advanced techniques such as deep learning, real-time fraud detection, and continuous learning. These improvements will enhance scalability, accuracy, and adaptability, making it a more robust solution for fraud prevention.

## Future Scope

Potential future improvements include:
- **Advanced Models:** Explore algorithms like XGBoost and Neural Networks to capture more complex fraud patterns, potentially leading to better fraud detection performance.
- **Anomaly Detection:** Implement unsupervised models like Autoencoders or One-Class SVM to identify fraudulent patterns without relying on labeled data, which is particularly useful for evolving fraud techniques.
- **Real-Time Detection:** Develop a real-time fraud detection system using streaming tools like Apache Kafka or Spark Streaming to monitor transactions as they occur, ensuring immediate identification of fraudulent activities.
- **Continuous Learning:** Integrate continuous learning systems to adapt to new fraud patterns over time, retraining models with fresh transaction data to maintain high detection accuracy.
- **Explainability:** Use tools like SHAP or LIME to enhance model interpretability, making it easier to explain fraud predictions to stakeholders and improve decision-making.

## Acknowledgments

I am sincerely grateful to **Prof. Sumona Mondal** and **Naveen Reddy** for their invaluable guidance and support throughout this project. Their mentorship has been pivotal in my academic journey, providing me with the insights and encouragement needed to successfully complete this work. Their constructive feedback and expertise have greatly enriched my understanding and development throughout the course of this project.

## References

- Dighe, D., Patil, S., & Kokate, S. (2018). Detection of credit card fraud transactions using machine learning algorithms and Neural Networks. *ICCUBEA*.
- Gupta, A., Lohani, M. C., & Manchanda, M. (2021). Financial fraud detection using Naive Bayes algorithm in highly imbalanced datasets. *Journal of Discrete Mathematical Sciences and Cryptography*, 24(5), 1559–1572.

