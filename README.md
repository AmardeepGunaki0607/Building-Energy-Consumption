# Statistical Machine Learning and Parametric Optimization of Building Thermal Dynamics

**Course Project Topic 16:** Building Energy Consumption  
**Authors:** Amardeep Gunaki, Shankar Chalwadi  
**Technology Stack:** Python, Streamlit, Pandas, NumPy, SciPy, Statsmodels, Patsy, Scikit-Learn, Matplotlib, Seaborn  

---

## 📌 Executive Summary
This repository contains a professional, production-grade Python Streamlit web application for analyzing building thermal performance data based on the **UCI Energy Efficiency dataset** ($N = 768$ building archetypes compiled by Tsanas and Xifara using Ecotect thermodynamic simulations).

The application executes an end-to-end statistical machine learning pipeline structured across five core analytical modules:
1. **Module 1: Exploratory Data Analysis & Envelope Orthogonality** — Bimodal load distribution profiling and correlation matrix analysis.
2. **Module 2: Resampling & Bootstrap Confidence Intervals** — Nonparametric Monte Carlo bootstrap ($B = 2,000$) computing Wald, Percentile, and BCa 95% CIs.
3. **Module 3: Five-Step One-Way ANOVA on Glazing Area** — Formal hypothesis testing on $X_7$ Glazing Area ($F = 15.821, p = 5.32 \times 10^{-10}$, $\eta^2 = 5.85\%$, Tukey HSD).
4. **Module 4: Comparative Regression Architectures & Residual Diagnostics** — OLS Linear Baseline, Quadratic, Cubic, and Natural Cubic Splines with 3/5 knots, evaluated via AIC/BIC/10-fold CV-RMSE and a 4-panel residual diagnostic suite.
5. **Module 5: Discriminant Analysis & Risk-Sensitive Metrics** — Operational thresholding at sample median $\tau = 18.95 \text{ kWh/m}^2$, comparing LDA, QDA, and $\ell_2$-regularized Logistic Regression, optimizing the risk-weighted $F_2\text{-score} = 0.9845$.

---

## 📂 Project Architecture

```
Building-Energy-Consumption/
│
├── app.py                           # Main Streamlit Application Entry Point
├── requirements.txt                 # Project dependencies
├── README.md                        # Project documentation (this file)
├── implementation_plan.md           # Master Implementation Plan
│
├── data/
│   └── energy_efficiency.csv        # Primary UCI Energy Efficiency Dataset
│
├── src/
│   ├── __init__.py
│   ├── data_loader.py               # Dataset loading, validation, and schema checks
│   ├── preprocessing.py            # Column renaming, factor mapping, and target creation
│   ├── eda.py                       # Summary stats, correlations, bimodality analysis
│   ├── bootstrap_analysis.py        # Nonparametric bootstrap & 4 CI frameworks
│   ├── anova_analysis.py            # Five-Step One-Way ANOVA protocol & Tukey HSD
│   ├── regression_analysis.py       # Linear and polynomial regression fits
│   ├── spline_analysis.py           # Natural cubic splines (patsy) & model comparison
│   ├── classification.py            # LDA, QDA, Logistic Regression classifiers
│   ├── evaluation.py                # 4-panel regression diagnostics & F2-score metrics
│   └── visualization.py             # Publication-quality Matplotlib & Seaborn plots
│
├── models/                          # Serialized model artifacts
│
└── tests/                           # Pytest Test Suite
    ├── test_data.py
    ├── test_statistics.py
    ├── test_regression.py
    └── test_classification.py
```

---

## 🚀 Quick Start Guide

### 1. Prerequisites
Ensure Python 3.10+ is installed on your system.

### 2. Installation
Clone the repository and install dependencies:
```bash
git clone https://github.com/your-username/Building-Energy-Consumption.git
cd Building-Energy-Consumption
pip install -r requirements.txt
```

### 3. Data Requirement
Ensure the UCI dataset file `energy_efficiency.csv` or `ENB2012_data.xlsx` is placed in the `data/` directory:
- Source: [UCI Energy Efficiency Dataset](https://archive.ics.uci.edu/ml/datasets/energy+efficiency)

### 4. Run the Streamlit Application
Launch the interactive web application:
```bash
streamlit run app.py
```

### 5. Execute Test Suite
Run unit tests across data, statistics, regression, and classification modules:
```bash
pytest
```

---

## 📊 Summary of Analytical Findings

| Analytical Component | Key Metric / Output | Empirical Finding |
| :--- | :--- | :--- |
| **Bimodality Driver** | $X_5$ Overall Height | $3.5\text{m}$ single-story structures occupy $< 20\text{ kWh/m}^2$, while $7.0\text{m}$ two-story structures form the upper mode ($28-36\text{ kWh/m}^2$). |
| **Bootstrap 95% CI** | BCa Interval | Mean Heating Load $\bar{Y}_1 \in [21.591, 23.031]\text{ kWh/m}^2$ ($B=2,000$). |
| **ANOVA Effect Size** | $\eta^2$ (Glazing Area $X_7$) | $F = 15.821, p = 5.32 \times 10^{-10}$, explaining $5.85\%$ of total load variance. |
| **Regression Optimization** | Natural Cubic Spline (3 Knots) | Reduces 10-Fold CV-RMSE to $7.280$ and AIC to $5230.6$, resolving linear parabolic curvature. |
| **Classification Optimization** | QDA Classifier | Test Accuracy $= 98.05\%$, ROC-AUC $= 0.9975$, $F_2\text{-Score} = 0.9845$ (only 1 False Negative out of 77). |

---

## 📜 Deliverables Alignment
- **8-Chapter Technical Report Layout:** Aligned with syllabus criteria for problem description, EDA, resampling, hypothesis testing, splines, classification, architectural guidelines, and theoretical limitations.
- **10-Slide Viva Presentation Structure:** Complete slide-by-slide defense talking points for oral evaluation.

---

## 👥 Authors & Academic Alignment
- **Amardeep Gunaki**
- **Shankar Chalwadi**  
*Statistical Machine Learning Course Project Topic 16*
