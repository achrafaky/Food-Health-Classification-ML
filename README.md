
# 🥗 Food Health Classification ML
> **Machine Learning multiclasse pour la prédiction des scores de santé nutritionnelle.**

---

<div align="center">

![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-ee4c2c?style=for-the-badge&logo=xgboost&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

[**Explorer le Notebook**](#-getting-started) • [**Voir les Résultats**](#-results) • [**L'Équipe**](#-authors--contact)

</div>

---

## 🎯 Project Objective
Développement d'un modèle de **classification multi-classe** capable de prédire avec précision le `health_score` d'un produit alimentaire. 

* **Finalité** : Intégration dans un système de recommandation alimentaire intelligent.
* **Classes cibles** : 60, 65, 70, 75 (Scores de santé).

---

## 📊 Dataset & Features
Le modèle s'appuie sur `food_database.csv`, contenant des indicateurs nutritionnels clés :

| Feature | Description | Importance (RF) |
| :--- | :--- | :--- |
| `calories` | Énergie (kcal) | 🟥🟥🟥🟥🟥 (31%) |
| `fat_g` | Lipides totaux | 🟥🟥🟥🟥⬜ (28%) |
| `sugar_g` | Teneur en sucre | 🟥🟥🟥⬜⬜ (22%) |
| `protein_g`| Protéines | 🟥⬜⬜⬜⬜ (8%) |

> **Preprocessing** : Imputation par médiane (numérique) et mode (catégoriel), suivi d'un One-Hot Encoding pour la variable `food_type`.

---

## 🧠 Methodology
Nous avons testé et comparé 5 algorithmes avec une approche de **stratified 80/20 split** :

1.  **Random Forest** (Ensemble Learning) - *Gagnant* 🏆
2.  **Decision Tree**
3.  **K-Nearest Neighbors** (KNN)
4.  **Logistic Regression** (Baseline)
5.  **Gaussian Naive Bayes**

---

## 🏆 Results
Le **Random Forest** surpasse les autres modèles grâce à sa gestion des relations non-linéaires.

| Model | Accuracy | F1-Score (Macro) |
| :--- | :---: | :---: |
| **Random Forest** | **0.93** | **0.60** |
| Decision Tree | 0.91 | 0.56 |
| KNN | 0.89 | 0.53 |

**Optimisation** : Un `GridSearchCV` a permis de fixer `n_estimators: 200` pour une stabilité maximale.

---

## 🚀 Getting Started

### Installation
```bash
# Cloner le projet
git clone [https://github.com/achrafaky/Food-Health-Classification-ML.git](https://github.com/achrafaky/Food-Health-Classification-ML.git)
cd Food-Health-Classification-ML

# Installer les dépendances
pip install pandas numpy matplotlib seaborn scikit-learn xgboost jupyter