# Introduction

## Business Understanding:

#### The project focuses on SyriaTel, a telecommunications company facing customer churn issues due to increased competition. Our aims to develop predictive models to forecast customers that are likely to leave, thus helping SyriaTel retain its customer base.

## Data Understanding:

- The dataset used for analysis, named `telecom_dataset`. 
- It contains information about customers using SyriaTel's services. 
- It can be accessed on Kaggle. 
- The dataset has 3333 rows and 21 columns in CSV format.
- The columns include information such as state, account length, area code, phone number, international plan, voice mail plan, call details (day, evening, night, international), and customer service calls, along with a churn indicator.

## Data Preperation:
- No missing values in the dataset. 
- Imported relevant libraries for data analysis and machine learning tasks, including pandas, numpy, seaborn, matplotlib, and scikit-learn.

### Exploratory Data Analysis (EDA)


![churn distribution](https://github.com/Abuz254/glowing-octo-computing-machine/blob/main/Images/download%20(5).png)

## Data Modeling:

- Defined pipelines for Logistic Regression, SVM, Decision Tree, and KNN classifiers.
- These are models that benefit from feature scaling, reason to include a StandardScaler.

### Training:
- Fitted each pipeline on the training data.

### Initial Evaluation:
Evaluated each pipeline on the test data and printed the accuracy.

### Hyperparameter Tuning:
- Defined parameter grids for each model.
- Used GridSearchCV to find the best hyperparameters for each model.

### Re-Evaluation:
- Refitted the pipelines with the best found parameters.
- Evaluated and print the accuracy, precision, recall, and F1-score for each classifier.

### Confusion Matrix Plotting: 
Decision Tree classifier was plotted using a custom function.