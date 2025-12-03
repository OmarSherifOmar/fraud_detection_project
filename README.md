

# 🏥 Healthcare Provider Fraud Detection

*Machine Learning Project – GIU*

---

## 🎯 **Project Objective**

The goal of this project is to build a machine learning pipeline that:

* 🔎 **Detects potentially fraudulent healthcare providers**
* ⚖️ **Handles heavy class imbalance** (~10% fraud cases)
* 🔍 **Produces interpretable results** for investigators
* 🚨 **Prioritizes high-risk providers** to reduce investigation workloads
* 📝 Provides **full justification** for data preparation, modeling, evaluation, and error analysis

---

## 🧠 **Dataset Description**

**Source:** Kaggle – *Healthcare Provider Fraud Detection Analysis*

### **Included Files**

| File                        | Description                                   |
| --------------------------- | --------------------------------------------- |
| `Train_Beneficiarydata.csv` | Patient demographics, chronic conditions      |
| `Train_Inpatientdata.csv`   | Inpatient admissions, procedures, claim costs |
| `Train_Outpatientdata.csv`  | Outpatient visits & tests                     |
| `Train_Labels.csv`          | Provider-level fraud labels (**Yes / No**)    |

### 🔗 **Key Identifiers**

* **BeneID** → links patients to claims
* **Provider** → links claims to final fraud label

---

## 🛠 **Pipeline Overview**

### **1. 🔍 Data Understanding & Exploration**

*Notebook: `01_data_exploration_and_feature_engineering.ipynb`*

Key steps:

* Merging multiple tables using `BeneID` and `Provider`
* Checking missing values and inconsistencies
* Exploring patient demographics, inpatient/outpatient claims
* Comparing behavior patterns between **fraud** and **non-fraud** providers
* Visualizing distributions, correlations, and cost behavior

**Engineered provider-level features include:**

* Total claim counts
* Average / max claim amounts
* Percentage of chronic conditions
* Visit/procedure patterns
* Cost ratios
* Patient distribution metrics

---

### **2. ⚖ Handling Class Imbalance**

Fraud ≈ **10%** → highly imbalanced dataset

Techniques evaluated:

* 🧮 **Class weighting**
* ➕ **SMOTE oversampling**
* ➖ **Random undersampling**
* 💰 **Cost-sensitive learning**

**Priority Metrics:**

* Precision
* Recall
* F1-Score
* **PR-AUC** (best for imbalance)
* *(Accuracy avoided due to misleading results)*

---

### **3. 🤖 Modeling**

*Notebook: `02_modeling.ipynb`*

Models evaluated:

| Model                                      | Reason                                          |
| ------------------------------------------ | ----------------------------------------------- |
| **Logistic Regression**                    | Baseline, interpretable                         |
| **Random Forest**                          | Handles tabular + mixed data well               |
| **Gradient Boosting (XGBoost / LightGBM)** | Best performance, handles imbalance             |
| **SVM**                                    | Tested, but high cost for large imbalanced data |

Evaluation based on:

* Interpretability
* Performance on imbalanced data
* Training speed
* Real-world deployability

---

### **4. 📉 Model Evaluation & Error Analysis**

*Notebook: `03_evaluation.ipynb`*

Includes:

* Cross-validation
* ROC-AUC & PR-AUC
* Confusion matrices
* Precision-Recall curves

**Error Analysis:**

* 🔴 **False Positives:**
  Often due to high billing frequency or unusual cost spikes
* 🟠 **False Negatives:**
  Low-amount claims with subtle suspicious patterns
* 🔧 **Recommendations:**
  Feature expansion, anomaly detection, cost-benefit thresholds


## 🏁 **Final Deliverables**

* ✔ Reproducible notebooks
* ✔ Clean, structured GitHub repo
* ✔ Full technical report
* ✔ Error analysis
* ✔ Presentation slides (10 minutes)


