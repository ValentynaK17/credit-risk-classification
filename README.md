# credit-risk-classification
Building a model that can identify the creditworthiness of borrowers using Logistic regression along with oversampling of train data set.
## Repository Contents
- **Credit_Risk** directory contains:
   - *credit_risk_classification.ipynb* with the scripts for prediction the creditworthiness using different approaches <br>
   - **Resources** directory contains:
     - *lending_data.csv* file with input data <br>
   - **Output** directory contains image with metrics plot <br>
## Installation
 - Having Python installed on your machine along with Jupyter Notebook available, clone this repository to your local machine <br>
## Usage
 - Run the *credit_risk_classification.ipynb* script using Jupyter Notebook <br>

## Credit Risk Analysis Report
The purpose of the analysis is to build a model that can help with making lending decisions by accurately predicting of the likelihood of loan payment, based on such financial data as loan size, interest rate, borrower income, total debt.<br>
In order to predict the creditworthiness of borrowers we are using a dataset of historical lending activity from a peer-to-peer lending services company, that has information about loan healthiness for different combinations of: <br>
 - loan size, 
 - interest rate, 
 - borrower income along with debt to it, 
 - number of accounts,
 - derogatory marks 
 - and total debt.<br>
 
The assumption is that data are represented here in consistent currency. The model is build using 77536 records in total with:<br>
  - 75036 healthy loans
  - 2500 high-risk loans.<br>
Having 75% of those data for training purposes (only 3.3% of them represent high-risk loans) and the rest for testing the output.<br>

Before applying the machine learning we:<br>
 - investigate the data to be sure its clean, normalized and in the format acceptable by ML models (e.g. numerical values)
 - split dataset into training and test one.<br>
 
Looking for binary classification the Logistic Regression model was used as a main choice.<br>
Having that only 3% of label data are marked as high-risk loans we used resampling method in addition.<br>
Having input data with too different means per feature, added few experiments with re-sampled input data, but they did not seem to improve the performance.<br>

## Results
#### Logistic Regression Model trained on original feature data:
 - Balanced accuracy score for the model: **0.94**.
 - Confusion matrix for the model:
   
|   | Predicted as Healthy| Predicted as High-Risk|
|----------|----------|----------|
|**Actually Healthy**| 18679 | 80 |
|**Actually  High-Risk**| 67 | 558|

 - Classification report for the model:
   
|   | Precision| Recall|
|----------|----------|----------|
|**Healthy Loan**| 1.00 | 1.00 |
|**High-Risk Loan**| 0.87 | 0.89|


#### Logistic Regression Model trained on oversampled feature data:
 - Balanced accuracy score for the model: **1.00**.
 - Confusion matrix for the model:
   
|   | Predicted as Healthy| Predicted as High-Risk|
|----------|----------|----------|
|**Actually Healthy**| 18668 | 91 |
|**Actually  High-Risk**| 2 | 623|

 - Classification report for the model:
   
|   | Precision| Recall|
|----------|----------|----------|
|**Healthy Loan**| 1.00 | 1.00 |
|**High-Risk Loan**| 0.87 | 1.00|

## Summary
Logistic Regression Model trained on oversampled training set can be recommended for prediction of high-risk loans, because out of all the high-risk loans the model recognized almost 100% records on test data, having overall accuracy roughly 100%. <br>
However, it has a slightly worse results with healthy loans recognition - a slightly more healthy loans were predicted as high risk ones - it keeps the overall precision in general at the same level as other variations: from all the records which model marked as high risk 13% were predicted incorrectly. And overall healthy loans are predicted pretty good here as the model made mistakes with recognition of this category in less than 1% cases for test data.<br>
<img src="https://github.com/ValentynaK17/credit-risk-classification/blob/main/Credit_Risk/Output/Model_Output_Comparison.png" width="600"> <br>
