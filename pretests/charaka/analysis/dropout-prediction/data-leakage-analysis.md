# Data Leakage Analysis: `has_unregistration` Feature

## Executive Summary

This document investigates a **critical data leakage issue** in the dropout prediction model. The feature `has_unregistration` (and related features) directly encode information about the target variable, leading to artificially inflated model performance that would not generalize to real-world early warning systems.

---

## 1. Problem Identification

### 1.1 Feature Creation

The `has_unregistration` feature is created in the preprocessing pipeline:

```python
# Unregistration indicator (dropout indicator)
df['has_unregistration'] = df['date_unregistration'].notna().astype(int)
```

**Definition:**
- `has_unregistration = 1` if `date_unregistration` is not null (student has an unregistration date)
- `has_unregistration = 0` if `date_unregistration` is null (student does not have an unregistration date)

### 1.2 Target Variable

The target variable `is_dropout` is created from:

```python
student_info['is_dropout'] = (student_info['final_result'] == 'Withdrawn').astype(int)
```

**Definition:**
- `is_dropout = 1` if `final_result == 'Withdrawn'` (student dropped out)
- `is_dropout = 0` otherwise (student did not drop out)

### 1.3 The Leakage

**Critical Issue:** Students who withdraw from a course receive an unregistration date. Therefore:
- If `has_unregistration = 1` → Student has unregistered → Student has dropped out
- If `has_unregistration = 0` → Student has not unregistered → Student likely did not drop out

**The feature is essentially a direct indicator of the target variable.**

---

## 2. Evidence of Data Leakage

### 2.1 Feature Importance

From the model training results:
- **`has_unregistration`**: 99.3% feature importance
- **All other features combined**: < 1% importance

This extreme dominance indicates the model is relying almost entirely on this single feature.

### 2.2 Model Performance

**With leakage features:**
- Test Accuracy: 99.83%
- Test F1 Score: 0.9973
- Test ROC-AUC: 0.9998
- Confusion Matrix: Only 11 errors out of 6,519 test samples

**This performance is artificially high** because the model is essentially checking:
```
IF has_unregistration == 1:
    PREDICT dropout
ELSE:
    PREDICT no dropout
```

### 2.3 Data Statistics

From the dataset:
- **Total students**: 32,593
- **Dropout rate**: 31.16% (10,156 students)
- **Students with unregistration dates**: ~30.9% (10,072 students)
- **Students without unregistration dates**: ~69.1% (22,521 students)

The near-perfect alignment between dropout rate and unregistration rate confirms the leakage.

---

## 3. Affected Features

The following features should be **removed** from the model:

1. **`has_unregistration`** - Binary indicator of unregistration (direct leakage)
2. **`date_unregistration`** - The actual unregistration date (leakage)
3. **`days_until_unregistration`** - Derived from `date_unregistration` (leakage)

**Note:** These features are only available **after** a student has dropped out, making them useless for predictive early warning systems.

---

## 4. Real-World Implications

### 4.1 Why This Matters

In a **real early warning system**, you want to predict dropout **before** it happens to enable intervention. The unregistration date is only recorded **after** a student has already withdrawn, making it:

1. **Not actionable**: By the time you know the unregistration date, it's too late to intervene
2. **Not predictive**: It doesn't help predict future dropouts
3. **Misleading**: The high performance gives false confidence in the model

### 4.2 Expected Impact of Removal

When these features are removed, we expect:

- **Lower model performance** (likely 80-90% accuracy instead of 99%+)
- **More balanced feature importance** across behavioral and demographic features
- **More realistic and useful predictions** for early intervention

### 4.3 Features That Should Remain

The model should rely on **predictive features** that are available early in the course:

- **VLE Engagement**: `total_vle_clicks`, `vle_engagement_rate`, `vle_interaction_days`
- **Assessment Performance**: `avg_assessment_score`, `num_assessments`, `weighted_avg_score`
- **Registration Timing**: `date_registration`, `registered_early`, `days_before_start`
- **Demographics**: `gender_encoded`, `region_encoded`, `age_band_encoded`, `imd_band_encoded`
- **Academic History**: `num_of_prev_attempts`, `studied_credits`
- **Course Information**: `module_presentation_length`, `presentation_year`

These features are available **during** the course and can be used for early intervention.

---

## 5. Recommendations

### 5.1 Immediate Actions

1. **Remove leakage features** from the feature set:
   - `has_unregistration`
   - `date_unregistration`
   - `days_until_unregistration`

2. **Retrain all models** without these features

3. **Re-evaluate model performance** with realistic expectations

### 5.2 Model Validation

After removing leakage features:

1. **Compare performance** with/without leakage features
2. **Analyze feature importance** to identify truly predictive features
3. **Validate on temporal splits** (train on earlier semesters, test on later semesters)
4. **Use cross-validation** to ensure robust performance estimates

### 5.3 Documentation

1. **Document the leakage issue** in model metadata
2. **Update preprocessing pipeline** to exclude these features by default
3. **Add data validation checks** to prevent similar issues in the future

---

## 6. Alternative Use Cases

If you need to use `date_unregistration` for analysis, consider:

1. **Time-to-event analysis**: Predict **when** a student will drop out (survival analysis)
2. **Post-hoc analysis**: Analyze patterns in students who dropped out
3. **Temporal validation**: Use unregistration dates to create time-based train/test splits

However, these should **not** be used as features for predicting dropout.

---

## 7. Conclusion

The `has_unregistration` feature (and related features) represent a **critical data leakage issue** that:

- Inflates model performance to unrealistic levels (99%+)
- Provides no actionable insights for early intervention
- Misleads stakeholders about model capabilities

**Removing these features is essential** for building a realistic and useful dropout prediction system that can actually help identify at-risk students early enough for intervention.

---

## References

- Model Training Notebook: `model-training.ipynb`
- Preprocessing Notebook: `dropout-prediction.ipynb`
- Model Metadata: `models/model_metadata.json`
- Interpretability Analysis: `../interpretability-analysis.md`

