# UCI Student Performance Dataset Analysis

## Overview
This folder contains preprocessing and analysis code for the UCI Student Performance datasets.

## Files
- **process_uci_spd.ipynb** - Main analysis notebook

## Notebook Contents

The `process_uci_spd.ipynb` notebook provides a comprehensive analysis of both datasets:

### 1. Data Loading
- Loads `student-mat.csv` (Mathematics)
- Loads `student-por.csv` (Portuguese)

### 2. Basic Information
- Dataset shapes and dimensions
- Column names and data types
- First rows preview

### 3. Missing Values Analysis
- Checks for null values
- Reports completeness

### 4. Statistical Summaries
- Numeric feature statistics
- Categorical feature distributions

### 5. Target Variable Analysis (Grades)
- G1 (first period grade)
- G2 (second period grade)
- G3 (final grade)
- Distribution visualizations

### 6. Key Feature Distributions
- Age distribution
- Study time, failures, absences
- Behavioral patterns

### 7. Dataset Comparison
- Side-by-side metrics
- Comparative statistics

### 8. Correlation Analysis
- Top correlations with final grade
- Feature importance indicators

### 9. Correlation Heatmaps
- Full correlation matrices
- Visual relationship maps

### 10. Key Insights & Recommendations
- Preprocessing suggestions
- Feature engineering ideas
- Dataset combination feasibility

## How to Run

1. Ensure you have the required libraries:
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```

2. Open `process_uci_spd.ipynb` in Jupyter or VS Code

3. Run all cells sequentially (or use "Run All")

## Expected Outputs

- Statistical summaries
- Distribution plots
- Correlation analysis
- Actionable insights for preprocessing

## Next Steps

After running this notebook, you'll have a clear understanding of:
- Dataset structure and quality
- Key features affecting student performance
- How to preprocess for modeling
- Whether/how to combine the two datasets
