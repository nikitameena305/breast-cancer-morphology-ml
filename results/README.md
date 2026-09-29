# Results

Machine-readable outputs from the project are stored here so the headline results can be inspected without re-running every notebook.

## Logistic Regression
- metrics
- top feature coefficients

## K-Means
- clustering metrics
- patient-level cluster results

## SVM
- metrics

## Random Forest
- train/test metrics
- confusion matrix
- MDI feature importance
- permutation importance

## GMM
- metrics
- BIC/AIC values
- cluster composition
- PCA variance

## Final synthesis
The `final/` directory contains the consolidated supervised test results, supervised 5-fold CV results, unsupervised comparison, and representation-level CV results.

## Feature analysis and PCA
The `feature_selection/` and `pca/` directories contain the ANOVA ranking, PCA explained variance, and PC1 loading summaries used in the final interpretation.

Hierarchical Clustering did not have a separate exported CSV in the available source-results folder. Its ARI, NMI and silhouette values are therefore preserved in the consolidated final unsupervised table rather than inventing an unsupported standalone file.
