# 📊 Exploratory Data Analysis (EDA) – Cleaned Health Records

This directory contains the exploratory data analysis (EDA) conducted on the `cleaned_health_records.csv` dataset as part of the **DSA2040A – Data Mining Group Project** (Group 3).

---

## 🧾 Contents

- `Imported_health_records.csv`(renamed) – Final cleaned dataset (no missing values, consistent formatting).
- `Health_EDA.ipynb` – Jupyter Notebook with all EDA steps and insights.

---

## 🔍 Exploratory Focus

- General dataset overview (data types, missing values, duplicates).
- Statistical summaries for numeric columns (e.g., age, BMI, hospital stay days).
- Correlation matrix for numerical attributes.
- Readmission patterns explored against:
  - Diagnosis types
  - Gender
  - Medication adherence
  - Cholesterol level
  - Smoking status
  - Physical activity

---

## ✅ Key Insights (ANALYST DISCUSSION)
Project: Patient Readmission Risk Analysis


🔍 KEY FINDINGS:
1.⁠ ⁠Overall Readmission Rate: 15% (15 out of 100 patients)

2.⁠ ⁠Highest Readmission by Diagnosis:
   - Asthma, Diabetes, and Hypertension all have 17.6% readmission — the highest in the dataset.
   - These conditions should be prioritized for intervention programs.

3.⁠ ⁠Medication Adherence Paradox:
   - Adherent patients have a higher readmission rate (16.0%) than non-adherent (14.0%).
   - Likely explanation: sicker patients are more likely to adhere to medication but still face complications.
   - Recommendation: Do not assume adherence = lower risk. Consider disease severity.

4.⁠ ⁠Chronic Patients at Higher Risk:
   - 16.4% readmission rate vs 12.1% for non-chronic
   - Longer hospital stays (6.9 vs 6.4 days)
   - Significantly higher risk scores (3.10 vs 2.06)

5.⁠ ⁠Top Risk Profile:
   - Smoker + High Cholesterol + High BMI → Risk Score = 6.0 (maximum)
   - These patients need proactive monitoring, even if not yet readmitted.

✅ RECOMMENDATIONS:
•⁠  ⁠Launch targeted care management for patients with Asthma, Diabetes, and Hypertension.
•⁠  ⁠Investigate why adherent patients are readmitted — is treatment effective?
•⁠  ⁠Use the risk_score to flag high-risk patients for early intervention (e.g., lifestyle coaching).
•⁠  ⁠Validate findings with larger real-world data — this is synthetic but trend-aware.

---

## ✅ 1. Data Overview

- **Total Records**: 100
- **Columns**: 14 features (categorical, numerical, date-based)
- **Missing Values**: None
- **Duplicate Records**: None

---

## 📊 2. Key Variable Distributions

- **Gender**:
  - Male: 50%
  - Female: 50%
- **Smoking Status**:
  - Smoker: 50%
  - Non-smoker: 50%
- **Medication Adherence**:
  - Adherent: 50%
  - Non-adherent: 50%
- **Cholesterol Level**:
  - Low: 34%
  - Normal: 33%
  - High: 33%
- **Diagnosis Breakdown**:
  - Hypertension: 17
  - Diabetes: 17
  - Asthma: 17
  - Healthy: 17
  - Obesity: 16
  - Heart Disease: 16

---

## 📈 3. Readmission Analysis

- **Overall Readmission Rate**: 15%
- **Top Diagnoses by Readmission Rate** *(17.6%)*:
  - 🫁 Asthma
  - 🩸 Diabetes
  - 🫀 Hypertension
- **Readmission by Gender**:
  - Female: 7 readmitted
  - Male: 8 readmitted
- **Readmission by Medication Adherence**:
  - Adherent: 8 readmitted
  - Non-adherent: 7 readmitted

---

## 🔁 4. Crosstab Insights

### Cholesterol Level vs Diagnosis

- **High Cholesterol**:
  - Most common in *Asthma* and *Heart Disease* patients
- **Normal Cholesterol**:
  - Linked to *Diabetes* and *Obesity*
- **Low Cholesterol**:
  - Seen mostly in *Healthy* and *Hypertension*

### Smoking Status vs Diagnosis

- **Smokers**:
  - Most common in *Hypertension* and *Obesity*
- **Non-smokers**:
  - Linked to *Healthy*, *Diabetes*, and *Heart Disease*

---

## 🗓 5. Visit Dates

- **Range**: `2023-01-01` to `2024-05-10`

---

## 💾 6. Exported Outputs

All descriptive statistics and crosstab results were saved as `.csv` files inside the `/Data/` folder for downstream analysis and visualization.

---

## 🔍 Notes

This EDA focuses strictly on **descriptive statistics**. Visual insights will be presented by a separate team member using the exported `.csv` files generated in this notebook.


---

## 📦 How to Use

1. Clone the project or download this folder.
2. Ensure `pandas` is installed in your environment:
   ```bash
   pip install pandas
3.Run all codes in Health_EDA.ipynb in Order

