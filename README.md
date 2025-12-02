🎯 Project Objective

The goal is to build a model that:

Detects potentially fraudulent providers

Handles heavy class imbalance (~10% fraud cases)

Produces interpretable results for investigators

Prioritizes high-risk providers to reduce investigation overhead

This includes full justification of data prep, modeling choices, evaluation, and error analysis.


GIU_2620_67_26747_2025-11-10T21…

🧠 Dataset Description

Source: Kaggle – Healthcare Provider Fraud Detection Analysis

Included Files:

Train_Beneficiarydata.csv – patient demographics & chronic conditions

Train_Inpatientdata.csv – hospital admissions, procedures, costs

Train_Outpatientdata.csv – outpatient visits & tests

Train_labels.csv – provider fraud labels (Yes / No)

Key Identifiers:

BeneID → links patients to claims

Provider → links claims to final fraud label

GIU_2620_67_26747_2025-11-10T21…

🛠 Pipeline Breakdown
1. 🔍 Data Understanding & Exploration

In 01_data_exploration_and_feature_engineering.ipynb, we:

Join multi-table data using BeneID and Provider

Assess missing values & inconsistencies

Do EDA on patients, claims, and providers

Compare fraud vs non-fraud behavior patterns

Visualize class distribution, claim amounts, correlations, etc.

We also engineer provider-level aggregated features such as:

Claim counts

Average claim amounts

Percentage of chronic conditions

Cost ratios

Visit/procedure patterns


GIU_2620_67_26747_2025-11-10T21…

2. ⚖ Handling Class Imbalance

Fraud cases ≈ 10% → heavily skewed dataset.
Our notebook compares multiple strategies:

Class weighting

Oversampling (SMOTE)

Undersampling

Cost-sensitive learning

Metrics prioritized:

Precision

Recall

F1-score

PR-AUC

Accuracy is not used as a reliable indicator.


GIU_2620_67_26747_2025-11-10T21…

3. 🤖 Modeling

Implemented in 02_modeling.ipynb.

Primary model options examined:

Logistic Regression (baseline, interpretable)

Random Forest (robust for tabular mixed data)

Gradient Boosting (XGBoost/LightGBM for best performance)

SVM (tested but limited for large + imbalanced datasets)

We justify each algorithm based on:

Interpretability

Performance on imbalanced data

Computational cost

Real-world applicability


GIU_2620_67_26747_2025-11-10T21…

4. 📉 Model Evaluation

In 03_evaluation.ipynb, we run:

Cross-validation

ROC-AUC and PR-AUC

Confusion matrices

Precision-Recall curves

We also include an error analysis section with:

Case studies of false positives

Case studies of false negatives

Discussion of why the model failed in each scenario

Suggestions for future improvements


GIU_2620_67_26747_2025-11-10T21…

📝 How to Run the Project
1. Clone the repo
git clone https://github.com/<your-username>/fraud_detection_project.git
cd fraud_detection_project

2. Install dependencies
pip install -r requirements.txt

3. Add dataset

Place the four CSV files under data/
(or run the download instructions if included).

4. Run the notebooks in order:

01_data_exploration_and_feature_engineering.ipynb

02_modeling.ipynb

03_evaluation.ipynb

📊 Results Summary

(You’ll fill this section after finishing your results)
Example template:

Best Model: Random Forest / XGBoost / Logistic Regression

Best Metric (e.g., PR-AUC): 0.87

False Positive Patterns: Overbilling, high claim frequency

False Negative Patterns: Low-amount but suspicious patterns missed

Business Impact: Reduces investigation workload by X%

👥 Team Members

(Add your team names)

🏁 Final Deliverables

✔ Structured GitHub repo
✔ Full technical report
✔ Presentation slides (~10 minutes)
✔ Reproducible notebooks
✔ Clear modeling justification and error analysis

If you want, I can also generate:
✨ requirements.txt
✨ A polished technical report template
✨ Your full presentation structure + slides outline
✨ A more aesthetic version of the README with banners, icons, and emojis

Just say the word.
