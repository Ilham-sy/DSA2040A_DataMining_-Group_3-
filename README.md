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

- **Medication adherence** impacts readmission: non-adherent patients had a higher chance of being readmitted.
- **Diabetes** was only observed in patients with **normal cholesterol** and **non-smoking** status.
- **Asthma** and **Hypertension** were more common in patients who **smoked** or had **high cholesterol**.
- **Physical activity** correlated with diagnosis type:
  - Active individuals mostly had asthma or heart disease.
  - Sedentary individuals mostly had hypertension or were labeled obese.
- Weak positive correlation found between **age** and **hospital stay days**.

---

## 📦 How to Use

1. Clone the project or download this folder.
2. Ensure `pandas` is installed in your environment:
   ```bash
   pip install pandas
3.Run all codes in Health_EDA.ipynb in Order

