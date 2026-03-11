# FactoryGuard AI – IoT Predictive Maintenance Engine

## Project Overview

FactoryGuard AI is a machine learning project that predicts **machine failures using IoT sensor data**. The goal of this system is to help industries perform **predictive maintenance**, which means detecting machine problems before they cause breakdowns. This helps reduce downtime, maintenance cost, and production loss.

The project follows a full machine learning pipeline including **data preprocessing, feature engineering, model training, model comparison, explainable AI, and model deployment**.

---

# Dataset

This project uses the **AI4I 2020 Predictive Maintenance Dataset**, which contains sensor data from industrial machines.

### Key Features

* **Type** – Machine type
* **Air temperature [K]** – Ambient temperature
* **Process temperature [K]** – Machine internal temperature
* **Rotational speed [rpm]** – Machine speed
* **Torque [Nm]** – Force applied by machine
* **Tool wear [min]** – Tool usage time
* **Machine failure** – Target variable (0 = No Failure, 1 = Failure)

Columns such as **UDI** and **Product ID** are removed because they are not useful for prediction.

---

# Libraries Used

The project is implemented using Python and the following libraries:

* **pandas** – Data processing
* **numpy** – Numerical computation
* **matplotlib & seaborn** – Data visualization
* **scikit-learn** – Machine learning algorithms
* **imblearn (SMOTE)** – Handling imbalanced data
* **XGBoost** – Advanced boosting algorithm
* **SHAP** – Explainable AI
* **joblib** – Saving trained model

---

# Project Workflow

## 1. Data Engineering

* Load dataset
* Remove unnecessary columns
* Encode categorical variables
* Handle missing values
* Perform correlation analysis
* Create new rolling features

These steps improve the quality of data used for machine learning.

---

## 2. Handling Imbalanced Data

Machine failures occur less frequently than normal operations. To solve this problem, **SMOTE** is used to generate synthetic samples for the minority class and balance the dataset.

---

# Models Used

Three machine learning models were trained and compared:

### 1. Logistic Regression (Baseline Model)

Logistic Regression was used as a **baseline model** to understand the initial performance.

Advantages:

* Simple and fast
* Easy to interpret

However, it cannot capture complex patterns in sensor data.

---

### 2. Random Forest

Random Forest is an ensemble learning algorithm that combines multiple decision trees.

Advantages:

* Handles nonlinear relationships
* Reduces overfitting
* Works well with structured datasets

Hyperparameters were optimized using **RandomizedSearchCV**.

---

### 3. XGBoost (Best Performing Model)

XGBoost is a gradient boosting algorithm that improves prediction accuracy by learning from previous errors.

Advantages:

* Very high accuracy
* Handles complex relationships
* Strong performance on structured datasets

After comparing all models, **XGBoost achieved the highest accuracy and best F1 score**, so it was selected as the **final production model**.

---

# Model Performance Comparison

| Model               | Purpose        | Performance                           |
| ------------------- | -------------- | ------------------------------------- |
| Logistic Regression | Baseline Model | Moderate accuracy                     |
| Random Forest       | Ensemble Model | Better than baseline                  |
| XGBoost             | Final Model    | Highest accuracy and best performance |

**XGBoost performed the best and is the most useful model for predicting machine failures in this project.**

---

# Model Evaluation Metrics

The models were evaluated using:

* **F1 Score**
* **Recall**
* **ROC-AUC**
* **Confusion Matrix**

Recall is very important in this project because missing a machine failure could lead to expensive equipment damage.

---

# Explainable AI

The project uses **SHAP (SHapley Additive Explanations)** to explain model predictions.
SHAP helps identify which features contribute the most to predicting machine failures.

---

# Model Deployment

After training the final model, it is saved using Joblib:

```python
joblib.dump(best_model, "factoryguard_model.pkl")
```

The saved model can be integrated into:

* Industrial IoT systems
* Monitoring dashboards
* Predictive maintenance platforms

---

# Key Features of the Project

* Machine failure prediction using IoT sensor data
* Handles imbalanced dataset using SMOTE
* Comparison of multiple machine learning models
* XGBoost used as final high-accuracy model
* Explainable AI using SHAP
* Deployment-ready model

---

# Conclusion

FactoryGuard AI demonstrates how machine learning can be used in industrial environments to build predictive maintenance systems. By predicting machine failures early, industries can improve efficiency and reduce operational risks.

---

**Author:** Grecy Patel
Machine Learning Project
