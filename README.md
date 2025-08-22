# 🩺 Predicting 30-Day Readmission in Diabetic Patients  
*(Educational demo using XGBoost + SHAP)*

## 📌 Project Overview
Hospital readmissions within 30 days are costly for healthcare systems and stressful for patients.  
Identifying high-risk patients early can support better care management and potentially reduce avoidable readmissions.  

In this project, we use the **Diabetes 130-US hospitals dataset (1999–2008)** to:  
- Train a machine learning model (**XGBoost**) to predict 30-day readmission.  
- Apply **SHAP** for explainability at **global, patient, and cohort levels**.  
- Visualize the most important risk factors driving readmission.  

⚠️ **Disclaimer:** This project is for **educational purposes only** (Coursera *AI for Medicine* specialization).  
It is **not intended for clinical use**.

---

## 🗂 Dataset
- **Name:** Diabetes 130-US hospitals (1999–2008)  
- **Size:** >100,000 admissions across 130 hospitals  
- **Features:** demographics, labs, hospital utilization, medications, outcomes  
- **Target:** Readmission within 30 days (`<30`)  
- **Source:** [UCI ML Repository](https://archive.ics.uci.edu/ml/datasets/diabetes+130-us+hospitals+for+years+1999-2008) / Kaggle mirrors  

---

## ⚙️ Project Workflow
1. **Data Cleaning & Feature Engineering**
   - Convert age brackets to numeric midpoints.
   - Create binary flags for elevated A1C and glucose.
   - Encode medication use and dosage changes.
   - Include utilization variables (number of inpatient visits, meds, diagnoses).

2. **Model Training**
   - Train **XGBoost** with early stopping.
   - Handle class imbalance via `scale_pos_weight`.

3. **Evaluation**
   - ROC-AUC and PR-AUC (important for imbalanced medical data).
   - ROC and Precision-Recall curves.

4. **Explainability with SHAP**
   - **Global:** Beeswarm & bar plots.
   - **Local (patient-level):** Waterfall plots explaining single predictions.
   - **Cohort-level:** Risk profiles for defined subgroups.

---

## 📊 Results
- **ROC-AUC:** ~0.7 (varies slightly by random seed)  
- **PR-AUC:** ~0.2 (reflects strong class imbalance)  

### Example SHAP insights:
- Higher number of prior inpatient visits strongly increases readmission risk.  
- Elevated A1C and glucose are predictive of poor outcomes.  
- Some medications (e.g., insulin changes) also contribute to increased risk. 
