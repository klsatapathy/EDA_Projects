# PaySim Banking Fraud — Exploratory Data Analysis

Exploratory analysis of the [PaySim synthetic mobile-money dataset](https://www.kaggle.com/datasets/ealaxi/paysim1), examining transaction-level patterns to understand how fraudulent transactions differ structurally from legitimate ones.

## Goal

Identify structural signals in the data — transaction type, amount, and account balance behavior — that separate fraud from normal activity, as groundwork for a companion SQL analysis (window functions, anomaly-detection queries) built on the same dataset.

## Dataset

`Synthetic_Financial_datasets_log.csv` — synthetic mobile-money transaction log with fields including `step` (time unit), `type`, `amount`, `oldbalanceOrg`/`newbalanceOrig`, `oldbalanceDest`/`newbalanceDest`, `isFraud`, and `isFlaggedFraud`.

## What's in the notebook

| Section | Focus |
|---|---|
| 1. Data Overview | Shape, dtypes, missing values, summary statistics |
| 2. Fraud Class Balance | Fraud vs. legitimate transaction counts (~0.13% fraud rate) |
| 3. Transaction Type Distribution | Volume by type, and fraud rate by type |
| 4. Transaction Amount — Fraud vs. Legitimate | Log-scale amount distributions and boxplots |
| 5. Balance Discrepancy Analysis | `errorBalanceOrig` / `errorBalanceDest` as a fraud signal, account-draining pattern |
| 6. isFlaggedFraud vs. isFraud | How well the dataset's own flagging system performs |
| 7. Transaction Volume & Fraud Over Time | Hourly (`step`) transaction and fraud trends |
| 8. Correlation Heatmap | Relationships among numeric features |

## Key Findings

- Fraud is confined entirely to `TRANSFER` and `CASH_OUT` transactions — `PAYMENT`, `CASH_IN`, and `DEBIT` show zero fraud cases.
- The dataset's own `isFlaggedFraud` field catches only a tiny fraction of true fraud, meaning it can't be relied on alone.
- Fraudulent transactions frequently drain the origin account to exactly zero.
- Balance-reconciliation errors (`errorBalanceOrig`, `errorBalanceDest`) are a stronger structural signal than raw transaction amount.
- These patterns motivate the window-function and anomaly-detection queries used in the SQL portion of this project.

## Tools

Python, Pandas, Matplotlib, Seaborn.

## Run it yourself

```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook github_eda_paysim.ipynb
```

Make sure `Synthetic_Financial_datasets_log.csv` is in the same folder as the notebook (or update the `pd.read_csv(...)` path in the first code cell).
