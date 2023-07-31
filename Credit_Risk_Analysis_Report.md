# Credit Risk Analysis Report (Modele 20 Assignment)

## Overview of the Analysis

The purpose of this analysis is to identify a supervised machine learning model to accurately classify potential loans as healthy (0) or high-risk (1). I leveraged a dataset of historical lending activity from a peer-to-peer lending services company to build the model; the data included the following information: loan size, interest rate, borrower income, borrower's debt-to-income ratio, number of accounts the borrower has open, derogatory marks the borrower has received, the borrower's total debt, and the loan status (healthy or high-risk). 

For this analysis, I first built a supervised learning model with the original dataset. I started by separating the input variables from the variable I was trying to predict. In this case, all columns were treated as inputs (X) except for loan status, which is what our model is trying to predict (y). I then split the data into training and testing datasets so that I could use the training data to build the machine learning model and then the testing data to test the accuracy of the model. Specifically, I used a logistic regression model, and while the accuracy of this first model was good, but there was room for improvement. 

I then built a second supervised learning model that utilized the RandomOverSampler module to help account for an imbalance in the data between healthy and high-risk loans, in the hopes that this would improve the accuracy of the model. I fit the original training data to the random oversampler model and, using logistic regression, then made predictions based on a new classifier. This second model ultimately performed better than the first model.


## Results

The following outlines the results I observed in both models that I built. 

* Machine Learning Model 1:
  * Balanced accuracy: The balanced accuracy of the first model (using the original dataset) is 94.4%, which suggests that the model does a fair job of predicting the loan status. 
  * Precision: For healthy loans, the model has a precision score of nearly 100%, meaning that nearly 100% of all loans predicted as healthy were healthy in actuality. For high-risk loans, the model had a lower precision score, at about 87%; this means that 87% of the loans that were predicted to be high-risk actually were high-risk loans. 
  * Recall: For the healthy loans, the model has a recall score of nearly 100%, meaning that of all the actual healthy loans in the dataset, it correctly predicted nearly all of them to be healthy. On the other hand, for high-risk loans, the model only identified about 89% of all high-risk loans in the dataset. 

* Machine Learning Model 2:
  * Balanced accuracy: The balanced accuracy of the second model (using the resampled data) is 99.6%, which suggests that this model does a stellar job of predicting the loan status. 
  * Precision: For both healthy loans, the model has a prediction score of nearly 100%, meaning that nearly 100% of all loans predicted as healthy were healthy in actuality. For high-risk loans, the model had a lower precision score, at about 87%; this means that 87% of the loans that were predicted to be high-risk actually were high-risk loans. 
  * Recall: For both healthy and high-risk loans, the model has a recall score of nearly 100%, meaning that of all the actual healthy loans in the dataset and of all the actual high-risk loans in the dataset, the model accurately predicted nearly all of them to be healthy and high-risk, respectively. 


## Summary & Recommendation

Overall, we see that the second model using the resampled data performs better than the first model, especially on balanced accuracy as well as the recall score for the high-risk loans. In this use case, the recall score for high-risk loans is especially critical, since recall for high-risk loans tells us of all high-risk loans in the dataset, how many does the model actually predict in actuality. In this case, a high-risk loan that the model classifies as healthy would be considered a false negative, and a false negative in this case is a risk for the bank because it could lead to a loan default. (On the other hand, a false positive -- a healthy loan wrongly classified as a high-risk loan -- is less of a concern for the bank.) 

The second model minimizes the chance that a high-risk loan will wrongly be classified as a healthy loan, and therefore reduces overall financial risk for the bank. I recommend that the bank employ the second model for classifying potential borrowers' overall creditworthiness. 