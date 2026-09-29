# Data

The notebooks are designed to run reproducibly even when the raw CSV is not committed.

If `breast_cancer.csv` is present in this directory, the notebooks load it directly. Otherwise they reconstruct the equivalent Wisconsin Diagnostic Breast Cancer dataset using `sklearn.datasets.load_breast_cancer`.

Expected original structure:

- `id`
- `diagnosis` where B = benign and M = malignant
- 30 morphology variables: 10 mean, 10 standard-error and 10 worst measurements

Dataset size used in this project: 569 observations.
