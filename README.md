<div align="center">

# 🌾 Karnataka Rice Yield Prediction

**Exploratory data analysis and machine learning pipeline for predicting district-level rice yield across Karnataka**

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](#license)
[![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat-square)]()

</div>

---

## 📖 Overview

This project analyzes historical, district-wise rice cultivation data for the state of **Karnataka, India**, and builds regression models to predict **All-Seasons Rice Yield (kg/hectare)** from area, season-mix, and prior-season yield features.

It was built as part of the **ANNAM.AI** project — *Fundamentals of AI Using Agriculture Data Set* — and walks through the full data-science workflow: cleaning raw government agricultural data, exploring seasonal and regional patterns, engineering features, and comparing multiple ML models on prediction accuracy.

> 🎓 **Project:** ANNAM.AI — Fundamentals of AI Using Agriculture Data Set
> 🏫 **Author:** Syamala Umesh Sai Hanuma Prasad — Vishnu Institute of Technology

---

## ✨ Highlights

- 📊 **Full exploratory data analysis** — top-producing districts, season-wise area/production splits, yield distributions, and correlation heatmaps
- 🗺️ **District-level comparison** across all **30 districts** of Karnataka, benchmarked against the state average
- 🤖 **Three regression models compared head-to-head**: Linear Regression, Random Forest, and Gradient Boosting
- 🔍 **Feature importance analysis** to identify what actually drives rice yield
- 🎯 **Sample inference demo** — predicting yield for a held-out district scenario
- 🎨 Clean, publication-style Matplotlib/Seaborn visualizations with a consistent green/gold agricultural color theme

---

## 🗂️ Repository Structure

```
karnataka-rice-yield-prediction/
├── Karnataka_rice_ml_analysis.ipynb   # Main analysis + ML notebook
├── ICRISAT-District Level Data.csv    # Source agricultural dataset
└── README.md                          # You are here
```

---

## 🧰 Tech Stack

| Category            | Tools                                             |
|----------------------|----------------------------------------------------|
| Language             | Python 3                                          |
| Data handling        | `pandas`, `numpy`                                 |
| Visualization        | `matplotlib`, `seaborn`                           |
| Machine Learning      | `scikit-learn` (Linear Regression, Random Forest, Gradient Boosting) |
| Environment          | Jupyter Notebook                                  |

---

## 🔬 Methodology

The notebook (`Karnataka_rice_ml_analysis.ipynb`) follows a structured pipeline:

1. **Load & Clean Data** — drops the state-total row, strips column whitespace, and renames verbose bund-correction columns to simplified names (`Kharif_Area`, `Rabi_Area`, `Summer_Area`, `Total_Area`).
2. **Exploratory Data Analysis**
   - Top 10 districts by production and by yield
   - Season-wise (Kharif / Rabi / Summer) area and production breakdown
   - Yield distribution histogram with mean/median markers
   - Area vs. Yield scatter, colored by production
   - Correlation heatmap across area/yield/production features
   - Full district-by-district yield ranking vs. the state average
3. **Feature Engineering**
   - Label-encoded district identity
   - Season-share ratios (`Kharif_ratio`, `Rabi_ratio`, `Summer_ratio`)
   - Prior-season yields (`Kharif_Yield`, `Summer_Yield`) as predictive signals
4. **Model Training & Evaluation** — a 75/25 train-test split feeds three regressors, scored on R², RMSE, and MAE
5. **Feature Importance** — extracted from the Random Forest model to rank predictive drivers
6. **Inference Demo** — predicts yield for a sample district scenario and checks it against the actual recorded value

---

## 📈 Results

Model comparison on the held-out test split:

| Model               | R² Score | RMSE (kg/ha) | MAE (kg/ha) |
|----------------------|:--------:|:------------:|:-----------:|
| Linear Regression     | 0.730    | 269.5        | 197.5       |
| **Random Forest**     | **0.840**| **207.5**    | **155.9**   |
| Gradient Boosting     | 0.832    | 212.4        | 178.9       |

**Random Forest** was the strongest performer and was refit on the full dataset for feature-importance analysis and inference, reaching an in-sample **R² of 0.983**.

<details>
<summary>📌 Sample prediction output</summary>

```
Predicted All-Seasons Yield for Raichur: 3148 kg/ha
Actual value in dataset: 3144 kg/ha
```

</details>

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### Running the notebook

```bash
git clone https://github.com/Umesh-369/karnataka-rice-yield-prediction.git
cd karnataka-rice-yield-prediction
jupyter notebook Karnataka_rice_ml_analysis.ipynb
```

> ⚠️ **Note on the dataset:** the notebook loads a Karnataka-only, 30-district CSV (`Crop_Rice_Area_in_Hectares_Production_in_Tonnes_Yield_in_Kgs_Hectare.csv`) with pre-computed `Kharif_Area`, `Rabi_Area`, `Summer_Area`, and `All Seasons_Yield` columns. If you're working from `ICRISAT-District Level Data.csv`, filter it down to Karnataka districts and derive/rename these columns first (or point `pd.read_csv(...)` at your prepared file) before running the cells.

---

## 📊 Dataset

The underlying data is sourced from **ICRISAT's District Level Database**, a long-running agricultural dataset covering Indian districts across decades, including area (1000 ha), production (1000 tonnes), and yield (kg/ha) for rice and several other crops. This project narrows the scope to Karnataka's 30 districts and focuses on rice cultivation across the Kharif, Rabi, and Summer seasons.

---

## 🗺️ Roadmap

- [ ] Add cross-validation and hyperparameter tuning for the tree-based models
- [ ] Incorporate rainfall/weather variables as additional predictors
- [ ] Package the trained model behind a simple prediction script or API
- [ ] Extend analysis to multi-year time-series forecasting

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/Umesh-369/karnataka-rice-yield-prediction/issues) or open a pull request.

## 📄 License

This project is available under the [MIT License](LICENSE).

## 🙏 Acknowledgements

- Dataset: [ICRISAT District Level Database](http://data.icrisat.org/dld/)
- Built as part of the **ANNAM.AI — Fundamentals of AI Using Agriculture Data Set** coursework

---

<div align="center">

Made with 🌾 for Karnataka's farming community

</div>
