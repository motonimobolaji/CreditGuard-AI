##Risk Indicators Report


## Overview

I created this report to identify the transaction characteristics that may indicate fraudulent activity within the CreditGuard AI dataset. Understanding these fraud indicators before developing machine learning models allows me to better interpret the data, engineer meaningful features, and explain why certain transactions are considered high risk. Rather than relying solely on algorithms, I want to understand the business reasoning behind each risk factor so that the final model reflects how fraud analysts evaluate suspicious transactions.

## Risk Indicators

###Transaction Amount
Risk Contribution: High

Description:
I consider the transaction amount to be one of the strongest fraud indicators because unusually large purchases often fall outside of a customer's normal spending behavior. Even though high value purchases can be legitimate, they become more suspicious when combined with other indicators such as foreign transactions, low device trust scores, or location mismatches.

Business Reasoning




###Transaction Hour
Risk Contribution: Mid

Description:
I use the transaction hour to identify unusual purchasing patterns throughout the day. Transactions that happen at hours late at night or early in the morning may indicate fraudulent activity because fraudsters often would try their hand when cardholders are less likely to notice unauthorized purchases. Time alone does not determine fraud, but when you combine it with other factors and risk indicators it provides valuable context.

Business Reasoning




###Merchant Category
Risk Contribution: Mid

Description: 
After doing research, certain types of businesses and industries experience higher rates of fraudulent transactions than others. Understanding where purchases occur allows me to identify industries that may require additional fraud monitoring and helps provide context for transaction behavior.

Business Reasoning




###Foreign Transaction
Risk Contribution: High

Description:
I consider foreign transactions to be a significant fraud indicator because unauthorized purchases frequently occur outside of a customer's home country. While many international purchases are legitimate, this feature becomes much more meaningful when evaluated with other suspicious behaviors.

Business Reasoning




###Location Mismatch
Risk Contribution: High

Description:
I use location mismatches to identify transactions where the purchase location differs from the cardholder's expected location. This may indicate that someone other than the legitimate cardholder is using the credit card. Although travel can create legitimate mismatches, this feature remains an important indicator of potential fraud.

Business Reasoning




###Device Trust Score
Risk Contribution: High

Description:
I believe the device trust score risk level is high. I consider the device trust score to be a valuable indicator because it measures how familiar or reliable a device is based on its previous activity. Transactions that are being made from unknown or low-trust devices may suggest the account has been compromised or unauthorized access. This feature helps distinguish trusted customer behavior from potentially fraudulent activity.

Business Reasoning



###Velocity Last 24 Hours
Risk Contribution: Mid- High

Description:
I use transaction velocity to measure how many transactions a cardholder has made within the previous 24 hours. While a high number of transactions does not automatically indicate fraud, an unusual spike in purchasing activity may suggest that a stolen credit card is being used before it can be reported or blocked. I believe this feature becomes significantly more valuable when evaluated alongside other risk indicators such as transaction amount, foreign transactions, location mismatches, and device trust scores rather than being considered on its own.

Business Reasoning



###Cardholder Age
Risk Contribution: Low

Description:
I consider the risk level of the cardholder's age low. After doing research, card fraudsters don't have a target audience they intentionally reach out to, because when they steal card information, it is in bulk, so they rely more on data breaches, phishing, and digital skimming to steal people's card information. I think the cardholder age is important to look at, because we can still find some great insights when it's combined with other factors of the columns. 

Business Reasoning



## Overall Fraud Strategy
After evaluating each feature individually, I do not expect any single variable to accurately identify fraudulent transactions on its own. Instead, I believe fraud is best detected by evaluating multiple risk indicators together to build a complete picture of a transaction. For example, a large transaction amount combined with a foreign transaction, a location mismatch, a low device trust score, and an unusually high transaction velocity represents a much stronger indication of fraud than any one of those features alone.
As I continue developing CreditGuard AI, I will focus on identifying how these features interact with one another rather than relying on individual variables. My goal is to build a machine learning model that recognizes these relationships, assigns an appropriate fraud risk score to each transaction, and helps fraud analysts prioritize the transactions that require immediate investigation.

## Reflection

## Reflection

Completing this Risk Indicators Report helped me think beyond the dataset and begin approaching the project from the perspective of a fraud analyst rather than just a data scientist. Instead of viewing each column as a variable for a machine learning model, I focused on understanding how different transaction behaviors may contribute to fraudulent activity and why they matter in a real-world banking environment.

This process also reinforced an important lesson: no single feature should determine whether a transaction is fraudulent. Instead, the combination of multiple risk indicators provides a more complete picture of potential fraud. Developing this understanding has given me a stronger foundation for the next phases of the project, where I will validate these assumptions through exploratory data analysis and begin building predictive models based on the patterns I discover.


## Next Steps

For my next steps, I will develop my business questions by turning my current business assumptions into measurable questions that I can answer through exploratory data analysis (EDA). By validating these risk indicators with the dataset, my goal is to determine which features are most strongly associated with fraudulent transactions and identify the patterns that will guide my feature engineering and machine learning decisions.








