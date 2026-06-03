# Rai-Ragavi

## 🏥 About me

I'm a dual-qualified healthcare professional (BDS + MSc Applied Psychology)
with 3+ years of clinical documentation experience across 6 EHR platforms —
Cerner, ModMed, eClinicalWorks, Meditech, CureMD, and Medent.

I specialise in reviewing, correcting, and validating AI-generated clinical
notes as a Super Medical Scribe — catching what the model misses because I
understand the clinical context behind every line.

I'm now building a healthcare data analyst portfolio, applying Python, SQL,
Power BI, and FHIR standards to real clinical datasets.

---

## 📁 Portfolio projects

| Project | Description | Tools | Status |
|---|---|---|---|
| [ehr-data-quality-audit](https://github.com/Rai-Ragavi/ehr-data-quality-audit) | Audits EHR datasets for missing fields, duplicates & ICD-10 errors | Python, pandas, Excel | 🔄 In progress |
| [patient-readmission-analysis](https://github.com/Rai-Ragavi/patient-readmission-analysis) | Analyses 30-day readmission rates by diagnosis and demographics | Python, matplotlib | ✅ Completed | 
| [healthcare-operations-dashboard](https://github.com/Rai-Ragavi/healthcare-operations-dashboard) | Interactive dashboard — patient volume, diagnoses, provider workload | Power BI / Tableau | 🔜 Coming soon |
| [healthcare-sql-queries](https://github.com/Rai-Ragavi/healthcare-sql-queries) | Library of 15+ annotated SQL queries for real healthcare questions | SQL | 🔜 Coming soon |
| [clinical-notes-nlp](https://github.com/Rai-Ragavi/clinical-notes-nlp) | Extracts diagnoses, medications & procedures from unstructured notes | Python, spaCy | 🔜 Coming soon |

---
# Patient 30-Day Readmission Analysis 🏥

> *"As a medical scribe, I documented these encounters firsthand — this project analyzes what happens after the patient leaves."*

---

## Overview

Hospital readmissions within 30 days of discharge are a key quality metric in U.S. healthcare. The Centers for Medicare & Medicaid Services (CMS) penalizes hospitals with excess readmissions under the **Hospital Readmissions Reduction Program (HRRP)**, making this a high-stakes clinical and operational problem.

This project builds a reproducible Python analysis of 30-day readmission patterns across diagnoses, age groups, and length of stay — the same factors I observed firsthand while scribing in inpatient settings.

## About This Project

Using real ICU data from MIMIC-III Demo, the analysis covers:
- 129 hospital admissions across 100 unique patients
- 30-day readmission flag computed from actual admission/discharge timestamps
- Breakdown by diagnosis (ICD-9), age group, and length of stay
- 4 publication-ready charts saved as PNG files
- Written entirely in Python using pandas, matplotlib, and seaborn

---

## Dataset

**Source:** PhysioNet MIMIC-III Clinical Database Demo v1.4  
**Reference:** [MIMIC-III Demo](https://physionet.org/content/mimiciii-demo/1.4/)

Real ICU data: 129 admissions | 100 unique patients. Readmission flags, age groups, and length of stay were computed directly from raw timestamps in the MIMIC-III files.

Files used: `ADMISSIONS.csv`, `PATIENTS.csv`, `DIAGNOSES_ICD.csv`

```bash
python readmission_analysis.py
```

---

## Key Findings

| Metric | Value |
|---|---|
| Overall 30-day readmission rate | **8.5%** (11/129) |
| Highest-risk diagnosis | Heart Failure & Sepsis (12.5%) |
| Age group with highest risk | 40–64 (13.3%) |
| LOS group with highest risk | Medium stay 4–7d (14.6%) |
| Avg days to readmission | 10.2 days |

### Readmission by Diagnosis
Heart Failure and Sepsis tied at the highest readmission rate (12.5%), consistent with their complex, chronic nature and the difficulty of stabilizing patients at discharge. Both conditions frequently require ongoing management that, if interrupted, leads to rapid deterioration.

### Age Group Trends
Patients aged 40–64 had the highest readmission rate at 13.3%, slightly above the 65+ group (7.5%). In an ICU dataset, older patients often have more structured post-discharge follow-up, while middle-aged patients may be discharged with less oversight.

### Length of Stay
Medium-stay patients (4–7 days) had the highest readmission rate at 14.6% — suggesting these patients were sick enough to require a multi-day stay but may have been discharged before full stabilization. Long-stay patients (8+ days) had a lower rate of 6.0%, possibly because extended stays allowed more thorough recovery.

---

## Visualizations

| Chart | Description |
|---|---|
| `chart_by_diagnosis.png` | Horizontal bar chart of readmission rate per diagnosis |
| `chart_by_age.png` | Line chart of readmission trend across age groups |
| `chart_by_los.png` | Bar chart of readmission rate by length-of-stay category |
| `chart_demographics.png` | Readmission rate by gender and insurance type |

---

## Project Structure

```
Readmission/
├── analysis.py                  # Python script (written from scratch)
├── readmission_analysis.py      # Full modular analysis script
├── requirements.txt             # Python dependencies
├── README.md                    # This file
├── ADMISSIONS.csv               # MIMIC-III source data
├── PATIENTS.csv                 # MIMIC-III source data
├── DIAGNOSES_ICD.csv            # MIMIC-III source data
├── chart_by_diagnosis.png
├── chart_by_age.png
├── chart_by_los.png
└── chart_demographics.png
```

---

## Methodology

1. **Data loading** — Joined `ADMISSIONS`, `PATIENTS`, and `DIAGNOSES_ICD` using pandas merge on `subject_id` and `hadm_id`.
2. **Feature engineering** — Computed length of stay from timestamps, age from date of birth (year-based to handle MIMIC's de-identification), and ICD-9 diagnosis groups via prefix mapping.
3. **Readmission flag** — Used `groupby().shift(-1)` to find each patient's next admission and flagged those within 30 days of discharge.
4. **Analysis** — Computed readmission rates using `groupby()` and `agg()` across diagnosis, age group, LOS, gender, admission type, and insurance.
5. **Visualization** — Four `matplotlib`/`seaborn` charts saved as 150 dpi PNGs.

---

## Limitations

- Demo dataset has only 129 admissions — rates for individual diagnoses have wide confidence intervals.
- Several diagnoses (COPD, Stroke, Acute MI) had 0 readmissions due to small sample size, not true zero risk.
- No individual comorbidities (e.g., diabetes severity, CHF class) are captured, which are significant real-world predictors.
- Readmission flags are binary (30-day); time-to-readmission analysis would add clinical nuance.
- No predictive model is built here — this is a descriptive/exploratory analysis.

---

## Skills Demonstrated

- **Python** — data pipeline built from scratch, modular scripting, reproducible workflows
- **pandas** — data cleaning, multi-table joins, groupby aggregations, derived variables
- **matplotlib / seaborn** — publication-ready charts with annotations and consistent theming
- **Healthcare data literacy** — MIMIC-III schema, ICD-9 coding, CMS HRRP clinical context

---

## 🩺 Clinical background

- **3+ years** medical scribing across US healthcare providers
- **6 EHR platforms**: Cerner · ModMed · eClinicalWorks · Meditech · CureMD · Medent
- **AI scribing**: reviewing and validating AI-generated clinical documentation
- **Counsellor**: 1 year psychological support at Mindgardener
- **Resident Dental Surgeon**: Rosema Dental Clinic 3 years

---

## 🌐 Languages

English; Tamil; French

---
**Source:** PhysioNet MIMIC-III Clinical Database Demo v1.4  
**Reference:** [MIMIC-III Demo](https://physionet.org/content/mimiciii-demo/1.4/)
Real ICU data: 129 admissions | 100 unique patients. Readmission flags, age groups, and length of stay were computed directly from raw timestamps in the MIMIC-III files.
