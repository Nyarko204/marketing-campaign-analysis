# 📊 Marketing Campaign Analysis

A comprehensive Exploratory Data Analysis (EDA) and hypothesis testing project on a customer marketing dataset, structured around the **Four Ps of Marketing** (Product, Price, Place, Promotion).

---

## 🗂️ Project Overview

This notebook analyzes customer behavior and campaign performance to uncover actionable insights for marketing strategy. It covers the full data science pipeline — from raw data cleaning to statistical testing and business visualizations.

---

## 📁 Files

| File | Description |
|------|-------------|
| `Market_Campaigns.ipynb` | Main analysis notebook |
| `marketing_data.csv` | Source dataset (required) |

---

## 🔬 Analysis Pipeline

### Step 1 — Data Import & Cleaning
- Load dataset from CSV
- Clean column names
- Parse `Income` (strip `$`, `,` → float)
- Parse `Dt_Customer` dates

### Step 2 — Missing Value Imputation
- Standardize `Marital_Status` categories (e.g., `"Alone"`, `"YOLO"`, `"Absurd"` → `"Single"`)
- Impute missing `Income` values using group means (by `Education` × `Marital_Status`)

### Step 3 — Feature Engineering
- `Total_Children` = kids at home + teenagers at home
- `Age` = 2021 − `Year_Birth`
- `Total_Spending` = sum across all product categories
- `Total_Purchases` = web + catalog + store purchases

### Step 4 — Outlier Treatment
- Cap `Income` at the 99th percentile
- Remove improbable ages (≥ 100)

### Step 5 & 6 — Encoding & Correlation
- Ordinal encoding for `Education`
- One-hot encoding for `Marital_Status` and `Country`
- Correlation heatmap of all numeric features

### Step 7 — Hypothesis Testing
| Hypothesis | Method | Result |
|---|---|---|
| Age vs. store purchases | Pearson correlation | r = 0.14 |
| Children vs. web purchases | Pearson correlation | r = −0.14 |
| Store vs. web/catalog cannibalization | Pearson correlation | r = 0.51 / 0.56 |
| US vs. rest-of-world purchase volume | Independent t-test | p = 0.19 (not significant) |

### Step 8 — Business Visualizations
- 🏆 Total revenue by product category
- 📅 Campaign acceptance rate by age group
- 🌍 Accepted campaigns by country
- 👨‍👩‍👧 Total spending vs. number of children
- 🎓 Complaint distribution by education level

---

## 🛠️ Requirements

```bash
pip install pandas numpy matplotlib seaborn scipy
```

---

## 🚀 Usage

1. Place `marketing_data.csv` in the same directory as the notebook.
2. Open `Market_Campaigns.ipynb` in Jupyter.
3. Run all cells (`Kernel → Restart & Run All`).

---

## 📌 Key Findings

- **Wines and meat products** are the top revenue-generating categories.
- **Customers without children** spend significantly more overall.
- Channel purchases (store, web, catalog) are **positively correlated** — no strong cannibalization effect.
- Campaign acceptance rates vary by **age group**, with middle-aged customers showing higher response rates.
- No statistically significant difference in purchase volume between **US and international customers**.
