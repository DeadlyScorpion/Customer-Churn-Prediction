# 📉 Telco Customer Churn Prediction

![Python](https://img.shields.io/badge/Python-3.9-blueviolet)
![Pandas](https://img.shields.io/badge/Library-Pandas-green)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit_Learn-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## 📌 Executive Summary
Customer churn is a critical issue for telecommunications companies. This project analyzes customer demographics, services, and billing information to predict which customers are at risk of leaving.

**The Goal:** Identify key drivers of churn and build a machine learning model to predict at-risk customers with high sensitivity (Recall).

**The Result:** Developed a Logistic Regression model that identifies **80% of churners**, outperforming complex models like Random Forest and XGBoost on this specific dataset.

## 🔍 Key Business Insights
Through Exploratory Data Analysis (EDA) and Feature Importance analysis, we identified the top 4 drivers of churn:

1.  **Contract Type:** Customers on "Month-to-Month" contracts are the highest risk group.
2.  **Payment Friction:** Users paying via "Electronic Check" churn at significantly higher rates than those on automatic payments.
3.  **Tenure:** Churn risk is highest in the first 6 months; customers who survive this period become highly loyal.
4.  **Lack of Security:** Customers who do *not* subscribe to 'Online Security' or 'Tech Support' are more likely to leave.

## 🛠️ The Approach (Data Science Cycle)

### 1. Exploratory Data Analysis (EDA)
* Identified class imbalance (27% Churn rate).
* Discovered redundant features (`No phone service` / `No internet service`) and cleaned them.
* Visualized categorical distributions to form initial hypotheses.

### 2. Feature Engineering
* **Cleaning:** Handled missing values in `TotalCharges`.
* **Encoding:** Applied One-Hot Encoding to nominal variables and Label Encoding to ordinal variables (`Contract`).
* **Scaling:** Standardized numerical features (`Tenure`, `MonthlyCharges`) for linear modeling.

### 3. Model Building & Evaluation
Tested three distinct algorithms to find the best balance of Precision and Recall:

| Model | Class 1 Recall (Sensitivity) | F1-Score | Verdict |
| :--- | :---: | :---: | :--- |
| **Logistic Regression (Optimized)** | **0.80** | **0.62** | **🏆 Champion** |
| XGBoost (Weighted) | 0.76 | 0.60 | Runner Up |
| Random Forest (Tuned) | 0.46 | 0.53 | Poor performance on minority class |

*Note: We prioritized **Recall** because missing a churner (False Negative) is more costly to the business than a false alarm (False Positive).*

## 🚀 Strategic Recommendations
Based on the model findings, the following actions are recommended:
1.  **Incentivize Auto-Pay:** Offer a small discount for users switching from "Electronic Check" to "Credit Card (Auto)".
2.  **The "Security" Bundle:** Bundle 'Online Security' into standard packages to increase customer stickiness.
3.  **Tenure Bridge:** Target Month-to-Month users reaching the 5-month mark with promotional offers to lock them into 1-Year contracts.

## 📂 Project Structure
* `data/`: Contains the raw Telco Customer Churn dataset.
* `notebooks/`: The Jupyter Notebook with full code and analysis.

## 💻 How to Run
```bash
# Clone the repository
git clone [https://github.com/DeadlyScorpion/Customer-Churn-Prediction.git)

# Install dependencies
pip install pandas numpy scikit-learn seaborn matplotlib xgboost

# Run the notebook
jupyter notebook
