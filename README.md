# Tech Company Layoffs — Exploratory Data Analysis (MySQL)

## 📌 Project Overview
This project performs an **Exploratory Data Analysis (EDA)** on global tech company layoffs using **MySQL**. The dataset includes information on total employees laid off, percentage laid off, company funding, location/country, industry stage, and dates. 

The primary goal of this analysis is to uncover trends, identify which industries and companies were most affected, analyze monthly cumulative totals over time, and rank the top companies by total layoffs per year.

---

## 🛠️ SQL Concepts & Techniques Used
* **Data Aggregation & Grouping:** `SUM()`, `MAX()`, `GROUP BY`, `ORDER BY`
* **Date & String Manipulations:** `SUBSTRING()`, `YEAR()`
* **Window Functions:** `SUM() OVER()` for rolling cumulative totals, `DENSE_RANK() OVER()` for partitioned yearly rankings
* **Common Table Expressions (CTEs):** Used single and chained CTEs (`WITH` clauses) for complex multi-step transformations and filtering

---

## 📂 Repository Structure
```text
├── Exploratory_data_analysis.sql  # Complete MySQL script for EDA
└── README.md                      # Project documentation

```

---

## 🔍 Key Findings & Analytical Steps

### 1. Baseline Summary & Extremes

* **Max Layoffs:** Baseline maximums for `total_laid_off` and `percentage_laid_off` were evaluated to identify extreme cases.
* **100% Layoffs:** Filtered companies where `percentage_laid_off = 1` and sorted by `funds_raised_millions` to highlight highly funded startups that shut down entirely.

### 2. Aggregations by Dimensions

* **Top Companies:** Summarized total layoffs grouped by company to spot the hardest-hit organizations.
* **Geographic Impact:** Grouped total layoffs by country to assess regional impacts.
* **Company Stage:** Analyzed layoffs across funding and growth stages (e.g., Post-IPO, Series A-E).

### 3. Time Series & Rolling Totals

* **Monthly Layoffs:** Extracted year-month (`YYYY-MM`) using `SUBSTRING(date, 1, 7)` to observe monthly totals.
* **Rolling Total Cumulative Layoffs:** Applied the window function `SUM(total_off) OVER(ORDER BY MONTH)` inside a CTE to track the continuous running total of layoffs across time.

### 4. Yearly Ranking of Top Companies

* **Top 5 Companies per Year:** Constructed chained CTEs (`Company_Year` and `Company_Year_Rank`) using `DENSE_RANK() OVER (PARTITION BY years ORDER BY total_laid_off DESC)` to isolate and display the top 5 companies with the highest layoffs for each year.

---

## 🚀 How to Run

1. **Prerequisite:** Ensure MySQL Server and MySQL Workbench (or any preferred SQL client) are installed.
2. **Database Setup:** Load your cleaned table `layoffs_staging2` into your active database schema.
3. **Run Analysis:** Open `Exploratory_data_analysis.sql` and execute the queries sequentially.

---

## 👤 Author

* **Natalicio A. Siqueira** - [LinkedIn](https://www.linkedin.com/in/natalicio-aires-de-siqueira-5a220a1a2/) | [GitHub](https://github.com/Natalicioairesdesiqueira)

```

```
