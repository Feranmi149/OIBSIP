# Data Analysis Portfolio: Retail Sales EDA, Customer Segmentation & Data Cleaning

This repository contains three independent data analysis projects, each 
demonstrating a different core data skill: exploratory data analysis, 
unsupervised machine learning for customer segmentation, and professional 
data cleaning.

## Tools Used
Python, pandas, numpy, scikit-learn (KMeans, StandardScaler), matplotlib, 
seaborn, Jupyter Notebook (Google Colab)

---

## Task 1: EDA on Retail Sales Data

### Objective
Performed exploratory data analysis on a retail sales dataset to uncover 
sales trends, customer demographics, and product performance insights.

### Dataset
Retail sales dataset (1,000 transactions) containing customer demographics, 
product categories, quantities, and transaction amounts.

### Key Steps
- Loaded and inspected the dataset (shape, dtypes, null check)
- Calculated descriptive statistics for numeric columns
- Analyzed monthly and quarterly sales trends
- Explored customer demographics: age group distribution and gender breakdown
- Analyzed revenue by product category
- Built a correlation heatmap across numeric variables
- Cross-analyzed age group and gender against spend for a deeper insight

### Key Insights
- Electronics generated the highest revenue, closely followed by Clothing, 
  with Beauty slightly behind — spend is fairly balanced across categories
- Customers aged 46-55 make up the largest share of the customer base
- Female and Male customers are nearly evenly split overall
- Total Amount correlates strongly with Price per Unit (0.85) and moderately 
  with Quantity (0.37); Age shows almost no correlation with spend
- Non-obvious insight: customers under 18 show a notable gender gap — Female 
  customers in this age group spend considerably more per transaction than 
  Male customers, despite gender spend being balanced in every other age group

### Recommendations
1. Prioritize Electronics inventory and marketing slightly ahead of Clothing 
   and Beauty, given its current revenue lead
2. Investigate what drove the highest sales month and replicate those 
   conditions at other points in the year
3. Explore targeted product bundles or campaigns for young Female customers 
   (under 18), an under-leveraged high-value segment

---

## Task 2: Customer Segmentation Analysis (RFM + K-Means)

### Objective
Segmented an e-commerce customer base into distinct groups based on 
purchasing behaviour using RFM analysis and K-Means clustering, to enable 
targeted marketing strategies.

### Dataset
Retail sales dataset, aggregated per customer into RFM (Recency, Frequency, 
Monetary) features.

### Key Steps
- Built RFM features per customer
- Standardized features using StandardScaler before clustering
- Used the Elbow Method to determine the optimal number of clusters (K=4)
- Applied K-Means clustering with K=4
- Visualized clusters via scatter plots (Recency vs Monetary, Frequency vs Monetary)
- Profiled each cluster's average RFM values and customer count

### Cluster Profiles
| Cluster | Recency | Monetary | Segment |
|---------|---------|----------|---------|
| 3 | Low | High | Champions — recently active, high spenders |
| 0 | High | High | At-Risk High Spenders — high value, inactive |
| 1 | Low | Low | Recent Low Spenders — active but low value |
| 2 | High | Low | Inactive Low-Value — low priority |

Note: Frequency was constant (1.0) across all customers, since each customer 
made only a single transaction — segmentation was driven entirely by 
Recency and Monetary.

### Recommendations
1. **Champions:** Retain with loyalty rewards or early access to new products
2. **At-Risk High Spenders:** Launch a personalized win-back campaign with a 
   meaningful discount
3. **Recent Low Spenders:** Use cross-sell/upsell tactics to increase 
   average order value
4. **Inactive Low-Value:** Deprioritize heavy spend; a low-cost reactivation 
   email is reasonable but not a priority

---

## Task 3: Data Cleaning (Titanic Dataset)

### Objective
Took a deliberately messy dataset and systematically transformed it into a 
clean, analysis-ready dataset, documenting every decision.

### Dataset
Titanic passenger dataset (1,301 rows, 10 columns) — sourced with 
inconsistent headers, placeholder missing-value markers, and mixed data types.

### Key Steps
- Fixed a corrupted header row (real column names were misread as data)
- Produced a data quality report: null counts, duplicate rows, dtype issues
- Uncovered hidden placeholder values ("?" in age, "**" in fare) not 
  initially flagged as missing
- Handled missing values per column with documented justification:
  - Gender, Family, Embarked → mode imputation (low missing count, categorical/count data)
  - Age, Fare → median imputation (robust to skew/outliers)
- Removed 1 duplicate row
- Standardized formatting (gender and embarked were already consistent; 
  date converted from text to proper datetime)
- Detected outliers in Age and Fare using the IQR method; reviewed and 
  retained them as genuine values rather than errors
- Corrected data types across all columns
- Produced a before-vs-after summary table
- Saved the cleaned dataset to a new CSV file

### Before vs. After Summary
| Metric | Before | After |
|--------|--------|-------|
| Row Count | 1301 | 1300 |
| Null Count | 270 | 0 |
| Duplicate Count | 1 | 0 |

### Output
`cleaned_titanic_dataset.csv` — the final, cleaned dataset ready for analysis.
