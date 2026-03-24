
# Early Prediction of Alzheimer’s Disease Progression Using Clinical and Genetic Data (ADNI)

##  Overview
The project predicts Alzheimer's disease progression using clinical and genetic data from the ADNI (Alzheimer’s Disease Neuroimaging Initiative) dataset using clinical and genetic data.
It applies machine learning models to identify key factors influencing cognitive decline and assess patient risk.This project helps in early identification of patients at risk of Alzheimer’s disease progression, allowing timely medical intervention.
It also supports clinicians in decision-making by highlighting important clinical and genetic factors influencing cognitive decline.

The workflow includes:
- Data preprocessing and merging multiple clinical datasets
- Feature engineering
- Model training with multiple ML algorithms
- Evaluation using ROC-AUC and classification metrics
- Model explainability using SHAP

---

 Research Objective

Can baseline clinical and genetic features predict Alzheimer's disease progression using ADNI data?
 
---

##  Dataset

- Source: ADNI (Alzheimer’s Disease Neuroimaging Initiative)
- Dataset size: **From 12804 patients -> 495 patients (after preprocessing and cleaning)**

### Files Used

| File | Contents |
|---|---|
| `ADSL.csv` | Demographics (Age, Education, etc.) |
| `APOERES.csv` | Genetic data (APOE ε4 status) |
| `ADAS.csv` | Cognitive scores (ADAS-Cog) |
| `DXSUM_26Jan2026.csv` | Diagnosis and progression labels |

### Final Balanced Dataset

| Class | Count |
|---|---|
| No Progression | 263 |
| Progression | 232 |
| **Total** | **495 patients** |

 Original data was in `.r` format and converted to `.csv` for analysis using RStudio.

---

##  Methodology Pipeline

### 1️ Data Preprocessing

- Converted `.r` files to `.csv` using RStudio
- Selected key features from multiple datasets
- Merged datasets using `RID`, `PTID`, and `VISCODE`
- Handled missing values and removed incomplete records
- Created binary progression labels

### 2️ Feature Engineering

| Feature | Description |
|---|---|
| `AGE` | Patient age |
| `EDUC` | Years of education |
| `MMSCORE` | Mini-Mental State Examination score |
| `CDRSB` | Clinical Dementia Rating - Sum of Boxes |
| `FAQTOTAL` | Functional Activities Questionnaire total score |
| `TOTSCORE_bl` | ADAS-Cog total score at baseline |
| `TOTAL13_bl` | ADAS-Cog 13-item score at baseline |
| `APOE4_carrier` | Presence of APOE ε4 allele (genetic risk factor) |

### 3️ Exploratory Data Analysis

- Distribution plots and summary statistics
- Pearson correlation heatmaps
  - Strong correlation found between `TOTSCORE_bl` and `TOTAL13_bl`
  - Moderate relationships between cognitive scores and progression
- Group comparisons (progression vs. non-progression)
- Statistical testing:
  - Independent t-test for continuous variables
  - Chi-square test for `APOE4_carrier` (categorical)
  - **Key finding:** APOE4 carrier status is significantly associated with disease progression
  - 
    <img width="687" height="590" alt="image" src="https://github.com/user-attachments/assets/c388ef14-3954-48e9-afab-731b2dd74bc5" />


### 4️ Machine Learning Models

**Models evaluated:**
- Logistic Regression
- Random Forest
- XGBoost

**Train-test split:** 80/20

**Evaluation metrics:** Accuracy, ROC-AUC, Precision, Recall, F1-score, Confusion Matrix

---

##  Results

| Model | Accuracy | ROC-AUC |
|---|---|---|
| Logistic Regression | 0.73 | **0.798** |
| XGBoost | 0.70 | 0.796 |
| Random Forest | 0.73 | 0.785 |

The ROC curve shows comparable performance across all models, with **Logistic Regression** slightly outperforming the others.

###  Best Model: Logistic Regression

- Highest ROC-AUC (0.798)
- Stable and interpretable performance
- Competitive with more complex ensemble models

<img width="691" height="547" alt="image" src="https://github.com/user-attachments/assets/f4871320-e7c1-414a-8956-66778b5bdaa2" />

---


##  Model Explainability (SHAP)

SHAP (SHapley Additive exPlanations) was used to interpret feature contributions to model predictions.

<img width="761" height="459" alt="image" src="https://github.com/user-attachments/assets/aba5152d-449f-4b00-b82f-5362e8ab3381" />


**Top features by importance:**

| Rank | Feature | Role |
|---|---|---|
| 1 | `TOTAL13_bl` | ADAS-Cog 13-item baseline — strongest predictor |
| 2 | `FAQTOTAL` | Functional impairment score |
| 3 | `AGE` | Patient age at baseline |
| 4 | `TOTSCORE_bl` | ADAS-Cog total baseline score |
| 5 | `CDRSB` | Dementia severity rating |

<img width="790" height="459" alt="image" src="https://github.com/user-attachments/assets/87ce71a7-6dfd-495c-9668-3e50150d5630" />


---

##  Key Insights

- Baseline cognitive scores (especially `TOTAL13_bl`) are the strongest predictors of progression.
- Functional impairment (`FAQTOTAL`) is highly associated with disease worsening.
- APOE4 carrier status is a significant genetic risk factor for progression.
- Combining clinical and genetic features improves predictive power.
- Simple interpretable models (Logistic Regression) perform competitively with complex ensemble models.

---

##  Tech Stack

- **Data conversion:** RStudio
- **Analysis & modeling:** Python, Jupyter Notebook
- **Data processing:** Pandas, NumPy, SciPy
- **Machine learning:** Scikit-learn, XGBoost
- **Visualization:** Matplotlib, Seaborn
- **Explainability:** SHAP
- **Version control:** Git & GitHub

---

##  Project Structure

```
├── Alzheimers_prediction_ADNI.ipynb
├── ADSL.csv
├── APOERES.csv
├── ADAS.csv
├── DXSUM_26Jan2026.csv
└── README.md
```

---

##  Limitations

- Relatively small final dataset (495 patients after cleaning)
- Retrospective analysis — causal inference not possible
- Limited to baseline features; no full time-series modeling of decline
- No external validation on an independent cohort

---

##  Future Work

- Hyperparameter tuning and cross-validation
- Time-series modeling of longitudinal cognitive decline
- Deep learning approaches (LSTM, Transformer-based models)
- External validation on independent Alzheimer's datasets
- Deployment as a clinical decision-support tool (Streamlit app)

---

##  Author

**Aiswarya Nandan Perumbilly**
*Indiana University Indianapolis*


