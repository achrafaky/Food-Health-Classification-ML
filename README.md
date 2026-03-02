```markdown
# 🥗 Food Health Classification ML

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0%2B-orange?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-1.24%2B-013243?logo=numpy&logoColor=white)](https://numpy.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.5%2B-11557c?logo=python&logoColor=white)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-0.12%2B-9c7c5e?logo=python&logoColor=white)](https://seaborn.pydata.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-1.7%2B-ee4c2c?logo=xgboost&logoColor=white)](https://xgboost.readthedocs.io/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

> **Classify food health scores automatically!**  
> This project aims to predict the health level of food items (scores 60, 65, 70, 75) based on their nutritional features, using various machine learning models. Ideal for nutrition apps and dietary planning.

---

## 🎯 **Project Objective**

Develop a **multi-class classification model** that accurately predicts the `health_score` of a food product from its nutritional information.  
The final model is designed to be integrated into a **food recommendation system** to help users make healthier choices.

---

## 📊 **Dataset**

- **Source**: `food_database.csv` (original data from food composition databases)
- **Target variable**: `health_score` (classes: 60, 65, 70, 75)
- **Features**:

| Feature       | Description                              | Type      |
|---------------|------------------------------------------|-----------|
| `calories`    | Energy content (kcal)                    | Numerical |
| `protein_g`   | Protein content (grams)                   | Numerical |
| `fat_g`       | Total fat (grams)                         | Numerical |
| `carbs_g`     | Carbohydrates (grams)                     | Numerical |
| `fiber_g`     | Dietary fiber (grams)                     | Numerical |
| `sugar_g`     | Sugar content (grams)                     | Numerical |
| `sodium_mg`   | Sodium content (milligrams)               | Numerical |
| `food_type`   | Category (e.g., Fruits, Dairy, Grains)    | Categorical |

> ⚠️ **Note**: The target was normalized during preprocessing; we restored the original labels for classification.

---

## 🧠 **Methodology**

### 🔄 **Data Preprocessing**
- Removed `food_name` (non‑predictive identifier)
- Imputed missing values: **median** for numerical, **mode** for categorical
- One‑hot encoding of `food_type`
- **No rescaling** of numerical features (already normalized in part 3)

### 🤖 **Models Tested** (default scikit‑learn parameters)
| Model               | Description                              |
|---------------------|------------------------------------------|
| Logistic Regression | Linear baseline                         |
| K‑Nearest Neighbors | Distance‑based non‑parametric           |
| Decision Tree       | Interpretable tree‑based                 |
| Random Forest       | Ensemble of trees (bagging)              |
| Gaussian Naive Bayes| Probabilistic with independence assumption|

All models were trained on the same **stratified 80/20 train‑test split** to ensure fair comparison.

### 📈 **Evaluation Metrics**
- **Accuracy**: overall correctness
- **Precision (macro)**: average precision per class
- **Recall (macro)**: average recall per class
- **F1‑Score (macro)**: harmonic mean of precision and recall (primary metric)

We chose **macro‑averaging** to give equal weight to each class, preventing bias toward the majority class (60).

---

## 🏆 **Results**

### 🔍 **Model Performance Comparison**

| Model                 | Accuracy | Precision (macro) | Recall (macro) | **F1‑Score (macro)** |
|-----------------------|----------|-------------------|----------------|----------------------|
| **Random Forest**     | **0.93** | **0.61**          | **0.59**       | **0.60**             |
| Decision Tree         | 0.91     | 0.57              | 0.56           | 0.56                 |
| KNN                   | 0.89     | 0.54              | 0.53           | 0.53                 |
| Logistic Regression   | 0.85     | 0.45              | 0.44           | 0.44                 |
| Naive Bayes           | 0.71     | 0.34              | 0.34           | 0.34                 |

📊 **Random Forest** emerges as the best model, thanks to its ability to capture complex non‑linear relationships between nutrients.

### ❌ **Error Analysis**
- Most misclassifications occur between **adjacent classes** (e.g., 60 ↔ 65), which is acceptable given the continuous nature of health scores.
- Minority classes (70, 75) are less accurately predicted due to limited samples.

### 🔧 **Hyperparameter Tuning (GridSearchCV)**
- Grid search on `n_estimators`, `max_depth`, `min_samples_split` for Random Forest
- **Best parameters**: `{'max_depth': None, 'min_samples_split': 2, 'n_estimators': 200}`
- **F1‑score improvement**: marginal (+0.01), indicating default params were already near‑optimal.

### 📌 **Feature Importance** (Random Forest)
```
calories  ████████████████████████████████████ 0.31
fat_g     ████████████████████████████████     0.28
sugar_g   ██████████████████████████           0.22
carbs_g   ███████████████                      0.12
...       ...
```
(For a detailed chart, see the notebook.)

---

## 🚀 **Getting Started**

### 1. Clone the repository
```bash
git clone https://github.com/achrafaky/Food-Health-Classification-ML.git
cd Food-Health-Classification-ML
```

### 2. Install dependencies (recommended: create a virtual environment)
```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost jupyter
```

### 3. Launch Jupyter Notebook
```bash
jupyter notebook Projet2_MMSD.ipynb
```
Follow the cells to run the complete analysis.

---

## 👥 **Authors & Contact**

| Name               | Role                                  | Links |
|--------------------|---------------------------------------|-------|
| **Achraf Akiyaf**  | Team Member & GitHub Maintainer       | [![Email](https://img.shields.io/badge/Email-akiyafachraf19%40gmail.com-red?logo=gmail&logoColor=white)](mailto:akiyafachraf19@gmail.com) [![LinkedIn](https://img.shields.io/badge/LinkedIn-Achraf_Akiyaf-0077B5?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/achraf-akiyaf-b40286284/) |
| Lahmini Hiba       | Team Member                           | |
| Belhaouz Salma     | Team Member                           | |
| Abrkan Bilal       | Team Member                           | |
| SMAILI Hasna       | Team Member                           | |
| OUMAHRIR Brahim    | Team Member                           | |

> We are a group of Master's students in Mathematical Modeling and Data Science (MMSD) passionate about applying machine learning to real‑world problems.

---

## 📄 **License**
This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.

---

## ⭐ **Show Your Support**
If you like this project, please give it a **star** on GitHub – it helps others discover it!

---

**Happy predicting!** 🚀
```