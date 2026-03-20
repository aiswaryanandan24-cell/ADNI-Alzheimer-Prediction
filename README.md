# 🧠 Alzheimer’s Disease Progression Prediction Using Clinical and Genetic Data (ADNI)

## 📌 Overview
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

## 📊 Dataset

- Source: ADNI (Alzheimer’s Disease Neuroimaging Initiative)
- Dataset size: **From 12804 patients -> 495 patients (after data cleaning)**

### Files used:
- `ADSL.csv` → Demographics (Age, Education, etc.)
- `APOERES.csv` → Genetic data (APOE status)
- `ADAS.csv` → Cognitive scores
- `DXSUM_26Jan2026.csv` → Diagnosis & progression

 Original data was in `.r` format and converted to `.csv` for analysis using RStudio.

---

## ⚙️ Data Processing

- Selected key features from multiple datasets
- Merged datasets using:
  - `RID`
  - `PTID`
  - `VISCODE`
- Handled missing values
- Created progression labels

---

## 🧪 Features Used

- AGE 
- EDUC
- MMSCORE: Mini-Mental State Examination/Cognitive score
- CDRSB: Clinical Dementia Rating
- FAQTOTAL: Functional Activities Questionnaire Score
- TOTSCORE_bl: ADAS-Cog Total Score – baseline
- TOTAL13_bl: ADAS-Cog 13-item score – baseline
- APOE4_carrier: presence of APOE ε4 allele
- Target Label- Binary (If Dx=Alzheimer’s Disease (1) otherwise 0 )

---

## 🤖 Models Used

1. **XGBoost Classifier**
2. **Logistic Regression**
3. **Random Forest**

---

## 📈 Results

### 🔹 XGBoost
- Accuracy: **0.70**
- AUC: **0.796**

### 🔹 Logistic Regression
- Accuracy: **0.73**
- AUC: **0.798**

### 🔹 Random Forest
- Accuracy: **0.73**
- AUC: **0.785**

<img width="691" height="547" alt="image" src="https://github.com/user-attachments/assets/f4871320-e7c1-414a-8956-66778b5bdaa2" />

---

## 📊 ROC Curve Comparison

The ROC curve shows comparable performance across all models, with Logistic Regression slightly outperforming others.

---

## 🔍 Feature Importance (SHAP)

Top important features:
1. **TOTAL13_bl**
2. **FAQTOTAL**
3. **AGE**
4. **TOTSCORE_bl**
5. **CDRSB**


<img width="761" height="459" alt="image" src="https://github.com/user-attachments/assets/38d80de0-32c2-4580-aca3-7a3d2c37c3ff" />

---

## 🔗 Correlation Analysis

- Strong correlation between:
  - `TOTSCORE_bl` and `TOTAL13_bl`
- Moderate relationships between cognitive scores and progression
<img width="687" height="590" alt="image" src="https://github.com/user-attachments/assets/7e3f9b04-bba8-4e9a-b0ad-6f4011e573c8" />


---

## 📊 Statistical Testing

- **t-test** used for numerical features
- **Chi-square test** used for categorical variable (`APOE4_carrier`)

### Key finding:
- APOE4 carrier status is significantly associated with disease progression

---

## 🧠 Key Insights

- Cognitive baseline scores are strong predictors of progression
- APOE4 genetic marker plays an important role
- Combining clinical + genetic data improves prediction

---

## 🛠️ Tech Stack

- RStudio
- Python  
- Pandas  
- NumPy  
- Scikit-learn  
- XGBoost  
- Matplotlib / Seaborn  
- SHAP  
- SciPy  
- Jupyter Notebook  
- Git & GitHub  

---

## 📁 Project Structure


├── Alzheimers prediction ADNI.ipynb

├── ADSL.csv

├── APOERES.csv

├── ADAS.csv

├── DXSUM_26Jan2026.csv

└── README.md


---

## 🚀 Future Work

- Hyperparameter tuning
- Cross-validation
- Deep learning models
- Deployment (Streamlit app)

---

## 👩‍💻 Author

Aiswarya Nandan Perumbilly, 
Indiana Univeristy Indianapolis
