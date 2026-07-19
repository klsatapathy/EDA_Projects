# Olist Brazilian E-Commerce — Exploratory Data Analysis

An end-to-end exploratory data analysis of the [Olist Brazilian E-Commerce Public Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) — covering revenue trends, product performance, customer segmentation, retention, and operations (delivery & payments), built in pandas/matplotlib/seaborn.

This is the Python/EDA companion to a parallel SQL + Power BI analysis of the same dataset.

## 📊 What's Inside

| Section | What it covers |
|---|---|
| Data Overview & Quality Checks | Missing values, order status distribution, delivered-order filtering |
| Revenue & Growth Trends | Monthly revenue, MoM growth %, seasonal (Black Friday) spike |
| Product Performance | Top categories by revenue, volume vs. price trade-off (bubble chart) |
| Customer Segmentation (RFM) | Recency/Frequency/Monetary scoring, segment breakdown (Champions, At Risk, etc.) |
| Cohort Retention | Monthly cohort retention heatmap |
| Delivery & Reviews | Delivery timeliness vs. review score |
| Geography | Delivery time by state |
| Payments | Payment method mix, installments vs. order value |

## 🔑 Key Findings

- **Growth:** Orders scaled from ~750/month (Jan 2017) to a stable ~6–7K/month by 2018, with a clear Black Friday spike in Nov 2017.
- **Products:** Health & Beauty and Watches/Gifts are high-margin categories; Bed/Bath/Table drives volume at lower margins.
- **RFM:** Champions (~8% of customers) drive disproportionate revenue — a classic Pareto pattern.
- **Retention:** Month-1 retention is below 1% across every cohort — the platform behaves as a largely one-time-purchase marketplace.
- **Delivery:** Late deliveries roughly halve average review scores and carry a much higher negative-review rate.
- **Geography:** North/Northeast Brazil states face significantly longer delivery times, reflecting regional infrastructure gaps.
- **Payments:** Credit card dominates; higher installment counts correlate with higher average order values.

## 🛠️ Tech Stack

- Python — pandas, numpy
- matplotlib, seaborn
- Jupyter Notebook

## 📁 Repo Structure

```
.
├── README.md
└── olist_eda_analysis.ipynb
```

## ▶️ Running Locally

1. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) and place the CSVs in a `data/` folder.
2. Update the `DATA_DIR` path at the top of the notebook if needed.
3. Install dependencies:
   ```
   pip install pandas numpy matplotlib seaborn
   ```
4. Open `olist_eda_analysis.ipynb` and run all cells.

## 🔗 Related Work

A SQL (MySQL) analysis with an accompanying Power BI dashboard, covering the same business questions, is available in my [data-science-core-toolkit](https://github.com/klsatapathy/data-science-core-toolkit) repo.

## 👤 Author

**Lokanath Satapathy**
[GitHub](https://github.com/klsatapathy) · [LinkedIn](https://www.linkedin.com/in/lokanath-satapathy-9271732a2)
