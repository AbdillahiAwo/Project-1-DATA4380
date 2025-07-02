# Diabetes Prediction

* This project applies multiple machine learning models to predict diabetes in pregnant individuals using health metrics from the Diabetes Dataset.

## Overview

  * **Definition of the tasks / challenge**  The objective is to classify whether a pregnant individual has diabetes based on features such as glucose levels, insulin, BMI, age, blood pressure, and others.
  * **Your approach** We approach this as a binary classification problem. After filtering the dataset for individuals with pregnancies greater than zero, we cleaned the data, scaled the features, and trained multiple models: Logistic Regression (baseline), Random Forest, and XGBoost. We used SMOTE to address class imbalance and employed cross-validation and ROC AUC to evaluate model performance.
  * **Summary of the performance achieved** Logistic Regression achieved a test accuracy of approximately 78% and an AUC of 0.83. Random Forest and XGBoost outperformed it, with XGBoost reaching an AUC above 0.86. Learning curves showed good generalization with minimal overfitting.
## Summary of Workdone

### Data

* Data:
  * Type: Tabular data in CSV format.
    * Input: CSV file with medical measurements including glucose, insulin, BMI, blood pressure, age, etc
    * Output:  Binary variable (Outcome) indicating presence of diabetes.
  * Size: 768 instances (before filtering)
  * Instances 650 pregnant individuals (After filtering)
  * Train Test Split: 80%-20%
  * Validation: Performed with 5-fold cross-validation 

#### Preprocessing / Clean up

* Dropped Id column as irrelevant
* Filtered dataset to include only individuals with Pregnancies > 0
* Replaced zeroes in Glucose, BloodPressure, SkinThickness, Insulin, and BMI with NaN
* Imputed missing values using the mean
* Applied StandardScaler to all features
* Used SMOTE to balance classes in the training data
  
#### Data Visualization

-I used a heatmap to visualize the correlations between features, which helped identify which variables, like Glucose and BMI, had the strongest relationships with the diabetes outcome.

  ![download](https://github.com/user-attachments/assets/84c2a089-6c5f-4b7d-85f0-9ff72f0b52f7)


### Problem Formulation

* Define:
  * Input: 8 numerical features (Glucose, BloodPressure, Insulin, BMI, etc.)
  * Output: Binary classification (0 = non-diabetic, 1 = diabetic)
  * Models
    * Logistic Regression (baseline model)
    * Random Forest Classifier
    * XGBoost Classifier
  * Logistic Regression: max_iter=1000
  * Random Forest: Tuned n_estimators, max_depth, min_samples_split
  * XGBoost: Used default settings with early stopping in advanced stages

### Performance Comparison

Model	Accuracy
Logistic Regression	~78%	
Random Forest	~81%	
XGBoost	~83%	

### Conclusions

* All models performed well, with XGBoost providing the best accuracy and AUC.
* Feature scaling and class balancing (SMOTE) improved model stability.
* Glucose and BMI were key predictors, while Pregnancies had moderate positive correlation with diabetes outcome.

### Future Work

* Tune hyperparameters for XGBoost more deeply
