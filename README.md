# 💊 PharmaPulse — Pharma Sales & Market Analytics

![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-SQLite-07405E?logo=sqlite&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-Forecasting-F7931E?logo=scikit-learn&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-Dashboard-3F4F75?logo=plotly&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green.svg)

An end-to-end Python data analytics project simulating a **pharmaceutical commercial analytics engagement** — the kind of work a pharma/healthcare-focused consulting analytics team (e.g. ZS Associates) does for clients: sales performance, patient journey analysis, and sales force effectiveness.

---

## 📋 Table of Contents
- [Why This Project](#-why-this-project)
- [Project Structure](#-project-structure)
- [Dataset](#-dataset)
- [Analysis Breakdown](#-analysis-breakdown)
- [Key Insights](#-key-insights)
- [How to Run](#-how-to-run)
- [Sample Output](#-sample-output)
- [Tech Stack](#-tech-stack)

---

## 🎯 Why This Project

Pharma commercial analytics revolves around a few recurring frameworks: **Revenue = Volume × Price** decomposition, **patient journey / adherence funnels**, and **sales force effectiveness**. This project builds a realistic (synthetically generated) dataset and works through each of those lenses using Python, SQL, and a forecasting model — an end-to-end pipeline from raw data to an interactive dashboard.

> **Note on the data:** Real pharma commercial datasets aren't publicly available, so this uses a synthetic dataset generated with realistic underlying mechanics (seasonality, price elasticity, rep-skill effects on call efficiency, patient adherence drop-off). The insights the analysis surfaces are genuine outputs of that simulation, not hand-picked numbers.

## 📁 Project Structure

```
pharmapulse/
├── data/
│   ├── pharma_sales.csv       # 5,760 rows — 24 months × 6 drugs × 40 reps
│   ├── reps.csv                # rep roster: tenure, region, skill
│   ├── monthly_agg.csv         # aggregated monthly revenue/units
│   ├── rep_performance.csv     # per-rep calls, revenue, revenue/call
│   └── forecast.csv            # 6-month forward revenue forecast
├── scripts/
│   ├── 01_generate_data.py     # synthetic data generator
│   ├── 02_eda_analysis.py      # pandas / matplotlib / seaborn EDA
│   ├── 03_sql_analysis.py      # SQLite: joins, window functions, CTEs
│   ├── 04_forecasting.py       # linear trend + seasonality forecast
│   └── 05_dashboard.py         # interactive Plotly HTML dashboard
├── outputs/
│   ├── charts/                 # 6 PNG charts from the EDA
│   └── dashboard.html          # interactive dashboard (open in browser)
├── requirements.txt
└── README.md
```

## 🗂 Dataset

| File | Rows | Description |
|---|---|---|
| `pharma_sales.csv` | 5,760 | Monthly sales by drug, region, rep, and HCP segment |
| `reps.csv` | 40 | Sales rep roster with region, tenure, skill factor |

**Key columns:** `drug`, `therapy_area`, `region`, `rep_id`, `hcp_segment`, `calls_made`, `units_sold`, `unit_price`, `revenue`, `new_rx`, `refill_rx`, `discontinued_patients`

## 🔍 Analysis Breakdown

| Script | Analysis | Business Framework |
|---|---|---|
| `02_eda_analysis.py` | Revenue trend + Volume/Price split | Revenue = Volume × Price decomposition |
| `02_eda_analysis.py` | Therapy area / drug mix | Portfolio prioritization |
| `02_eda_analysis.py` | Regional performance | Territory / market sizing |
| `02_eda_analysis.py` | Patient adherence by therapy area | **Patient journey funnel** (New Rx → Refill → Discontinuation) |
| `02_eda_analysis.py` | Calls vs. revenue, tenure vs. efficiency | **Sales force effectiveness & sizing** |
| `03_sql_analysis.py` | 6 SQL queries | JOINs, `LAG`, `RANK`, running totals, CTEs |
| `04_forecasting.py` | Linear trend + seasonal dummies | Interpretable revenue forecasting |

## 💡 Key Insights

- **Total simulated revenue:** ₹82.3M over 2 years
- **Top therapy area:** Diabetes | **Top region:** East
- **Lowest patient adherence:** Respiratory (~77%) — flags a need for patient support program investment
- **Rep tenure vs. productivity:** weak correlation (r ≈ 0.32) — suggests skill/territory matter more than experience alone
- **6-month forecast:** upward trend, hold-out test R² = 0.70

## ⚙️ How to Run

```bash
git clone https://github.com/<your-username>/pharmapulse.git
cd pharmapulse
pip install -r requirements.txt

python scripts/01_generate_data.py
python scripts/02_eda_analysis.py
python scripts/03_sql_analysis.py
python scripts/04_forecasting.py
python scripts/05_dashboard.py
```

Then open `outputs/dashboard.html` in any browser — no server required.

## 📊 Sample Output

Charts generated in `outputs/charts/`:
- `01_revenue_trend_decomposition.png`
- `02_therapy_drug_mix.png`
- `03_regional_performance.png`
- `04_patient_funnel_adherence.png`
- `05_sales_force_effectiveness.png`
- `06_revenue_forecast.png`

## 🛠 Tech Stack

- **Python** — pandas, numpy for data manipulation
- **Visualization** — matplotlib, seaborn, Plotly
- **SQL** — SQLite (joins, window functions, CTEs)
- **ML** — scikit-learn (linear regression forecasting)

---

### Author
Built by Harsh as a portfolio project applying pharma commercial analytics frameworks.
