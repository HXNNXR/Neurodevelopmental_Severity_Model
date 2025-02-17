# Neurodevelopmental Severity Prediction Model  

## Introduction  

Neurodevelopmental disorders in early childhood can affect cognitive, social, and motor development. I wanted to see if machine learning could help predict the severity of developmental difficulties in Sri Lankan children. The idea was to explore whether a data-driven approach could assist in public health decision-making and early intervention strategies.  

## Data Collection & Processing  

I used data from the **Sri Lanka Demographic and Health Survey (DHS) 2016**, specifically the child disability module. The dataset includes responses from mothers of children aged 2-5 years on different types of developmental difficulties, including speech clarity, vision, motor skills, and cognitive development.  

Since this dataset focuses on **functional difficulties rather than clinical diagnoses**, I thought it would be useful for predicting relative risk rather than confirming conditions.  

When I first loaded the dataset, I noticed missing values and formatting inconsistencies. To clean and prepare it for modeling, I:  
- Filled missing values using mean/mode imputation  
- Selected key features related to speech, motor function, and cognitive abilities  
- Converted categorical variables into numerical format  
- Standardized features for consistency  

After cleaning, I split the data into an **80/20 training and testing set**. The final dataset contained **40 training samples and 10 test samples**, which wasn’t a lot but was enough for an initial test.  

## Model Development  

I started with a simple linear regression model to test basic relationships between features and severity.  

**Linear Regression Results:**  
- Mean Absolute Error (MAE): 0.79  
- Mean Squared Error (MSE): 1.59  
- R² Score: 0.64  

While the model captured some patterns, it struggled with non-linear interactions, so I tested more advanced models.  

I ran a **Random Forest Regression**, which performed better than linear regression but still had room for improvement:  

**Random Forest Results:**  
- MAE: 1.23  
- MSE: 3.02  
- R² Score: 0.32  

I also tested **XGBoost Regression**, but it performed worse:  

**XGBoost Results:**  
- MAE: 1.50  
- MSE: 3.99  
- R² Score: 0.09  

Since Random Forest was the best-performing model, I fine-tuned it using grid search to optimize hyperparameters.  

**Optimized Random Forest Results:**  
- MAE: 1.29  
- MSE: 3.33  
- R² Score: 0.25  

Although tuning improved the model, it’s still not highly accurate, so further refinement is needed.  

## Feature Importance Analysis  

I ran a feature importance analysis to see which factors influenced predictions the most.  

| Feature                         | Importance Score |
|--------------------------------|----------------|
| Child’s speech clarity           | 21.5%          |
| Vision difficulties              | 18.8%          |
| Cognitive slowness indicators     | 17.2%          |
| Presence of convulsions/fits      | 9.7%           |
| Can’t understand words            | 9.0%           |

Surprisingly, **hearing difficulties had little impact (1.3%)**, suggesting it may not be a strong predictor in this dataset.  

## Findings & Next Steps  

The model has potential but is currently limited by dataset size and complexity. Right now, the main issues are:  
- **Small dataset size** – The training data is limited, making generalization difficult.  
- **Severity score variation** – More granular data on neurodevelopmental severity would likely improve predictions.  
- **Non-linear relationships** – A different model, such as an ensemble approach, may capture these better.  

For the next steps, I plan to:  
- Expand the dataset with additional child health records.  
- Test alternative models, including ensemble methods.  
- Refine feature selection to improve predictive accuracy.  
- Validate predictions against real-world clinical assessments.  

## Potential Applications  

If improved, this model could help identify children at higher risk of developmental difficulties. It could be useful for:  
- Public health agencies assessing risk factors in early childhood.  
- Policy discussions on early intervention programs.  
- Research into neurodevelopmental disorders in Sri Lanka.
- 
## Repository Contents  

- `neurodevelopmental_severity_model.pkl` – Trained Random Forest model  
- `feature_importance.csv` – Feature ranking from importance analysis  
- Jupyter Notebook – Full code for preprocessing, model training, and evaluation  

This is the first iteration of the model, and I’ll be improving it over time. Let me know your thoughts or if you have any suggestions for making it better.  
