# AirPulse AI — Urban Air Exposure & Sensor Intelligence

## AICTE | IBM SkillsBuild Data Analytics with AI Internship 2026 | BharatCares

### Project Overview

**AirPulse AI** is an end-to-end Data Analytics and AI/ML project that converts hourly air-quality observations into interpretable environmental intelligence.

The project combines:

- Data cleaning and preprocessing
- Time-series feature engineering
- Exploratory Data Analysis (EDA)
- A relative Exposure Pressure Index
- NO2 prediction using multiple ML models
- Model evaluation using MAE, RMSE and R²
- Permutation-based model explainability
- Isolation Forest anomaly detection
- Automated analyst-style insights
- SDG-oriented recommendations

The objective is not simply to predict pollution values, but to create a complete analytical workflow that answers:

1. When are NO2 levels relatively higher?
2. Which variables are most useful for NO2 prediction?
3. How well can different ML models predict NO2?
4. Which observations are unusual?
5. How can these findings support environmental monitoring?

---

## Problem Statement

Raw air-quality datasets contain many pollutant, sensor and environmental variables, but raw measurements do not directly provide actionable analytical intelligence.

AirPulse AI addresses this by combining descriptive analytics, predictive machine learning, explainability and anomaly detection in one reproducible workflow.

---

## Dataset

**Dataset:** UCI Machine Learning Repository — Air Quality

**Dataset URL:** https://archive.ics.uci.edu/dataset/360/air%2Bquality

**DOI:** 10.24432/C59K5F

The dataset contains 9,358 hourly observations collected from March 2004 to February 2005. It includes pollutant reference measurements, sensor responses, temperature, relative humidity and absolute humidity.

The UCI dataset uses `-200` to represent missing values. The project converts these values to missing data before preprocessing.

---

## Technologies Used

- Python
- Jupyter Notebook / Google Colab
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- OpenPyXL

---

## Machine Learning

The project predicts `NO2(GT)` using:

1. **Linear Regression**
2. **Gradient Boosting Regressor**
3. **Random Forest Regressor**

A chronological holdout is used instead of randomly mixing observations, making the evaluation more appropriate for time-dependent data.

### Final Model Results

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 27.240 | 35.854 | 0.558 |
| Gradient Boosting | 27.487 | 36.254 | 0.548 |
| Random Forest | 28.483 | 37.266 | 0.523 |

The completed run selected **Linear Regression** by lowest holdout RMSE.

---

## Explainability

Permutation importance was used to identify variables most useful to the selected model.

Top predictive drivers from the completed run:

| Feature | Mean Importance |
|---|---:|
| PT08.S2(NMHC) | 16.3944 |
| C6H6(GT) | 12.9216 |
| NOx(GT) | 9.9529 |
| CO(GT) | 6.0322 |
| PT08.S5(O3) | 5.1777 |

Permutation importance indicates predictive reliance; it does **not** establish causation.

---

## Anomaly Detection

Isolation Forest was used to identify unusual multivariate observations.

**Detected multivariate anomalies: 3.0%**

An anomaly is treated as a candidate for further investigation and does not automatically mean that a sensor is faulty.

---

## Exposure Pressure Index

The project creates a relative **Exposure Pressure Index (EPI)** from pollutant percentile signals.

Final run:

- **High/Very-High relative pressure observations: 20.6%**
- **Peak average NO2 hour: 19:00**
- **Peak average NO2 month: February**

The EPI is a project-specific analytical indicator. It is **not** a medical risk score, AQI replacement, or regulatory classification.

---

## Project Workflow

```text
Official UCI Dataset
        ↓
Data Cleaning
        ↓
Timestamp Engineering
        ↓
Feature Engineering
        ↓
Exploratory Data Analysis
        ↓
Exposure Pressure Index
        ↓
Time-Ordered ML Evaluation
        ↓
Model Explainability
        ↓
Anomaly Detection
        ↓
AI Analyst Brief
        ↓
Recommendations
```

---

## Setup and Run

### Option 1 — Google Colab

1. Open Google Colab.
2. Upload `TusharBorse_AirPulseAI.ipynb`.
3. Run the notebook from top to bottom.
4. Internet access is required for downloading the official UCI dataset.

### Option 2 — Local Jupyter

Create a virtual environment:

```bash
python -m venv .venv
```

Windows:

```bash
.venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter:

```bash
jupyter notebook
```

Open:

```text
TusharBorse_AirPulseAI.ipynb
```

Then run all cells.

---

## Key Findings

- The completed analysis found **19:00** as the peak average NO2 hour.
- **February** had the highest average NO2 among the analyzed months.
- **20.6%** of observations were in the combined High/Very-High relative pressure bands.
- **3.0%** of observations were detected as multivariate anomalies.
- Linear Regression achieved **RMSE 35.854** and **R² 0.558** on the chronological holdout.
- PT08.S2(NMHC), C6H6(GT), NOx(GT), CO(GT) and PT08.S5(O3) were the strongest predictive drivers in the selected model.

---

## SDG Alignment

### SDG 3 — Good Health and Well-Being
Supports data-driven environmental monitoring and analytical understanding of air-quality patterns.

### SDG 11 — Sustainable Cities and Communities
Supports data-driven understanding of urban environmental conditions.

---

## Responsible AI and Limitations

- The dataset represents a historical monitoring deployment in an Italian city.
- Results should not be treated as current air-quality conditions for another location.
- The Exposure Pressure Index is relative to this dataset.
- Model performance on historical data does not guarantee future performance.
- Feature importance does not establish causal relationships.
- Anomaly detection does not diagnose sensor failure.
- Production deployment should use current/local data and domain validation.

---

## Project Deliverables

```text
TusharBorse_AirPulseAI.ipynb
requirements.txt
TusharBorse_ProjectReport.docx
README.md
```

---

## Author

**Tushar Borse**

AICTE | IBM SkillsBuild Data Analytics with AI Internship 2026
