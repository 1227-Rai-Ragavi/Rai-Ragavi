# Dr. Rai Ragavi — Clinical AI Portfolio

Clinical AI Trainer & QA Specialist | AI-Generated Note Validation | BDS + MSc Applied Psychology

Chennai, India · rai96ragavi@gmail.com · LinkedIn — linkedin.com/in/rai-ragavi

## 🏥 About me

I validate and improve AI — specifically the AI that talks to doctors.

For 3+ years I've worked inside AI-assisted clinical documentation workflows, reviewing and correcting AI-generated notes across internal medicine, cardiology, orthopaedics, and dentistry. I know exactly where ambient AI breaks down: it misses nuance in ROS, hallucinates medications in complex polypharmacy cases, and struggles with specialist shorthand. I've caught and corrected those errors at volume, across 6 EHR platforms.

My dual background is unusual in this space:


A BDS in Dental Surgery gives me direct clinical validity for dental AI tools (Pearl AI, Overjet, VideaHealth)
An MSc in Applied Psychology positions me for behavioural health AI, conversational care models, and digital therapeutic products


I'm now building a healthcare data and AI portfolio — combining clinical domain knowledge with Python, SQL, and Power BI to work on problems that matter in health AI.

## Clinical AI background

- **AI output QA**: 3+ years reviewing and correcting AI-generated clinical notes — catching hallucinations, ROS gaps, and medication errors before physician sign-off
- **EHR depth**: 6 platforms (Cerner, ModMed, eClinicalWorks, Meditech, CureMD, Medent) across internal medicine, cardiology, orthopaedics, and dentistry
- **Dental AI domain**: BDS-qualified reviewer for dental diagnostic AI tools
- **Behavioural health AI**: 1-year digital therapy platform — CBT-based frameworks
- **Structured data**: Medical coding background in ICD-10-CM and CPT — clinical data classification that feeds AI training pipelines
---

## 📁 Portfolio projects

| Project | Description | Tools | Status |
|---|---|---|---|
| ([https://github.com/Rai-Ragavi/ehr-data-quality-audit](https://github.com/1227-Rai-Ragavi/ehr-data-quality-audit)) | Audits EHR datasets for missing fields, duplicates & ICD-10 errors | Python, pandas, Excel | ✅ Completed |
| ([https://github.com/Rai-Ragavi/patient-readmission-analysis](https://github.com/1227-Rai-Ragavi/patient-readmission-analysis)) | Analyses 30-day readmission rates by diagnosis and demographics | Python, matplotlib | ✅ Completed | 
| ([https://github.com/Rai-Ragavi/healthcare-operations-dashboard](https://github.com/1227-Rai-Ragavi/Healthcare-ops-dashboard)) | Interactive dashboard — patient volume, diagnoses, provider workload | Power BI / Tableau | ✅ Completed|
| [healthcare-sql-queries](https://github.com/Rai-Ragavi/healthcare-sql-queries) | Library of 15+ annotated SQL queries for real healthcare questions | SQL | 🔜 Coming soon |
| [clinical-notes-nlp](https://github.com/Rai-Ragavi/clinical-notes-nlp) | Extracts diagnoses, medications & procedures from unstructured notes | Python, spaCy | 🔜 Coming soon |

---
---
# EHR Data Quality Audit 🔍

"Built from direct experience managing documentation across 6 EHR platforms — I know exactly where data quality breaks down."

Audits a patient dataset across 6 issue categories and produces a formatted multi-sheet Excel report:

Missing required fields (patient ID, provider, ICD-10)
Duplicate records (exact, same patient + encounter, same name + DOB)
ICD-10 validation using WHO ICD-10-CM format regex
Date format inconsistencies and future DOB errors
Non-standard categorical values (gender encoding)
Implausible clinical outliers (BMI, systolic/diastolic BP)

Sample results on 520 synthetic records: 131 flagged (25.2%) across 6 error categories — severity-rated HIGH / MEDIUM / LOW. Report output: 7-sheet Excel workbook with KPI summary, flagged records, and per-issue breakdowns.

Clinical context: These checks target the most common failure points in real EHR platforms — sentinel value abuse, free-text leaking into coded fields, date format fragmentation across systems, and duplicate patient IDs introduced during EHR migrations.

---
# Patient 30-Day Readmission Analysis 🏥

"As a medical scribe, I documented these encounters firsthand — this project analyses what happens after the patient leaves."

Uses real ICU data from MIMIC-III Clinical Database Demo — 129 admissions, 100 unique patients.

Key findings:

| Metric | Value |
|--------|-------|
| Overall 30-day readmission rate | 8.5% (11/129) |
| Highest-risk diagnosis | Heart Failure & Sepsis (12.5%) |
| Age group with highest risk | 40–64 (13.3%) |
| LOS group with highest risk | Medium stay 4–7d (14.6%) |
| Avg days to readmission | 10.2 days |

Clinical interpretation: Medium-stay patients (4–7 days) had the highest readmission rate — suggesting discharge before full stabilisation. This pattern is directly relevant to AI-assisted discharge risk scoring tools now being built into EHR platforms.

Scope & next steps: This is a descriptive/exploratory analysis. Next iteration: logistic regression readmission predictor using the full MIMIC-III dataset, with comorbidity features and time-to-readmission modelling.


# Healthcare Operations Dashboard

"Built to understand the operational conditions that drive AI adoption in health systems — provider load, visit volume, documentation patterns."

Star-schema Power BI dashboard across 9,000 synthetic patient encounters covering patient volume, average visit duration, top diagnoses, and provider workload.

Clinical AI interpretation: Provider workload distribution maps directly to documentation burden — the primary driver behind ambient AI scribing adoption. High-volume, high-documentation-load specialities (internal medicine, cardiology) are where tools like Nuance DAX, Suki, and Nabla see the fastest adoption. This dashboard visualises exactly that pressure.

DAX measures: Total Encounters · Avg Duration (min) · Unique Patients

Star schema: 1 fact table + 3 dimension tables (providers, diagnoses, locations)A portfolio project demonstrating healthcare analytics using a synthetic star-schema dataset (9,000 patient encounters) built in Power BI. Covers patient volume, average visit duration, top diagnoses, and provider workload — with filters for date range, speciality, and location.

---
**Skills**

Python · pandas · matplotlib · seaborn · SQL · Power BI · DAX

ICD-10-CM · CPT · EHR workflows · MIMIC-III · clinical NLP · data quality

AI output validation · clinical annotation · healthcare data standards · HL7/FHIR

## 🌐 Languages

English; Tamil; French

---
All datasets used are either publicly available (MIMIC-III Demo via PhysioNet) or fully synthetic. No real patient data used in any project.
Contentpdfpdf

