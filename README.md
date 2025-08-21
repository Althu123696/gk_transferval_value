# **GK TransferVal – Goalkeeper Market Value Prediction**

## 📌 Overview
GK TransferVal is a data science project that predicts **football goalkeeper's market values** using historical performance metrics, demographics, and league-related factors.  
Built with **reproducibility** in mind, the project follows a clean pipeline from raw data to deployment-ready artifacts, demonstrating both technical execution and business storytelling.

---

## 🎯 Objectives
- Predict **goalkeeper market values** with high accuracy using ML models.
- Create a **modular, reusable** pipeline that can be extended to other positions.
- Showcase **real-world analytics skills** for portfolio impact.
- Present insights in a **recruiter-friendly storytelling format**.

---

## 🛠 Tech Stack
- **Language:** Python 3.12.6
- **Core Libraries:** pandas, numpy, scikit-learn, matplotlib, seaborn, joblib
- **Environment:** Jupyter Notebook / Python scripts
- **Data Sources:** Curated dataset containing goalkeeper stats, league information, and market values

---

**Data Collection & Cleaning**

Gathered goalkeeper performance data:player,nation,club, matches played, saves, clean sheets, age, league details by excel.

Handled missing values using median (numeric) and mode (categorical) imputation.

Removed extreme outliers using z‑score thresholds.

Saved the cleaned dataset in data/processed/.

2️⃣**Feature Engineering**

Calculated per‑90 metrics (saves per 90, goals conceded per 90, etc.).

Added market context features such as league coefficient, contract length, and age group.

Encoded categorical variables via OneHotEncoder.

Stored transformation logic for reproducibility.

3️⃣ **Exploratory Data Analysis** (EDA)
Correlation heatmaps revealed strongest predictors of market value.

Visualized market value trends by age, league level, and performance tiers.

Identified storytelling insight: Younger goalkeepers in top leagues tend to appreciate in value faster.

4️⃣ **Model Training**
Baseline model: Linear Regression for interpretability.
Tuned model: Random Forest Regressor for improved accuracy.

**Evaluation metrics**:

RMSE: ~7.00

MAE: ~

R²: 0.4

5️⃣ **Model Saving**

Scaler: model/scaler.pkl

Model: model/linear_regression_model.pkl

Saved using joblib for consistent reuse.

6️⃣ **Prediction Script Example**

python
import joblib
import pandas as pd

# Load artifacts

scaler = joblib.load("artifacts/scaler.pkl")
model = joblib.load("artifacts/gk_value_model.pkl")

# Sample input

new_players = pd.DataFrame([
    {
        "Nation": "England",
        "League": "Premier League",
        "club": "Tottenham",
        "Age": 25,
        "matches played": 12,
        "goals conceded": 18,
        "Saves": 45,
        "clean sheets": 4
    }
    ])
# **Scale & predict**

scaled = scaler.transform(sample)
prediction = model.predict(scaled)
print(f"Predicted market value: €{prediction[0]:,.0f}")
📜 Key Learnings
Importance of consistent feature scaling between training and inference.

Storing artifacts avoids mismatch errors during deployment.

Combining EDA with storytelling boosts clarity and recruiter engagement.

 How to Run
Clone the Repository

bash

git clone https://github.com/username/GK-TransferVal.git
cd GK-TransferVal
Install Dependencies

bash

pip install -r requirements.txt
Train the Model

bash

python src/train_model.py
Make Predictions

bash
python src/predict.py

## 📂 Repository Structure
```plaintext
GK-TransferVal/
│
├── data/
│   ├── raw/               # Original datasets
│   ├── processed/         # Cleaned and engineered data
│
├── notebooks/
│   ├── predict_value.ipynb
│  
├── reports
│   
│
├── models
│   ├── scaler.pkl         # Feature scaler
│   ├── linear_regression_model.pkl # Trained model
        expected_feature.json
│
├── README.md
└── requirements.txt


