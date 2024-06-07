# PROJECT TITLE: SyriaTel

## Business Understanding:

#### The project focuses on SyriaTel, a telecommunications company facing customer churn issues due to increased competition. Our aim is to develop a predictive model to forecast customers that are likely to leave, thus helping SyriaTel retain its customer base.

## Data Understanding:

- The dataset used for analysis, named `telecom_dataset.csv`. 
- It contains information about customers using SyriaTel's services. 
- It can be accessed on Kaggle. 
- The dataset has 3333 rows and 21 columns in CSV format.
- The columns include information such as state, account length, area code, phone number, international plan, voice mail plan, call details (day, evening, night, international), and customer service calls, along with a churn indicator.

## Data Preperation:
- No missing values in the dataset. 
- Imported relevant libraries for data analysis and machine learning tasks, including pandas, numpy, seaborn, matplotlib, and scikit-learn.

# Exploratory Data Analysis (EDA)

#### Normalize Numerical Features: 
Numerical features were normalized using MinMaxScaler to ensure they are on a similar scale, which is crucial for models sensitive to feature scaling.

#### One-Hot Encoding for Categorical Features: 
The 'state' column was converted to numerical format using one-hot encoding to handle categorical data.

#### Binary Encoding for Plans: 
Binary encoding was applied to 'international plan' and 'voice mail plan', mapping 'yes' to 1 and 'no' to 0.

#### Encode Target Variable: 
The `churn` column was encoded as 0 and 1 to be used as the target variable for classification models.

#### Drop Irrelevant Features: 
Features like `phone number` is dropped as they do not contribute to the predictive modeling.

## Visualizations

![churn distribution](https://github.com/Abuz254/glowing-octo-computing-machine/blob/main/Images/download%20(5).png)

- Out of 3,333 customers in the dataset:
- 483 have terminated their contract with SyriaTel.
- That is 14.5% of customers lost.
- Distribution of the binary classes shows a data imbalance.
- This needed to be addressed before modeling as an unbalanced feature can cause the model to make false predictions.

![Visualize churn by state](https://github.com/Abuz254/glowing-octo-computing-machine/blob/main/Images/download(6).png)

- West Virginia (WV) has a notable churn count.
- Look into West Virginia based on the feature of International Plan and Churn.

![Churn by international plan in West Virginia](https://github.com/Abuz254/glowing-octo-computing-machine/blob/main/Images/download(7).png)

- Customers without an international plan (‘no’) who did not churn (‘False’) constitute the majority.
- A smaller number of customers without an international plan (‘no’) did churn (‘True’).
- The number of customers with an international plan (‘yes’) is significantly lower overall.

##### Therefore;
- Most West Virginia customers do not have an international plan.
- Among those without an international plan, the majority remain loyal.
- The churn rate is relatively low for both groups.

Further analysis on West Virginia on the feature Voice Mail Plan and Churn.

![Churn by voice mail plan in West Virginia](https://github.com/Abuz254/glowing-octo-computing-machine/blob/main/Images/download(8).png)

Almost the same situation as the International Plan, the Voice mail plan shows a similar trend.

- Most West Virginia customers do not have a voice mail plan.
- Among those without a voice mail plan, the majority remain loyal (did not churn).
- The churn rate is relatively low for both groups.

Look into customer service calls feature

![Visualize churn by customer service calls](https://github.com/Abuz254/glowing-octo-computing-machine/blob/main/Images/download(9).png)

- Customers who made 4 or more service calls are at a higher risk of churning.
- Relationship between service calls and churn suggests that customer satisfaction with service interactions plays a crucial role.
- Focus on resolving issues effectively during the first few calls to prevent escalation.
- Reach out to customers who make multiple calls to address their concerns promptly.
- Use customer feedback from service calls to enhance overall service quality.

![Compute confusion matrix](https://github.com/Abuz254/glowing-octo-computing-machine/blob/main/Images/download(14).png)

- True Positives (TP): 76 - Churn customers that the model correctly predicted as churn.
- False Positives (FP): 7 - Non-churn customers that the model incorrectly predicted as churn.
- True Negatives (TN): 559 - Non-churn customers that the model correctly predicted as non-churn.
- False Negatives (FN): 25 - Churn customers that the model incorrectly predicted as non-churn.

![Feature Importance Plot](https://github.com/Abuz254/glowing-octo-computing-machine/blob/main/Images/download(15).png)

- The feature indicates that total day minutes has the highest importance score among the features used in the XGBoost model.
- Has an importance score of approximately 306.0.
- This suggests that total day minutes significantly influences the model’s predictions, particularly when it comes to predicting customer churn.
- Customers’ total call duration during the day appears to be a critical factor in determining whether they are likely to churn or remain with the service.
- If a customer spends more time on calls during the day, it may impact their likelihood of churning.

![ROC Curve](https://github.com/Abuz254/glowing-octo-computing-machine/blob/main/Images/download(16).png)

- The closer the ROC curve is to the top-left corner, the better the model’s performance.
- The AUC is approximately 0.92, indicating strong predictive accuracy.
- XGBoost model performs well, as evidenced by the high AUC.

#### Correlation with Target Variable:
- Correlation coefficients between numerical features and churn is calculated and visualized to identify important predictors.
- Correlation analysis revealed that features like `total day minutes`, `total day charge`, `total international minutes`, `total international charge`, and `customer service calls` have notable correlations with churn.

## Model Building

Five machine learning models were built and evaluated to predict customer churn:

- Logistic Regression
- Support Vector Machine (SVM)
- Decision Tree
- K-Nearest Neighbors (KNN)
- XGBoost

- A pipeline approach was used to ensure consistent and efficient data preprocessing and model training. 
- Hyperparameter tuning was performed using GridSearchCV to optimize model performance.

#### Performance Metrics
Performance of each model was evaluated using metrics such as train accuracy, test accuracy, F1-score, precision, and recall. 
These metrics provided insights into each model's effectiveness in predicting customer churn.

## Conclusion
- XGBoost model demonstrated the best performance across all evaluated metrics, making it the most effective model for predicting customer churn. 
- With high accuracy, precision, and recall, XGBoost provides a reliable tool for identifying customers at risk of leaving. 
- Implementing this model enables SyriaTel to target retention efforts effectively, improving customer satisfaction and reducing churn rates.