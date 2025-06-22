# 🌾 Sowing Success: Crop Recommendation via Soil Metrics

![Python](https://img.shields.io/badge/Python-3.10-blue)
![numpy](https://img.shields.io/badge/numpy-1.24.3-yellowgreen)
![pandas](https://img.shields.io/badge/pandas-1.5.3-blueviolet)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.2.2-green)
![shap](https://img.shields.io/badge/shap-0.41.0-orange)
![matplotlib](https://img.shields.io/badge/matplotlib-3.7.1-red)
![License](https://img.shields.io/badge/license-MIT-brightgreen)

---

![Banner](https://cdn11.bigcommerce.com/s-jl3t5tg/product_images/uploaded_images/rwanda7.jpg)

---

## 📖 Project Overview

This project applies **multi-class classification** to predict the most suitable crop for a field based on soil metrics, helping farmers make informed decisions that maximize yield.

Given the high cost of measuring soil nutrients, our model assists in:

* Reducing soil testing overhead
* Prioritizing key features influencing crop success
* Improving farming productivity using interpretable AI

We explore linear models and advanced explainability techniques (SHAP) to uncover which soil metrics most influence crop selection.

---

## 🗃️ Dataset

* **File:** `soil_measures.csv`
* **Rows:** 2,200+ observations
* **Features:**

  * `N`, `P`, `K` — Nitrogen, Phosphorous, and Potassium levels
  * `pH` — Soil acidity/alkalinity
  * `crop` — Target label: the optimal crop for given soil metrics

Each row corresponds to a unique soil profile, with the crop being the recommended planting choice under those conditions.

---

## 🔧 Data Preprocessing & Feature Engineering

* **Label encoding** of categorical crop labels for classification.
* **Standardization** of numerical soil features using `StandardScaler`.
* **Train-test split** with stratification to ensure balanced class representation.
* **Manual feature ablation** to assess individual predictive contributions of `N`, `P`, `K`, and `pH`.

---

## ⚙️ Modeling & Evaluation

| Model               | Metric Used    | Notes                                    |
| ------------------- | -------------- | ---------------------------------------- |
| Logistic Regression | Macro F1 Score | Used both full and single-feature inputs |

Key insights:

* **Potassium (K)** had the highest standalone predictive strength.
* **pH** alone was largely non-predictive, but combined effects explored via SHAP.

---

## 🔍 Model Interpretability (SHAP)

We utilized SHAP (SHapley Additive exPlanations) to analyze feature contributions at multiple levels:

### 🔹 Individual Predictions — Waterfall Plot

<img src="https://raw.githubusercontent.com/shap/shap/master/docs/artwork/waterfall_rotation.png" width="600"/>

Each bar shows how a single feature contributed to the classification for one data point.

---

### 🔹 Class-Level Insight — SHAP Summary Plot

<img src="https://raw.githubusercontent.com/slundberg/shap/master/docs/artwork/shap_summary_plot.png" width="600"/>

Top features driving predictions for individual crop classes.

---

### 🔹 Global Feature Importance — SHAP Bar Plot

<img src="https://raw.githubusercontent.com/shap/shap/master/docs/artwork/bar.png" width="600"/>

Aggregate influence of all features across the model’s decisions.

---

## 🎯 Final Results

* Logistic Regression achieved solid performance with interpretable weights.
* SHAP revealed:

  * `K` and `N` are consistently influential.
  * Some crops are sensitive to combinations (e.g., `P + pH`).
* pH has low linear influence but interacts with others non-linearly.

---

## 🚀 How to Use

1. Clone or download the repo.

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Open and run the Jupyter Notebook to:

   * Load and preprocess the dataset
   * Train and evaluate models
   * Generate SHAP plots for interpretability

---

## 📊 Feature Importance

| Feature | Avg. Coefficient Weight | F1 Score (solo) | SHAP Insights               |
| ------- | ----------------------- | --------------- | --------------------------- |
| K       | High                    | Highest         | Strong positive contributor |
| N       | Moderate                | Second-best     | Influential for many crops  |
| P       | Moderate                | Mixed           | Paired with others (pH)     |
| pH      | Low                     | Weak            | Influential only in context |

---

## 📚 References & Tools

* [scikit-learn](https://scikit-learn.org/) for model building and evaluation
* [SHAP](https://shap.readthedocs.io/) for explainable ML
* [Matplotlib](https://matplotlib.org/) for plotting results
* [NumPy](https://numpy.org/) and [Pandas](https://pandas.pydata.org/) for data processing

---

## ⚖️ License

This project is licensed under the **MIT License** — see the LICENSE file for details.
