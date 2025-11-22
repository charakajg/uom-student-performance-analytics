# Model Training Results: Comparative Analysis

## Executive Summary

This document provides a comprehensive comparison of model training results across three prediction tasks:
1. **Dropout Prediction** (OULAD dataset)
2. **Pass/Fail Prediction** (UCI and xAPI datasets)
3. **Final Grade Prediction** (OULAD and UCI datasets)

---

## 1. Dropout Prediction

### Dataset Overview
- **Source**: OULAD (Open University Learning Analytics Dataset)
- **Samples**: 32,593 students
- **Features**: 35 features (demographics, engagement, assessment performance, VLE interactions)
- **Target**: Binary classification (Dropout = 1, Not Dropout = 0)
- **Class Distribution**: 31.16% dropout rate (moderate imbalance)

### Model Performance

| Model | Validation F1 | Validation ROC-AUC | Test F1 | Test ROC-AUC |
|-------|---------------|-------------------|---------|--------------|
| **Gradient Boosting** (Best) | **0.9941** | **0.9988** | **0.9973** | **0.9998** |
| Random Forest | 0.9938 | 0.9990 | - | - |
| AdaBoost | 0.9935 | 0.9991 | - | - |
| Naive Bayes | 0.9932 | 0.9986 | - | - |
| XGBoost | 0.9926 | 0.9991 | - | - |
| Logistic Regression | 0.9926 | 0.9986 | - | - |
| SVM | 0.9923 | 0.9983 | - | - |
| K-Nearest Neighbors | 0.9852 | 0.9967 | - | - |

### Key Findings
- **Excellent Performance**: All models achieved very high performance (>99% accuracy)
- **Best Model**: Gradient Boosting with F1 = 0.9973 and ROC-AUC = 0.9998 on test set
- **Generalization**: Minimal overfitting (validation and test performance are very close)
- **Feature Importance**: `has_unregistration` is the most important feature (99.3% importance)
- **Confusion Matrix**: Only 11 errors out of 6,519 test samples (2 FP, 9 FN)

### Strengths
- Rich feature set (35 features) including VLE engagement, assessment scores, and registration timing
- Large dataset (32,593 samples) provides robust training
- Excellent model generalization with consistent performance across splits

---

## 2. Pass/Fail Prediction

### Dataset Overview
- **Sources**: UCI Student Performance Dataset (1,044 samples) and xAPI Dataset (480 samples)
- **Features**: 5 features (gender, absences, engagement, parental support, academic level)
- **Target**: Binary classification (Pass = 1, Fail = 0)
- **Class Distribution**: ~74-78% pass rate (moderate imbalance)

### Model Performance - Direction 1: Train on UCI → Test on xAPI

| Model | Validation F1 (UCI) | Test F1 (xAPI) | Performance Drop |
|-------|---------------------|----------------|-----------------|
| **Naive Bayes** (Best) | **0.8864** | **0.3717** | **-0.5146** |
| SVM | 0.8846 | - | - |
| Random Forest | 0.8800 | - | - |
| Gradient Boosting | 0.8775 | - | - |
| Logistic Regression | 0.8750 | - | - |
| K-Nearest Neighbors | 0.8686 | - | - |

**Test Set Performance (xAPI)**:
- Accuracy: 0.3521
- Precision: 0.6479
- Recall: 0.2606
- F1 Score: 0.3717
- ROC-AUC: 0.5053

### Model Performance - Direction 2: Train on xAPI → Test on UCI

| Model | Validation F1 (xAPI) | Test F1 (UCI) | Performance Drop |
|-------|---------------------|---------------|-----------------|
| **Gradient Boosting** (Best) | **0.9793** | **0.8762** | **-0.1031** |
| K-Nearest Neighbors | 0.9660 | - | - |
| Naive Bayes | 0.9645 | - | - |
| Random Forest | 0.9517 | - | - |
| Logistic Regression | 0.9150 | - | - |
| SVM | 0.8919 | - | - |

**Test Set Performance (UCI)**:
- Accuracy: 0.7797
- Precision: 0.7797
- Recall: 1.0000
- F1 Score: 0.8762
- ROC-AUC: 0.5188

### Key Findings

#### Direction 1 (UCI → xAPI)
- **Severe Performance Degradation**: Massive drop from 0.8864 to 0.3717 F1 score (-51.5%)
- **Poor Generalization**: Model fails to generalize across datasets
- **Possible Causes**: 
  - Dataset distribution shift between UCI and xAPI
  - Limited feature set (only 5 features)
  - Different data collection methods/contexts

#### Direction 2 (xAPI → UCI)
- **Better Generalization**: Moderate drop from 0.9793 to 0.8762 F1 score (-10.3%)
- **Recall = 1.0**: Model predicts all students as "Pass" (no false negatives for Pass class)
- **Poor Precision for Fail Class**: Model cannot distinguish Fail cases (0.00 precision)

### Challenges
- **Cross-Dataset Generalization**: Significant performance degradation when testing on different datasets
- **Limited Features**: Only 5 features may not capture sufficient information
- **Dataset Differences**: UCI and xAPI datasets likely have different characteristics/distributions
- **Class Imbalance**: Models tend to predict majority class (Pass)

---

## 3. Final Grade Prediction

### Dataset Overview
- **Sources**: OULAD (25,820 samples) and UCI (1,044 samples)
- **Features**: 7 features (absences, academic history, age, education background, engagement, gender, support indicator)
- **Target**: Regression (normalized final grade 0-1)
- **Task Type**: Continuous value prediction

### Model Performance - Direction 1: Train on OULAD → Test on UCI

| Model | Validation R² (OULAD) | Test R² (UCI) | Performance Drop |
|-------|----------------------|---------------|------------------|
| **Gradient Boosting** (Best) | **0.1536** | **-0.8703** | **-1.0239** |
| SVR | 0.1383 | - | - |
| Linear Regression | 0.1263 | - | - |
| Ridge Regression | 0.1263 | - | - |
| Lasso Regression | -0.0000 | - | - |
| Random Forest | -0.0157 | - | - |
| K-Nearest Neighbors | -0.0335 | - | - |

**Test Set Performance (UCI)**:
- MSE: 0.0698
- RMSE: 0.2641
- MAE: 0.2091
- R²: **-0.8703** (negative R² indicates worse than baseline)
- MAPE: 362,266,913.80%

### Model Performance - Direction 2: Train on UCI → Test on OULAD

| Model | Validation R² (UCI) | Test R² (OULAD) | Performance Drop |
|-------|---------------------|-----------------|------------------|
| **Gradient Boosting** (Best) | **0.1167** | **-1.3443** | **-1.4610** |
| K-Nearest Neighbors | 0.0632 | - | - |
| Ridge Regression | 0.0622 | - | - |
| Linear Regression | 0.0620 | - | - |
| SVR | 0.0428 | - | - |
| Random Forest | 0.0201 | - | - |
| Lasso Regression | -0.0082 | - | - |

**Test Set Performance (OULAD)**:
- MSE: 0.0682
- RMSE: 0.2612
- MAE: 0.2252
- R²: **-1.3443** (negative R² indicates worse than baseline)
- MAPE: 8,985,142.58%

### Key Findings

#### Both Directions
- **Very Poor Performance**: Negative R² values indicate models perform worse than a simple baseline (predicting the mean)
- **Severe Overfitting**: Models fail completely when tested on different datasets
- **Low Validation R²**: Even on validation sets, R² is very low (0.12-0.15), indicating weak predictive power
- **Feature Importance**: 
  - `absences_normalized`: 48.4% importance
  - `engagement`: 32.0% importance
  - Other features have minimal impact

### Challenges
- **Cross-Dataset Failure**: Models completely fail when tested on different datasets
- **Weak Predictive Power**: Even on validation sets, models explain only 12-15% of variance
- **Limited Features**: 7 features may be insufficient for accurate grade prediction
- **Dataset Mismatch**: OULAD and UCI datasets have fundamentally different distributions
- **Regression Difficulty**: Predicting exact grades is more challenging than binary classification

---

## Comparative Analysis

### Performance Summary Table

| Task | Best Model | Validation Metric | Test Metric | Generalization | Status |
|------|------------|------------------|-------------|----------------|--------|
| **Dropout Prediction** | Gradient Boosting | F1: 0.9941<br>ROC-AUC: 0.9988 | F1: 0.9973<br>ROC-AUC: 0.9998 | Excellent | ✅ Success |
| **Pass/Fail (UCI→xAPI)** | Naive Bayes | F1: 0.8864 | F1: 0.3717 | Poor | ⚠️ Limited |
| **Pass/Fail (xAPI→UCI)** | Gradient Boosting | F1: 0.9793 | F1: 0.8762 | Moderate | ⚠️ Limited |
| **Final Grade (OULAD→UCI)** | Gradient Boosting | R²: 0.1536 | R²: -0.8703 | Very Poor | ❌ Failure |
| **Final Grade (UCI→OULAD)** | Gradient Boosting | R²: 0.1167 | R²: -1.3443 | Very Poor | ❌ Failure |
