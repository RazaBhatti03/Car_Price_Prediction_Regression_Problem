# Car Price Prediction using Machine Learning

This project aims to predict car prices based on various technical and categorical attributes such as mileage, fuel type, engine volume, gearbox type, and more. Despite extensive feature engineering, tuning, and model optimization, achieving a high-performing model proved to be a challenge — reflecting the true complexity and noise in real-world automotive datasets.

---

## Objective

To build a machine learning pipeline that can estimate used car prices using structured data and understand what influences pricing the most.

---

## Dataset Overview

- **Dataset:** Structured CSV file of car listings
- **Size:** 19,237 records, 18+ features
- **Target Variable:** `Price` (Regression)

---

##  Workflow Summary

-  **Data Cleaning**
  - Removed inconsistencies, standardized units
  - Cleaned mileage, engine volume, and categorical noise
-  **Feature Engineering**
  - Created grouped features (`Manufacturer_grouped`)
  - Extracted numerical engine volume from text
  - Removed zero and unrealistic mileage
-  **Encoding**
  - Used Label Encoding, One-Hot, and Target Encoding as needed
-  **Outlier Detection**
  - Outliers identified using percentile logic
-  **Modeling**
  - Models used: `DecisionTreeRegressor`, `RandomForestRegressor`, `Lasso` for feature selection
  - Applied Cross-validation and GridSearchCV for tuning

---

##  Baseline Model (Decision Tree Regressor)

| Metric            | Train         | Test          |
|------------------|---------------|---------------|
| R² Score         | 88.07%        | ❌ -0.22       |
| MAE              | -             | 27,709.63      |
| MSE              | -             | 273B+          |

> Despite strong performance on the training data, the model **overfitted** severely and failed to generalize.

---

##  Final Model (After Lasso Feature Selection + Re-Tuning)

| Metric            | Train         | Test          |
|------------------|---------------|---------------|
| R² Score         | 0.006         | ❌ -0.0004     |
| MAE              | -             | 22,389.22      |

- Feature selection was done using **Lasso**, which reduced noise.
- Random Forest and Decision Trees were tuned extensively using `GridSearchCV`.

> Still, the model **did not improve significantly**, which indicates the complexity or noise in the data.

---

##  Challenges & Key Insights

- Many features had **very weak correlation** with `Price`.
- Target variable showed **high variance** and heavy tail distribution.
- Even after feature selection, scaling, outlier removal, and hyperparameter optimization, models were **unable to learn strong price patterns**.

---

##  Conclusion

This project reveals a key truth in real-world machine learning:  
> "Even with well-prepared pipelines and extensive tuning, model performance depends heavily on data quality and signal strength."

The repository remains open for improvements and experimentation.  
Anyone with better ideas, fresh modeling strategies, or domain-specific knowledge (especially in automotive pricing) is welcome to **fork** and enhance this work.

---


---

##  Next Steps for Contributors

- Try **Gradient Boosting** or **XGBoost**
- Test **log transformation** of `Price`
- Investigate **clustering by Manufacturer or Category**
- Explore **external data** like market trends or location

---

##  Acknowledgment

This project reflects detailed preprocessing, visualization, and modeling efforts.  
Despite challenges, it is a solid base for further development, MLOps deployment, or advanced experimentation.

---


