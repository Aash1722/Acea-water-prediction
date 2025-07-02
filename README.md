# Acea-water-prediction

**Project Title**: Predictive Modelling of Water Body Dynamics  

## 📌 Project Overview

This project implements a **machine learning-based predictive model** to forecast water levels across multiple types of water bodies — including **springs, lakes, rivers, and aquifers** — using real-world data from the Acea Group in Italy. The models aim to handle diverse environmental and hydrological conditions, simulate extreme weather scenarios like droughts, and help develop more sustainable water resource management strategies.

Two models are compared:  
- **Linear Regression**  
- **Random Forest Regression**  

The results highlight the **superior performance of Random Forest Regression** across most waterbody types, particularly in robustness and accuracy.

---

## 💡 Objectives

1. **Predict Water Levels** under varying seasonal and environmental conditions.
2. **Understand Environmental Impact** by analyzing variables like rainfall and temperature.
3. **Evaluate and Compare Models** using metrics such as MAE, MSE, R², Skewness, and Kurtosis.
4. **Simulate Extreme Events** (e.g., droughts, floods) and assess model resilience.

---

## 📊 Dataset Description

The dataset consists of **9 separate files**, each representing a different waterbody:

| Type      | Waterbodies Included               | Number of Datasets |
|-----------|------------------------------------|---------------------|
| Springs   | Lupa, Arno, Peschiera              | 3                   |
| Lakes     | Bilancino                          | 1                   |
| Rivers    | Tevere                             | 1                   |
| Aquifers  | Auser, Luco, Doganella, Petrignano | 4                   |

Each file contains time series data on:
- **Rainfall**
- **Temperature**
- **Hydrometry**
- **Water levels (depth)**
- **Other location-specific features**

---

## 🧪 Methodology

### 🧼 Data Cleaning
- Missing values imputed using **KNNImputer**
- Resampling frequencies tested: **Weekly (W)**, **Monthly (M)**, **Semi-monthly (SM)**
- Shift periods: 1, 2, 3 (used for lag-based time prediction)

### ⚙️ Feature Engineering
- Resampling, lagged targets, and trend extraction
- Target: **Depth-to-groundwater** for aquifers

### 📚 Modeling
- **Linear Regression** (baseline)
- **Random Forest Regression** (non-linear, ensemble model)
- Hyperparameter tuning via **RandomizedSearchCV**
- Preprocessing: **RobustScaler**

### 📈 Evaluation Metrics
- **Mean Squared Error (MSE)**
- **Mean Absolute Error (MAE)**
- **R² Score**
- **Skewness**
- **Kurtosis**
- **Residual Analysis**

---

## 🔍 Results (Aquifer Subset)

| Aquifer     | Best Frequency | Shift | Model        | MAE   | MSE   | R² Score |
|-------------|----------------|-------|--------------|--------|--------|----------|
| Auser       | SM             | 1     | RandomForest | 0.32   | 0.21   | 0.75     |
| Doganella   | M              | 1     | RandomForest | 2.73   | 14.55  | 0.65     |
| Luco        | SM             | 1     | RandomForest | 0.71   | 0.98   | 0.88     |
| Petrignano  | W              | 3     | RandomForest | 1.91   | 4.76   | 0.84     |

> Random Forest consistently outperformed Linear Regression in all cases.

---

## 📁 Repository Structure

Acea-water-prediction/
├── data/ # CSV files for each waterbody
├── notebooks/ # Jupyter Notebooks for EDA and modeling
├── src/ # Scripts for data processing, modeling, and evaluation
│ ├── data_preparation.py
│ ├── feature_engineering.py
│ ├── model_training.py
├── results/ # Graphs, metrics, and residual plots
├── README.md
---

## 🌊 Significance

This framework can be used by:
- **Utility companies** to manage water supply proactively
- **Environmental scientists** to study drought patterns
- **Government bodies** to guide policy around water conservation

---

## 📌 Key Libraries Used

- `pandas`, `numpy`, `matplotlib`, `seaborn`
- `scikit-learn`
- `scipy.stats`
- `statsmodels`
- `KNNImputer`, `RobustScaler`, `RandomForestRegressor`

---

## 📈 Visualizations

The notebook includes:
- Correlation heatmaps
- Prediction vs actual plots
- Residual and regression plots
- Probability plots and boxplots for model diagnostics

---

## 📎 References

1. [Acea Water Prediction – Kaggle Competition](https://www.kaggle.com/competitions/acea-water-prediction)
2. Tibshirani, R. (1996). Regression Shrinkage and Selection via the Lasso.
3. Biau, G. (2012). Analysis of Random Forests Model.
4. [Acea Group Website](https://www.gruppo.acea.it/en)

---

## 📜 License

This project is for academic and educational purposes only. Reuse requires proper citation.



