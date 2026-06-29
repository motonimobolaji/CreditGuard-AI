# Data Dictionary

## Overview

I created this data dictionary to serve as a reference for every feature used throughout the CreditGuard AI project. By documenting each variable and its purpose, I can maintain a consistent understanding of the dataset as I progress through data cleaning, exploratory data analysis, feature engineering, machine learning, and dashboard development. This document will also make it easier for future team members or stakeholders to understand the dataset without needing to inspect the raw data directly.

---

## Dataset Information

| Column              | Data Type | Description                                                                  | Example     | Expected Values                         |
|---------------------|-----------|------------------------------------------------------------------------------|-------------|-----------------------------------------|
| transaction_id      | Integer   | Unique identifier assigned to each transaction.                              | 100235      | Unique positive integer                 |
| amount              | Float     | Dollar amount of the transaction.                                            | 249.99      | Greater than or equal to 0              |
| transaction_hour    | Integer   | Hour of the day the transaction occurred (24-hour clock).                    | 14          | 0–23                                    |
| merchant_category   | Object    | Type of merchant where the transaction occurred.                             | Electronics | Electronics, Grocery, Gas, Travel, etc. |
| foreign_transaction | Binary    | Indicates whether the purchase occurred outside the customer's home country. | 1           | 0 = No, 1 = Yes                         |
| location_mismatch   | Binary    | Indicates whether the billing address and transaction location differ.       | 0           | 0 = Match, 1 = Mismatch                 |
| device_trust_score  | Integer   | Trust score assigned to the customer's device.                               | 82          | 0–100                                   |
| velocity_last_24h   | Integer   | Number of transactions made within the previous 24 hours.                    | 6           | Greater than or equal to 0              |
| cardholder_age      | Integer   | Age of the cardholder.                                                       | 34          | Typically 18–100                        |
| fraud               | Binary    | Indicates whether the transaction is fraudulent. (Target Variable).          | 1           | 0 = Legitimate, 1 = Fraud               |

---

## Feature Categories

I categorized the dataset into different feature types because each type requires a different approach during data preparation and machine learning. The transaction_id serves only as a unique identifier and will not be used for model training. Numerical features such as amount, transaction_hour, device_trust_score, velocity_last_24h, and cardholder_age contain measurable values that I can analyze statistically and use directly in predictive models. The merchant_category feature is categorical and will require encoding before model training. Binary features (foreign_transaction and location_mismatch) represent yes-or-no conditions and can typically be used directly after validation. Finally, the fraud column is my target variable, representing the outcome that I want my machine learning model to predict.

| Category        | Features                                                      |
|-----------------|---------------------------------------------------------------|
| Identifier      | transaction_id                                                |
| Numerical       | amount, device_trust_score, velocity_last_24h, cardholder_age |
| Time-Based      | transaction_hour                                              |
| Categorical     | merchant_category                                             |
| Binary          | foreign_transaction, location_mismatch                        |
| Target Variable | fraud                                                         |

---


## Data Quality Expectations

Before beginning any analysis or model development, I will evaluate the dataset for missing values, duplicate records, incorrect data types, invalid numerical ranges, inconsistent categorical values, and class imbalance. Performing these validation checks will help ensure that my analysis is based on accurate, complete, and reliable data. I've heard that high quality data is essential for building trustworthy machine learning models and producing meaningful business insights.


## Data Cleaning Plan

Before performing exploratory data analysis or training any machine learning models, I will complete a thorough data cleaning process. I will identify and remove duplicate records, inspect the dataset for missing values, verify that every feature has the correct data type, validate that numerical values fall within realistic ranges, and standardize any inconsistent categorical values. Once the dataset has been cleaned, I will be confident that it is suitable for feature engineering, predictive modeling, and visualization throughout the remainder of the CreditGuard AI project.


## Reflection

Completing this data dictionary gave me a clear understanding of the dataset and how each feature contributes to the fraud detection problem. This document will serve as a reference throughout the remainder of the project.

## Next Steps

My next step is to identify the key fraud indicators within the dataset and evaluate how each feature contributes to fraud risk. This analysis will guide my exploratory data analysis and feature engineering decisions.


