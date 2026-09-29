# Breast Cancer Morphology ML

Supervised and unsupervised machine-learning analysis of breast-tumour morphology using the Wisconsin Diagnostic Breast Cancer dataset.

## Research question

**To what extent do supervised and unsupervised learning methods reveal consistent diagnostic structure in breast-tumour morphology, and can this structure be represented using a smaller subset of morphological features?**

## Project overview

The project compares complementary views of the same morphology data:

- **Supervised learning:** Logistic Regression, SVM, Random Forest
- **Unsupervised learning:** K-Means, Hierarchical Clustering, Gaussian Mixture Model
- **Feature analysis:** ANOVA F-scores and feature importance
- **Dimensionality reduction:** PCA
- **Robustness:** 5-fold stratified cross-validation

The dataset contains **569 observations** and **30 morphology features**.

## Main findings

- Supervised models showed consistently high discrimination.
- 5-fold CV results:
  - Logistic Regression: accuracy 0.9737 ± 0.0166, ROC-AUC 0.9953 ± 0.0053
  - SVM: accuracy 0.9772 ± 0.0163, ROC-AUC 0.9945 ± 0.0060
  - Random Forest: accuracy 0.9526 ± 0.0131, ROC-AUC 0.9895 ± 0.0077
- Clustering recovered meaningful but incomplete structure related to diagnosis.
- Morphology features repeatedly highlighted included concave points, concavity, radius, perimeter and area.
- The 10 worst-measurement features retained performance comparable to all 30 features.
- Seven principal components retained about 90% of total variance while preserving most predictive information.

These results are **internal validation on this dataset**, not evidence of clinical diagnostic performance.

## Repository structure

```
breast-cancer-morphology-ml/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   └── README.md
├── notebooks/
│   ├── 01_preprocessing.ipynb
│   ├── 02_logreg_kmeans.ipynb
│   ├── 03_svm_hierarchical.ipynb
│   ├── 04_rf_gmm.ipynb
│   ├── 05_final_comparison.ipynb
│   └── 06_feature_selection_pca.ipynb
├── figures/
│   └── README.md
└── .github/
    └── workflows/
        └── verify.yml
```

## Reproduce the analysis

### 1. Clone the repository

```bash
git clone https://github.com/nikitameena305/breast-cancer-morphology-ml.git
cd breast-cancer-morphology-ml
```

### 2. Create an environment

```bash
python -m venv .venv
source .venv/bin/activate
```

On Windows:

```powershell
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Run the notebooks

Start Jupyter:

```bash
jupyter lab
```

Run the notebooks in numerical order from **01** to **06**.

The notebooks first look for `data/breast_cancer.csv` (or `../data/breast_cancer.csv` when launched from the notebooks directory). If the CSV is absent, they rebuild the equivalent Wisconsin Diagnostic Breast Cancer data from `sklearn.datasets.load_breast_cancer`, so the repository remains reproducible without a Colab-only upload.

## Reproducibility design

- Fixed random seeds are used where relevant.
- Train/test separation is preserved.
- Standardization and PCA are fitted on training data or placed inside cross-validation pipelines.
- 5-fold stratified CV is used for model robustness checks.
- Supervised and unsupervised metrics are reported separately because they answer different questions.
- GitHub Actions executes the notebooks from a clean environment to detect broken repository-only assumptions.

## Notebook guide

| Notebook | Purpose |
|---|---|
| 01 | Data loading, cleaning and train/test preparation |
| 02 | Logistic Regression and K-Means |
| 03 | SVM and Hierarchical Clustering |
| 04 | Random Forest and GMM |
| 05 | Final supervised/unsupervised comparison and cross-validation |
| 06 | Feature selection, Mean/SE/Worst comparison and PCA |

## Limitations

The dataset is relatively small (569 observations), features are correlated, and there is no independent external clinical validation. Cross-validation here is internal validation only.

## Author

Nikita Meena
