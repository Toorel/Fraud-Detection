# Fraud-Detection

## Project Goals

We will attempt to predict financial fraud and derive information about the commonalities between different fraudulent transactions. Nearly half of all Americans have experienced identity theft or some other form of financial fraud. This experience can be both personally violating and extraordinarily expensive. In 2020 financial losses to fraud totaled over $700 billion dollars. Beyond the economic losses experienced overall the effects of financial fraud individually can be devastating and can take years to recover from. Organizations and individuals alike need protection from these types of crimes and accurate prediction can save millions or even billions of dollars and provide peace of mind. Security breaches resulting in fraud have deleterious effects on the reputation of any organization especially when considering financial data where the utmost security is expected. For this reason in the organizational case the losses to financial fraud are twofold, not only are they financial losses in the form of fraudulent transactions but financial losses from potential customers who are wary due to reputational damage.

## Structure of Dataset

This financial fraud dataset is composed of over 6 millions transactions with 11 separate columns. 

- step - maps a unit of time in the real world. In this case 1 step is 1 hour of time. Total steps 744 (30 days simulation).
- type - CASH-IN, CASH-OUT, DEBIT, PAYMENT and TRANSFER.
- amount - amount of the transaction in local currency.
- nameOrig - customer who started the transaction
- oldbalanceOrg - initial balance before the transaction
- newbalanceOrig - new balance after the transaction
- nameDest - customer who is the recipient of the transaction
- oldbalanceDest - initial balance recipient before the transaction. Note that there is not information for customers that start with M (Merchants).
- newbalanceDest - new balance recipient after the transaction. Note that there is not information for customers that start with M (Merchants).
- isFraud - This is the transactions made by the fraudulent agents inside the simulation. In this specific dataset the fraudulent behavior of the agents aims to profit by taking control or customers accounts and try to empty the funds by transferring to another account and then cashing out of the system.
- isFlaggedFraud - The business model aims to control massive transfers from one account to another and flags illegal attempts. An illegal attempt in this dataset is an attempt to transfer more than 200.000 in a single transaction.

## Assessment plan

To assess our work we will compare the results of our predicted dataset to the labels provided on whether a transaction is fraudulent using mean squared error as our measure. It is important we use a proper metric to measure model performance as not all mistakes are equal for fraud.  
Specifically false positives are much less costly than false negatives as missing fraud can be a significant failure for an organization and a terrible situation for an individual. Our assessment metrics will mirror this as we will use recall as the primary judge of our algorithms effectiveness. 

We will use an 80/20 test-train split on the rebalanced dataset and to prevent overfitting to our training split we will use k-fold cross validation sampling between k different segments of our training data for evaluation and hyperparameter tuning, before our final evaluation on the test set.

We will use an ROC curve on the rebalanced dataset to compare the TPR and FPR as attempting to use an ROC curve on the original dataset would not be effective as there is a significant class imbalance. 

To assess our clusters we will try a number of different values of k, visualize the various clusters and provide some descriptive analysis of each individual cluster. 

