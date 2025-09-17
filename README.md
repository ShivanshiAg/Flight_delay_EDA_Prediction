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

* EDA over **\~1M+ records** (scalable patterns, memory‑safe filtering/aggregation).
* Clean feature pipeline: handling nulls/outliers, encoding categoricals, time features (month, DoW, hour), airport/carrier joins.
* Baseline models (examples): Logistic Regression / Random Forest / Gradient Boosting for classification; Linear/XGBoost for regression.
* Explainability: feature importances, partial patterns (e.g., peak hours, hub airports, seasonal spikes).

> Replace/confirm the bullets above with the exact techniques you finalized in the notebook.

---

## 📂 Repository Structure

```
.
├── casestudy-flightdelay.ipynb   # Main analysis & modeling notebook
├── data/                         # (Optional) local folder for raw/processed CSVs (gitignored)
├── models/                       # (Optional) saved models / artifacts (gitignored)
├── reports/                      # (Optional) exported charts & HTML reports
├── requirements.txt              # (Optional) pinned dependencies
└── README.md                     # This file
```

> Tip: add a `.gitignore` to exclude large CSVs and artifacts (e.g., `data/*`, `models/*`).

---

## 🗃️ Dataset

* **Source options:** U.S. DOT / BTS On‑Time Performance data (flights, carriers, airports), or a curated subset.
* **Typical fields:** `Year, Month, DayOfWeek, FlightDate, Airline, FlightNum, Origin, Dest, CRSDepTime, DepTime, CRSArrTime, ArrTime, DepDelay, ArrDelay, Cancelled, Distance, TaxiOut, TaxiIn, AirTime`, etc.
* **Target(s):**

  * **Classification**: `is_delayed` (e.g., ArrDelay > 15 minutes)
  * **Regression**: `ArrDelay` (minutes)

> Update this section with the exact dataset(s) and any filters you applied (year range, carriers, airports).

---

## ⚙️ Setup & Environment

**Prereqs:** Python 3.10+ recommended, `pip` or `conda`, Jupyter/VS Code.

```bash
# (Option A) with conda
conda create -n flight-delay python=3.10 -y
conda activate flight-delay
pip install -r requirements.txt    # if present

# (Option B) with venv
python -m venv .venv
# Windows: .venv\Scripts\activate    |   macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
```

If you don’t have a `requirements.txt` yet, start with:

```txt
pandas
numpy
scikit-learn
matplotlib
plotly
seaborn
jupyter
xgboost            # if used
lightgbm           # if used
pyarrow            # if using parquet
```

---

## ▶️ How to Run

1. **Clone & open** the repo in VS Code or Jupyter Lab.
2. **Activate** your environment (see above) and install dependencies.
3. **Place data** in `data/` (or update file paths in the notebook).
4. **Open** `casestudy-flightdelay.ipynb` and run cells top to bottom.

Optional:

* Export charts to `/reports`.
* Persist trained models to `/models` for reuse.

---

## 🧼 Data Cleaning & Feature Engineering (Summary)

* Handle missing values: dep/arr times, taxi times, cancellation codes.
* Remove (or cap) extreme outliers in delays.
* Create derived features: `is_weekend`, `hour_of_day`, `season`, `is_peak`, `route = Origin-Dest`, `carrier_route`.
* Encode categoricals: target/one‑hot encodings for carrier, origin, dest.
* Split strategy: time‑aware split (train on past, test on future) or stratified random split.

> Replace with the exact steps you implemented.

---

## 📊 EDA – What We Looked At

* Delay distribution & skew; cancellation patterns.
* Seasonal/weekly/hourly trends; hub vs regional airports.
* Carrier comparisons; route‑level hotspots.
* Correlations across numeric features (Distance, TaxiOut/In, AirTime, CRS times).
* Traffic proxies: flights per hour/airport, utilization windows.

Add a few example figures (save from the notebook into `/reports` and embed):

![Sample: Delay distribution](reports/fig_delay_distribution.png)
![Sample: Delays by hour](reports/fig_delays_by_hour.png)

---

## 🤖 Modeling (Baseline)

**Classification:**

* Metrics: Accuracy, Precision/Recall, F1, ROC‑AUC, PR‑AUC.
* Baselines: Dummy (majority), Logistic Regression, Random Forest, Gradient Boosting/XGBoost.

**Regression:**

* Metrics: MAE, RMSE, R², MAPE (if applicable).
* Baselines: Mean/Median predictor, Linear Regression/Regularized, Tree‑based (RF/XGB).

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
* [ ] Promote to a script/CLI (e.g., `src/` with `train.py`, `predict.py`).
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
