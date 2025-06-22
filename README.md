---

# 🌾 Analyzing Feature Importance in Multi-class Classification: Crop Recommendation via Soil Metrics

![Python](https://img.shields.io/badge/Python-3.10-blue)
![numpy](https://img.shields.io/badge/numpy-1.24.3-yellowgreen)
![pandas](https://img.shields.io/badge/pandas-1.5.3-blueviolet)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.2.2-green)
![shap](https://img.shields.io/badge/shap-0.41.0-orange)
![matplotlib](https://img.shields.io/badge/matplotlib-3.7.1-red)
![License](https://img.shields.io/badge/license-MIT-brightgreen)

---

## 📖 Project Overview

This project applies **Machine Learning**, specifically **multi-class classification**, to predict the most suitable crop for a field based on soil metrics, helping farmers make informed decisions that maximize yield.

Assessing soil condition through essential metrics such as nitrogen, phosphorous, potassium levels, and pH value is a key part of agricultural planning. Each crop has an ideal combination of soil nutrients that supports optimal growth.
Given the high cost of measuring soil nutrients, our model assists in:

* Reducing soil testing overhead
* Prioritizing key features influencing crop success
* Improving farming productivity using interpretable AI

We explore advanced explainability techniques (SHAP) to uncover which soil metrics most influence crop selection.
---

## 🗃️ Dataset

* **File:** `soil_measures.csv`
* **Rows:** 2,200+ observations
* **Features:**

  * `N`, `P`, `K` — Nitrogen, Phosphorous, and Potassium levels
  * `pH` — Soil acidity/alkalinity
  * `crop` — Target label: the optimal crop for given soil metrics(22 different crops)

Each row corresponds to a unique soil profile, with the crop being the recommended planting choice under those conditions.

---

## 🔧 Data Preprocessing & Feature Engineering

* **Label encoding** of categorical crop labels for classification.
* **Standardization** of numerical soil features using `StandardScaler`.
* **Train-test split** with stratification to ensure balanced class representation.
* **Manual feature ablation** to assess individual predictive contributions of `N`, `P`, `K`, and `pH`.

---

## 📊 Feature Importance

| Feature | Avg. Coefficient Weight | F1 Score (solo) | SHAP Insights               |
| ------- | ----------------------- | --------------- | --------------------------- |
| K       | High                    | Highest         | Strong positive contributor |
| N       | Moderate                | Second-best     | Influential for many crops  |
| P       | Moderate                | Mixed           | Paired with others (pH)     |
| pH      | Low                     | Weak            | Influential only in context |

---

## 🔍 Model Interpretability (SHAP)

We utilized SHAP (SHapley Additive exPlanations) to analyze feature contributions both at:

* **Individual level** (waterfall plots for sample predictions)
* **Class level** (summary plots for each crop)
* **Global level** (bar chart aggregating across all crops)

This helped identify **interaction effects** between soil features that impact the model's crop recommendation decisions.

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

## 📚 References & Tools
* [SHAP](https://shap.readthedocs.io/en/latest/) for complete explanation of game theoritic approach in explaining individual feature contribution to the output of any Machine Learning model.
* 

---

## ⚖️ License

This project is licensed under the **MIT License** — see the LICENSE file for details.

---
