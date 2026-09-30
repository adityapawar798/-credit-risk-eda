# Credit Risk EDA - Home Credit Default Risk

## Problem Statement
Understand which factors (income, age, job stability, loan amount, external credit score) influence loan default.

## Dataset
[application_train.csv - Kaggle dataset](https://www.kaggle.com/datasets/sarahashmi/application-train-csv)

Original source: Home Credit Default Risk (Kaggle competition)

File used: `application_train.csv` (~307k rows, 122 columns)

Note: The dataset is not included in this repository because of its large size. You can download it from the Kaggle link above.

## Tools
Python, Pandas, NumPy, Matplotlib, Seaborn (Google Colab)

## Approach
1. Data loading and column selection
2. Missing value handling and data cleaning
3. Univariate analysis
4. Bivariate analysis (default rate by segment)
5. Feature engineering (credit-to-income ratio, annuity-to-income ratio)
6. Correlation analysis

## Charts

**Correlation heatmap:** EXT_SOURCE_2 has the strongest linear relationship with default (-0.16).

<img width="930" height="746" alt="heatmap" src="https://github.com/user-attachments/assets/6cf1e614-7d36-445d-81d3-667966616da7" />

**Default rate by credit-to-income ratio:** The relationship is non-linear. Default rate is highest in the middle groups (about 8.5-9%) and lower at both extremes (about 7.2-7.4%).

<img width="554" height="526" alt="credit_ratio" src="https://github.com/user-attachments/assets/6c98e8d9-dc4f-4e66-b7ee-1befcf9f0b4f" />

**Default rate by age group:** Younger applicants tend to have a higher default rate, and the rate decreases as age increases.

<img width="562" height="479" alt="age_group" src="https://github.com/user-attachments/assets/129cd5bb-d889-4955-9950-145617ba0450" />


## Key Findings
- Only about 8.07% of applicants defaulted, so the data is heavily imbalanced.
- EXT_SOURCE_2 is the strongest linear predictor of default (correlation -0.16).
- AGE (-0.08) and YEARS_EMPLOYED (-0.07) have a weak negative relationship with default.
- The credit-to-income ratio has a non-linear relationship with default: default rate peaks in the middle groups (~8.5-9%) and is lower at both extremes (~7.2-7.4%).
- AMT_CREDIT and AMT_GOODS_PRICE are almost duplicates (correlation 0.99).

## Recommendations
- Give the most weight to external credit scores in loan approval.
- Apply extra verification for younger applicants and those with short employment history.
- Do not use the credit-to-income ratio alone; analyse it together with loan type.
- Remove one of the highly correlated features before modelling.
- Use Recall, Precision and ROC-AUC instead of accuracy, since the data is imbalanced.

## Limitations
- Only application_train.csv was used (other tables such as bureau data were not included).
- Correlation does not imply causation.
- Only 18 columns were selected for analysis.

## Notebook
See `Credit_EDA_Project.ipynb` for the full analysis and charts.
