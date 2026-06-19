# Rai-Ragavi

## 🏥 About me
## Clinical AI background

- **AI output QA**: 3+ years reviewing and correcting AI-generated clinical notes — catching hallucinations, ROS gaps, and medication errors before physician sign-off
- **EHR depth**: 6 platforms (Cerner, ModMed, eClinicalWorks, Meditech, CureMD, Medent) across internal medicine, cardiology, orthopaedics, and dentistry
- **Dental AI domain**: BDS-qualified reviewer for dental diagnostic AI tools — Pearl AI, Overjet, VideaHealth
- **Behavioural health AI**: 1 year digital therapy platform — CBT-based frameworks directly applicable to conversational AI and mental health LLM safety
- **Structured data**: Medical coding background in ICD-10-CM and CPT — clinical data classification that feeds AI training pipelines
---

## 📁 Portfolio projects

| Project | Description | Tools | Status |
|---|---|---|---|
| [ehr-data-quality-audit](https://github.com/Rai-Ragavi/ehr-data-quality-audit) | Audits EHR datasets for missing fields, duplicates & ICD-10 errors | Python, pandas, Excel | ✅ Completed |
| [patient-readmission-analysis](https://github.com/Rai-Ragavi/patient-readmission-analysis) | Analyses 30-day readmission rates by diagnosis and demographics | Python, matplotlib | ✅ Completed | 
| [healthcare-operations-dashboard](https://github.com/Rai-Ragavi/healthcare-operations-dashboard) | Interactive dashboard — patient volume, diagnoses, provider workload | Power BI / Tableau | ✅ Completed|
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
**Source:** PhysioNet MIMIC-III Clinical Database Demo v1.4  
**Reference:** [MIMIC-III Demo](https://physionet.org/content/mimiciii-demo/1.4/)
Real ICU data: 129 admissions | 100 unique patients. Readmission flags, age groups, and length of stay were computed directly from raw timestamps in the MIMIC-III files.
---
# EHR Data Quality Audit 🔍

An end-to-end data quality audit pipeline for Electronic Health Record (EHR) datasets — built with Python and pandas, with a formatted multi-sheet Excel report as output.

> *"Built from direct experience managing documentation across 6 EHR platforms — I know exactly where data quality breaks down."*

---

## What It Does

Audits a patient dataset across **6 issue categories** and produces a formatted Excel report flagging every record that needs review.

| Check | What It Catches |
|---|---|
| Missing fields | Required fields (patient ID, provider, ICD-10, etc.) left blank |
| Duplicate records | Exact duplicates, same patient + encounter, same name + DOB |
| ICD-10 validation | Malformed codes (`DIAB`, `ICD-E11`, `Z999.99`, free-text leaks) |
| Date format audit | Non-ISO dates (`MM/DD/YYYY`, `DD-MM-YYYY`), future dates in DOB |
| Categorical inconsistencies | Non-standard gender values (`M`, `FEMALE`, `male`) |
| Clinical outliers | Implausible BMI, systolic BP, diastolic BP values |

---

## Sample Results (520 synthetic records)

```
Total records:       520
Records flagged:     131  (25.2%)
Clean records:       389  (74.8%)

Missing required fields:     32 records   HIGH
Duplicate records:           26 records   HIGH
Invalid ICD-10 codes:        23 records   HIGH
Date format / future date:   28 records   MEDIUM
Non-standard gender:         18 records   LOW
Implausible clinical values: 16 records   HIGH
```

---

## Excel Report Output

The report is saved as `EHR_Quality_Report.xlsx` with 7 sheets:

- **Summary** — KPI cards, issue breakdown table with severity ratings
- **Field Completeness** — % complete per field, color-coded Good / Review / Poor
- **Flagged Records** — all records needing review, sorted by issue count
- **ICD-10 Errors** — invalid codes with the submitted value and format guidance
- **Date & Format Issues** — non-standard dates and gender inconsistencies
- **Duplicates** — flagged rows grouped by duplicate type
- **Clinical Outliers** — implausible BMI and BP values with threshold reference

---

## Project Structure

```
ehr-data-quality-audit/
│
├── ehr-audit.ipynb        # Jupyter notebook — full audit pipeline:
│                          # data loading, all 6 quality checks,
│                          # summary stats, and Excel report generation
│
├── sample-ehr-data.csv    # Synthetic EHR dataset used for the audit
│
└── README.md
```

---

## How to Run

**1. Install dependencies**
```bash
pip install pandas openpyxl jupyter
```

**2. Open the notebook**
```bash
jupyter notebook ehr-audit.ipynb
```

**3. Run all cells**

The notebook loads `sample-ehr-data.csv`, runs all six audit checks, prints summary statistics, and generates a formatted multi-sheet Excel report (`EHR_Quality_Report.xlsx`) in the same folder.

---

## Tech Stack

- **Python 3.x**
- **pandas** — data loading, missing value detection, duplicate logic
- **re** (stdlib) — ICD-10 regex validation
- **datetime** (stdlib) — date parsing and format detection
- **openpyxl** — Excel workbook creation, formatting, multi-sheet output

---

## ICD-10 Validation Logic

Uses the WHO ICD-10-CM format regex:

```
^[A-TV-Z][0-9]{2}(\.[A-Z0-9]{1,4})?$
```

Valid: `I10`, `E11.9`, `Z00.00`, `G43.909`  
Invalid: `DIAB`, `ICD-E11`, `E-11`, `Z999.99`, `E11.99999`

---

## Clinical Context

These checks target the most common failure points seen across real EHR platforms:

- **Sentinel values** (`999`, `0`) used as nulls when a field doesn't accept blanks — common in legacy systems
- **Free-text leaking into coded fields** (`DIAB` instead of `E11.9`) — common with manual entry workflows
- **Date format fragmentation** across systems that export in different regional formats
- **Duplicate patient IDs** introduced during EHR migrations when patient matching fails
- **Non-standard gender values** that break downstream HEDIS and MIPS quality measure queries

---

## Dataset

Uses a synthetic dataset generated with realistic demographic distributions, encounter patterns, and intentionally injected quality issues. No real patient data is used. The generator (`step1_generate_ehr.py`) can be adapted to audit real EHR exports by replacing the CSV source.

---

## Skills Demonstrated

`Python` `pandas` `data cleaning` `healthcare data standards` `ICD-10` `EHR` `openpyxl` `Excel automation` `data quality` `HL7/FHIR readiness`

# Healthcare Operations Dashboard

A portfolio project demonstrating healthcare analytics using a synthetic star-schema dataset (9,000 patient encounters) built in Power BI. Covers patient volume, average visit duration, top diagnoses, and provider workload — with filters for date range, specialty, and location.

---

## What this project demonstrates

- Star schema data modeling (fact + 3 dimension tables)
- Power BI: DAX measures, model relationships, slicers, multi-page report layout
- Healthcare KPI design: volume trends, throughput, diagnostic mix, provider utilization

---

## Dataset

| File | Rows | Description |
|------|------|-------------|
| `data/fact_encounters.csv` | 9,000 | One row per patient visit (Jun 2025 – May 2026) |
| `data/dim_providers.csv` | 42 | Provider roster with specialty, department, location, FTE |
| `data/dim_diagnoses.csv` | 20 | ICD-10-style diagnosis code lookup |
| `data/dim_locations.csv` | 4 | Ohio clinic sites (Columbus, Dublin, Grove City) |

Generated by `generate_dataset.py` using NumPy with seed 42 (fully reproducible).

---

## Dashboard (Power BI)

**Page 1 — Executive Summary:** Patient volume by department, avg visit duration by specialty, slicers  
**Page 2 — Clinical Mix:** Top diagnoses by encounter count  
**Page 3 — Provider Workload:** Encounters per provider  

DAX measures: `Total Encounters`, `Avg Duration (min)`, `Unique Patients`

---
## Tools & skills

- **Power BI Desktop** — data modeling, DAX, report design  
- **Git / GitHub** — version control, portfolio publishing  

---

## Compliance note

All data is fully synthetic. No real patient records used. Follows HIPAA Safe Harbor de-identification principles.

---

## License

MIT — free to use, fork, and adapt.

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

