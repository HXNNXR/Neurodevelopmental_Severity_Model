# Neurodevelopmental Severity Prediction Model  

Neurodevelopmental disorders in early childhood can have a significant impact on long-term cognitive, social, and motor development. I wanted to explore whether machine learning could be used to predict the severity of developmental difficulties in Sri Lankan children. The goal was to see if a data-driven approach could contribute to early identification and intervention strategies in public health.  

For this project, I used data from the Sri Lanka Demographic and Health Survey (DHS) 2016, specifically the child disability module. The dataset includes responses from mothers of children aged 2-5 years on their child’s speech clarity, vision, motor function, and cognitive abilities. Since the dataset focuses on functional difficulties rather than clinical diagnoses, I thought it would be useful for predicting relative risk rather than providing definitive conclusions. After loading the dataset, I noticed missing values and formatting inconsistencies, so I cleaned it by filling missing values using mean/mode imputation, selecting key features related to developmental difficulties, and converting categorical variables into a numerical format for standardization. Once the dataset was processed, I split it into an 80/20 training and testing set. The final dataset consisted of 40 training samples and 10 test samples, which wasn’t a large dataset but enough for an initial model test.  

I started with a simple linear regression model to check for basic relationships between features and developmental severity. The model produced a mean absolute error of 0.79 and an R² score of 0.64, which indicated some predictive power but also suggested that a more advanced approach was needed. I then tested a Random Forest Regression model, which performed slightly better with an R² score of 0.32, while an XGBoost Regression model performed worse with an R² of only 0.09. Since Random Forest performed best, I optimized its hyperparameters through grid search, which resulted in a final R² score of 0.25. Although this was an improvement, the model still has significant room for refinement, particularly in terms of handling non-linear interactions and increasing accuracy.  

To understand which factors had the biggest impact on predictions, I ran a feature importance analysis. The most influential predictors were speech clarity, vision difficulties, cognitive slowness, and the presence of convulsions or fits. Interestingly, hearing difficulties contributed very little to the model, suggesting it may not be a strong indicator in this dataset. The feature importance ranking is shown below:  

| Feature                         | Importance Score |
|---------------------------------|----------------|
| Child’s speech clarity          | 21.5%          |
| Vision difficulties             | 18.8%          |
| Cognitive slowness indicators   | 17.2%          |
| Presence of convulsions/fits    | 9.7%           |
| Can’t understand words          | 9.0%           |
| Difficulty in walking/movement  | 4.5%           |
| Late in standing/walking        | 4.3%           |
| Hearing difficulties            | 1.3%           |

Although the Random Forest model performed best, the results still indicated a need for improvement. Below is a comparison of the models I tested:  

| Model                     | Mean Absolute Error (MAE) | Mean Squared Error (MSE) | R² Score |
|---------------------------|--------------------------|--------------------------|----------|
| **Linear Regression**      | 0.79                     | 1.59                     | 0.64     |
| **Random Forest**         | 1.23                     | 3.02                     | 0.32     |
| **XGBoost**               | 1.50                     | 3.99                     | 0.09     |
| **Optimized Random Forest** | 1.29                     | 3.33                     | 0.25     |

At this stage, the model is functional but needs further refinement. The biggest limitations are the small dataset, limited variance in severity scores, and the challenge of capturing non-linear relationships. Moving forward, I plan to expand the dataset, test alternative models such as ensemble learning, and refine feature selection to improve predictive accuracy. There is also potential to validate the model against real-world clinical assessments, which could help make the predictions more applicable in practice.  

If improved, this model could be useful for public health agencies assessing child development risks, policy discussions on early intervention strategies, and research into neurodevelopmental disorders in Sri Lanka. The repository contains the trained Random Forest model file, a CSV with ranked feature importance, and a Jupyter Notebook documenting the full process, including data preprocessing, model training, and evaluation.  

This is just the first iteration of the model, and I’ll be working on improvements over time. Let me know your thoughts or if you have any suggestions!

