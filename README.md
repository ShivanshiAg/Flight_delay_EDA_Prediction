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

## 🗃️ Dataset
* Fields: `FL_DATE, DEP_TIME, ARR_TIME, DEP_DELAY, ARR_DELAY, DISTANCE, ORIGIN, DEST, AIRLINE etc.
* Target: `delay_flag = 1 if ARR_DELAY>0 else 0`

---

## 🧼 Data Cleaning & Feature Engineering
* Convert dates to datetime
* Create `DEP_HOUR`, `ARR_HOUR`, `MONTH`, `DAY_OF_WEEK`
* Drop nulls and duplicates
* Filter invalid times and zero/negative distances
* Encode categoricals (airline, origin, dest)
* Train/test split for modeling

---

## 📊 EDA Highlights
* Delay distribution (class imbalance)
* Temporal trends by month, weekday, hour
* Airport-wise and carrier-wise delay rates
* Top 10 most delay-prone airports
* Correlation between distance, airtime, and delays

---

## 🤖 Modeling
* Models: Logistic Regression, Random Forest, Gradient Boosting
* Metrics: Accuracy, Precision, Recall, F1, ROC-AUC
* Best model: **Random Forest** (ROC-AUC ≈ 0.78, Accuracy ≈ 0.70)

---

## 🔍 Key Insights
* Peak hours (evenings) → more delays
* Large hub airports → consistently higher delay probability

---

## ✅ Results
* **Random Forest** achieved:
  * Accuracy ≈ 0.70
  * ROC-AUC ≈ 0.78
  * F1 ≈ 0.64
* Identified top 10 high-delay airports to target for scheduling buffers

---

## 🗺️ Roadmap
* Add weather features (NOAA/METAR)
* Build route-level traffic features
* Streamlit dashboard for real-time risk scoring
* Add model drift monitoring

---

## 🙌 Acknowledgements
* pandas, scikit-learn, matplotlib, seaborn, plotly

---

## 📣 Citation
