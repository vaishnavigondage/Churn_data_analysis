# Customer Churn Analysis Dashboard

An end-to-end customer churn analysis on a telecom dataset: cleaning messy raw data, then building an interactive **Power BI** dashboard to identify who churns, when, and why.



---

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Data Cleaning](#data-cleaning)
- [Dashboard Features](#dashboard-features)
- [Key Insights](#key-insights)
- [Recommendations](#recommendations)
- [Tech Stack](#tech-stack)
- [Repository Structure](#repository-structure)
- [How to Use](#how-to-use)
- [Author](#author)

---

## Project Overview

Customer churn is one of the costliest problems for subscription businesses, since retaining a customer is usually cheaper than acquiring a new one. This project answers:

- What is the overall churn rate, and how many customers have we lost?
- Which contract types and tenure bands carry the highest churn?
- How do add-on services (Online Security, Online Backup) relate to revenue and churn?
- Which retained customers are at **high risk** of leaving next?

## Dataset

| Item | Detail |
|---|---|
| File | `Churn Analysis data.csv` |
| Raw rows | 7,048 |
| Rows after cleaning | 7,043 unique customers |
| Columns | 21 |
| Target | `Churn` (Yes / No) |

**Column groups**
- **Demographics:** `gender`, `SeniorCitizen`, `Partner`, `Dependents`
- **Account:** `tenure`, `Contract`, `PaperlessBilling`, `PaymentMethod`
- **Services:** `PhoneService`, `MultipleLines`, `InternetService`, `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`
- **Billing:** `MonthlyCharges`, `TotalCharges`

## Data Cleaning

The raw file was intentionally "unclean". Issues found and fixed:

| Issue | Fix |
|---|---|
| 5 duplicate rows | Removed duplicates |
| 126 missing `TotalCharges` values | Handled (e.g. new customers with 0 tenure) rather than leaving blanks |
| `$` symbol in some `MonthlyCharges` values (e.g. `$29.85`) | Stripped symbol, converted column to numeric |
| Inconsistent `Contract` labels (`month to month` vs `Month-to-month`) | Standardized to one label |
| Trailing whitespace in `PaymentMethod` (e.g. `Electronic check `) | Trimmed whitespace |

## Dashboard Features

The Power BI dashboard (`Churn_DataSet_Dashboard.pdf`) contains:

- **KPI cards:** Total Customers, Churn Rate %, Churned Customers
- **Customer Retention Overview:** donut chart of churned vs retained
- **Churned Customers by Contract:** bar chart by contract type
- **Churn Rate % by Tenure Band:** 0–6, 6–12 and 12+ months
- **Retained Customers by Risk Type:** Normal vs High Risk segmentation
- **Sum of Monthly Charges by Online Security and Online Backup:** stacked column
- **Sum of Monthly Charges by Customer Type:** Existing vs New customers
- **Avg Monthly Charges by Churn status**

## Key Insights

| Metric | Value |
|---|---|
| Total customers | **7,043** |
| Churned customers | **1,869** |
| Churn rate | **26.54%** |
| Retained customers flagged High Risk | **633** (vs 4,541 Normal) |

1. **Month-to-month contracts drive churn.** 1,655 of the 1,869 churned customers (about 89%) were on month-to-month plans, versus 166 on one-year and just 48 on two-year contracts.
2. **Early tenure is the danger zone.** Churn is 52.94% in the first 6 months, 35.89% for 6–12 months, and drops to 17.13% after 12 months.
3. **Add-on services matter.** Customers without Online Security account for a large share of monthly revenue and show a larger churned portion in the stacked chart, suggesting protective services may support retention.
4. **633 retained customers are High Risk**, a ready-made target list for proactive retention campaigns.

## Recommendations

- Offer discounts or incentives to move **month-to-month customers onto 1–2 year contracts**.
- Build a stronger **onboarding and engagement program for the first 6 months**.
- **Bundle or promote Online Security / Online Backup** to customers without them.
- Run **targeted outreach to the 633 High Risk customers** before they churn.

## Tech Stack

- **Power BI Desktop:** data modeling, DAX measures, visualization
- **Power Query / Python (pandas) / Excel:** data cleaning *(keep the one you used)*
- **Dataset:** Telco Customer Churn (IBM sample data, modified)

## Repository Structure

```
├── data/
│   └── Churn Analysis data.csv         # Raw dataset
├── dashboard/
│   ├── Churn_Analysis.pbix             # Power BI file (add if available)
│   └── Churn_DataSet_Dashboard.pdf     # Dashboard export
├── images/
│   └── dashboard.png                   # Preview image used above
└── README.md
```

## How to Use

1. Clone the repo:
```bash
   git clone https://github.com/<your-username>/<repo-name>.git
```
2. Open `Churn_Analysis.pbix` in **Power BI Desktop** (or view the PDF export directly).
3. If refreshing the data, point the data source to `data/Churn Analysis data.csv` and apply the cleaning steps above.

## Author

**Vaishnavi Gondage**

[LinkedIn](https://www.linkedin.com/in/vaishnavi-gondage/) · [Email](mailto:vaishnavigondage20@gmail.com)

---
*If you found this project useful, consider giving it a ⭐*
