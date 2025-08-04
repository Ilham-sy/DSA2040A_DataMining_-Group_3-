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

## ✅ Key Insights

This report presents the **non-visual exploratory data analysis (EDA)** of a healthcare dataset. The analysis focuses on cleaning, summarizing, and identifying trends related to patient readmission and health behavior. Visualization will be handled separately.

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

