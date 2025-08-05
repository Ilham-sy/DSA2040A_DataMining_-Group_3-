HEALTHCARE PROJECT GROUP 3
Overview
This project generates and analyzes a synthetic dataset of 100 patient health records to study hospital readmission risks. The dataset simulates real-world health data, including demographic and clinical variables such as age, diagnosis, BMI, smoking status, and readmission status. The project follows a structured data pipeline:

ETL (Extract, Transform, Load): Generates synthetic data, enriches it with derived features (e.g., risk score, chronic condition flag), and saves it in raw and transformed formats.
Exploratory Data Analysis (EDA): Examines data distributions, correlations, and relationships between variables like diagnosis, readmission, and risk factors.
Analysis: Computes key metrics, such as readmission rates by diagnosis and the impact of medication adherence, to identify high-risk patient groups.
Visualization: Creates plots to visualize distributions, correlations, and group comparisons, aiding in the interpretation of findings.

The goal is to identify patterns in readmission risks and provide actionable recommendations for healthcare interventions, such as targeting high-risk diagnoses or investigating medication adherence effects.
Project Goals

Generate reproducible synthetic health data to simulate patient records.
Perform ETL to clean and enrich data for analysis.
Conduct EDA to understand data distributions and relationships.
Analyze readmission rates and risk factors to identify high-risk patient profiles.
Visualize key findings to support decision-making.
Provide recommendations for reducing hospital readmissions.

Dataset

Source: Synthetically generated using Python’s faker library and deterministic calculations with a random seed (42) for reproducibility.
Fields:
patient_id: Unique 5-digit identifier (10001–10100).
name: Synthetic patient name.
age: Patient age (20–79).
gender: Male or Female.
diagnosis: One of Hypertension, Diabetes, Asthma, Healthy, Obesity, or Heart Disease.
blood_pressure: Systolic/diastolic (e.g., "100/60").
bmi: Body Mass Index, calculated from weight and height.
smoking_status: Smoker or Non-smoker.
physical_activity: Sedentary, Moderate, or Active.
cholesterol_level: Low, Normal, or High.
medication_adherence: Adherent or Non-adherent.
hospital_stay_days: Number of days in hospital (0–14).
readmitted: Yes or No, indicating hospital readmission.
visit_date: Date of hospital visit (2023-01-01 to 2024-05-10).
age_group: Adult (<60) or Elderly (≥60).
risk_score: Calculated score (0–6) based on smoking, cholesterol, and BMI.
is_chronic: 1 for chronic conditions (Hypertension, Diabetes, Asthma, Heart Disease), 0 otherwise.


Size: 100 records.
Output Files:
Raw data: data/raw/health_records.csv
Transformed data: data/transformed/cleaned_health_records.csv
Analysis outputs: Various CSV files (e.g., correlation_matrix.csv, diagnosis_counts.csv) in Data/.



Installation
To run the project, ensure you have Python 3.12+ and the required libraries installed.

Clone the repository:git clone https://github.com/username/patient-readmission-analysis.git
cd patient-readmission-analysis


Install dependencies:pip install pandas faker seaborn matplotlib


Verify the directory structure:├── data/
│   ├── raw/
│   ├── transformed/
│   ├── Data/  # For EDA outputs
├── notebooks/
│   ├── data_generation.ipynb
│   ├── Health_EDA.ipynb
├── README.md



Usage

Generate Data:

Open notebooks/data_generation.ipynb in Jupyter Notebook:jupyter notebook notebooks/data_generation.ipynb


Run all cells to generate and save:
health_records.csv (raw data) in data/raw/.
cleaned_health_records.csv (transformed data with enriched fields) in data/transformed/.


The notebook also performs initial analysis and generates an analyst report.


Perform EDA:

Open notebooks/Health_EDA.ipynb in Jupyter Notebook:jupyter notebook notebooks/Health_EDA.ipynb


Run cells to generate summary statistics, value counts, correlations, and crosstabs, saved as CSVs in Data/.


Visualize Data:

The visualization code (provided separately) generates:
A correlation heatmap for numeric features (age, bmi, hospital_stay_days, risk_score).
Histograms for age, bmi, hospital_stay_days, and risk_score distributions.
A bar chart comparing mean values of numeric features by chronic condition status.
A boxplot of bmi by diagnosis.


Save the visualization code in a script (e.g., visualizations.py) and run:python visualizations.py


Outputs are displayed as plots (requires a graphical environment).



ETL Process

Extract: Synthetic data is generated using faker for names and deterministic calculations for other fields (e.g., age = 20 + (i % 60)). A random seed ensures reproducibility.
Transform:
Calculates bmi from weight and height.
Formats blood_pressure as a string (e.g., "100/60").
Assigns readmitted based on a modulo condition (i % 7 == 0).
Enriches data with:
age_group: Adult (<60) or Elderly (≥60).
risk_score: Based on smoking (+2), high cholesterol (+2), and BMI (≥30: +2, ≥25: +1).
is_chronic: Flags chronic conditions.


Removes duplicates and standardizes visit_date to datetime.


Load: Saves raw data as health_records.csv and transformed data as cleaned_health_records.csv.

Reasoning: The ETL process ensures data consistency and enriches the dataset with derived features for analysis. The synthetic data mimics real-world health records but uses deterministic patterns, which may limit variability.
Exploratory Data Analysis (EDA)
The EDA (in Health_EDA.ipynb) includes:

Summary Statistics: For numeric columns (age, bmi, hospital_stay_days, patient_id).
Missing Values and Duplicates: Checks for data quality (none found in this synthetic dataset).
Categorical Counts: For diagnosis, gender, smoking_status, physical_activity, cholesterol_level, medication_adherence, and readmitted.
Correlations: Computes a correlation matrix for numeric columns, saved as Data/correlation_matrix.csv.
Crosstabs: Analyzes relationships like readmission vs. diagnosis, medication adherence, gender, cholesterol level, and smoking status.
Date Range: Identifies the range of visit_date (2023-01-01 to 2024-05-10).
Readmission Rates: Calculates rates by diagnosis, highlighting Asthma, Diabetes, and Hypertension (17.6%).

Reasoning: The EDA provides a comprehensive view of the dataset, identifying distributions and relationships critical for understanding readmission risks. The focus on readmission rates and categorical variables aligns with the project’s goal.
Analysis
The analysis (in data_generation.ipynb) computes:

Overall Readmission Rate: 15% (15/100 patients).
Readmission by Diagnosis: Asthma, Diabetes, and Hypertension have the highest rates (17.6%), followed by Heart Disease and Obesity (12.5%), and Healthy (11.8%).
Medication Adherence Impact: Adherent patients have a higher readmission rate (16.0%) than non-adherent (14.0%), suggesting sicker patients adhere more but face complications.
Chronic vs. Non-Chronic Patients:
Chronic: 16.42% readmission rate, 6.93-day average stay, 3.10 average risk score.
Non-Chronic: 12.12% readmission rate, 6.39-day average stay, 2.06 average risk score.


Risk Score Drivers: Smokers with high cholesterol and BMI ≥ 35 have the highest risk score (6.0).

Reasoning: The analysis identifies high-risk groups and counterintuitive findings (e.g., adherence paradox), guiding targeted interventions. The synthetic data’s deterministic nature creates uniform patterns, which should be validated with real-world data.
Visualizations
The visualization code generates:

Correlation Heatmap: Shows correlations between age, bmi, hospital_stay_days, and risk_score using Seaborn’s heatmap.
Histograms:
age: Distribution across 20–79 years.
bmi: Distribution, ranging from ~22 to ~35.
hospital_stay_days: Distribution, 0–14 days.
risk_score: Distribution, showing risk levels (0–6).


Bar Chart: Compares mean age, bmi, hospital_stay_days, and risk_score for chronic vs. non-chronic patients.
Boxplot: Shows bmi distribution by diagnosis, highlighting variability.

Reasoning: The visualizations effectively highlight distributions and relationships. The heatmap reveals weak correlations (e.g., age and hospital_stay_days: 0.22), while histograms show the spread of key variables. The bar chart and boxplot emphasize differences between chronic/non-chronic patients and BMI across diagnoses, supporting the analysis findings.
Key Findings

Readmission Rate: 15% overall (15/100 patients).
High-Risk Diagnoses: Asthma, Diabetes, and Hypertension (17.6% readmission rate).
Adherence Paradox: Adherent patients have a higher readmission rate (16.0%) than non-adherent (14.0%), possibly due to disease severity.
Chronic Patients: Higher readmission rate (16.4% vs. 12.1%), longer stays (6.9 vs. 6.4 days), and higher risk scores (3.10 vs. 2.06).
Top Risk Profile: Smokers with high cholesterol and BMI ≥ 35 (risk score = 6.0).
EDA Insights: Balanced categorical distributions (e.g., 50% Male/Female, 50% Smoker/Non-smoker) and weak numeric correlations due to synthetic data patterns.

Recommendations

Targeted Interventions: Launch care management programs for Asthma, Diabetes, and Hypertension patients due to their high readmission rates.
Investigate Adherence: Explore why adherent patients have higher readmission rates, considering disease severity or treatment efficacy.
Risk-Based Monitoring: Use risk_score to flag high-risk patients (e.g., smokers with high cholesterol and BMI) for lifestyle coaching or preventive care.
Data Validation: Validate findings with real-world data, as synthetic data may oversimplify patterns.
Enhance Data: Split blood_pressure into numeric columns and introduce more randomization to mimic real-world variability.

Limitations

Synthetic Data: Deterministic patterns (e.g., readmission every 7th patient) limit real-world applicability.
Blood Pressure Format: Stored as strings, restricting numerical analysis.
Limited Correlations: Weak correlations in numeric data due to synthetic generation.
Small Dataset: 100 records may not capture complex relationships.

Future Work

Incorporate real-world data for validation.
Add more randomization to data generation (e.g., weighted probabilities for diagnoses).
Split blood_pressure into systolic and diastolic for deeper analysis.
Expand visualizations (e.g., scatter plots for risk_score vs. bmi by diagnosis).

Contributing

Fork the repository.
Create a feature branch:git checkout -b feature-branch


Commit changes:git commit -m "Add feature"


Push to the branch:git push origin feature-branch


Open a Pull Request.
