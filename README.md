# ✈️ Flight Delay EDA & Prediction

A reproducible, end-to-end analysis of U.S. flight delays: data ingestion → cleaning → exploratory analysis → feature engineering → modeling → evaluation → insights & recommendations.

> Notebook: `casestudy-flightdelay.ipynb`

---

## 📌 Project Goals
* Understand drivers of flight delays (carrier, airports, seasonality, distance, taxi times, etc.)
* Build predictive models to classify **Delayed vs On-Time**
* Translate findings into **operational recommendations** (scheduling, buffers, carrier/route selection)

---

## 🧱 Key Highlights
* EDA on **~1M flight records**
* Clean pipeline: null removal, duplicates, outlier filtering, feature engineering (hour of day, weekday, month)
* Models: Logistic Regression, Random Forest, Gradient Boosting
* Best model: **Random Forest** (~0.70 Accuracy, ~0.78 ROC-AUC)
* Explainability: feature importances and SHAP plots

---

## 📂 Repository Structure
├── casestudy-flightdelay.ipynb # Main analysis & modeling notebook

└── README.md

---
## 📦 Dataset

📂 Key fields: FL_DATE, DEP_TIME, ARR_TIME, DEP_DELAY, ARR_DELAY, DISTANCE, ORIGIN, DEST, AIRLINE

🎯 Target: delay_flag = 1 if ARR_DELAY > 0 else 0
 
 ---
 
## 🧪 Data Cleaning & Feature Engineering

🗓️ Converted dates to datetime

🕒 Created DEP_HOUR, ARR_HOUR, MONTH, DAY_OF_WEEK

❌ Dropped nulls and duplicates

⚠️ Filtered invalid times and zero/negative distances

🏷️ Encoded categorical variables (AIRLINE, ORIGIN, DEST)

✂️ Split dataset into train/test sets for modeling

---

## 📊 Exploratory Data Analysis Highlights

⚖️ Delay distribution — revealed class imbalance (more on-time flights)

📅 Temporal patterns — delays peak during evenings, weekends, and holidays

🛫 Airport-wise delay rates — found top 10 most delay-prone airports

🏢 Carrier-wise performance analysis

📏 Correlation between distance, airtime, and delays

---

## 🤖 Modeling & Evaluation
Model	Accuracy	ROC-AUC	F1 Score
Random Forest (baseline)	0.70	0.78	0.64
XGBoost	0.76	0.81	0.68
LightGBM	0.77	0.82	0.69
CatBoost	0.78	0.83	0.70

📌 Random Forest used as baseline and to build relevant features for ensemble models

🚀 Boosting models (XGBoost, LightGBM, CatBoost) gave higher accuracy after tuning

⚙️ Hyperparameter tuning (Grid / Randomized search) further improved performance

---

## 💡 Key Insights

🌆 Peak-hour (evening) departures → higher chance of delays

🛬 Large hub airports → consistently higher delay probability

🕓 Higher taxi-out times showed correlation with delays

✅ Results & Business Impact

📌 Identified top 10 high-delay airports

⏳ Proposed scheduling buffers for these high-risk routes

💹 Potential to reduce late arrivals and improve on-time performance

---

## 🗺️ Future Roadmap

☁️ Integrate weather features (NOAA/METAR)

📍 Build route-level traffic features

📊 Deploy Streamlit dashboard for real-time risk scoring

📉 Add model drift monitoring on new data

---

## 🙌 Acknowledgements

📚 Libraries: pandas, scikit-learn, xgboost, lightgbm, catboost, matplotlib, seaborn, plotly

---
