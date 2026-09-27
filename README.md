# 🛒 Sample Superstore — Sales Data Analytics
## Data Analytics Internship Project · Pranita Nande

A complete end-to-end data analytics project built on the **Sample Superstore** retail dataset.
Covers data cleaning, KPI calculation, dimensional analysis, discount impact, risk & opportunity
identification, and data-driven business recommendations — delivered as a Jupyter notebook,
a Word project report, and a Python script that generates **12 charts** and a **self-contained HTML report**.

> **The original CSV is never modified.** All processing is done on an in-memory copy.

---

## 📂 Project Structure

```
archive/
├── samplesuperstore.csv                              # Original dataset (read-only, NEVER modified)
├── PranitaNande_Superstore_Sales_Analysis.ipynb      # ★ Main Jupyter notebook (13 sections, 12 charts)
├── PranitaNande_Superstore_Sales_ProjectReport.docx  # ★ Word project report
├── superstore_analysis.py                            # Equivalent standalone Python script
├── superstore_cleaned.csv                            # Cleaned copy (generated on run)
├── superstore_report.html                            # Self-contained HTML report (generated on run)
├── requirements.txt                                  # pip install dependencies
├── charts/                                           # 12 PNG charts (generated on run)
│   ├── c1_category.png
│   ├── c2_subcategory.png
│   ├── c3_discount.png
│   ├── c4_seasonality.png
│   ├── c5_annual.png
│   ├── c6_segment.png
│   ├── c7_region.png
│   ├── c8_states.png
│   ├── c9_top_products.png
│   ├── c10_loss_products.png
│   ├── c11_shipmode.png
│   └── c12_scatter.png
└── README.md
```

---

## 📊 Dataset Source

| Field        | Detail |
|---|---|
| **Name**     | Sample Superstore |
| **File**     | `samplesuperstore.csv` |
| **Rows**     | 10,194 |
| **Columns**  | 21 |
| **Period**   | January 2023 – December 2026 |
| **Geography**| United States + Canada |
| **Origin**   | Tableau public sample dataset (widely used for BI/analytics training) |

### Columns

| # | Column | Type | Description |
|---|---|---|---|
| 1 | Row ID | Integer | Sequential row identifier |
| 2 | Order ID | String | Unique order reference |
| 3 | Order Date | Date | Date order was placed |
| 4 | Ship Date | Date | Date order was shipped |
| 5 | Ship Mode | Category | Shipping tier (Standard, Second, First, Same Day) |
| 6 | Customer ID | String | Unique customer reference |
| 7 | Customer Name | String | Customer full name |
| 8 | Segment | Category | Consumer / Corporate / Home Office |
| 9 | Country/Region | Category | United States or Canada |
| 10 | City | String | Order destination city |
| 11 | State/Province | String | US state or Canadian province |
| 12 | Postal Code | String | ZIP / FSA code |
| 13 | Region | Category | Central / East / South / West |
| 14 | Product ID | String | Unique product reference |
| 15 | Category | Category | Furniture / Office Supplies / Technology |
| 16 | Sub-Category | Category | 17 sub-categories |
| 17 | Product Name | String | Product full name |
| 18 | Sales | Decimal | Revenue per line item ($) |
| 19 | Quantity | Integer | Units ordered |
| 20 | Discount | Decimal | Discount rate applied (0.0 – 0.8) |
| 21 | Profit | Decimal | Net profit per line item ($) |

---

## 🎯 Project Objectives

1. **Inspect & clean** the raw dataset without modifying the source file
2. **Calculate KPIs** — Total Sales, Total Profit, Profit Margin, AOV, Orders, Customers, Avg Discount, Loss Rate
3. **Analyse performance** across Category, Sub-Category, Segment, Region, Ship Mode, and Time
4. **Quantify the discount–profit relationship** and identify the tipping-point discount level
5. **Identify business risks** from data patterns (loss-making products, regions, customers)
6. **Surface opportunities** for revenue and margin growth
7. **Deliver actionable recommendations** using the Fact → Insight → Action framework
8. **Visualise findings** in 12 publication-quality charts
9. **Package everything** into a single self-contained HTML report

---

## 🛠️ Technologies

| Tool | Version | Purpose |
|---|---|---|
| **Python** | 3.9+ | Core language |
| **pandas** | ≥ 1.5 | Data loading, cleaning, aggregation |
| **matplotlib** | ≥ 3.6 | Chart generation (12 PNGs) |
| **seaborn** | ≥ 0.12 | Plot theming |
| **base64** _(stdlib)_ | — | Embed charts into self-contained HTML |
| **webbrowser** _(stdlib)_ | — | Auto-open HTML report after run |
| **pathlib** _(stdlib)_ | — | Cross-platform file paths |

> `jinja2` is listed in the script header for reference but is **not required** — the HTML is built with f-strings.

---

## ⚙️ Setup Steps

### 1. Prerequisites

Make sure **Python 3.9 or later** is installed:

```bash
python --version
```

### 2. Clone / Download the project

```bash
# If using git
git clone <your-repo-url>
cd archive

# Or just place samplesuperstore.csv and superstore_analysis.py in the same folder
```

### 3. Create a virtual environment (recommended)

```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS / Linux
python3 -m venv venv
source venv/bin/activate
```

### 4. Install dependencies

```bash
pip install pandas matplotlib seaborn
```

Or using a requirements file:

```bash
pip install -r requirements.txt
```

**`requirements.txt`** contents:

```
pandas>=1.5
matplotlib>=3.6
seaborn>=0.12
```

---

## ▶️ Execution Steps

### Run the full analysis

```bash
python superstore_analysis.py
```

**What happens when you run it:**

| Step | Action | Output |
|---|---|---|
| 1 | Load raw CSV | Console: shape, dtypes, missing value report |
| 2 | Clean data | `superstore_cleaned.csv` |
| 3 | Print KPI dashboard | Console: formatted KPI table |
| 4–9 | Print dimensional tables | Console: Category, Segment, Region, Discount, Time-Series, Customer breakdowns |
| 10–11 | Print risks & opportunities | Console: flagged issues with quantified impact |
| 12 | Print recommendations | Console: Fact → Insight → Action for each recommendation |
| 13 | Generate 12 charts | `charts/c1_category.png` … `charts/c12_scatter.png` |
| 14 | Generate HTML report | `superstore_report.html` (auto-opens in browser) |

### Expected runtime

~10–20 seconds on a standard laptop (chart rendering is the bottleneck).

### Output files

```
superstore_cleaned.csv    # Cleaned dataset with derived columns
superstore_report.html    # Standalone HTML — open in any browser, no server needed
charts/                   # 12 PNG chart files
```

---

## 📋 Script Structure (14 Sections)

```
superstore_analysis.py
│
├── [Helpers]       fmt_usd(), summarise(), section(), save_fig()
│
├── Section 1       Load & Inspect
├── Section 2       Data Cleaning
├── Section 3       KPI Dashboard
├── Section 4       Category & Sub-Category Analysis
├── Section 5       Segment Analysis
├── Section 6       Regional Analysis
├── Section 7       Discount vs Profit Analysis
├── Section 8       Time-Series & Seasonality
├── Section 9       Customer & Product Analysis
├── Section 10      Risk Identification
├── Section 11      Opportunity Identification
├── Section 12      Business Recommendations (Fact → Insight → Action)
├── Section 13      Chart Generation (12 charts)
└── Section 14      HTML Report Generation
```

---

## 🔑 Key Findings

### KPIs (4-Year Cumulative, 2023–2026)

| KPI | Value |
|---|---|
| Total Sales | **$2.33M** |
| Total Profit | **$292K** |
| Profit Margin | **12.56%** |
| Total Orders | **5,111** |
| Total Customers | **804** |
| Avg Order Value (AOV) | **$455** |
| Avg Discount | **15.54%** |
| Loss Transactions | **1,901 (18.6%)** |

### Finding 1 — Discounts Above 30% Are Always Loss-Making
Every single transaction with a discount greater than 30% generates negative profit.
The 874 rows at 51–80% discount alone destroyed **$77,030** in profit — equal to 26% of
all profits earned by the rest of the business.

### Finding 2 — Furniture Is a Margin Problem, Not a Sales Problem
Furniture is the #2 category by sales ($754K) but generates only **$19,730 in profit (2.6% margin)**.
Tables sub-category alone: $208K in sales, **−$17,753 loss (−8.5% margin)**.

### Finding 3 — Central Region Margin Is Half the West's
West region achieves a **15.0% margin**; Central manages only **7.9%** despite being the 3rd-highest
revenue region. Texas (−$25.7K), Illinois (−$12.6K), and Ohio (−$17.0K) are the biggest loss states.

### Finding 4 — Home Office Is the Most Underserved Segment
Home Office has the **highest profit margin (14.0%)** across all three segments but the smallest
customer base — only **149 customers** out of 804. It is the single highest-potential growth lever.

### Finding 5 — Strong, Predictable Seasonality
September, November, and December are peak months **every year** without exception.
Q4 (Oct–Dec) consistently accounts for **~38% of annual revenue**.
February is the weakest month every year.

### Finding 6 — Consistent YoY Growth
| Year | Sales | Profit | Margin |
|---|---|---|---|
| 2023 | $494K | $51.7K | 10.5% |
| 2024 | $473K | $62.0K | 13.1% |
| 2025 | $614K | $82.7K | 13.5% |
| 2026 | $746K | $95.9K | 12.9% |

Sales grew **+51% from 2023 to 2026**; profit grew **+86%** over the same period.

### Finding 7 — Top Customer by Revenue Is Unprofitable
Sean Miller — the #1 customer by sales ($25K) — generates **−$1,981 in profit**.
Managing by revenue rank alone hides relationship-level losses.

---

## 💡 Business Recommendations Summary

| # | Recommendation | Expected Impact |
|---|---|---|
| 1 | Cap all discounts at 20% | Recover $80–100K profit/yr |
| 2 | Reprice or discontinue Tables | Eliminate −$17.7K annual loss |
| 3 | Fix Central region discount discipline | Close 7-point margin gap vs West |
| 4 | Grow the Home Office segment | High-margin revenue with existing products |
| 5 | Pre-stock Q4; run Q1 loyalty campaigns | Smooth seasonality, protect Q4 margins |
| 6 | Build a customer profitability scorecard | Identify and remediate net-negative accounts |

Each recommendation follows the **Fact → Insight → Action** framework — see `superstore_report.html`
or the console output of Section 12 for full details.

---

## 📎 Data Quality Notes

| Issue | Detail | Status |
|---|---|---|
| Missing values | None across all 21 columns | ✅ No action needed |
| Duplicate rows | None | ✅ No action needed |
| US ZIP codes (438 rows) | Leading zero stripped (e.g. `7036` → `07036`) | ✅ Fixed in script |
| Canadian postal codes | Partial FSA codes only (e.g. `M7A`) | ⚠️ Flagged; not correctable without reference table |
| Date format | M/D/YYYY strings | ✅ Parsed to datetime in script |

---

## 🔒 Data Integrity Guarantee

```python
# The original file is loaded once, read-only
df_raw = pd.read_csv("samplesuperstore.csv", dtype={"Postal Code": str})

# All transformations happen on a copy
df = df_raw.copy()

# The original is never written to
# df_raw.to_csv(...)  ← this line does NOT exist anywhere in the script
```

The cleaned output is saved to a **separate file** (`superstore_cleaned.csv`).
`samplesuperstore.csv` remains byte-for-byte identical before and after running the script.

---

## 👤 Author

**Pranita Nande**
Data Analytics Intern

---

*Built with Python · pandas · matplotlib · seaborn*
