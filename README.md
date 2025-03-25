# Module 17 Practical Application 3 - Comparing Classifiers

## Overview

This project aims to compare the performance of the classifiers K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines.  I will run this analysis utilizing a dataset related to marketing bank products over the telephone. The goal is to understand which algorithm performed best for this particular business problem and dataset, providing insights that could optimize future marketing efforts.

The Jupyter workbook that was used to come to the above findings is available in this GitHub repository here: [module_17_assignment_workbook.ipynb](https://github.com/cjplumer/module17_submission/blob/main/module_17_assignment_workbook.ipynb)

## Dataset

The dataset used for this analysis contains information from a Portuguese banking institution's direct marketing campaigns (phone calls) conducted between May 2008 and November 2010. It consists of 41,188 records with 21 columns, including:

### Client Information:
* age: Customer's age (numeric)
* job: Type of employment (e.g., admin, blue-collar, entrepreneur)
* marital: Marital status (divorced, married, single, unknown)
* education: Education level (basic, high school, university degree, etc.)
* default: Has credit in default (yes, no, unknown)
* housing: Has housing loan (yes, no, unknown)
* loan: Has personal loan (yes, no, unknown)

### Campaign Information:
* contact: Communication type (cellular, telephone)
* month: Last contact month
* day_of_week: Last contact day of the week
* duration: Last contact duration in seconds
* campaign: Number of contacts during this campaign
* pdays: Days since client was last contacted
* previous: Number of contacts before this campaign
* poutcome: Outcome of the previous marketing campaign

### Economic Context:
* emp.var.rate: Employment variation rate
* cons.price.idx: Consumer price index
* cons.conf.idx: Consumer confidence index
* euribor3m: Euribor 3-month rate
* nr.employed: Number of employees

### Target Variable:
* y: Whether the client subscribed to a term deposit (yes, no)

The dataset showed significant class imbalance, with the majority of clients not subscribing to term deposits.


## Methodology

The following steps were undertaken for the analysis:

### 1. Data Preparation:
* Examined the dataset for missing values (none were found)
* Identified categorical features requiring encoding
* Applied one-hot encoding to categorical variables
* Standardized numerical features to ensure equal scale influence
### 2. Feature Engineering:
* Initially used a limited set of client demographic features
* Later expanded to include all features except duration
### 3. Model Training & Evaluation:
* Split data into 80% training and 20% testing sets
* Established a baseline model using the most frequent class predictor
* Trained four classifier models with default parameters
* Compared models on training time, training accuracy, and test accuracy
* Applied hyperparameter tuning using GridSearchCV with 5-fold cross-validation
* Evaluated models with metrics beyond accuracy (precision, recall, F1-score, AUC)
### 4. Feature Importance Analysis:
* Identified the most influential features in prediction
* Analyzed how these features affect subscription likelihood


## Key Findings

### 1. Model Performance:
* Decision Tree and SVM models generally outperformed KNN and basic Logistic Regression
* After hyperparameter tuning, accuracy improved across all models
* Decision Tree provided the best balance of performance, interpretability, and training time
* The baseline accuracy (predicting "no" for all clients) was approximately 88%, reflecting the class imbalance
### 2. Feature Importance:
* Economic indicators (euribor3m rate, employment variation) were among the most predictive features
* Previous campaign outcome very likely influenced subscription signup
* Client's age and job type were more important than other demographic factors
* Contact month reflected seasonal patterns in subscription rates
### 3. Evaluation Metrics:
* While accuracy was high across models (89-92%), precision and recall for the "yes" class were much lower
* F1-scores for the minority class (yes) highlighted the challenge of correctly identifying potential subscribers
* AUC values provided a more balanced assessment of model performance
