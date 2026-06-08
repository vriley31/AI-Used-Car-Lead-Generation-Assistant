# Personal Bank Loan Prediction Model
# 🏦 Bank Personal Loan Acceptance Prediction

## 📌 Project Overview

Financial institutions spend significant resources marketing loan products to customers who may never convert. This project uses predictive analytics and classification modeling to identify customers who are most likely to accept a personal loan offer.

Using the Bank Loan Modeling dataset, a Decision Tree Classification model was developed to analyze customer demographic and financial behavior data and predict loan acceptance. The goal was to improve marketing efficiency, increase conversion rates, and support data-driven decision-making within the financial services industry.

---

## 🎯 Business Problem

Can customer demographic and financial behavior data be used to predict whether a customer will accept a personal loan offer?

Financial institutions often use broad marketing campaigns that generate low conversion rates and unnecessary expenses. By identifying customers with a higher probability of accepting a loan offer, organizations can:

- Improve marketing ROI
- Reduce customer acquisition costs
- Increase loan conversion rates
- Personalize marketing efforts
- Improve customer engagement

---

## 📊 Dataset Information

**Dataset:** Bank Personal Loan Modeling

**Source:** Kaggle

The dataset contains 5,000 customer records and 14 variables.

### Key Variables

| Variable | Description |
|-----------|-------------|
| Age | Customer age |
| Experience | Years of professional experience |
| Income | Annual income ($000) |
| Family | Family size |
| CCAvg | Average monthly credit card spending |
| Education | Education level |
| Mortgage | Mortgage balance |
| Securities Account | Investment account ownership |
| CD Account | Certificate of Deposit ownership |
| Online | Online banking usage |
| CreditCard | Credit card ownership |
| Personal Loan | Target variable |

---

## 🛠 Technologies Used

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Scikit-Learn
- Jupyter Notebooks

---

## 🔍 Data Auditing & Preparation

The dataset underwent extensive profiling and quality checks prior to modeling.

### Data Validation Activities

✔ Missing Value Analysis

✔ Duplicate Record Analysis

✔ Descriptive Statistics Review

✔ Data Type Validation

✔ Feature Selection

✔ Train/Test Split

### Data Cleaning Steps

- Verified no missing values existed
- Verified no duplicate records existed
- Removed non-predictive variables:
  - ID
  - ZIP Code
- Created training and testing datasets
- Validated binary target variable

---

## 📈 Exploratory Data Analysis

Several visualizations were created to better understand customer behavior and identify predictive patterns.

### Visualizations

- Personal Loan Distribution
- Income Distribution Histogram
- Correlation Heatmap
- Feature Importance Analysis
- Decision Tree Visualization
- Confusion Matrix

### Key Findings

- Higher-income customers were more likely to accept loans.
- Customers with CD Accounts demonstrated significantly higher conversion rates.
- Average Credit Card Spending was a strong predictor.
- Education level influenced loan acceptance behavior.
- Existing product relationships increased the likelihood of conversion.

---

## 🤖 Predictive Model

### Model Selected

**Decision Tree Classifier**

Decision Trees were selected because they:

- Handle both numerical and categorical variables
- Support binary classification problems
- Provide interpretable business rules
- Generate visual decision pathways
- Support regulatory transparency

---

## 📊 Model Results

### Performance Metrics

| Metric | Result |
|----------|----------|
| Accuracy | XX% |
| Precision | XX% |
| Recall | XX% |
| F1 Score | XX% |

*(Update with your actual model results.)*

---

## 📌 Feature Importance

Top predictors of loan acceptance:

1. Income
2. CD Account
3. CCAvg
4. Education
5. Family

These variables were found to have the greatest impact on predicting customer loan acceptance behavior.

---

## 💡 Business Recommendations

Based on the analysis, financial institutions should:

### Target High-Probability Customers

Focus marketing campaigns on customers exhibiting characteristics associated with higher conversion rates.

### Improve Customer Segmentation

Develop personalized marketing strategies based on customer financial profiles.

### Increase Cross-Selling Opportunities

Leverage existing customer relationships to promote additional lending products.

### Continuously Monitor Model Performance

Regularly retrain models to account for changing customer behavior and economic conditions.

---

## ⚖ Ethical Considerations

Predictive analytics within financial services requires responsible data governance.

### Risks

- Algorithmic bias
- Customer privacy concerns
- Regulatory compliance issues
- Fair lending considerations

### Mitigation Strategies

- Regular bias testing
- Model monitoring
- Transparent decision-making processes
- Compliance reviews
- Strong data governance practices

---

## 📷 Project Screenshots

### Personal Loan Distribution

![Loan Distribution](images/loan_distribution.png)

### Feature Importance

![Feature Importance](images/feature_importance.png)

### Decision Tree Visualization

![Decision Tree](images/decision_tree.png)

### Confusion Matrix

![Confusion Matrix](images/confusion_matrix.png)

---

# ==========================================
# Bank Personal Loan Prediction Project
# Victoria Riley
# ==========================================

# Import libraries
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import (
    accuracy_score,
    classification_report,
    confusion_matrix
)

# ------------------------------------------
# Load Dataset
# ------------------------------------------

df = pd.read_excel(
    "data/Bank_Personal_Loan_Modelling.xlsx",
    sheet_name="Data"
)

print("Dataset Shape:", df.shape)
print(df.head())

# ------------------------------------------
# Data Profiling
# ------------------------------------------

print("\nMissing Values:")
print(df.isnull().sum())

print("\nDuplicate Records:")
print(df.duplicated().sum())

print("\nSummary Statistics:")
print(df.describe())

# ------------------------------------------
# Data Preparation
# ------------------------------------------

# Remove non-predictive columns

df_model = df.drop(
    columns=["ID", "ZIP Code"]
)

# Features and target

X = df_model.drop(
    columns=["Personal Loan"]
)

y = df_model["Personal Loan"]

# ------------------------------------------
# Train/Test Split
# ------------------------------------------

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.30,
    random_state=42,
    stratify=y
)

print("\nTraining Shape:", X_train.shape)
print("Testing Shape:", X_test.shape)

# ------------------------------------------
# Build Decision Tree Model
# ------------------------------------------

model = DecisionTreeClassifier(
    criterion="gini",
    max_depth=4,
    min_samples_leaf=20,
    random_state=42
)

model.fit(X_train, y_train)

# ------------------------------------------
# Predictions
# ------------------------------------------

y_pred = model.predict(X_test)

# ------------------------------------------
# Model Evaluation
# ------------------------------------------

accuracy = accuracy_score(
    y_test,
    y_pred
)

print("\nModel Accuracy:")
print(round(accuracy * 100, 2), "%")

print("\nClassification Report:")
print(
    classification_report(
        y_test,
        y_pred
    )
)

print("\nConfusion Matrix:")
print(
    confusion_matrix(
        y_test,
        y_pred
    )
)

# ------------------------------------------
# Feature Importance
# ------------------------------------------

importance = pd.DataFrame({
    "Feature": X.columns,
    "Importance": model.feature_importances_
})

importance = importance.sort_values(
    by="Importance",
    ascending=False
)

print("\nFeature Importance:")
print(importance)

# ------------------------------------------
# Feature Importance Visualization
# ------------------------------------------

plt.figure(figsize=(10, 6))

plt.barh(
    importance["Feature"],
    importance["Importance"]
)

plt.gca().invert_yaxis()

plt.title(
    "Feature Importance for Loan Acceptance"
)

plt.xlabel("Importance Score")
plt.ylabel("Features")

plt.tight_layout()

plt.show()
---

## 👩‍💻 Author

**Victoria Riley**

MS Information Technology – Analytics Candidate  
Capella University

Data Analytics | Predictive Modeling | Business Intelligence | Marketing Analytics | Financial Services Analytics

📫 Connect with me on GitHub and LinkedIn!
