# Hospital Database Analysis — Exploratory Data Analysis (EDA)

**Author:** Lokanath Satapathy
**Dataset:** [Hospital Management Dataset (Kaggle)](https://www.kaggle.com/datasets/kanakbaghel/hospital-management-dataset)
**Notebook:** `hospital_eda.ipynb`
**Companion:** `hospital_analysis.sql` (SQL-based analysis with joins, window-function ranking, and RFM patient segmentation)

## Overview

This notebook explores a hospital operations dataset spanning five tables — patients, doctors, appointments, treatment, and billing — using Python for data cleaning and visualization. It covers patient demographics, doctor staffing, appointment outcomes, treatment revenue, and billing/payment risk.

## Data

The notebook expects the following CSV files in the working directory:

| File | Description |
|---|---|
| `patients.csv` | Patient demographics, date of birth, registration date, insurance provider |
| `doctors.csv` | Doctor specialization and years of experience |
| `appointments.csv` | Appointment date, status (completed / no-show / cancelled, etc.) |
| `treatment.csv` | Treatment type, cost, treatment date, linked to appointments |
| `billing.csv` | Bill amount, payment status, payment method |

Update the file paths in the **Load Data** section if your CSVs live elsewhere.

## Requirements

```bash
pip install pandas numpy matplotlib seaborn
```

Tested with Python 3.10.

## Notebook Structure

1. **Setup & Imports** — loads pandas, numpy, matplotlib, seaborn; sets plot styling defaults.
2. **Load Data** — reads all five CSVs and prints row/column counts.
3. **Data Cleaning & Type Conversion** — parses date columns, derives patient `age` from date of birth, and checks for missing values across all tables.
4. **Patient Demographics** — age distribution and gender split; patient counts by insurance provider.
5. **Doctor Overview** — doctor counts by specialization; years-of-experience distribution.
6. **Appointment Outcomes** — appointment status breakdown; appointment volume by day of week; no-show/cancellation rate by day of week.
7. **Treatment & Revenue Analysis** — treatment cost distribution by type; total revenue by treatment type.
8. **Monthly Revenue Trend** — appointments merged with treatment costs, aggregated into a monthly revenue trend line.
9. **Billing & Payment Risk** — payment status breakdown by count vs. by total amount; bill counts by payment method.
10. **Summary of Findings** — narrative recap of the key takeaways from each section above.

## Key Findings (from the notebook's summary)

- **Demographics:** Age and gender distribution establish the baseline patient profile.
- **Doctors:** Specialization mix and experience spread show where staffing capacity is concentrated.
- **Appointments:** The no-show/cancelled share quantifies lost scheduling capacity; the day-of-week breakdown flags which days need stronger reminder workflows.
- **Revenue:** Treatment-type cost distribution and the monthly trend line highlight which services drive revenue and how demand moves over time.
- **Billing:** The payment-status split (by count vs. by amount) shows whether financial risk is concentrated in a few high-value bills or spread evenly.

## How to Run

1. Place `patients.csv`, `doctors.csv`, `appointments.csv`, `treatment.csv`, and `billing.csv` in the same directory as the notebook (or update the paths in Section 2).
2. Install the requirements above.
3. Open `hospital_eda.ipynb` in Jupyter and run all cells top to bottom.

## Related

For deeper relational analysis — including joins across all five tables, window-function-based doctor/appointment ranking, and RFM (Recency, Frequency, Monetary) patient segmentation — see `hospital_analysis.sql` in this repo.
