# NVidia-market-analysis
In-Depth Analysis of Nvidia’s Customer Landscape

## Overview 📋

This project performs an end-to-end exploratory data analysis and regression modeling on NVIDIA's market performance data, spanning multiple years, regions, product categories, and customer segments. The goal is to extract actionable business insights from sales, marketing, and customer behavior data to understand what drives NVIDIA's revenue growth.

**Core Question:** What factors most significantly influence NVIDIA's sales revenue, and how has the company's market performance evolved over time?

---

## Dataset Features 🗃️

| Feature | Description |
|---|---|
| `Date` | Calendar date of the observation |
| `Product Category` | High-level product classification (GPU, AI hardware, software) |
| `Product Name` | Specific product model (RTX 4090, A100, Tesla V100, etc.) |
| `Region` | Geographic market (North America, APAC, Europe, etc.) |
| `Units Sold` | Number of units sold on a given date and region |
| `Customer Segment` | Target group (Gaming, Data Center, Enterprise, etc.) |
| `Customer Type` | Individual, SMB, Enterprise, or Government |
| `Customer Satisfaction` | Survey-based satisfaction score (1–5) |
| `Marketing Spend (USD)` | Marketing investment for the product/region |
| `Discount Percentage (%)` | Promotional discount offered to customers |
| `Competitor Influence` | Level of competitive pressure (Low / Medium / High) |
| `Return Rate (%)` | Percentage of units returned by customers |
| `AI/ML Adoption Rate (%)` | Share of customers adopting AI/ML-related features |
| `Ad Campaign Effectiveness` | ROI or conversion-based marketing performance metric |
| `Customer Retention Rate (%)` | Percentage of repeat or ongoing customers |
| `Product Launch Date` | Date the product model was first released |
| `Competitor Product` | Competing product affecting NVIDIA's sales |
| `Market Share (%)` | NVIDIA's share of the total market by segment/region |
| `Sales Revenue (USD)` | Total revenue generated (target variable) |

---

## Analysis Workflow 🔬

The notebook follows a structured pipeline across 12 steps:

**1. Import Libraries** — pandas, matplotlib, seaborn, statsmodels, numpy

**2. Load Data** — reads `nvidia_market_analytics.csv` into a DataFrame

**3. Data Dictionary** — full feature reference table

**4. Data Profiling** — `.sample()`, `.info()`, `.describe()` for an initial look at shape and types

**5. Data Cleaning** — column renaming for coding compatibility; datetime conversion for `Date` and `Product Launch Date`; one-hot encoding readiness; median imputation for numeric nulls and mode imputation for categorical nulls; duplicate check (none found)

**6. EDA (Exploratory Data Analysis)** — average units sold by product category; total units sold over time (2012 peak: 3.3M units); total sales revenue time series (2024 peak: $722B+); average revenue by region; market share by product category; revenue distribution before vs. after 2020

**7. Categorical Encoding** — one-hot encoding with `drop_first=True` across all category-type columns

**8. Correlation Analysis** — full correlation heatmap across all encoded features

**9. Linear Regression (Full Model)** — OLS regression with 30 predictors including units sold, marketing spend, discount, AI/ML adoption, customer retention, region dummies, product dummies, competitor dummies, and more

**10. Model Adjustment** — simplified to the single statistically significant predictor (`RTX 4090`) after removing variables with insignificant p-values

**11. Final Conclusions** — business interpretation and strategic recommendations

**12. Export** — cleaned data exported to `nvidia_market_analytics_processed.csv`

---

## Key Findings 🔑

**Units Sold** are relatively stable across years, suggesting mature and steady market demand — except for a notable dip in 2024, pointing to a possible product mix shift toward higher-ASP items.

**Sales Revenue** grew exponentially from 2010 to 2024, reaching a peak of over $722 billion in total, despite flat unit volumes. This gap between units and revenue signals strong pricing power, especially driven by AI/data center products.

**Regional Performance:** South America leads in average revenue per transaction at ~$43.8M, while Middle East is the lowest at ~$38.4M. North and South America are the highest-priority regions for marketing allocation.

**Market Share** is nearly evenly distributed across all product categories (24–25% each), indicating broad adoption of NVIDIA technologies across gaming, data center, OEM, and AI hardware segments.

**Regression Insight:** After removing statistically insignificant variables, only `ProductName_RTX 4090` remained significant — suggesting that flagship GPU product presence is the strongest binary predictor of elevated revenue in this dataset. The low R² confirms that a simple linear model is insufficient to capture the full complexity; more advanced ML approaches are recommended for future work.

---

## Technologies Used 💻

- **Python** — primary language
- **pandas** — data loading, cleaning, and manipulation
- **matplotlib / seaborn** — data visualization
- **statsmodels (OLS)** — linear regression modeling
- **numpy** — numerical operations
- **Jupyter Notebook** — interactive analysis environment

---

## How to Run ▶️

1. Clone this repository
2. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/jamesanderson23/nvidia-data-for-business-insights) and place `nvidia_market_analytics.csv` in the root folder
3. Install dependencies:
```bash
   pip install pandas matplotlib seaborn statsmodels numpy
```
4. Open and run the notebook:
```bash
   jupyter notebook Steven_Nguyen_TU_Final_Project.ipynb
```

---

## Limitations & Future Work ⚠️

The linear regression model explains very little of the variance in sales revenue (R² ≈ 0%), meaning the true drivers are non-linear and complex. Future improvements could include tree-based models (Random Forest, XGBoost), time series forecasting, interaction terms between marketing spend and region, and incorporating external macro indicators such as GPU market reports or competitor earnings data.

---

## Author 👤

**Steven Nguyen**
Temple University — Business Analytics
