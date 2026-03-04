# CRC Diagnostics: Microbiome-Based Prediction

This project implements a machine learning pipeline to distinguish Colorectal Cancer (CRC) patients from healthy controls using 16S rRNA sequencing data. The focus is on identifying stable microbial biomarkers across different tree-based algorithms.

## Key Results

* **Recall:** **100%** (0 false negatives), crucial for medical screening applications.
* **Accuracy:** **83.3%** on the hold-out test set.
* **ROC-AUC:** **0.875**, indicating strong model discriminative power.

## Project Structure

The analysis is divided into five logical stages, each documented within the notebook:

### 1. Data Integration & Taxonomy
* Merged patient metadata with ASV (Amplicon Sequence Variant) tables.
* Mapped cryptic sequence IDs to `Genus_Species` format for biological interpretability.

### 2. Feature Engineering & Filtering
* **Normalization:** Converted raw counts to log-relative abundances.
* **Sparsity Filtering:** Removed rare taxa present in less than 10% of samples to reduce noise.

### 3. Statistical Feature Selection
* Performed **Mann-Whitney U tests** to identify differentially abundant bacteria.
* Selected features with $p < 0.05$ as input for the predictive models.

### 4. Model Training & Validation
* Compared **Random Forest** (Bagging) and **XGBoost** (Boosting).
* Implemented stratified 80/20 splitting to maintain class balance.

### 5. Interpretation & Biomarkers
* Extracted feature importance scores to rank microbial drivers.
* **Top Markers:** *Anaerostipes_sp* and *Fusicatenibacter_sp* were consistently identified.

## Conclusion

The high agreement between different algorithms on feature importance highlights the robustness of the discovered biomarkers for potential clinical diagnostic applications.

## Tech Stack

* **Python:** Pandas, NumPy, Scikit-learn, XGBoost.
* **Visualization:** Matplotlib, Seaborn.
