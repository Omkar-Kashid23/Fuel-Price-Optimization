Perfect — here’s a **much simpler README**, with **badges** and **one clear diagram**, while keeping it **professional and submission-ready**.

You can copy–paste this directly as `README.md`.

---

# ⛽ Fuel Price Optimization (ML Project)

![Python](https://img.shields.io/badge/Python-3.9+-blue)
![ML](https://img.shields.io/badge/Machine%20Learning-RandomForest%20%7C%20XGBoost-green)
![Status](https://img.shields.io/badge/Status-Completed-success)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📌 Overview

This project builds a **Machine Learning–based pricing system** that recommends an **optimal daily fuel price** for a petrol retail company operating in a competitive market.

The system predicts demand using historical data and **simulates multiple price options** to select the price that **maximizes expected profit**, while following business rules.

---

## 🎯 Business Goal

Set **one optimal price per day** to maximize:

[
\textbf{Profit} = (\text{Price} - \text{Cost}) \times \text{Volume}
]

Challenges:

* Demand is uncertain
* Competitor prices change daily
* Pricing must respect business constraints

---

## 📂 Data

### Historical Data

`oil_retail_history.csv`

* date
* price
* cost
* competitor prices
* volume sold

### Daily Input

`today.json` (known at start of day)

```json
{
  "date": "2025-01-20",
  "last_price": 102.5,
  "cost": 96.2,
  "comp1_price": 101.8,
  "comp2_price": 102.0,
  "comp3_price": 101.6
}
```

---

## 🏗️ Project Structure

```
fuel-price-optimization/
│
├── data/
│   ├── oil_retail_history.csv
│   └── today.json
│
├── notebooks/
│   ├── eda.ipynb
│   ├── training.ipynb
│   └── optimization.ipynb
│
├── models/
│   └── demand_model.pkl
│
├── src/
│   ├── features.py
│   ├── train.py
│   └── predict.py
│
└── README.md
```

---

## 🔄 System Flow (Diagram)

```text
Historical Data (CSV)
        ↓
Feature Engineering
        ↓
Demand Model (Random Forest)
        ↓
Daily Input (today.json)
        ↓
Price Simulation
        ↓
Profit Calculation
        ↓
Best Price Recommendation
```

---

## 🤖 Machine Learning

* **Target**: Daily fuel volume (demand)
* **Models**:

  * Random Forest (primary)
  * XGBoost (comparison)
* **Key Features**:

  * Price & cost
  * Competitor prices
  * Price difference
  * Lagged demand
  * Rolling demand average
  * Day of week

> The model is used for **relative price comparison**, not perfect demand prediction.

---

## 💰 Price Optimization Logic

1. Generate candidate prices near last price
2. Predict demand for each price
3. Compute expected profit
4. Apply business rules:

   * Max daily price change
   * Minimum margin
   * Competitive bounds
5. Select price with highest profit

---

## 📊 Example Output

```json
{
  "recommended_price": 101.9,
  "expected_volume": 8400,
  "expected_profit": 49500
}
```

---

## 🚀 How to Run

```bash
pip install -r requirements.txt
python src/train.py
python src/predict.py --input data/today.json
```

---

## 🔮 Future Improvements

* Add weather / holiday data
* Store-level pricing
* Reinforcement learning
* API deployment (FastAPI)
* Scheduled daily runs (Airflow / Cron)

---

## 🧠 Key Takeaway

This project focuses on **realistic pricing decisions**, combining ML demand prediction with **business-constrained optimization**, rather than chasing high prediction accuracy.

---

## 👤 Author

**Omkar Kashid**
📧 [okashid104@gmail.com](mailto:okashid104@gmail.com)

---
