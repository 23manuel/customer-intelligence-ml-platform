---

# Segmented Customer Intelligence Pipeline

This project demonstrates a full **customer analytics and forecasting pipeline** for a financial services business. It combines **behavioral analysis, customer segmentation, fraud detection, and Customer Lifetime Value (CLV) forecasting** into a single, scalable workflow.

The goal is to deliver **actionable business insights** while maintaining **efficient and memory-safe data processing** for large datasets.

---

## Key Business Insights

* **Churn is negligible**: Only 1 percent of customers break their normal activity pattern. Predicting churn is unnecessary.
* **Behavior drives value**: Transaction frequency and spending intensity are stronger predictors of customer value than income or demographics.
* **Segmented targeting**: Four distinct customer groups are identified, guiding marketing and retention strategies.
* **Fraud and risk monitoring**: Unusual transactions are flagged, helping prevent revenue loss.
* **Optimized resource allocation**: Automated predictions cover the majority of customers, while high-value users receive dedicated attention.

---

## Notebook Workflow

The notebook is structured into **six main epics**, each focusing on a specific part of the analytics pipeline:

### Epic 1 & 2: Foundation and Transaction Intensity Mapping

* Efficiently load and clean large datasets using **Polars**.
* Compute key customer metrics such as total spend, number of transactions, average transaction amount, and account lifespan.
* Calculate dynamic churn based on user activity patterns.
* Merge user, transaction, and card data into a single, memory-efficient DataFrame.

### Epic 4: Customer Segmentation

* Convert Polars data to **Pandas** for machine learning compatibility.
* Scale key behavioral and financial features.
* Apply **K-Means clustering** to identify four customer segments: Casual Users, High Credit Users, Regular Users, and High Volume Users.
* Visualize clusters to communicate insights to business stakeholders.

### Epic 5: Anomaly and Fraud Detection

* Train an **Isolation Forest** model on a representative sample of transactions.
* Flag the top 1 percent of unusual transactions for review.
* Identify high-value outliers and large refunds or chargebacks.

### Epic 6: Customer Lifetime Value Forecasting

* Train an initial **XGBoost** model using only demographic data.
* Observe low predictive accuracy, highlighting that behavior drives spending more than demographics.
* Upgrade to a **hybrid model** combining demographics with transaction behavior metrics.
* Evaluate model performance and feature importance for business insight.

### Epic 6.3: Segmented Forecasting with Specialist Agents

* Train **four separate XGBoost models**, one per customer segment.
* Reduce prediction errors for mid-tier customers while highlighting risks with high-value users.
* Provide a strategic roadmap for combining AI automation with human oversight.
* Export trained models and scalers as `.pkl` files for production deployment or API integration.

---

## Technical Requirements

```text
polars
pyarrow
pandas
scikit-learn
xgboost
matplotlib
seaborn
joblib
```

Install all packages using:

```bash
pip install polars pyarrow pandas scikit-learn xgboost matplotlib seaborn joblib
```

---

## Dataset Structure

* **transactions_data.csv**: Records of customer transactions with timestamps and amounts.
* **users_data.csv**: Customer demographic and financial information.
* **cards_data.csv**: Credit card details per customer, including limits and number of cards.

---

## Outcomes and Business Value

* **Reduced prediction error**: Overall system error dropped from $111,000 to $108,000.
* **High reliability for everyday customers**: Prediction error around $49,000 for mid-tier users.
* **Strategic focus on high-value customers**: AI flags the top 20 percent for human oversight.
* **Scalable insights**: Segmented modeling provides targeted marketing, retention strategies, and risk management.
* **Actionable visualizations**: Clear cluster plots and feature importance charts support business decision-making.

---

## Usage Instructions

1. Open the notebook in **Google Colab**.
2. Mount Google Drive and set `base_path` to the folder containing CSV datasets.
3. Run the notebook sequentially through all epics.
4. Review cluster summaries, flagged transactions, and CLV forecasts.
5. Use exported `.pkl` models for production deployment or API integration.

---

