# Regression Modeling of Medical Insurance Costs
# README.md

## Introduction
This project analyzes the Medical Costs dataset to understand how demographic and health factors influence individual insurance charges. Using regression modeling techniques, this analysis explores how variables such as **age**, **BMI**, and **smoking status** contribute to medical cost prediction.  

The workflow includes:

- Data inspection  
- Exploratory data analysis  
- Feature engineering  
- Baseline linear modeling  
- Improved modeling with pipelines  
- Model comparison and insights  

The project demonstrates how regression supports **forecasting**, **population health analysis**, and **cost-related decision-making**.

[My Regression Notebook](https://github.com/ssowers2/ml_regression_sowers/tree/main/notebooks/final/regression_sowers.ipynb)
[Peer Review](https://github.com/ssowers2/ml_regression_sowers/blob/main/notebooks/peer_review.md)

---

## Section 1: Import and Inspect the Data

### Tools & Libraries
- **Pandas**, **NumPy** for data handling  
- **Matplotlib**, **Seaborn** for visualization  
- **Scikit-Learn** for preprocessing, regression models, and evaluation metrics  
- **Pipelines** for structured modeling workflows  

### Key Actions
- Loaded dataset (`insurance.csv`)  
- Reviewed structure using `.info()`  
- Displayed first 10 rows  
- Confirmed zero missing values  
- Verified that data types were correct  
- Reviewed summary statistics  

### Reflection 1
- Dataset loaded cleanly with **1,338 rows × 7 columns**  
- No missing data  
- Variables appear within normal and expected ranges  
- Structure is ready for modeling without corrections  

---

## Section 2: Data Exploration & Preparation

### Visualizations Generated
- **Histograms** for numeric features (age, BMI, children, charges)  
- **Boxplots** for smoker vs. charges & region vs. charges  
- **Count plots** for sex, smoker status, and region  

### Feature Engineering
- Converted `"smoker"` to numeric:  
  - `"yes"` → `1`  
  - `"no"` → `0`  
  - New feature: `smoker_num`

### Reflection 2

#### **Patterns in Numeric Features**
- **Age:** Spread across adult ranges; slight peaks in late 20s & late 50s  
- **BMI:** Bell-shaped around 25–35; right tail outliers  
- **Children:** Right-skewed; most have 0–2 children  
- **Charges:** Strongly right-skewed; many high-cost outliers  

#### **Patterns in Categorical Features**
- Smokers show **much higher charges**  
- Southeast region has slightly higher typical charges  
- Sex distribution is nearly even  
- Smoker distribution is **imbalanced**  
- Region distribution is fairly even  

#### **Outliers & Anomalies**
- Very high charges among smokers  
- Mild BMI outliers  
- No invalid values  

#### **Preprocessing**
- No cleaning required  
- Outliers retained because they are real cases  
- Encodings planned for categorical variables  

---

## Section 3: Feature Selection & Justification

### **Selected Features (X)**
1. **age** – Costs increase with age  
2. **bmi** – Higher BMI correlates with increased charges  
3. **smoker_num** – Strongest cost driver in the dataset  

### **Target Variable (y)**
- **charges** – Continuous variable for insurance cost prediction  

### **Definition of X and y**
```python
X = df[["age", "bmi", "smoker_num"]]
y = df["charges"]

Instructions on how to set up your virtual environment and run your notebook locally.
