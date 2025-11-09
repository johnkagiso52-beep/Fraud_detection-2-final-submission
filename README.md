Fraud Detection in African Mobile Transactions Using ML and XAI
Project Overview
This capstone project develops a robust, transparent, and intelligent fraud detection system tailored for the African mobile money ecosystem. By leveraging machine learning and Explainable AI (XAI), the project addresses the critical challenges of class imbalance and model interpretability, providing a reliable tool to enhance financial security and customer trust.

Key Achievements:

Achieved 96.54% accuracy and 99.08% recall in detecting fraudulent transactions using the XGBoost model.

Successfully addressed severe class imbalance (0.13% fraud) using SMOTE and random undersampling.

Integrated SHAP (XAI) to provide clear, actionable explanations for model predictions, enhancing trust and auditability.

Identified that fraud is exclusively concentrated in 'CASH_OUT' and 'TRANSFER' transaction types, providing a strategic focus for monitoring.

Business Understanding
The rapid growth of mobile money in Africa has been accompanied by an increase in sophisticated financial fraud. Traditional rule-based systems are often ineffective and lack adaptability. This project delivers a data-driven solution that helps:

Financial Institutions & FinTechs: Reduce financial losses and ensure regulatory compliance.

Telecom Providers: Secure their mobile money platforms and protect user data.

Regulators: Gain insights into fraud patterns to refine oversight frameworks.

End-Users: Benefit from safer and more reliable digital transactions.

Dataset
This project uses the PaySim dataset, a synthetic mobile money transaction dataset generated from real-world transactional logs.

Source: Kaggle - PaySim Financial Dataset

Size: ~6.3 million transactions.

Features: 11 original features, including step, type, amount, nameOrig, oldbalanceOrg, newbalanceOrig, nameDest, oldbalanceDest, newbalanceDest, isFraud, isFlaggedFraud.

Key Characteristic: Severe class imbalance, with only 0.13% of transactions labeled as fraudulent (isFraud = 1).

Methodology
The project follows the CRISP-DM (Cross-Industry Standard Process for Data Mining) methodology.

1. Data Understanding & Exploration (EDA)
Analyzed data structure, missing values, and duplicates (none found).

Performed univariate and bivariate analysis to understand fraud patterns.

Key Finding: Fraud is only present in CASH_OUT and TRANSFER transactions, and these fraudulent transactions are typically of a higher monetary value.

2. Data Preprocessing
Feature Engineering: Created new features balanceDiffOrig and balanceDiffDest (the difference in account balances before and after a transaction).

Encoding: Applied one-hot encoding to the categorical type feature.

Scaling: Standardized numerical features (amount, balanceDiffOrig, balanceDiffDest) using StandardScaler.

Data Balancing: Addressed class imbalance using a hybrid approach:

Random Undersampling of the majority class (non-fraud).

SMOTE (Synthetic Minority Oversampling Technique) to generate synthetic samples of the minority class (fraud).

3. Modeling
Multiple machine learning algorithms were trained and evaluated to identify the best performer:

Ensemble Methods: XGBoost, LightGBM, Random Forest, AdaBoost

Linear Models: Logistic Regression, Linear SVC, Perceptron

Other Models: K-Nearest Neighbors (KNN), Decision Tree

4. Evaluation & Explainability
Evaluation Metrics: Accuracy, Precision, Recall, F1-Score, and AUC-ROC.

Model Interpretation: Used SHAP (SHapley Additive exPlanations) with the best-performing model (XGBoost) to explain predictions globally and locally.

Results
The XGBoost model demonstrated superior performance, as summarized below:

Model	Accuracy	Precision	Recall	F1-Score
XGBoost	96.54%	94.28%	99.08%	96.62%
LightGBM	96.12%	94.01%	99.07%	96.46%
Random Forest	96.09%	93.45%	99.06%	96.17%
Logistic Regression	95.89%	92.41%	99.06%	95.62%
Key Insights from SHAP Analysis:
The most important feature for fraud detection was balanceDiffOrig (the change in the originator's balance).

amount and balanceDiffDest were also highly influential.

Transaction types CASH_OUT and TRANSFER were confirmed as significant fraud indicators, while DEBIT and CASH_IN had negligible impact.
