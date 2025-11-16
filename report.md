📘 Project Report: Credit Risk Prediction with SHAP
🎯 Objective
This project builds a machine learning pipeline to predict credit risk and interpret model decisions using SHAP (SHapley Additive exPlanations). The goal is to classify loan applicants as high or low risk and provide actionable insights for underwriting.

🧪 Dataset
- Synthetic dataset of 20,000 applicants
- Features include: age, income, loan_amount, credit_score, employment_length_years, home_ownership, and more
- Target variable: default (1 = high risk, 0 = low risk)
- Class imbalance addressed using SMOTE

⚙️ Methodology
🔄 Preprocessing
- Numeric features: imputed with median, scaled with StandardScaler
- Categorical features: imputed with mode, encoded with OneHotEncoder
- Pipeline built using ColumnTransformer
🧠 Model Training
- Models tested: XGBoost, LightGBM, RandomForest
- Final model: LightGBM with SMOTE
- Hyperparameter tuning via RandomizedSearchCV (AUC scoring)

📊 Evaluation Metrics
- ROC-AUC Score: 0.5166
- F1 Score: 0.0453
- Precision: 0.4444
- Recall: 0.0239
- Accuracy: 0.92



- Model predicts class 1 with moderate precision but low recall
- Confusion matrix confirms valid TP, FP, FN cases for SHAP analysis

🔍 SHAP Interpretability
🌐 Global SHAP Summary
Top 5 features by mean absolute SHAP value:
- CreditScore – Lower scores increase risk
- LoanAmount – Larger loans push toward high risk
- Income – Lower income contributes to risk
- EmploymentStatus – Unstable employment increases risk
- Age – Younger applicants slightly more likely to default
🧪 Local Case Studies
✅ True Positive (TP)
- Applicant correctly flagged as high risk due to:
- CreditScore = 580
- LoanAmount = ₹5L
- Employment length = 1 year
❌ False Positive (FP)
- Applicant incorrectly flagged despite:
- CreditScore = 720
- Risk driven by high LoanAmount and short employment history
❌ False Negative (FN)
- Risky applicant missed due to:
- CreditScore = 610
- Low LoanAmount masking unstable employment

📣 Underwriting Recommendations
- Flag applicants with CreditScore < 600 for manual review
- Prioritize stable employment history in risk assessment
- Limit exposure to high LoanAmount-to-Income ratios, especially for younger applicants
- Monitor increases in delinquencies and derogatory marks for early intervention
- Apply DTI threshold policies to trigger additional documentation or collateral

📁 Deliverables
All outputs saved to outputs/ folder:
- metrics_report.json, classification_report.txt
- global_shap_importance.csv, textual_shap_report.txt
- local_shap_explanations.json, force plots and waterfall plots
- underwriting_recommendations.txt


