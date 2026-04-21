# Early-Prediction-of-Complicated-Pediatric-Appendicitis-Using-Temporal-Causal-Risk-Modelling



##  Project Overview
This project develops an advanced machine learning framework to predict **pediatric appendicitis severity** using clinical, laboratory, and imaging data.

The model classifies patients into:
- **Uncomplicated Appendicitis (UA)**
- **Complicated Appendicitis (CA)**

The system integrates **temporal feature engineering, causal modeling, class imbalance handling, and ensemble learning** to improve prediction accuracy and clinical reliability.

---

## Dataset
- Total samples: **782 patients**
- Features: **58+ clinical variables**
- Includes:
  - Demographics (Age, Sex, BMI)
  - Laboratory markers (CRP, WBC, Neutrophils)
  - Clinical symptoms
  - Ultrasound findings
  - Appendicitis scores

---

##  Methodology

###  Data Preprocessing
- Missing value handling (imputation)
- Label encoding for categorical features
- Feature normalization using **StandardScaler**
- Dataset expanded to **61 features after preprocessing**

---

###  Class Imbalance Handling
- Applied **SMOTE (Synthetic Minority Oversampling Technique)**
- Balanced dataset:
  - Before: Imbalanced classes
  - After: Equal distribution (529 vs 529)

---

###  Temporal Feature Engineering
- Used **Length of Stay** as temporal anchor
- Computed velocity-based features:
CRP_velocity = (CRP - baseline) / log(T + 1)
WBC_velocity = (WBC - baseline) / log(T + 1)
NEU_velocity = (Neutrophils - baseline) / log(T + 1)


- Created:
  - **Inflammatory Progression Index (IPI)**

---

###  Causal Feature Modeling
- Constructed **Directed Acyclic Graph (DAG)**
- Identified key causal features:
  - Appendix Diameter
  - Inflammatory Progression Index

- Generated:
  - **Causal Risk Score**
  - **Urgency Factor**
  - Weighted feature interactions

---

###  Models Used

The following models were trained and compared:

- **CatBoost**
- **LightGBM**
- **XGBoost**
- **Random Forest**
- **Logistic Regression**

---

###  Ensemble Model
Final predictions are generated using:
Ensemble Probability = mean(all model probabilities)


- Threshold used: **0.35** (for class imbalance)
- Improves:
  - Stability
  - Generalization
  - Clinical reliability

---

###  Uncertainty Estimation (Conformal Prediction)
- Applied **conformal prediction**
- Generates:
  - Single prediction (high confidence)
  - Set prediction {UA, CA} (uncertain case)

- Helps in:
  - Clinical safety
  - Risk-aware decision making

---

##  Results Summary

| Model           | Accuracy | AUC   |
|----------------|----------|-------|
| CatBoost       | 0.9427   | 0.9762 |
| LightGBM       | 0.9363   | 0.9756 |
| XGBoost        | 0.9172   | 0.9696 |
| Random Forest  | 0.9299   | 0.9715 |
| Logistic       | 0.8981   | 0.8913 |


---

##  Key Observations
- **CatBoost achieved best individual performance**

- Temporal features significantly enhance prediction quality
- Causal modeling improves interpretability
- SMOTE improves minority class detection

---

##  Evaluation Metrics
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion Matrix

---

##  Project Structure
- `Predictive_Final.ipynb` → Full implementation
- Dataset file (Excel)
- Visualization plots
- Model evaluation outputs

---

##  Tech Stack
- Python
- Pandas, NumPy
- Scikit-learn
- CatBoost
- LightGBM
- XGBoost
- Imbalanced-learn (SMOTE)
- Matplotlib, Seaborn

---

##  Limitations
- Moderate dataset size (782 samples)
- Retrospective clinical data
- Potential dataset bias
- Requires external validation

---

##  Future Scope
- Real-time hospital deployment
- Integration with EHR systems
- Deep learning models for tabular data
- Multi-center dataset validation
- Improved uncertainty calibration

---

##  Conclusion
This project demonstrates that combining **temporal feature engineering, causal modeling, and ensemble learning** significantly improves appendicitis severity prediction. The framework provides a **robust and clinically relevant decision-support system**.


