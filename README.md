# 🔻 Funnel Analysis Project

A complete end-to-end funnel analysis project built entirely from scratch using SQL Server and Power BI. The project investigates why an e-commerce website has a low conversion rate and identifies where users are dropping off in the purchase journey.

> **Note on the dataset:** The dataset used in this project was synthetically generated for educational purposes. The analysis therefore focuses on methodology, structure, and analytical reasoning rather than real-world business insights. All queries, segmentation logic, and recommendations were written independently.

---

## 🗂️ Project Structure

```
funnel-analysis/
│
├── datasets/
│   ├── user_table.csv
│   ├── home_page_table.csv
│   ├── search_page_table.csv
│   ├── payment_page_table.csv
│   └── payment_confirmation_table.csv
│
├── scripts/
│   ├── 01_database_exploration.sql
│   ├── 02_user_overview.sql
│   ├── 03_funnel_building.sql
│   ├── 04_dropoff_analysis.sql
│   ├── 05_segmentation.sql
│   └── 06_reporting_and_recommendations.sql
│
└── README.md
```

---

## 🗄️ Data Model

The dataset represents user journeys through a 4-page e-commerce website:

| Table | Description |
|-------|-------------|
| `user_table` | All users with sex, device, and signup date |
| `home_page_table` | Users who visited the home page |
| `search_page_table` | Users who performed a search |
| `payment_page_table` | Users who reached the payment page |
| `payment_confirmation_table` | Users who completed a purchase |

**The Funnel:**
```
Home Page → Search Page → Payment Page → Confirmation Page
```

> All tables connect to `user_table` via `user_id`. A user appears in a page table only if they visited that page.

---

## 🔍 Analysis Steps

### Step 1 — Database Exploration
- Checked for nulls across all tables
- Verified row counts per table to get an early picture of the funnel
- Checked referential integrity between user_table and page tables
- Identified date range.

### Step 2 — User Overview
- Total users.

### Step 3 — Funnel Building
Built the complete funnel in a single query using UNION ALL and LAG() window functions to calculate conversion rates between each step.


### Step 4 — Drop-off Analysis
Calculated drop-off volume and rate between each funnel step.


### Step 5 — Segmentation Analysis
Rebuilt the funnel broken down by device and sex using PARTITION BY in window functions.


### Step 6 — Reporting & Recommendations
1. **Prioritize the Search → Payment experience** — 86% drop-off at this step is the single biggest revenue loss point
2. **Investigate the home page** — losing 50% of users before they even search suggests the home page lacks a compelling call to action
3. **Invest in mobile** — mobile users convert at double the rate of desktop users despite being fewer in number
4. **Do not segment by sex** — both groups behave identically.

---

## 🛠️ Tools & Technologies

- **Database**: SQL Server
- **Language**: T-SQL
- **Visualization**: Power BI
- **Concepts**: Funnel analysis, conversion rate optimization, cohort segmentation, window functions, CTEs

---

## 📊 Dashboard Preview

![Device Segmentation]
![Sex Segmentation]

---

## 👤 About This Project

This project was built as part of a personal data analytics portfolio. All queries were written independently including the funnel building logic, drop-off calculations, segmentation design, and final recommendations. The goal was to simulate a real analyst task — investigating a business problem, identifying the root cause, and presenting actionable recommendations.
