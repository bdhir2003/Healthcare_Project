Healthcare Project – Predicting Early Readmission Rates in Diabetic Patients
 Overview

This project focuses on predicting 30-day hospital readmission for diabetic patients using machine learning on the UCI Diabetes Dataset (130 U.S. hospitals, 1999–2008).
The aim is not only to achieve strong predictive performance but also to evaluate fairness across demographic groups such as race, gender, and age.

The dataset contains 101,766 patient records and 50 clinical + demographic features.
After data cleaning and feature selection, 24 key features were used to build and compare multiple ML models.

This project is still under development — the next phase includes improving fairness metrics and integrating a lightweight LLM module based on the Random Forest model for interpretability.

Data Summary

Dataset: UCI Diabetes 130-US hospitals (1999–2008)

Total samples: 101,766

Initial features: 50 (13 numerical, 37 categorical)

Final selected features: 24 (11 numerical, 13 categorical)

Final data shape: (101,766, 24)

Class distribution before balancing:

Readmission Category	Count
No readmission	54,864
Readmission >30 days	35,545
Readmission <30 days	11,357

Applied SMOTE (Synthetic Minority Oversampling Technique) to balance minority classes:
Final balanced classes each have ≈35,545 samples.

 Feature Selection

After analyzing correlations, descriptive statistics, and diabetes-related literature, 24 features were finalized:

Numerical Variables

admission_type_id

discharge_disposition_id

admission_source_id

time_in_hospital

num_lab_procedures

num_procedures

num_medications

number_outpatient

number_emergency

number_inpatient

number_diagnoses

Categorical Variables

race

gender

age

medical_specialty

diag_1, diag_2, diag_3

max_glu_serum

A1Cresult

insulin

change

diabetesMed

readmitted
🤖 Models and Results
1. Random Forest

Accuracy: ~69%

Fairness Results:

By Race: Lower accuracy for Caucasian (0.575) and African American (0.591); higher for Asian (0.645) and Unknown (0.687).

By Gender: Nearly equal (Female: 0.581, Male: 0.585).

By Age: 0–10 years group had very high accuracy (0.897, small sample), while elderly groups (80–90 years) had lower accuracy (~0.55–0.65) and higher false negatives (0.124).

2. XGBoost

Accuracy: ~67%

Similar fairness trends:

Race and age showed the most disparity.

Gender remained balanced.

3. Logistic Regression

Accuracy: ~66%

Clear racial and age disparities observed:

Elderly and Caucasian groups faced higher false negatives (missed predictions).

Gender performance remained nearly equal.

4. Deep Neural Network (DNN)

Accuracy: ~65%

Similar fairness pattern as Random Forest:

Age and race disparities persist.

Gender fairness remains stable.

📉 Fairness Insights

Race: Asian and Unknown race groups achieved better accuracy; Caucasian and African American groups were more likely to be misclassified.

Gender: Minimal disparity — performance nearly identical across male and female patients.

Age: Children (0–10 years) had high accuracy, but very small samples. Older adults (80–90 years) were most likely to be missed by the model (higher false negative rate).

➡️ Conclusion: Fairness gaps are most visible across age and race, while gender predictions remain balanced.

🧮 Tools & Technologies

Python

pandas, numpy

scikit-learn

imbalanced-learn (SMOTE)

matplotlib, seaborn

XGBoost

TensorFlow/Keras (for DNN)

 Project Workflow

Data Cleaning – Removed missing/invalid values, encoded categorical columns.

Feature Selection – Based on correlation and diabetes research.

Data Balancing – Applied SMOTE to handle class imbalance.

Model Training – Logistic Regression, Random Forest, XGBoost, DNN.

Performance Evaluation – Accuracy, precision, recall, F1, confusion matrix.

Fairness Analysis – Checked disparities by race, gender, and age.

Next Steps – LLM integration and model explainability interface.

🚧 Current Status

✅ Data processed and cleaned
✅ Feature selection completed
✅ Model comparison completed (RF, XGBoost, LR, DNN)
✅ Fairness report generated
🚧 Next step: LLM module based on Random Forest interpretability

👨‍💻 Author

Bobby Dhir
Undergraduate Student, University of Nebraska Omaha
Supervised by Dr. Anoop Mishra & Dr. Deepak Khazanchi
