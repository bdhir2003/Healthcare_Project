#  Healthcare_Project  
**Predicting 30-Day Hospital Readmission in Diabetic Patients Using Machine Learning**

---

##  Overview
This project predicts **early hospital readmission (within 30 days)** for diabetic patients using the **UCI Diabetes Dataset (130 U.S. hospitals, 1999–2008)**.  
The goal is to build a machine learning model that can help hospitals identify high-risk patients early and evaluate **fairness across race, gender, and age**.

The dataset includes **101,766 patient records** with **50 original features**.  
After preprocessing and feature selection, **24 important features** were used to train and compare multiple machine learning models.

This project is **still under development**, and future versions will include an **LLM-based module** integrated with the Random Forest model for interpretability.

---

##  Dataset Summary
- **Dataset:** UCI Diabetes (130 hospitals, 1999–2008)  
- **Samples:** 101,766  
- **Original Features:** 50 (13 numerical, 37 categorical)  
- **Selected Features:** 24 (11 numerical, 13 categorical)  
- **Shape:** (101,766, 24)

###  Class Distribution (Before Balancing)
| Category | Count |
|-----------|--------|
| No readmission | 54,864 |
| Readmission after 30 days | 35,545 |
| Readmission within 30 days | 11,357 |

To balance the dataset, **SMOTE (Synthetic Minority Oversampling Technique)** was applied:
- Final balanced distribution: 35,545 samples per class

---

##  Feature Selection
Feature selection was based on **correlation analysis**, **descriptive statistics**, and **medical literature** on diabetes readmission.

**Numerical Variables**
- admission_type_id  
- discharge_disposition_id  
- admission_source_id  
- time_in_hospital  
- num_lab_procedures  
- num_procedures  
- num_medications  
- number_outpatient  
- number_emergency  
- number_inpatient  
- number_diagnoses  

**Categorical Variables**
- race  
- gender  
- age  
- medical_specialty  
- diag_1, diag_2, diag_3  
- max_glu_serum  
- A1Cresult  
- insulin  
- change  
- diabetesMed  
- readmitted  

---

##  Model Performance

| Model | Accuracy | Notes |
|--------|-----------|-------|
| Random Forest | ~69% | Best performance, used for fairness testing |
| XGBoost | ~67% | Stable results but slightly lower accuracy |
| Logistic Regression | ~66% | Simpler, interpretable baseline |
| Deep Neural Network (DNN) | ~65% | Slightly underperformed classical models |

---

##  Fairness Analysis

### By Race
- **Lowest Accuracy:** Caucasian (0.575), African American (0.591)  
- **Higher Accuracy:** Asian (0.645), Unknown (0.687)  
- **Observation:** Racial disparities exist — some groups are better predicted than others.

### By Gender
- **Female:** 0.581  
- **Male:** 0.585  
- **Observation:** Gender predictions are fair and balanced.

### By Age
- **Children (0–10 years):** Very high accuracy (0.897) but small sample size (39 patients)  
- **Adults (30–80 years):** Accuracy around 0.55–0.65  
- **Elderly (80–90 years):** Lower accuracy, higher false negatives (0.124)  
- **Observation:** Models struggle to detect readmission risk in elderly patients.

---

##  Tools and Libraries
- Python  
- pandas · numpy · scikit-learn  
- imbalanced-learn (SMOTE)  
- matplotlib · seaborn  
- XGBoost  
- TensorFlow / Keras (for DNN)

---

##  Workflow
1. **Data Cleaning:** Removed invalid and missing values, encoded categorical variables  
2. **Feature Selection:** Based on correlation and domain research  
3. **Balancing:** Applied SMOTE to handle class imbalance  
4. **Model Training:** Random Forest, XGBoost, Logistic Regression, DNN  
5. **Evaluation:** Accuracy, Precision, Recall, F1, Confusion Matrix  
6. **Fairness Testing:** Analyzed bias across race, gender, and age  
7. **Next Steps:** Add LLM-based interpretability and visualization dashboard

---

##  Current Status
 Data preprocessing completed  
 Feature selection finalized  
 Models trained and compared  
 Fairness evaluation done  
 Next Step: LLM integration + result visualization

---

##  Author
**Bobby Dhir**  
Undergraduate Student, University of Nebraska Omaha  
Supervised by **Dr. Anoop Mishra** & **Dr. Deepak Khazanchi**

---

###  Summary
Machine learning project using healthcare data to predict **30-day readmission** for diabetic patients.  
Focuses on **accuracy, fairness, and ethical AI** — currently expanding into an **LLM-integrated system**.
