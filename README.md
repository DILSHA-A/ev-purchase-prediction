# 🚗⚡ EV Purchase Prediction

Predicting whether a person will buy an electric vehicle — built for Kaggle's Playground Series S6E9.

**Public Leaderboard Score: 0.94122** | **Cross-Validated ROC-AUC: 0.9415**

---

## 📌 Problem

A binary classification task: predict the probability that a person will purchase an EV (`Will_Buy_EV`), evaluated using ROC-AUC — a metric that rewards correctly ranking likely buyers above unlikely ones.

## 📊 Dataset

- 668,665 training rows · 286,571 test rows · 14 features
- No missing values
- Imbalanced target: ~17.5% positive class (EV buyers)

## 🔍 Exploratory Data Analysis

Rather than assuming which features matter, I compared feature averages between buyers and non-buyers to find real signal.

**Strong predictors found:**
- `Range_Anxiety_Level` — buyers overwhelmingly report low range anxiety
- `Subsidy_Available` — the single biggest driver of purchase likelihood
- `Environmental_Concern_Level` — clear separation between buyers and non-buyers
- `Annual_Income_USD` — buyers skew notably higher income
- `Home_Charging_Possible` — meaningful lift when charging at home is possible

**Weak predictors:** `Gender`, `City_Type`, `Current_Car_Type`, `Age` — little to no difference between classes.

## 🛠️ Approach

1. Cleaned and encoded categorical features
2. Benchmarked three models on a held-out validation split
3. Validated the winner with 5-fold cross-validation
4. Trained the final model on the full training set

## 🏆 Model Comparison

| Model | Validation ROC-AUC |
|---|---|
| Logistic Regression | 0.9172 |
| Random Forest | 0.9384 |
| **LightGBM** | **0.9418** |

LightGBM was selected as the final model, confirmed with 5-fold CV (mean ROC-AUC: 0.9415).

## 🧰 Tools

Python · pandas · scikit-learn · LightGBM · Kaggle Notebooks

## 📓 Notebook

[View the full notebook on Kaggle](https://www.kaggle.com/code/dilshaminnu/ev-purchase-prediction-lightgbm-eda)
