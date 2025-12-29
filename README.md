# Telco-churn-EDA
exploratory data analysis (EDA) on a Telco customer churn dataset to identify key factors influencing customer retention and churn patterns
# Telco Customer Churn Analysis

## Overview
This notebook performs an exploratory data analysis (EDA) on a Telco customer churn dataset to identify key factors influencing customer retention and churn patterns.

---

## 1. Data Import & Exploration

### Load Dataset
- Read the Telco Churn dataset from CSV
- Display dataset shape and basic information about columns and data types

### Data Inspection
- **Shape**: Shows number of rows (customers) and columns (features)
- **Column Names**: Lists all features in the dataset
- **Data Types**: Identifies numeric vs categorical columns
- **Missing Values**: Checks for null values using `isnull().sum()`
- **Duplicates**: Identifies and counts duplicate rows

---

## 2. Data Cleaning

### TotalCharges Conversion
The `TotalCharges` column contains some invalid string values (spaces, non-numeric characters at position 488).

**Fix Applied**:
- Strip whitespace from all values
- Replace empty strings with NaN (missing values)
- Convert to numeric using `pd.to_numeric()` with `errors='coerce'` (invalid values become NaN)
- Result: Column is now numeric and ready for calculations

---

## 3. Overall Churn Rate Calculation

### Method
- Normalize column names (remove extra spaces)
- Normalize `Churn` values (strip, lowercase, compare to "Yes")
- Calculate: (Count of churned customers / Total customers) × 100
- Results: 
  - **Precise rate**: e.g., 26.45%
  - **Integer range**: e.g., 26-27%

**Key Insight**: ~26% of customers have churned overall.

---

## 4. Tenure Analysis

### Visualization
- Box plot comparing tenure (months with company) by churn status

### Finding
- **Churned customers**: Average 18 months
- **Retained customers**: Average 38 months
- **Insight**: Customers at higher risk in early stages (first 6-12 months)
- **Action**: Focus on onboarding and early engagement strategies

---

## 5. Monthly Charges Analysis

### Visualization
- Box plot comparing monthly charges by churn status

### Finding
- Churned customers tend to have higher monthly charges
- **Insight**: Price sensitivity may drive churn decisions

---

## 6. Contract Type Analysis

### Visualization
- Count plot showing churn distribution across contract types

### Churn Rates by Contract Type (sorted high to low)
- **Month-to-Month**: ~42% churn rate (highest)
- **One Year**: ~11% churn rate
- **Two Year**: ~3% churn rate (lowest)

### Key Insight
- Contract length is a **strong churn predictor**
- Longer contracts = lower churn (customer commitment)
- **Action**: Promote longer contract options for retention

---

## 7. Internet Service Type Analysis

### Visualization
- Count plot showing churn distribution by internet service

### Churn Rates by Internet Service (sorted high to low)
- **Fiber Optic**: ~42% churn rate (highest)
- **DSL**: ~19% churn rate
- **No Internet**: ~7% churn rate (lowest)

### Key Insight
- Fiber optic customers are significantly more likely to churn
- May indicate price expectations or service quality issues
- **Action**: Targeted retention strategies for fiber optic segment

---

## 8. Correlation Matrix

### Purpose
- Identifies relationships between numeric variables and churn
- Helps find which numeric features most impact churn behavior
- Excludes categorical and ID columns (non-numeric)

### Interpretation
- Positive correlation: Feature increases → Churn likely increases
- Negative correlation: Feature increases → Churn likely decreases

---

## 9. Payment Method Analysis

### Visualization
- Count plot showing churn by payment method

### Churn Rates by Payment Method (sorted high to low)
- **Electronic Check**: ~45% churn rate (highest)
- **Mailed Check**: ~20% churn rate
- **Bank Transfer**: ~16% churn rate
- **Credit Card**: ~11% churn rate (lowest)

### Key Insight
- Payment method strongly influences churn
- Electronic check users are least engaged/committed
- Credit card users show highest retention
- **Action**: Incentivize customers to switch from electronic check to automated methods (credit card, bank transfer)

---

## Summary of Key Findings

1. **Tenure**: Highest churn in first 18 months
2. **Contract Type**: Month-to-month = 42% churn vs 3% for 2-year
3. **Internet Service**: Fiber optic = 42% churn vs 7% without internet
4. **Payment Method**: Electronic check = 45% churn vs 11% for credit card
5. **Monthly Charges**: Churned customers pay more on average

## Recommendations

- Focus retention efforts on early-stage customers (first 18 months)
- Promote longer-term contracts as churn reduction strategy
- Provide targeted support for fiber optic customers
- Encourage migration to credit card or bank transfer payments
- Investigate service quality issues with fiber optic and electronic check segments
