Here's a coherent and corrected version of your README:

---

# 🧠 Predicting Obesity Risk Using NHANES Data and Machine Learning

This repository presents a data-driven obesity classification system built using health and lifestyle survey data from **NHANES**. The modeling pipeline, developed in **R**, integrates **feature selection**, **cross-validation**, and **hyperparameter tuning** across multiple algorithms to classify individuals into five distinct obesity categories.

---

## 📋 Project Summary

Obesity is a growing global health crisis. This project analyzes over 7,800 individual records from the U.S. NHANES dataset (2011–2018) to predict obesity classes with high accuracy. Models are trained using a combination of physiological, behavioral, and biochemical features.

---

## 🎯 Goals

* Clean, integrate, and preprocess multi-cycle NHANES datasets (2011–2018)
* Engineer physiological features such as Body Water and Basal Metabolic Rate (BMR)
* Impute missing values using MICE
* Apply Recursive Feature Elimination (RFE) to reduce dimensionality
* Tune hyperparameters using grid/random search with cross-validation
* Compare classification performance across five machine learning models
* Deliver interpretable and reproducible results in R

---

## 🔍 Dataset

* **Source:** [NHANES](https://www.cdc.gov/nchs/nhanes/)
* **Cycles Used:** 2011–2018
* **Records:** \~7,837 adults (age ≥18)
* **Final Feature Set:** 40+ variables including:

  * **Demographics:** `Gender`, `Age`, `Pregnancy`
  * **Physical Activity & Sleep:** `Vigorous_Work`, `Moderate_Activity`, `Sleep_Hours`
  * **Clinical Biometrics:** `Fat_Percent`, `BP`, `Triglycerides`, `Uric_Acid`, `CRP`
  * **Engineered Features:** `Body_Water`, `Basal_Metabolic_Rate`

![image](https://github.com/user-attachments/assets/3f4ec34e-db34-4e79-aca9-d64ba25a8768)

### 🧾 Target Variable

`Obesity_Category`, classified by BMI:

* `Non-Obese` (<25)
* `Pre-Obese` (25–30)
* `Obesity Class I` (30–35)
* `Obesity Class II` (35–40)
* `Obesity Class III` (≥40)

![image](https://github.com/user-attachments/assets/f57dfc1b-e8ca-4385-898a-a9663fe566c7)

---

## 🧠 Models Used

All models were implemented and tuned in **R** using the `caret`, `e1071`, `randomForest`, `class`, and `nnet` packages.

### 📊 Machine Learning Algorithms

| Model                                    | Tuned Parameters                  |
| ---------------------------------------- | --------------------------------- |
| **Polytomous Logistic Regression (PLR)** | –                                 |
| **Decision Tree (rpart)**                | `cp`, `maxdepth`                  |
| **Random Forest**                        | `mtry`                            |
| **Support Vector Machine (SVM)**         | `C`, `sigma`                      |
| **K-Nearest Neighbors (KNN)**            | `k`, with preprocessing (scaling) |

Each model was optimized using **k-fold cross-validation** and **grid search**.

---

## 🧬 Feature Selection (RFE)

Feature selection was performed using Recursive Feature Elimination (RFE) with **Polytomous Logistic Regression** as the base model. Predictors (excluding categorical variables) and the target variable `Obesity_Category` were defined. A 3-fold cross-validation was used to assess feature subsets. The selected features, along with summary metrics and performance visualizations, helped improve model efficiency and reduce overfitting.

![image](https://github.com/user-attachments/assets/8ba374e6-d556-4904-9009-d58aeaa61ea7)
![image](https://github.com/user-attachments/assets/c46adffc-753b-49aa-92af-cdd22e53c085) 

---

## 📈 Evaluation Metrics

Model performance was evaluated using:

* Accuracy
* Macro and Weighted Precision
* Macro and Weighted Recall
* Macro and Weighted F1-Score
* Confusion Matrix
* Feature Importance Plots (for tree-based models)

---

## ⚙️ Workflow & Pipeline

1. **Data Cleaning & Filtering**

   * Remove individuals under 18 and pregnant participants
   * Eliminate highly correlated features (e.g., BMI, Waist, Hip)
   * Harmonize data across NHANES cycles

2. **Missing Data Imputation**

   * Use `mice` with Predictive Mean Matching (PMM)
   * Apply Multinomial Logistic Regression for categorical data

3. **Feature Engineering**

   * Compute `Body_Water` and `BMR`

4. **Feature Selection**

   * Perform RFE with 3-fold CV using PLR

5. **Model Training & Tuning**

   * k-fold Cross-Validation
   * Hyperparameter tuning via Grid/Random Search

---

## 🛠 Tools and Packages

* **Language:** R ≥ 4.1
* **Key Packages:**

  * Modeling: `caret`, `randomForest`, `e1071`, `nnet`, `class`
  * Imputation: `mice`
  * Visualization: `ggplot2`, `forcats`, `stringr`
  * Utility: `dplyr`, `Metrics`, `pROC`

---

## 💡 Highlights & Key Findings

* 🔁 **RFE** enabled selection of a compact and interpretable feature subset
* 🏆 **Random Forest** achieved the best overall performance (F1-weighted)
* ⚖️ Excluding BMI and related size metrics improved generalization and reduced overfitting

![1_page-0001](https://github.com/user-attachments/assets/2968a474-07b1-4345-82a2-55f0baa9953f)
![1_page-0002](https://github.com/user-attachments/assets/0a8d7eed-1457-435c-94a1-7894a07945ad)
![image](https://github.com/user-attachments/assets/c58f81e3-5556-48ca-9cd5-40903af65db8)
