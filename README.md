# E-Commerce Customer Lifetime Value (CLV) Prediction

A machine learning project that predicts **Customer Lifetime Value (CLV)** from e-commerce order and customer data, built as part of the **IBM SkillsBuild Data Analytics with AI Academic Internship Program**, conducted by **BharatCares** in association with **AICTE**.

## Project Description

E-commerce businesses generate large volumes of order-level data — customer demographics, payment details, discounts, shipping costs, and profitability. This project uses that data to build a **regression model** that predicts a customer's **Customer Lifetime Value**, i.e. the total future value a customer is expected to bring to the business.

Being able to predict CLV lets a business:
- Identify high-value customers early and prioritize retention efforts
- Target marketing and loyalty spend more efficiently
- Segment customers by predicted long-term value rather than just past purchases

The project covers the full data science workflow: data cleaning, exploratory data analysis (EDA), feature engineering, model training, model comparison/evaluation, and saving the final model for reuse.

## Dataset

- **Name:** E-Commerce Sales & Customer Analytics (150k records, selected columns)
- **File:** `ecommerce_sales_customer_analytics_150k-selected-columns.csv`
- **Size used in this notebook:** ~66,800 order records, 25 columns
- **Key columns:** `order_id`, `order_date`, `order_time`, `order_status`, `sales_channel`, `customer_id`, `customer_age`, `gender`, `customer_segment`, `payment_method`, `payment_status`, `discount_amount`, `tax_amount`, `shipping_cost`, `net_sales`, `product_cost`, `profit`, `profit_margin_percentage`, `customer_lifetime_value` (target), `is_repeat_customer`, `customer_order_count`

> Place the dataset CSV file in the same folder as the notebook before running it (or update the file path in the "Load Dataset" cell).

## Technologies Used

| Category | Tools / Libraries |
|---|---|
| Language | Python 3 |
| Data handling | pandas, numpy |
| Visualization | matplotlib, seaborn |
| Machine Learning | scikit-learn (Linear Regression, Random Forest Regressor, Gradient Boosting Regressor) |
| Model persistence | joblib |
| Environment | Jupyter Notebook |

## Project Workflow

1. **Data Loading & Cleaning** — load the CSV, inspect structure, handle missing values (`return_status` / `return_reason` are legitimately empty for non-returned orders), check duplicates
2. **Exploratory Data Analysis** — distribution of CLV, CLV by customer segment/repeat-customer status, correlation heatmap of numeric features
3. **Feature Engineering** — extract year/month/day-of-week/hour from order date & time
4. **Preprocessing** — label-encode categorical features, train/test split (80/20), feature scaling for Linear Regression
5. **Model Training** — Linear Regression, Random Forest Regressor, Gradient Boosting Regressor
6. **Evaluation** — MAE, RMSE, R² comparison across models; actual-vs-predicted plot; feature importance chart for the best model
7. **Model Saving** — best model and preprocessing objects (`scaler`, `label_encoders`, `feature_columns`) saved with `joblib`
8. **Inference Example** — a `predict_clv()` helper function demonstrating prediction on a new, unseen order

## Setup & Run Instructions

1. **Clone / download** this project folder.
2. **Create a virtual environment** (recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate      # Windows: venv\Scripts\activate
   ```
3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
4. **Place the dataset** (`ecommerce_sales_customer_analytics_150k-selected-columns.csv`) in the same directory as the notebook.
5. **Launch Jupyter and run the notebook:**
   ```bash
   jupyter notebook YourName_ProjectName.ipynb
   ```
   Run all cells in order (`Cell -> Run All`).
6. After training, the notebook saves these artifacts in the working directory:
   - `best_clv_model.pkl` — the trained model
   - `feature_scaler.pkl` — fitted `StandardScaler`
   - `label_encoders.pkl` — fitted `LabelEncoder` objects for each categorical column
   - `feature_columns.pkl` — list of feature columns used, in order

## Key Results

- Three regression models were trained and compared using **MAE**, **RMSE**, and **R² score** on a held-out 20% test set.
- The **Gradient Boosting Regressor** gave the best R² score among the three models tested (see the "Model Evaluation & Comparison" section of the notebook for exact numbers, which will vary slightly by environment/random seed).
- **Profit, net sales, and number of past orders** were consistently among the top predictors of Customer Lifetime Value.

## Repository / File Structure

```
├── YourName_ProjectName.ipynb    # Main project notebook (EDA + model training/evaluation)
├── requirements.txt              # Python dependencies
├── YourName_ProjectReport.docx   # Full written project report
├── README.md                     # This file
└── ecommerce_sales_customer_analytics_150k-selected-columns.csv   # Dataset (not included — see Dataset section)
```

## Author

_Your Name_ — IBM SkillsBuild Data Analytics with AI Academic Internship, BharatCares x AICTE

