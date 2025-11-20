# PROJECT_SUMMARY.md  
### Regression Modeling of Medical Insurance Costs  
**Author:** Sabriya Sowers  

This document summarizes the key decisions, assumptions, and findings for my regression project using the Medical Costs dataset.

---

## **1. Problem Definition**
**Business / Analytical Question:**  
Can medical insurance charges be predicted based on demographic and health-related variables?

**Purpose of the Model:**  
To understand how features like age, BMI, and smoking status influence medical costs and to build a regression model that estimates total charges.

**Intended Users:**  
Students, analysts, or anyone learning regression modeling techniques.

---

## **2. Target Variable**
**Target variable name:** `charges`  
**Type:** Continuous (regression)  
**Description:** Total medical insurance cost for each individual.

---

## **3. Features Used**
I selected **three features** based on what I found during exploratory analysis:

- `age`
- `bmi`
- `smoker_num` (encoded from the `smoker` column)

These showed the strongest relationship with the target variable.

---

## **4. Feature Engineering**
- Encoded `smoker` into a numeric variable (`smoker_num` = 1 for yes, 0 for no).
- No new features were created.
- No features were removed.
- The dataset had no missing values, so no cleaning was needed.

---

## **5. Data Exploration Summary**
**Key Findings:**
- `charges` is highly right-skewed with many high-cost outliers.  
- Smokers show dramatically higher medical costs compared to non-smokers.  
- Age and BMI both trend upward with charges.  
- Regions and number of children are fairly balanced.  
- No invalid or impossible values were found.

---

## **6. Modeling Approach**
**Models Trained:**
1. Linear Regression  
2. Polynomial Regression (Degree = 3) using a pipeline that included:
   - Imputer  
   - PolynomialFeatures  
   - StandardScaler  
   - LinearRegression  

**Data Split:**  
- 80% training / 20% testing using `train_test_split`.

---

## **7. Evaluation Metrics**
Models were evaluated using:
- **R²**
- **MAE (Mean Absolute Error)**
- **RMSE (Root Mean Squared Error)**

These metrics help measure accuracy, error size, and how much variance the model explains.

---

## **8. Model Performance Summary**
**Linear Regression:**  
- Performed reasonably well but struggled with extreme high charges.

**Polynomial Regression (Degree 3):**  
- Higher R²  
- Lower MAE and RMSE  
- Captured nonlinear patterns more effectively  

**Conclusion:**  
Polynomial regression produced the strongest performance for this dataset.

---

## **9. Key Challenges**
- Handling the extreme outliers in the `charges` variable.  
- Making sure categorical values (especially smoker status) were encoded correctly.  
- Understanding how scaling affects polynomial models.

---

## **10. Insights & Real-World Impact**
- Smoking status was the strongest predictor of high medical charges.  
- BMI and age also had meaningful impacts on predicted costs.  
- The dataset showed nonlinear relationships, which made more complex models perform better.

---

## **11. Future Improvements**
If I had more time, I would try:
- Random Forest or Gradient Boosting models  
- Regularization techniques like Ridge or Lasso  
- Interaction features (e.g., BMI × smoker)  

---

## **12. Final Reflection**
This project helped me walk through an entire regression workflow—importing data, exploring patterns, selecting features, building pipelines, and comparing models. I learned how scaling and polynomial features can change model performance and how to evaluate results using multiple metrics. I’m most proud of pushing through challenges, fixing errors, and completing the full analysis successfully.

---
