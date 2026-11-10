# Customer Churn Analysis and Prediction

## Business Problem
A telecom company is losing customers. Which customers are likely to leave, and what factors drive them to leave?

## Goal
Find the main reasons for churn, predict which customers are at risk, and recommend ways to reduce churn.

## Dataset
Telco Customer Churn dataset (Kaggle): 7,043 customers and 21 columns. After cleaning, 7,032 customers and 20 columns remain.

## Tools
Python (pandas, matplotlib, seaborn, scikit-learn), Google Colab, GitHub

## Project Structure
| File | What it contains |
|---|---|
| `01_data_cleaning.ipynb` | Loading, cleaning and first findings |
| `02_eda.ipynb` | Exploratory data analysis and business insights |
| `03_model.ipynb` | Churn prediction models and evaluation |
| `churn_cleaned.csv` | Cleaned dataset used for analysis and modeling |

## Data Cleaning
- Converted `TotalCharges` from text to numbers.
- Dropped 11 rows with missing `TotalCharges` (new customers with 0 months tenure, not yet billed).
- Removed the `customerID` column and converted `SeniorCitizen` from 0/1 to No/Yes.

## Key Insights
- Overall churn rate is **26.6%**, so about 1 in 4 customers leaves.
- **Contract type:** month-to-month customers churn at 42.7%, compared with 11.3% for one-year and 2.8% for two-year contracts.
- **Tenure:** first-year customers churn at 47.7%, compared with 17.1% after the first year.
- **Internet service:** fiber optic customers churn at 41.9% (DSL: 19.0%) and also pay the highest monthly bills.
- **Add-on services:** customers without tech support or online security churn about 3 times more than those who have them.
- **Payment method:** electronic check users churn at 45.3%, about 3 times the rate of customers on automatic payment.

## Models
Data was split 80/20 into training and test sets (stratified, so churn is 26.6% in both). Class weights were balanced because only about 27% of customers churn.

| Model | Accuracy | Precision | Recall | ROC-AUC |
|---|---|---|---|---|
| Logistic Regression | 72.6% | 49.1% | 79.7% | 0.835 |
| Random Forest | 75.1% | 52.1% | 77.5% | 0.838 |

- Both models catch about 8 out of 10 customers who actually leave.
- The top predictors in the random forest were **tenure, total charges, two-year contract, monthly charges and fiber optic service**, which agree with the findings from the exploratory analysis.

## Recommendations
- Move month-to-month customers onto longer contracts with discounts or perks.
- Run an onboarding program focused on a customer's first 12 months.
- Bundle tech support and online security into plans.
- Encourage electronic check customers to switch to automatic payment.
- Review fiber optic pricing and service quality.

## Limitations
- Models were not tuned and use a single train/test split.
- Findings show associations, not proven causes.
- Tenure and total charges overlap strongly, so their importance is shared.

## How to Run
1. Open any notebook in Google Colab or Jupyter.
2. Upload `churn_cleaned.csv` to the same environment.
3. Run the cells from top to bottom.
