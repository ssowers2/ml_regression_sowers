# PROJECT_SUMMARY.md  
### Regression Modeling of Medical Insurance Costs  
**Author:** Sabriya Sowers  

This document summarizes the key decisions, assumptions, and findings for this regression project using the Medical Costs dataset.

---

## **1. Problem Definition**
**Business / Analytical Question:**  
Can medical insurance charges be predicted based on demographic and health-related variables?

**Purpose of the Model:**  
To explore how factors like age, BMI, and smoking status influence medical costs and to build a regression model that estimates total charges.

**Intended Users:**  
Students, analysts, or anyone learning regression modeling techniques.

---

## **2. Target Variable**
**Target variable name:** `charges`  
**Type:** Continuous (regression)  
**Description:** Total medical insurance cost for an individual.

---

## **3. Features Used**
I selected **three features** based on exploratory analysis:

- `age`
- `bmi`
- `smoker_num` (encoded from yes/no → 1/0)

These were chosen because they showed the strongest relationship with the target variable.

---

## **4. Feature Engineering**
- Encoded `smoker` into a numeric variable (`smoker_num` = 1 for yes, 0 for no).
- No additional new features were created.
- No features were removed.
- Data had no missing values, so no cleaning was required.

---

## **5. Data Exploration Summary**
**Findings:**
- `charges` is highly right-skewed with many high-cost outliers.  
- Smokers show dramatically higher charges compared to non-smokers.  
- BMI and age both show visible upward trends with charges.  
- Kid counts (`children`) and regions are fairly balanced.  
- No invalid or impossible values were detected.

---

## **6. Modeling Approach**
**Models Trained:**
1. **Linear Regression**
2. **Polynomial Regression (Degree = 3)** using a pipeline:
   - Imputer  
   - PolynomialFeatures  
   - StandardScaler  
   - LinearRegression  

**Data Split:**  
- 80% training / 20% testing (`train_test_split`)

---

## **7. Evaluation Metrics**
Evaluated the models using:
- **R²**
- **MAE** (Mean Absolute Error)
- **RMSE** (Root Mean Squared Error)

**Why these metrics:**  
They are standard for regression and show both error magnitude and how much variance the model explains.

---

## **8. Model Performance Summary**
**Linear Regression:**  
- Performed reasonably well but struggled with very high charges.

**Polynomial Regression (Degree 3):**  
- Higher R²  
- Lower MAE and RMSE  
- Captured nonlinear relationships more effectively.

**Conclusion:**  
Polynomial regression provided the best performance for this dataset.

---

## **9. Key Challenges**
- Managing extreme high-cost outliers that impacted model error.
- Ensuring smoker values were properly encoded before training.
- Understanding how scaling affects polynomial models.

---

## **10. Insights & Real-World Impact**
- Smoking status was the strongest cost driver.  
- BMI and age also meaningfully increase predicted medical costs.  
- Nonlinear relationships between variables make simple linear models less effective.

---

## **11. Future Improvements**
If more time were available, I would explore:
- Random Forest or Gradient Boosting models  
- Ridge/Lasso regularization  
- Creating interaction features (e.g., BMI × smoker status)  
- Log-transforming the target variable to handle skew

---

## **12. Final Reflection**
This project helped reinforce the full machine-learning workflow:
- Inspecting and cleaning data  
- Understanding relationships through visualizations  
- Selecting meaningful features  
- Applying pipelines  
- Comparing models with structured metrics  
  
Overall, this project helped me understand the full regression workflow. I learned how scaling and polynomial features affect a model, and I gained confidence working through errors and analysis challenges.

---