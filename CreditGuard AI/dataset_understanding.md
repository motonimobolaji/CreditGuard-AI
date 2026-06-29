#Dataset Understanding Report

This report will explain what each column in the data set means and how it could contribute to fraud detection

-Total Records: 10,000



#transaction_id
##Data Type: 
-int64  
##Business Meaning:
-Unique identifier for each transaction
##Why It Matters: 
-The transaction_id is not useful for predicting fraud, it just serves as the unique identifier for every transaction in the dataset. It allows each transaction to be tracked, referenced, and linked across databases, reports, dashboards, and fraud investigations.
##Possible Data Quality Issues:
-Duplicate transaction IDs
-Missing transaction IDs
-Incorrect format
## Possible Feature Engineering: Use as database primary key, 
-Use for transaction tracking and reporting


#amount
##Data Type: 
-float64
##Business Meaning: 
-Transaction amount
##Why It Matters: 
-The amount is one of the strongest indicators of potential fraud. Unusually large purchases may be suspicious, especially when combined with other risk factors such as foreign transactions, low device trust, or high transaction velocity.
##Possible Data Quality Issues:
-Missing values
-Negative amounts
-Zero-dollar transactions
-Extreme outliers
-Incorrect currency format
##Possible Feature Engineering:
-Large Transaction Flag
-Amount Categories (Small, Medium, Large)
-Log Transformation
-Amount Percentile
-Standardized Amount


#transaction_hour
##Data Type:
-int64
##Business Meaning: 
-Hour of transaction (0–23)
##Why It Matters: 
-The hour at which a transaction occurs can reveal behavioral patterns associated with fraud. Fraudulent transactions often occur during late-night or early-morning hours when customers are less likely to notice unauthorized purchases. Time-based patterns can improve the model's ability to identify suspicious activity.
##Possible Data Quality Issues:
-Missing values
-Invalid hours (less than 0 or greater than 23)
-Incorrect time zone conversions
##Possible Feature Engineering:
-Late Night Transaction Flag
-Morning/Afternoon/Evening Categories
-Business Hours Indicator
-Weekend vs Weekday (if date available)
-Peak Fraud Hours


#merchant_category
##Data Type: 
-object
##Business Meaning:
-Type of merchant
##Why It Matters: 
-Certain merchant categories experience higher fraud rates than others. For example, online electronics retailers or digital services may be targeted more frequently than grocery stores. Merchant categories provide valuable context about where fraudulent activity is most likely to occur.
##Possible Data Quality Issues:
-Missing categories
-Misspelled category names
-Duplicate categories with different spellings
-Inconsistent capitalization
##Possible Feature Engineering:
-One-Hot Encoding
-Merchant Risk Score
-High-Risk Merchant Flag
-Frequency Encoding


#foreign_transaction
##Data Type: 
-int64
##Business Meaning: 
-Indicates if transaction is international (0/1)
##Why It Matters: 
-International transactions generally carry a higher fraud risk because stolen credit cards are often used outside the customer's home country. While many foreign purchases are legitimate, this feature becomes particularly valuable when combined with additional risk indicators.
##Possible Data Quality Issues:
-Missing values
-Incorrect binary values
-Yes/No instead of 0/1
##Possible Feature Engineering:
-Binary Encoding
-Foreign Risk Score
-Combined Foreign + Location Mismatch Feature
-International Transaction Flag


#location_mismatch
##Data Type: 
-int64
##Business Meaning: 
-Billing vs transaction location mismatch (0/1)
##Why It Matters: 
-A mismatch between the billing address and transaction location may indicate unauthorized use of a credit card. Although customers may legitimately travel, this feature is commonly used by fraud detection systems because it often appears in fraudulent transactions.
##Possible Data Quality Issues:
-Missing values
-Incorrect binary values
-GPS or location recording errors
##Possible Feature Engineering:
-Binary Encoding
-Combined Risk Indicator
-Location Risk Score
-Travel Risk Feature


#device_trust_score
##Data Type: 
-int64
##Business Meaning: 
-Trust score of the device (0–100)
##Why It Matters:
-The device trust score measures how reliable or familiar the device is to the financial institution. Transactions originating from unknown or low-trust devices may indicate account compromise or fraudulent behavior. Device reputation is widely used in modern fraud detection systems.
##Possible Data Quality Issues:
-Missing values
-Scores outside the expected range (0–100)
-Incorrect scaling
##Possible Feature Engineering:
-Device Risk Category
-Trusted vs Untrusted Device Flag
-Normalized Trust Score
-Low Trust Indicator


#velocity_last_24h
##Data Type: 
-int64
##Business Meaning:
-Number of transactions in last 24 hours
##Why It Matters:
-Transaction velocity measures how many purchases occurred within the previous 24 hours.High transaction velocity is one of the strongest behavioral indicators of fraud, because fraudsters often make multiple transactions in a short period before a stolen card is blocked.
##Possible Data Quality Issues:
-Missing values
-Negative values
-Unrealistically large transaction counts
##Possible Feature Engineering:
-High Velocity Flag
-Velocity Categories
-Transaction Frequency Score
-Velocity Percentile


#cardholder_age
##Data Type: 
-int64
##Business Meaning:
-Age of the cardholder
##Why It Matters:
-Customer age may influence purchasing behavior and fraud patterns. While age should never be used as the sole indicator of fraud, it can provide useful context when combined with other variables. This feature may help identify behavioral differences across customer segments.
##Possible Data Quality Issues:
-Missing values
-Negative ages
-Unrealistic ages (e.g., under 18 or over 120)
-Incorrect data entry
##Possible Feature Engineering:
-Age Groups
-Age Buckets
-Standardized Age
-Age-Based Customer Segments


#fraud (target column)
##Data Type: 
-int64
##Business Meaning:
-Was the purchase fraudulent or  
##Why It Matters:
-The fraud column is the target variable that indicates whether a transaction is fraudulent or legitimate. It serves as the outcome the machine learning model will learn to predict. Accurate labeling is essential because the model's performance depends entirely on the quality and correctness of this variable.
##Possible Data Quality Issues:
-Missing labels
-Incorrect labels
##Possible Feature Engineering:
-No feature engineering (target variable should not be modified)
-Analyze class imbalance
-Apply oversampling (SMOTE) or undersampling during model training
-Use class weighting in machine learning algorithms

