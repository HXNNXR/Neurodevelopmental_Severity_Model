# Neurodevelopmental Severity Prediction Model  

## 🔄 Model Update: Version 2

In this updated version of the **Neurodevelopmental Severity Prediction Model**, I have:
- Incorporated **Low Birth Weight Data** as a feature
- Integrated **Public Health Expenditure Data** for additional context
- Retrained the model using the new dataset

### Performance Improvement:
| Metric | Previous Model | Updated Model (v2) |
|--------|---------------|-------------------|
| **Mean Absolute Error (MAE)** | 3.7139 | **3.5911** ✅ |
| **Mean Squared Error (MSE)** | 42.0318 | **41.0843** ✅ |
| **R² Score** | 0.6488 | **0.6567** ✅ |

The model now better predicts neurodevelopmental disorder severity in Sri Lankan children by integrating **biological and healthcare expenditure factors**. 

 **Latest model version:** `neurodevelopmental_severity_model_v2.pkl`

Let me know your thoughts! 

---------------------------------------------------------------------------------------------

## 🔄 Model : Version 1

Predicting Neurodevelopmental Severity in Sri Lankan Children Using Machine Learning
Neurodevelopmental disorders in early childhood can affect a child's cognitive, social, and motor skills, impacting their long-term development. I wanted to explore whether machine learning could help predict the severity of developmental difficulties in Sri Lankan children. The idea was to see if a data-driven approach could contribute to early detection and better intervention strategies.

For this project, I used data from the Sri Lanka Demographic and Health Survey (DHS) 2016, specifically focusing on child development indicators. The dataset includes responses from mothers of children aged 2-5 years, covering aspects like speech clarity, vision, motor function, and cognitive abilities. Since this data reflects functional difficulties rather than clinical diagnoses, I designed the model to estimate relative risk rather than make definitive conclusions.

Step 1: Data Cleaning & Preparation
The dataset had missing values and inconsistencies, so I cleaned it by:

Filling missing values using mean/mode imputation
Selecting key features related to developmental difficulties
Converting categorical variables into numerical format
Once processed, I split the dataset into training (80%) and test (20%) sets, resulting in 40 training samples and 10 test samples—a small but useful starting point.

Step 2: Model Testing & Performance
I first ran a Linear Regression model as a baseline test. It showed some predictive power (MAE: 0.79, R²: 0.64), but it was clear that a more advanced approach was needed.

I then tested Random Forest and XGBoost models:

Random Forest performed best (R²: 0.32), while
XGBoost performed the worst (R²: 0.09)
After optimizing the Random Forest model with hyperparameter tuning, the final R² score improved to 0.25, but there was still room for refinement.

Step 3: Feature Importance Analysis
To understand which factors contributed most to predictions, I ran a feature importance analysis. The top predictors were:

Feature	Importance Score
Child’s speech clarity	21.5%
Vision difficulties	18.8%
Cognitive slowness indicators	17.2%
Presence of convulsions/fits	9.7%
Can’t understand words	9.0%
Interestingly, hearing difficulties contributed very little, suggesting it may not be a strong predictor in this dataset.

Step 4: Expanding the Model
To improve accuracy, I incorporated public health expenditure data and child malnutrition indicators to see if broader socioeconomic factors influenced developmental difficulties. The updated model showed a slight improvement:

Model	MAE	MSE	R² Score
Baseline Random Forest	3.79	45.33	0.62
With Public Health & Child Malnutrition Data	3.59	41.08	0.65 
Next Steps
This is still a work in progress, and I plan to:

Expand the dataset to include more socioeconomic indicators
Test alternative models, including ensemble learning
Refine feature selection to increase predictive accuracy
Validate the model against real-world clinical assessments
If improved, this model could be useful for public health agencies, policy discussions on early interventions, and neurodevelopmental research in Sri Lanka.

I’d love to hear any feedback so do reach out!

