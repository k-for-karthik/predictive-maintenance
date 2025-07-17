# predictive-maintenance
ML project to predict Remaining Useful Life (RUL) and classify engine risk using NASA C-MAPSS dataset.

# 🛠️ Predictive Maintenance Using Machine Learning  
*A real-world case study using the NASA C-MAPSS dataset*

---

## ❗ The Problem

Aircraft engines operate under extreme conditions, and unexpected failures can lead to:
- 🚨 Safety risks  
- 🧰 Costly repairs  
- ✈️ Flight delays and operational losses

The current maintenance practices are either **reactive** (after failure) or **fixed-schedule**, but engine degradation patterns are not the same across all engines.

What we need is a **predictive system** that can:
- Forecast the **Remaining Useful Life (RUL)** of each engine
- Categorize engines by their **current risk level** so maintenance can be prioritized

---

## ✅ The Solution

We built a machine learning pipeline to:
1. **Predict the exact RUL** (number of cycles before engine failure) using regression
2. **Classify the engine’s condition** as:
   - `0` – High Risk (RUL ≤ 30)
   - `1` – Warning (RUL between 31 and 60)
   - `2` – Healthy (RUL > 60)
3. **Explain the predictions** using SHAP values so that engineers can understand what influenced the model

---

## 🧠 The Answer

### 🎯 What Did We Predict?

Our model predicts how many more cycles (flights) each engine can run before failure.

**Example predictions from the test dataset:**

| Engine ID | True RUL | Predicted RUL |
|-----------|----------|----------------|
|     1     |   112    |      110       |
|     2     |    98    |      92        |
|     3     |    69    |      75        |
|     4     |    82    |      79        |
|     5     |    91    |      85        |

This allows the maintenance team to:
> 🔧 Take action before an engine fails  
> 🎯 Allocate resources to engines with the least RUL  
> 🔍 Trust the system through explainable AI (SHAP)

---

## 🔄 Workflow Summary

| Step | Description |
|------|-------------|
| **Data Loading** | Loaded `train_FD001.txt`, `test_FD001.txt`, and `RUL_FD001.txt` |
| **Preprocessing** | Renamed columns, calculated RUL, removed low-variance sensors |
| **EDA** | Plotted sensor behavior, correlation heatmaps, and trend lines |
| **Feature Engineering** | Selected top 17 features: 3 operational settings + 14 sensors |
| **Regression** | Used XGBoost Regressor to predict RUL |
| **Classification** | Converted RUL into 3 classes and trained XGBoost Classifier |
| **Model Tuning** | Applied GridSearchCV to improve performance |
| **Explainability** | Used SHAP to highlight key sensor features impacting prediction |

---

## 📈 Model Performance

### 🔢 Regression – XGBoost Regressor (Tuned)
- **RMSE**: 31.87  
- **MAE** : 23.35  
- **R² Score**: 0.41  

### 🔤 Classification – XGBoost Classifier
- **Accuracy**: ~85%  
- **Top Features** (via SHAP): `sensor_11`, `sensor_9`, `sensor_4`, `sensor_12`

---

## 🧠 What We Learned

This project helped us:
- Understand end-to-end ML workflows
- Work with real-world sensor data
- Learn model tuning, evaluation, and explainability
- Understand how ML can assist in operational decision-making in critical industries like aviation

---

## ✅ Final Takeaway

> By predicting RUL and classifying engine health, this system enables **smart, proactive maintenance**. This can significantly reduce operational costs, enhance safety, and optimize resource allocation in airline fleets.

---

*Done as part of my ML internship to gain hands-on experience solving real-world business problems.*
