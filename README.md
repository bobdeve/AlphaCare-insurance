📘 ACIS Risk-Based Pricing Project
This project is part of a larger effort to build a data-driven insurance pricing system for ACIS (African Continental Insurance Services). The system includes end-to-end data exploration, hypothesis testing, and predictive modeling to support fair, accurate, and dynamic premium pricing.

✅ Task 1: Exploratory Data Analysis (EDA)
🎯 Goal:
Understand the structure, distribution, and relationships in the data.

🛠️ Key Steps:
Checked missing values and handled them appropriately.

Explored key variables like TotalPremium, TotalClaims, Province, Gender, and PostalCode.

Visualized claim distribution, premium patterns, and correlations.

📊 Findings:
Claim values are right-skewed: most people claim small amounts.

Gender has many "Not specified" entries.

Claim frequency and amount vary significantly across provinces and zip codes.

✅ Task 2: Data Version Control (DVC) Setup
🎯 Goal:
Ensure reproducibility and version control over data and modeling pipeline.

🛠️ Key Steps:
Initialized DVC in the project.

Set up .dvc files to track raw data files (e.g., data.csv).

Configured .gitignore to avoid pushing large raw data to GitHub.

Committed changes with a clear data pipeline and backup strategy.

🧠 Benefits:
Supports collaborative, reproducible ML workflows.

Keeps code clean while storing heavy data files separately.

✅ Task 3: Hypothesis Testing
🎯 Goal:
Use statistical testing to check whether certain attributes influence claim risk.

🛠️ Tests Performed:
Chi-square test for categorical variables (e.g., Province, ZipCode, Gender).

ANOVA test for continuous variables grouped by categories (e.g., TotalClaims by Province).

📈 Summary of Results:
Hypothesis	p-value	Result
Risk differs by Province (Frequency)	0.000	Reject H₀
Risk differs by Province (Severity)	0.000	Reject H₀
Risk differs by ZipCode (Frequency)	0.000	Reject H₀
Risk differs by ZipCode (Severity)	0.001	Reject H₀
Margin differs by ZipCode	0.096	Fail to Reject H₀
Risk differs by Gender	0.858	Fail to Reject H₀

🔍 Interpretation:
Location (Province, ZipCode) has a strong impact on claim patterns.

Gender shows no statistically significant impact.

✅ Task 4: Predictive Modeling & Risk-Based Pricing
🎯 Goals:
Predict Claim Severity (TotalClaims for records with claims).

Predict Claim Probability (likelihood a claim will happen).

Combine these into a Risk-Based Pricing Model.

🧪 Data Preparation:
Imputed missing values and created new features (e.g., Margin).

Encoded categorical data with One-Hot Encoding.

Used train_test_split with 80:20 ratio for modeling.

📦 Models Used:
Problem	Model Type	Algorithms	Metrics
Claim Severity	Regression	Linear Regression, Random Forest, XGBoost	RMSE, R²
Claim Probability	Classification	XGBoost Classifier	Accuracy, Precision, Recall, ROC-AUC

📉 Results:
XGBoost outperformed others in both tasks.

Risk-based premium formula used:

Premium
=
(
Predicted Probability
×
Predicted Severity
)
+
Expenses
+
Profit
Premium=(Predicted Probability×Predicted Severity)+Expenses+Profit
📌 Feature Importance:
Used SHAP to interpret top features.

Most important: ClientIncome, VehicleAge, Province, VehicleValue.

🚀 Key Takeaways
A dynamic, fairer premium system was built using real claims data.

The new model allows ACIS to offer personalized pricing based on actual risk.

SHAP helped explain how features like income and vehicle value affect claims.
