# Amazon Sales Dataset — Exploratory Data Analysis

An in-depth Exploratory Data Analysis (EDA) on 25,000+ Amazon clothing sales records (2024–2025), covering Men's, Women's, Kids', and Baby categories.

## Dataset

- **Records:** 25,000
- **Columns:** 19 (order, product, pricing, customer, and delivery attributes)
- **Time range:** July 2024 – June 2025

Key fields: `order_id`, `customer_id`, `product_name`, `main_category`, `sub_category`, `brand`, `price`, `quantity`, `discount_percent`, `final_price`, `payment_method`, `review_rating`, `order_date`, `delivery_days`, `is_returned`, `region`, `customer_age_group`, `device_type`.

## A. Data Cleaning

- Converted `order_date` to datetime
- Missing values (~1–5%) in `brand`, `price`, `payment_method`, `delivery_days`, `region`, `customer_age_group`, `device_type`
  - Categorical columns imputed with mode
  - Numerical columns (`price`, `delivery_days`) imputed with mean
- Outlier detection via IQR across all numeric columns (notable outliers in `final_price` and `review_rating`)
- Engineered features: `order_month`, `order_weekday`, `order_year`, `discount_amount`, `unit_price`, `delivery_speed`

## B. Univariate Analysis

- Distribution plots for price, final price, discount percent, review rating, delivery days
- Category share breakdowns (pie charts) across main category, sub-category, brand, payment method, region, age group, device type

## C. Bivariate & Multivariate Analysis

- Monthly revenue trend
- Revenue by category and brand
- Price vs. quantity sold
- Discount percent vs. quantity sold
- Return rate by category, brand, age group, and device type
- Customer segmentation: one-time buyers vs. high-value customers
- Delivery performance vs. review rating and return rate
- Rating patterns by brand, category, and region
- Return rate by payment method and device type
- Regional delivery time comparison
- Discount behavior by age group

## D. Hypotheses Explored

1. Longer delivery times negatively impact review ratings and increase returns
2. Certain age groups (e.g., 25–34) have higher average order values
3. Premium brands have lower return rates despite higher prices
4. Low review ratings are predictive of returns
5. Higher discounts increase quantity sold but also increase return rates

## E. Advanced Analysis

- **Cohort analysis** — monthly customer retention by first-purchase cohort
- **Customer segmentation** — K-Means clustering (3 clusters) on RFM (Recency, Frequency, Monetary) + return rate + avg rating
- **Price elasticity** — OLS regression of quantity on discount percent (no significant effect found)
- **Return prediction** — Logistic Regression baseline on price, quantity, discount, delivery days, review rating, and payment method (class imbalance limits recall on returns)
- **Anomaly detection** — flagging high-discount, high-quantity, returned orders
- **Delivery hotspots** — average delivery days by region and category

## F. Key Visualizations

- Monthly revenue & order volume trend
- Price distribution by category (boxplot)
- Correlation heatmap
- Return rate heatmap (category × region)
- Top 10 brands/regions by revenue
- Order count by payment method
- Price vs. quantity regression plot
- Delivery days vs. review rating regression plot
- RFM segmentation scatter plot
- Order value & rating comparison: returned vs. non-returned

## Tech Stack

- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn (StandardScaler, KMeans, Logistic Regression, OneHotEncoder)
- Statsmodels (OLS regression)

## Running Locally

```bash
git clone https://github.com/Midhat-Maryam/EDA-project.git
cd EDA-project
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels
jupyter notebook
```

Update the dataset path in the notebook to point to your local copy of the Amazon dataset CSV.

## License

MIT
