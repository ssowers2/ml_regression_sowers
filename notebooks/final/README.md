# Regression Modeling of Medical Insurance Costs

## Introduction
This project analyzes the Medical Costs dataset to understand how demographic and health factors influence individual insurance charges. Using regression modeling techniques, this analysis explores how variables such as **age**, **BMI**, and **smoking status** contribute to medical cost prediction.

The workflow includes:
- Data inspection  
- Exploratory data analysis  
- Feature engineering  
- Baseline linear modeling  
- Improved modeling with pipelines  
- Model comparison and insights  

This project demonstrates how regression supports **forecasting**, **population health analysis**, and **cost-related decision-making**.

- **My Regression Notebook:**  
  https://github.com/ssowers2/ml_regression_sowers/tree/main/notebooks/final/regression_sowers.ipynb

- **Peer Review:**  
  https://github.com/ssowers2/ml_regression_sowers/blob/main/notebooks/final/peer_review.md

---

## Section 1: Import and Inspect the Data

### Tools & Libraries
- **Pandas**, **NumPy** for data handling  
- **Matplotlib**, **Seaborn** for visualizations  
- **Scikit-Learn** for preprocessing, modeling, and evaluation
- **Pipelines** for structured modeling workflows  

### Key Actions
- Loaded dataset (`insurance.csv`)  
- Reviewed structure with `.info()`  
- Displayed first 10 rows  
- Confirmed zero missing values  
- Verified data types  
- Checked summary statistics  

### Reflection 1
- Dataset loaded cleanly with **1,338 rows × 7 columns**  
- No missing values  
- Numeric ranges look realistic  
- Data required no corrections before modeling  

---

## Section 2: Data Exploration & Preparation

### Visualizations
- Histograms for numeric features  
- Boxplots for smoker vs. charges and region vs. charges  
- Count plots for sex, smoker status, and region  

### Feature Engineering
- Encoded `"smoker"` into numeric form:  
  - `"yes"` → `1`  
  - `"no"` → `0`  
  - Created: `smoker_num`

### Reflection 2

#### Patterns in Numeric Features
- **Age:** Distributed broadly; peaks in late 20s & late 50s  
- **BMI:** Centered around 25–35 with right-tail outliers  
- **Children:** Right-skewed, majority have 0–2  
- **Charges:** Highly right-skewed with many high-cost outliers  

#### Patterns in Categorical Features
- Smokers have **much higher charges**  
- Slight regional variation  
- Sex almost evenly split  
- Smoker imbalance (more non-smokers)  

#### Outliers & Anomalies
- High charges among smokers  
- A few BMI outliers  
- No invalid values  

#### Preprocessing
- No cleaning required  
- Outliers kept (they represent real cases)  
- Encodings planned for categorical variables  

---

## Section 3: Feature Selection & Justification

### Selected Features (X)
- **age** — charges increase with age  
- **bmi** — higher BMI correlates with higher costs  
- **smoker_num** — strongest predictor in dataset  

### Target Variable (y)
- **charges** — total insurance cost (continuous)

### Definition of X and y
```python
X = df[["age", "bmi", "smoker_num"]]
y = df["charges"]
```

---

## Section 4: Modeling Approach (Summary)
This project evaluates:

1. **Baseline Linear Regression**
2. **Pipeline 1:** Imputer → StandardScaler → Linear Regression  
3. **Pipeline 2:** Imputer → PolynomialFeatures (degree 3) → StandardScaler → Linear Regression  

### Key Takeaways
- Linear regression worked well but struggled with high-cost outliers.  
- Polynomial regression (degree 3) significantly improved performance.  
- Scaling stabilized model behavior, especially with polynomial features.

---

## Section 5: Model Performance Summary
Metrics used:

- **R²**
- **MAE**  
- **RMSE**

### Findings
- Polynomial regression outperformed linear regression across all metrics.  
- Nonlinear patterns in the data were captured better by polynomial features.  

---

## Section 6: Final Thoughts & Insights

### 6.1 Summary of Findings
- Age, BMI, and smoking status reliably predict medical charges.  
- The polynomial model had the highest R² and lowest error metrics.  
- Medical cost data benefits from nonlinear modeling approaches.

### 6.2 Challenges Faced
- Managing extreme high-cost values  
- Choosing suitable features  
- Understanding model behavior with scaling and polynomial terms  

### 6.3 What I Would Try Next
- Random Forest Regression  
- Gradient Boosting  
- Ridge/Lasso  
- Interaction features (e.g., BMI × smoker)  
- Log transformation of charges  

### Reflection 6
This project helped me understand the full regression workflow—data exploration, feature selection, pipelines, scaling, modeling, and performance comparison. Working through errors helped me learn and build confidence.

---

# Additional Instructions for Reproducibility  
*(Added based on course template requirements.)*

## Set Up Your Virtual Environment

From the **project root directory**, run:

```shell
uv venv
uv python pin 3.12
uv sync --extra dev --extra docs --upgrade
uv run pre-commit install
uv run python --version
```

### Activate Environment

**Windows (PowerShell):**
```shell
.\.venv\Scripts\activate
```

## How to Run the Notebook Locally

Once your environment is active:

```shell
uv run jupyter notebook
```

Then open:

```
notebooks/final/regression_sowers.ipynb
```

OR open directly in VS Code using the built-in Jupyter extension.

---

## Daily Development Workflow (Recommended)

```shell
git pull
uv sync --extra dev --extra docs --upgrade
uv cache clean
git add .
uvx ruff check --fix
uvx pre-commit autoupdate
uv run pre-commit run --all-files
git add .
uv run pytest
```

---

## Build Documentation (if needed)

```shell
uv run mkdocs build --strict
uv run mkdocs serve
```

---

## Version Control Workflow

```shell
git add .
git commit -m "Describe your change"
git push -u origin main
```

---