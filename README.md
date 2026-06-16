# Medical Insurance Cost Analysis

## Overview

This project performs an Exploratory Data Analysis (EDA) and Statistical Analysis on a healthcare insurance dataset to understand the factors that influence individual medical insurance charges. The dataset contains demographic, lifestyle, and health-related information of insurance beneficiaries, including age, gender, BMI, smoking habits, number of children, residential region, and medical costs.

The analysis aims to uncover meaningful insights through visualization, correlation analysis, outlier detection, and hypothesis testing.

---

## Dataset Description

The dataset contains **1,338 records** and **7 features**:

| Feature  | Description                                                               |
| -------- | ------------------------------------------------------------------------- |
| age      | Age of the primary beneficiary (18–64 years)                              |
| sex      | Gender of the beneficiary (male/female)                                   |
| bmi      | Body Mass Index (kg/m²)                                                   |
| children | Number of dependents covered by insurance                                 |
| smoker   | Smoking status (yes/no)                                                   |
| region   | Residential region in the US (northeast, northwest, southeast, southwest) |
| charges  | Individual medical costs billed by health insurance                       |

---

## Technologies Used

* Python
* NumPy
* Pandas
* Matplotlib
* Seaborn
* SciPy
* Statsmodels
* Scikit-learn

### Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import scipy.stats as stats
from sklearn.preprocessing import LabelEncoder
from statsmodels.stats.proportion import proportions_ztest
```

---

## Project Workflow

### 1. Data Loading and Inspection

* Import dataset using Pandas.
* Examine dataset shape and structure.
* Check data types and missing values.

### 2. Exploratory Data Analysis (EDA)

#### Data Quality Checks

* Dataset shape: **1338 rows × 7 columns**
* No missing values detected.
* Mixed data types:

  * Numerical: age, bmi, children, charges
  * Categorical: sex, smoker, region

#### Statistical Summary

Key observations:

* Average age: **39.2 years**
* Average BMI: **30.66**
* Average insurance charge: **$13,270**
* Maximum insurance charge: **$63,770**

---

### 3. Distribution Analysis

Analyzed distributions for:

* Age
* BMI
* Charges

#### Findings

**BMI**

* Approximately normally distributed.
* Slight positive skew.

**Age**

* Nearly uniform distribution.
* Majority of customers are younger adults.

**Charges**

* Strong right-skewed distribution.
* Most beneficiaries incur relatively lower medical costs.

---

### 4. Outlier Detection

Boxplots and IQR methods were used.

| Variable | Outliers |
| -------- | -------- |
| BMI      | 9        |
| Age      | 0        |
| Charges  | 139      |

Key observation:

* Insurance charges contain a significant number of extreme values.
* Age does not contain outliers.

---

### 5. Categorical Variable Analysis

Studied distributions of:

* Children
* Gender
* Smoking Status
* Region

#### Key Findings

* Most beneficiaries have no children.
* Male and female populations are nearly balanced.
* Non-smokers significantly outnumber smokers.
* Southeast region has the highest number of participants.

---

### 6. Bivariate Analysis

Relationships examined between:

* Children vs Charges
* Gender vs Charges
* Smoking Status vs Charges
* Region vs Charges

#### Key Findings

* Smokers generally incur much higher medical expenses.
* Southeast region exhibits higher insurance charges.
* Individuals without children show wider charge variability.

---

### 7. Correlation Analysis

Categorical variables were label encoded before computing correlations.

#### Strongest Correlations

| Feature Pair     | Correlation |
| ---------------- | ----------- |
| Smoker ↔ Charges | 0.787       |
| Age ↔ Charges    | 0.299       |
| BMI ↔ Charges    | 0.198       |

The strongest predictor of insurance charges is smoking status.

---

## Statistical Hypothesis Testing

### Test 1: Do Smokers Pay Different Charges Than Non-Smokers?

**Method:** Independent Two-Sample T-Test

#### Hypotheses

* H₀: Mean charges of smokers and non-smokers are equal.
* H₁: Mean charges of smokers and non-smokers are different.

#### Result

```text
p-value = 8.27e-283
```

**Conclusion**

Reject H₀.

There is a statistically significant difference between the insurance charges paid by smokers and non-smokers.

---

### Test 2: Does BMI Differ Between Males and Females?

**Method:** Independent Two-Sample T-Test

#### Hypotheses

* H₀: Gender has no impact on BMI.
* H₁: Gender impacts BMI.

#### Result

```text
p-value = 0.0899
```

**Conclusion**

Fail to reject H₀.

There is no statistically significant difference in BMI between males and females.

---

### Test 3: Is Smoking Proportion Different Across Genders?

**Method:** Two-Proportion Z-Test

#### Result

```text
p-value = 0.0053
```

**Conclusion**

Reject H₀.

The proportion of smokers differs significantly between males and females.

---

### Test 4: Does Number of Children Affect Female BMI?

**Method:** One-Way ANOVA

#### Result

```text
p-value = 0.7158
```

**Conclusion**

Fail to reject H₀.

The number of children does not significantly affect BMI among female beneficiaries.

---

## Key Insights

* Smoking status is the strongest factor influencing medical insurance costs.
* Medical charges exhibit significant positive skewness and many outliers.
* Age moderately impacts insurance costs.
* BMI has some influence on charges but is not strongly correlated.
* Gender does not significantly affect BMI.
* Smoking prevalence differs significantly across genders.
* Regional differences exist, with the Southeast showing higher medical costs.

---

## Future Improvements

* Build predictive machine learning models for insurance cost estimation.
* Compare regression algorithms:

  * Linear Regression
  * Ridge Regression
  * Random Forest Regressor
  * XGBoost
* Perform feature engineering and model optimization.
* Develop an interactive dashboard using Streamlit or Power BI.

---

## Project Structure

```text
Medical-Insurance-Cost-Analysis/
│
├── insurance.csv
├── Medical_Insurance_Cost_Analysis.ipynb
├── README.md
```

---

## Author

Healthcare Insurance Cost Analysis Project

Focused on understanding the impact of demographic and lifestyle factors on medical insurance charges using statistical analysis and exploratory data visualization.
