# 📊 Customer Churn Prediction (End-to-End ML Pipeline)
<p align="center">
  <img
    src="assets/Customer Churn Prediction.png"
    alt="Customer Churn Prediction"
    width="100%"
  />
</p>
---

## 🧠 Problem Statement

Customer churn is a critical business problem where companies lose customers over time.
The objective of this project is to build a machine learning model that predicts whether a customer is likely to churn, enabling proactive retention strategies.

---

## 🎯 Objectives

* Predict churn (Yes/No)
* Understand key drivers of churn
* Optimize model performance beyond accuracy
* Translate results into business insights

---

## 📂 Dataset

Telco Customer Churn Dataset

### Features include:

* Customer demographics
* Account information
* Service usage
* Billing details

### Target:

* `Churn` → (1 = Yes, 0 = No)

---

## 🔍 Exploratory Data Analysis (EDA)

### Key Findings:

* Data is **imbalanced** (more non-churn than churn)
* Customers with **low tenure** churn more
* **High monthly charges** increase churn risk
* **Month-to-month contracts** have higher churn

---

## 🧹 Data Cleaning & Preprocessing

* Converted `TotalCharges` to numeric
* Removed missing values
* Dropped irrelevant columns (e.g., `customerID`)
* Applied **One-Hot Encoding** for categorical features

---

## ⚙️ Feature Engineering

Created new features to improve model understanding:

* `AvgCharge = TotalCharges / tenure`
* `IsNewCustomer` → tenure < 12
* `HighCharges` → MonthlyCharges > threshold

### Insight:

Feature engineering significantly improved model interpretability and performance.

---

## ⚖️ Handling Class Imbalance

Used:

* `class_weight="balanced"`

### Impact:

* Improved Recall (capturing churn cases)
* Prevented model bias toward majority class

---

## 🤖 Models Used

### 1) Logistic Regression

* Baseline model
* Required feature scaling
* High recall but lower precision

---

### 2) Decision Tree

* Non-linear model
* Captures complex relationships
* Prone to overfitting (controlled via max_depth)

---

### 3) Random Forest (Final Model)

* Ensemble of multiple trees
* Reduces overfitting
* Provides better generalization

---

## 📊 Model Evaluation

Used multiple metrics (NOT accuracy only):

* **Precision** → correctness of churn predictions
* **Recall** → ability to detect churn (critical)
* **F1-score** → balance between precision & recall

---

## 📉 Confusion Matrix

Used to analyze:

* False Positives (unnecessary actions)
* False Negatives (missed churn → high business cost)

---

## 🔧 Feature Importance Analysis

Top features influencing churn:

* `tenure`
* `TotalCharges`
* `MonthlyCharges`
* `AvgCharge`
* `Contract type`

### Insight:

* New customers are more likely to churn
* Higher cost → higher churn risk
* Long-term contracts reduce churn

---

## ✂️ Feature Selection

* Removed low-importance features
* Reduced noise in the dataset

### Result:

* Model became simpler
* Performance remained stable (Random Forest handles noise well)

---

## 🔁 Cross Validation

* Used 5-fold cross-validation
* Ensured model stability

### Result:

* Consistent F1-score across folds
* No significant overfitting

---

## 🔍 Hyperparameter Tuning

Used GridSearchCV to optimize:

* `n_estimators`
* `max_depth`
* `min_samples_split`

### Best Parameters:

* n_estimators = 200
* max_depth = 10
* min_samples_split = 5

---

## 🎚️ Threshold Tuning (Critical Step)

Instead of default 0.5, tested:

* 0.4 → High recall, low precision
* 0.5 → Best balance
* 0.6 → Higher precision, lower recall

### Final Decision:

* **Threshold = 0.5**

---

## 🏆 Final Model

**Random Forest (Tuned)**

### Configuration:

* n_estimators = 200
* max_depth = 10
* min_samples_split = 5
* class_weight = balanced

---

## 📈 Final Results

| Metric    | Score |
| --------- | ----- |
| Precision | ~0.54 |
| Recall    | ~0.71 |
| F1-score  | ~0.61 |
| Accuracy  | ~0.76 |

---

## 💼 Business Insights

* New customers need onboarding support
* High-paying customers need retention offers
* Contract duration strongly impacts churn
* Target high-risk customers early

---

## 🚀 Conclusion

This project demonstrates a complete ML pipeline:

* Data cleaning & preprocessing
* Feature engineering
* Model comparison
* Imbalance handling
* Hyperparameter tuning
* Threshold optimization

The final model achieves a strong balance between precision and recall, making it suitable for real-world deployment.

---

## 🧠 Key Skills Demonstrated

* Machine Learning Modeling
* Feature Engineering
* Model Evaluation & Optimization
* Handling Imbalanced Data
* Business Interpretation

---

## 📌 Future Improvements

* Deploy model (Streamlit / API)
* Use SHAP for explainability
* Try advanced models (XGBoost, LightGBM)

---

## 👨‍💻 Author

Mahmoud Morsy
