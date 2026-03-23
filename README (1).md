# 🛒 Superstore Sales Analysis

![Python](https://img.shields.io/badge/Python-3.11-blue?style=flat&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?style=flat&logo=pandas)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0?style=flat)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-F7931E?style=flat&logo=scikit-learn)
![XGBoost](https://img.shields.io/badge/XGBoost-0.67%20R²-red?style=flat)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat)

An end-to-end data science project analyzing the Superstore dataset to uncover sales trends, profitability drivers, and actionable business recommendations — using Python, Pandas, Seaborn, and Machine Learning.

---

## 📌 Project Overview

This project simulates a real-world business analytics task: given transactional sales data, identify what's driving revenue, what's destroying profit, and build a predictive model to forecast profitability.

---

## 📂 Project Structure

```
superstore-sales-analysis/
│
├── data/
│   └── Sample - Superstore.csv
│
├── notebooks/
│   └── superstore_analysis.ipynb
│
├── images/
│   ├── monthly_sales_trend.png
│   ├── sales_by_category.png
│   ├── top_10_products.png
│   ├── sales_by_region.png
│   ├── profit_vs_sales.png
│   ├── discount_vs_profit.png
│   └── subcategory_heatmap.png
│
└── README.md
```

---

## 🔧 Tools & Libraries

- Python 3.11
- Pandas
- Matplotlib & Seaborn
- Scikit-learn
- XGBoost

---

## 🧹 Data Cleaning & Feature Engineering

- Converted `Order Date` and `Ship Date` to datetime format
- Extracted `Order Month`, `Order Year`, `Order Quarter`, `Order Day`
- Created `Discount Bracket` bins using `pd.cut()` for discount analysis
- Label encoded categorical columns (`Category`, `Region`, `Sub-Category`) for ML models

---

## 📊 Exploratory Data Analysis

### 1. Monthly Sales Trend
- Q4 (November & December) dominates sales — classic holiday season peak
- February is the weakest month across all years

### 2. Sales by Category
- **Technology** leads all categories in total sales
- Office Supplies has the highest volume but lower revenue per order

### 3. Top 10 Products by Sales
- **Canon imageCLASS Copier** is the single highest-grossing product — significantly ahead of all others
- Classic 80/20 rule: a handful of products drive the majority of revenue

### 4. Sales by Region
- **West** region leads in total sales
- **South** underperforms significantly — potential for targeted marketing investment

### 5. Profit vs Sales Scatter
- Technology orders cluster in the profitable zone
- Furniture and Office Supplies have a high concentration of loss-making orders (below the zero-profit line)

### 6. Sub-Category Profit Heatmap
- **Tables** and **Bookcases** are the biggest profit drains
- **Supplies** also running at a loss
- **Fasteners** essentially break even — low priority category

---

## 💸 Discount Analysis — Key Finding

> **Discounts beyond 20% consistently result in negative profit.**

| Discount Bracket | Avg Profit |
|-----------------|------------|
| 0–10%           | Positive ✅ |
| 10–20%          | Positive ✅ |
| 20–30%          | Near zero ⚠️ |
| 30–50%          | Negative ❌ |
| 50%+            | Heavily negative ❌ |

**Recommendation:** Hard cap discounts at 20%. Restructure promotional strategy to use BOGO or seasonal offers rather than blanket percentage discounts.

---

## 🤖 Machine Learning — Profit Prediction

### Features Used
- Sales, Discount, Quantity, Category, Region, Sub-Category (encoded)

### Models Compared

| Model | R² Score | RMSE |
|-------|----------|------|
| Linear Regression | -0.70 | High |
| Random Forest (default) | -0.04 | 212 |
| Random Forest (tuned) | 0.07 | 212 |
| **XGBoost** | **0.67** | **125** ✅ |

### Why XGBoost Won
Random Forest builds trees independently and averages them. XGBoost builds trees **sequentially**, with each tree correcting errors of the previous — making it significantly more powerful on tabular business data.

### Feature Importance (XGBoost)

| Feature | Importance |
|---------|-----------|
| Sales | 0.75 |
| Discount | 0.16 |
| Sub-Category | 0.03 |
| Quantity | 0.02 |
| Region | 0.02 |
| Category | 0.01 |

### Model Limitation
Despite tuning, R² remained moderate — indicating that profit is influenced by factors not present in this dataset (supplier costs, negotiated shipping rates, return rates). This is a valid and important finding: **the model tells us what it can and cannot explain.**

---

## 💡 Business Recommendations

| Finding | Recommendation |
|---------|---------------|
| Q4 peak sales | Pre-load inventory, launch campaigns in October |
| Canon Copier dominance | Protect margins, bundle with accessories |
| South region underperforms | Invest in regional marketing & awareness |
| Tables & Bookcases losing money | Reprice or discontinue |
| Discount > 20% = losses | Hard cap at 20%, switch to seasonal promotions |
| Technology most profitable | Prioritize Technology in marketing spend |

---

## 🚀 Future Work

- [ ] Logistic Regression classifier — predict whether an order will be profitable (Yes/No)
- [ ] Customer segmentation using KMeans clustering
- [ ] Time series forecasting for monthly sales
- [ ] SQL integration for querying insights directly

---

## 👤 Author

**Vishal Lohchab**  
[GitHub](https://github.com/Lohchab1212)
