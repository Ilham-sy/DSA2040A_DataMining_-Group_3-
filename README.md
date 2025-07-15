# DSA2040A_DataMining_-Group_3-
A data mining project, applying ETL, analysis and visualization on the data.

# Health Data Mining Group Project

## Project Title
Mining Patterns in Patient Health Records for Better Preventive Care. 
This project focuses on extracting, transforming, and loading (ETL) health data to uncover insights that can lead to improved patient outcomes.

##  Project Structure
```
├── data
│   ├── raw
│   ├── processed
│   └── synthetic
├── notebooks
│   ├── etl
│   ├── analysis
│   └── visualization
├── src
│   ├── etl
│   ├── analysis
│   └── visualization
├── reports
│   ├── figures
│   └── final_report.md
├── requirements.txt
├── README.md
└── LICENSE
``` 
##  Project Goals
1. **ETL Process**: Extract and transform synthetic health data to prepare it for analysis.
2. **Data Mining**: Apply data mining techniques to discover patterns in patient health records.
3. **Visualization**: Create visualizations to effectively communicate findings.        
4. **Documentation**: Document the entire process, including challenges faced and solutions implemented.

## Documentation
- **README.md**: Overview of the project, goals, and structure.
- **Final Report**: Detailed documentation of the ETL process, data mining techniques used, and findings.
- **Notebooks**: Jupyter notebooks for ETL, analysis, and visualization.
- **Source Code**: Python scripts for ETL, analysis, and visualization tasks.  

## Expected Outcomes
- A comprehensive understanding of the ETL process applied to health data.
- Identification of key patterns in patient health records.
- Visualizations that highlight significant findings.
- A final report summarizing the project, methodologies, and insights gained.

## 👥 Team Members
- Ilham (ETL Lead)
- Samuel (EDA Lead)
- Ruth (Analyst)
- Maranga(Visualizer)
- Yar (Documenter)

## 🏥 Project Topic: Health

We aim to analyze patient health records to identify patterns in chronic conditions, lifestyle risks, and hospital readmissions. The goal is to use ETL + Data Mining techniques to provide insights that can improve preventive care.

## 📊 Data Description

We'll generate a synthetic health dataset containing:
- Demographics: Age, gender
- Lifestyle factors: Smoking status, activity level
- Clinical metrics: BMI, blood pressure, cholesterol
- Medical outcomes: Diagnosis, hospital stay, readmission

# ETL Process for Health Records Data
## Overview
This project focuses on extracting, transforming, and loading (ETL) health records data to uncover insights that can lead to improved patient outcomes. The ETL process involves extracting data from various sources, transforming it to fit the analysis needs, and loading it into a structured format for further analysis. 

## Steps
1. **Extract**: Read health records data from a CSV file.
2. **Transform**: Clean and enrich the data by:         
    - Handling missing values
    - Standardizing formats
    - Enriching data with additional information (e.g., age groups, risk scores)        
3. **Load**: Save the transformed data into a structured format (e.g., CSV) for analysis.   

## Code Snippet
```python
import pandas as pd         
import numpy as np
import os
# 1. Read health records data
input_file = 'health_records.csv'
df = pd.read_csv(input_file)  

# 2. Handle missing values
df.fillna(method='ffill', inplace=True)  # Forward fill for simplicity

# 3. Standardize formats        
df['visit_date'] = pd.to_datetime(df['visit_date'], errors='coerce')  # Convert to datetime 
    
# 4. Enrich data with additional information
def enrich_row(row):
    if row['age'] < 18:         
        age_group = 'Child'
    elif 18 <= row['age'] < 65:
        age_group = 'Adult'
    else:
        age_group = 'Senior'            
    risk_score = row['bmi'] * 0.1 + row['blood_pressure'] * 0.2
    is_chronic = row['chronic_condition'] == 'Yes'      
    return pd.Series([age_group, risk_score, is_chronic], index=['age_group', 'risk_score', 'is_chronic'])
    
# Apply to DataFrame
df[['age_group', 'risk_score', 'is_chronic']] = df.apply(enrich_row, axis=1)

# 5. Save DataFrame to CSV
output_dir = 'health_records'           
os.makedirs(output_dir, exist_ok=True)  # Create directory if it doesn't exist
output_file = os.path.join(output_dir, 'transformed_health_records.csv')        
df.to_csv(output_file, index=False)  # Save to CSV
```     

📝 Additional Notes
The ETL process ensures data is clean, consistent, and enriched for meaningful analysis.
Calculated fields (e.g., risk_score) help uncover patterns in patient data that support preventive care strategies.
The transformed dataset is suitable for:
Predictive analytics
Visualization and dashboarding
Clustering or classification in mining phase

Future enhancements:
Handle outliers more robustly (IQR or z-scores)
Automate ETL with tools like Apache Airflow or Prefect
Integrate NLP to extract insights from unstructured clinical notes
Privacy and ethics:
Dataset is simulated, but future real-world applications must comply with HIPAA/GDPR.
Collaborating with healthcare professionals can validate domain assumptions.