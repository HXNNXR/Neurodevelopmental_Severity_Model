# Neurodevelopmental Severity Prediction Model  

## Introduction  
Neurodevelopmental disorders in early childhood can impact long-term cognitive, social, and motor development. I wanted to explore how machine learning could be applied to predict the severity of developmental difficulties in Sri Lankan children using survey data. The goal was to see if a data-driven approach could support public health decision-making and early intervention strategies.  

## Data Collection & Processing  

### Dataset Selection  
I used data from the **Sri Lanka Demographic and Health Survey (DHS) 2016**, specifically the child disability module. This dataset includes responses from mothers of children aged 2-5 years on their child's developmental difficulties. The data covered:  
- Speech and language abilities  
- Vision and hearing impairments  
- Motor function challenges  
- Cognitive and behavioral difficulties  

Since this dataset focuses on **functional difficulties rather than clinical diagnoses**, I thought it would be useful for predicting relative risk rather than confirming conditions.  

### Data Cleaning & Preprocessing  
When I first loaded the dataset, I noticed some missing values and formatting inconsistencies. To clean and prepare it for modeling, I:  
- Filled missing values using mean/mode imputation  
- Selected key features related to speech, motor function, and cognitive abilities  
- Converted categorical variables into numerical format  
- Standardized features for consistency  

After cleaning, I split the data into an **80/20 training and testing set**. The final dataset contained **40 training samples and 10 test samples**, which isn’t a lot but was enough for an initial model test.  

## Model Development  

### Initial Approach: Linear Regression  
To start, I ran a simple linear regression model to see if basic relationships between features and severity could be captured. The results:  
- Mean Absolute Error (MAE): 0.79  
- Mean Squared Error (MSE): 1.59  
- R² Score: 0.64  

While the model worked, it struggled to handle **non-linear relationships** in the data, so I decided to try more advanced approaches.  

### Testing More Advanced Models  
To improve predictive accuracy, I tested other models:  

#### Random Forest Regression  
- MAE: 1.23  
- MSE: 3.02  
- R² Score: 0.32  

#### XGBoost Regression  
- MAE: 1.50  
- MSE: 3.99  
- R² Score: 0.09  

Random Forest performed better than XGBoost, but the overall accuracy was still lower than I wanted.  

### Hyperparameter Tuning for Random Forest  
To see if I could improve results, I fine-tuned the Random Forest model using grid search to optimize parameters like the number of trees and depth. The best model produced:  
- MAE: 1.29  
- MSE: 3.33  
- R² Score: 0.25  

Although this was an improvement, the model still has room for optimization.  

## Feature Importance Analysis  

To understand which features had the biggest impact on predictions, I ran a feature importance analysis. The most influential factors were:  

1. Child’s speech clarity (21.5%)  
2. Vision difficulties (18.8%)  
3. Cognitive slowness indicators (17.2%)  
4. Presence of convulsions/fits (9.7%)  

On the other hand, **hearing difficulties barely affected predictions (1.3%)**, so it may not be as relevant in this context.  

## Findings & Next Steps  

### Current Model Limitations  
- **Small dataset size**: The training data is limited, making generalization difficult.  
- **Severity score variation**: The dataset doesn’t provide a full range of neurodevelopmental severity levels, which could be limiting predictions.  
- **Non-linear relationships**: The current models may not be capturing more complex interactions between factors.  

### Future Improvements  
- Adding more data from similar sources to improve accuracy  
- Exploring ensemble models (e.g., combining Random Forest with other methods)  
- Experimenting with feature engineering to refine input variables  
- Comparing model predictions with real-world clinical assessments
- 
## Repository Contents  
- `neurodevelopmental_severity_model.pkl` – Trained Random Forest model  
- `feature_importance.csv` – Feature ranking from importance analysis  
- Jupyter Notebook – Full code for preprocessing, model training, and evaluation  

This is the first iteration of the model, and I’ll be improving it over time. Let me know your thoughts or if you have any suggestions for making it better!
