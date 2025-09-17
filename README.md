# ✈️ Flight Delay EDA & Prediction

A reproducible, end‑to‑end analysis of U.S. flight delays: data ingestion → cleaning → exploratory analysis → feature engineering → baseline models → evaluation → insights & recommendations.

> Notebook: `casestudy-flightdelay.ipynb`

---

## 📌 Project Goals

* Understand drivers of flight delays (carrier, airports, seasonality, weather proxies, distance, taxi times, etc.).
* Build baseline predictive models to classify **Delayed vs On‑Time** and/or estimate **Arrival Delay (minutes)**.
* Translate findings into **operational recommendations** (scheduling, buffers, carrier/route selection).

---

## 🧱 Key Highlights

* EDA (scalable patterns, memory‑safe filtering/aggregation).
* Clean feature pipeline: handling nulls/outliers, encoding categoricals, time features (month, DoW, hour), airport/carrier joins.
* Baseline models (examples): Logistic Regression / Random Forest / Gradient Boosting for classification
* Explainability: feature importances through SHAP analysis (e.g., peak hours, hub airports, seasonal spikes).

---

## 📂 Repository Structure

```
.
├── casestudy-flightdelay.ipynb   # Main analysis & modeling notebook

└── README.md                     # This file
```

---

## 🗃️ Dataset

* **Typical fields:** `Year, Month, DayOfWeek, FlightDate, Airline, FlightNum, Origin, Dest, CRSDepTime, DepTime, CRSArrTime, ArrTime, DepDelay, ArrDelay, Cancelled, Distance, TaxiOut, TaxiIn, AirTime`, etc.
* **Target(s):**

  * **Classification**: `is_delayed` (e.g., ArrDelay > 0 minutes)

---

## 🧼 Data Cleaning & Feature Engineering (Summary)

* Handle missing values: dep/arr times, taxi times, cancellation codes.
* Remove (or cap) extreme outliers in delays.
* Create derived features: `is_weekend`, `hour_of_day`, `season`, `is_peak`, `route = Origin-Dest`, `carrier_route`.
* Encode categoricals: target/one‑hot encodings for carrier, origin, dest.
* Split strategy: time‑aware split (train on past, test on future) or stratified random split.

---

## 📊 EDA – What We Looked At

* Delay distribution & skew; cancellation patterns.
* Seasonal/weekly/hourly trends; hub vs regional airports.
* Carrier comparisons; route‑level hotspots.
* Correlations across numeric features (Distance, AirTime, CRS times).
* Traffic proxies: flights per hour/airport, utilization windows.

---

## 🤖 Modeling (Baseline)

**Classification:**

* Metrics: Accuracy, Precision/Recall, F1, ROC‑AUC, PR‑AUC.
* Baselines: Dummy (majority), Logistic Regression, Random Forest, Gradient Boosting/XGBoost.

**Validation:**

* Train/validation/test split; optionally time‑series split.
* Cross‑validation and simple tuning (Grid/Randomized search).

> Document the **final model(s)** you chose and **why**.

---

## 🔍 Explainability & Insights

* Feature importance (model‑based) and interpretable patterns.
* Concrete insights (examples): peak‑hour departures from large hubs show higher delay risk; routes over X miles correlate with lower/larger variance; taxi‑out time is a strong early indicator.
* Practical actions: schedule buffers on specific routes/hours; prefer certain carriers/airports for on‑time reliability; surface risk scores in ops dashboards.

> Replace with your actual findings and charts.

---

## ✅ Results (Fill with your numbers)

* **Classification example:** ROC‑AUC = `0.78`, F1 = `0.62` on 2023‑Q4 holdout.
* **Regression example:** MAE = `7.9` mins, RMSE = `14.2` mins.
* **Business impact:** Identified top 10 high‑risk routes and peak windows → policy to add 10‑minute buffers reduced late arrivals by \~`X%`.

---

## 🗺️ Roadmap

* [ ] Add weather joins (METAR/NOAA) for stronger predictive power.
* [ ] Add airport/route capacity features (hourly load).
* [ ] Streamlit dashboard for risk scoring & what‑if analysis.
* [ ] Model monitoring: drift checks on new months.

---

## 🤝 Contributing

Pull requests welcome! Please open an issue to propose changes first.

---

## 🙌 Acknowledgements

* Open‑source libraries: pandas, scikit‑learn, matplotlib/plotly, xgboost, etc.

---

## 📣 Citation

If you use this project in academic or industry work, please cite this repository.

```text
Agarwal, S. (2025). Flight Delay EDA & Prediction. GitHub repository.
```
