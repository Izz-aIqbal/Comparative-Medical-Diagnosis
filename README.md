# Comparative Machine Learning for Medical Diagnosis Prediction

A robust machine learning framework designed to evaluate, tune, and compare multiple computational classifiers for binary medical outcome prediction using comprehensive clinical patient datasets.

---

## Executive Summary

Early and accurate clinical diagnosis is critical for effective patient care. This project implements a rigorous comparative analysis of six distinct machine learning algorithms to predict binary medical outcomes based on physiological features[cite: 11]. By combining meticulous data preprocessing, Stratified K-Fold cross-validation, hyperparameter tuning via Grid Search, and multi-metric evaluation (with primary emphasis on ROC-AUC), the pipeline identifies the optimal predictive model for clinical deployment.

---

## Dataset Description

The pipeline processes clinical records from `medical_diagnostic_dataset.csv`, focusing on key physiological indicators and a binary target outcome.

### Features
* **Age:** Patient age in years
* **BMI:** Body Mass Index (weight-to-height ratio)
* **Glucose:** Plasma glucose concentration levels
* **BloodPressure:** Diastolic blood pressure measurements
* **Insulin:** Serum insulin levels
* **SkinThickness:** Triceps skin fold thickness
* **Outcome:** Binary target label indicating disease presence (`1`) or absence (`0`)

---

## Methodology and Pipeline Architecture

### 1. Data Preprocessing & Quality Control
* **Missing Value Imputation:** Clinically impossible zero values recorded for physiological metrics (such as `Insulin` and `BloodPressure`) were handled using robust median imputation to preserve data integrity.
* **Feature Standardization:** All numeric features were scaled to ensure zero mean and unit variance, preventing magnitude bias during model convergence.
* **Data Splitting:** The dataset was partitioned into an 80% training set for model optimization and a held-out 20% test set for unbiased generalization evaluation.

### 2. Validation Strategy and Hyperparameter Tuning
* **Stratified K-Fold Cross-Validation:** Implemented 10-fold cross-validation, ensuring each fold preserved the original class distribution to yield stable performance estimates and prevent overfitting.
* **Grid Search Optimization:** Systematic hyperparameter tuning was conducted to identify optimal configurations for top-performing models (specifically Support Vector Machines and Random Forests).

### 3. Implemented Classifiers
The framework evaluates six diverse machine learning paradigms:
1. **Decision Tree:** Rule-based hierarchical partitioning[cite: 11].
2. **Random Forest:** Ensemble method combining multiple randomized decision trees[cite: 11].
3. **Support Vector Machine (SVM):** Maximum-margin hyperplane separation classifier[cite: 11].
4. **K-Nearest Neighbors (KNN):** Non-parametric proximity-based classification[cite: 11].
5. **Gaussian Naive Bayes:** Probabilistic classifier assuming feature independence[cite: 11].
6. **Artificial Neural Network (MLP):** Multi-layer perceptron capturing non-linear feature interactions[cite: 11].

---

## Evaluation Metrics

To provide a holistic clinical assessment, models were evaluated across multiple dimensions:
* **Accuracy:** Overall percentage of correct predictions[cite: 11].
* **Precision:** Ratio of true positives to total predicted positives, minimizing false alarms[cite: 11].
* **Recall (Sensitivity):** Ratio of true positives to actual positives, minimizing missed diagnoses[cite: 11].
* **ROC-AUC:** Primary evaluation metric measuring the model's discriminative capability across classification thresholds[cite: 11].

---

## Results and Performance Summary

* **Best Performer:** The **Tuned Support Vector Machine (SVM)** achieved the highest performance with a peak **ROC-AUC of ~0.89**, demonstrating superior diagnostic separation[cite: 11].
* **Secondary Performer:** The **Tuned Random Forest** delivered strong generalization with an **ROC-AUC of ~0.86**[cite: 11].
* **Baseline Models:** Remaining un-tuned models averaged an ROC-AUC of ~0.78, emphasizing the necessity of rigorous hyperparameter optimization[cite: 11].

### Feature Importance Analysis
Using Random Forest feature importance scoring, the primary clinical drivers of the prediction model were identified:
1. **Glucose (~19.5%):** Primary medical indicator for metabolic screening[cite: 11].
2. **BMI (~17.9%):** Core indicator reflecting patient weight and obesity correlation[cite: 11].
3. **Insulin (~17.2%):** Critical measurement tracking insulin resistance[cite: 11].

---

## Repository Structure

```text
.
├── data/
│   └── medical_diagnostic_dataset.csv
├── notebooks/
│   └── model_training_evaluation.ipynb
├── src/
│   ├── preprocessing.py
│   ├── train.py
│   └── evaluate.py
├── outputs/
│   └── roc_curves.png
├── requirements.txt
└── README.md
