# UCI Student Performance Dataset - Preprocessing & Analysis

## Overview
Comprehensive preprocessing and data mining preparation pipeline for the UCI Student Performance dataset (1,044 students, 33 features).

## Files
- **uci_combined_dataset_analysis.ipynb** - Complete analysis and preprocessing pipeline
- **process_uci_spd.ipynb** - Initial exploratory analysis (legacy)

## Main Notebook: `uci_combined_dataset_analysis.ipynb`

### 📋 Dataset Information
- **Source**: Combined Math & Portuguese courses (unified analysis)
- **Size**: 1,044 students × 33 features
- **Target**: G3 (final grade, 0-20 scale)
- **Data Quality**: No missing values, minimal outliers

### 🔧 Pipeline Components

1. **Data Dictionary** - Complete variable documentation with semantic categorization
2. **Exploratory Data Analysis** - Statistical summaries, feature categorization (Demographic, Family, School, Social, Health, Academic)
3. **Data Quality Assessment** - Missing values, duplicates, outlier detection (IQR method)
4. **Preprocessing Pipeline** - Label encoding, MinMax normalization, Z-score standardization
5. **Feature Engineering** - 9 derived features (parent_edu_avg, total_alcohol, social_score, study_goout_ratio, grade_progress metrics, binary flags)
6. **Correlation Analysis** - Heatmaps, top correlations with G3, highly correlated pairs
7. **Distribution Analysis** - 15+ visualizations (histograms, box plots, scatter plots, pair plots)
8. **Relationship Visualizations** - Feature relationships with final grade
9. **Target Variable Analysis** - Grade distributions, pass/fail analysis (~70% pass rate)
10. **Data Mining Preparation** - Ready datasets for classification, clustering, association rule mining
11. **Export** - 7 processed CSV files + encoding metadata (JSON)

### 📊 Output Datasets

Saved to `pretests/dinalie/processed/`:
- `uci_combined_processed_full.csv` - Complete processed dataset
- `uci_classification_ready.csv` - For regression/binary/multiclass classification
- `uci_clustering_ready.csv` - Standardized features for clustering
- `uci_association_ready.csv` - Categorical features for pattern mining
- `X_train_classification.csv`, `X_test_classification.csv` - Stratified train-test splits (80/20)
- `y_train_classification.csv`, `y_test_classification.csv` - Target variables
- `encoding_info.json` - Label encoder mappings and feature lists

## How to Run

1. **Install dependencies**:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn scipy jupyter ipykernel
   ```

2. **Select Jupyter kernel**: `uom-student-analytics` (Python 3.13.5)

3. **Open and run**: `uci_combined_dataset_analysis.ipynb` in VS Code or Jupyter

4. **Execute all cells** to generate analysis, visualizations, and export processed datasets

## Key Insights

- **Strong Predictors**: G1, G2 (prior grades), studytime, parent education
- **Negative Correlations**: Failures, alcohol consumption, absences
- **Performance**: 70% pass rate (G3 ≥ 10), 4 performance categories
- **Grade Progression**: Strong correlation between G1 → G2 → G3

## Next Steps

Use the exported datasets for:
- **Classification**: Grade prediction, pass/fail classification
- **Clustering**: Student segmentation, risk identification
- **Association Rule Mining**: Pattern discovery (e.g., failures → absences → poor performance)
- **Anomaly Detection**: Unusual student profiles
