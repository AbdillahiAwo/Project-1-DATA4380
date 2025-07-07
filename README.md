# Diabetes Prediction

* This repository applies K-Nearest Neighbors (KNN) to a diabetes prediction dataset filtered for pregnant individuals, using data from the https://www.kaggle.com/datasets/mathchi/diabetes-data-set.*

## Overview

The task is to predict the likelihood of diabetes in individuals who have experienced at least one pregnancy using a structured dataset with health measurements. We treat this as a binary supervised classification problem. My approach involves cleaning the dataset, selecting relevant features, scaling the data, and training a KNN model to classify individuals based on nearest neighbors in the feature space. The best model achieved approximately 79% accuracy and an AUC of 0.84 on the test set, indicating strong performance with a simple algorithm on a small dataset.

## Summary of Workdone

### Data

* Data:
  * Type: Tabular data in CSV format.
    * Input: 8 numeric features including Glucose, BMI, Age, and Pregnancies
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
Histograms compared the distribution of each feature across diabetic vs. non-diabetic outcomes
![download-3](https://github.com/user-attachments/assets/c9d922b4-09c4-4035-be36-b761a38688a1)
![download](https://github.com/user-attachments/assets/d40bd7fa-4d2e-43cd-ac3a-250182467a0d)
![download-1](https://github.com/user-attachments/assets/e5851abe-b828-4cc1-8b93-5f05091a2fe0)
![download-2](https://github.com/user-attachments/assets/e9d57d4e-444c-4636-9357-b5384ae2daa9)
These graphs show that diabetic individuals (orange) generally have higher glucose levels, more pregnancies, and slightly higher Diabetes Pedigree Function values compared to non-diabetics (blue), highlighting key differences between the two groups.
A heatmap was used to visualize correlations, revealing strong correlation between Glucose and Outcome
![download-4](https://github.com/user-attachments/assets/ee13919f-20ac-4d9c-a971-91eace6bb53d)

### Problem Formulation

* Define:
  * Input: 8 numerical features (Glucose, BloodPressure, Insulin, BMI, etc.)
  * Output: Binary classification (0 = non-diabetic, 1 = diabetic)
  * Models
    *K-Nearest Neighbors (KNN)
       *Tuned using n_neighbors from 1–20
       *Chosen for its suitability with small datasets and interpretability

### Training
 * Environment: Google Colab (default CPU)
 * Training time: Instantaneous (non-iterative training)
 * KNN requires no training phase; instead, it stores the training data
 * Hyperparameters tuned manually via cross-validation (choosing best k)

### Performance Comparison
Model	                 Accuracy	  AUC
KNN                    0.82       0.90
Logisitcal Regression  0.77       0.84
### Conclusions

* Both models performed well, with KNN providing the best accuracy and AUC.
* Feature scaling and class balancing (SMOTE) improved model stability.
* Glucose and BMI were key predictors, while Pregnancies had moderate positive correlation with diabetes outcome.
