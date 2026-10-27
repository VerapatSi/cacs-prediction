# Machine Learning for the Prediction of Coronary Artery Calcium Score Using Longitudinal Data

Code for the master's thesis of Verapat Sirichotikul, Biomedical Data Science, Faculty of Science, Kasetsart University.

The study predicts a coronary artery calcium score (CACS) of 100 or more from routine clinical and laboratory data, using two feature sets:

| Notebook | Feature set | Patients | Features |
|---|---|---|---|
| `snapshot_all_models.ipynb` | Snapshot: most recent values, days since each value, number of measurements, and six additional features | 1,095 | 47 |
| `trend_all_models.ipynb` | Trend: slope, delta, and standard deviation of each variable | 635 | 41 |

Both notebooks use the same procedure: five-fold cross-validation repeated three times (the same 15 folds for every model), imputation fitted on the training fold only, five models (logistic regression, random forest, support vector machine, XGBoost, and TabPFN), evaluation by accuracy, macro precision, macro recall, macro F1 score, and AUC, ROC curves, and permutation importance.

## Requirements

The analysis was run in Google Colaboratory with Python 3.13, pandas 2.2.3, NumPy 2.1.3, scikit-learn 1.6.1, XGBoost 3.4.1, TabPFN 9.2.0 (model weights version 3.5), and Matplotlib 3.10.0.

TabPFN needs a personal access token. In Colab, add it under **Secrets** with the name `TABPFN_TOKEN`. Do not write the token in the notebook.

## How to run

1. Open a notebook in Google Colaboratory and select a GPU runtime.
2. Run all cells and upload the data file when asked (`snapshot_730.csv` or `trend_730.csv`).
3. The results are saved as CSV and PNG files in the working folder. If Colab stops, run all cells again; the analysis continues from the last finished fold.

## Data availability

The patient data are not included in this repository, because they come from the medical records of Phramongkutklao Hospital and contain patient information. The study was approved by the Institutional Review Board, Royal Thai Army Medical Department (code Q010h/69_Exp). Requests for the data should be sent to the author and require approval from the Institutional Review Board.

## Outputs

| File | Content |
|---|---|
| `table10_snapshot.csv`, `table11_trend.csv` | Mean performance over the 15 folds and SD of the AUC |
| `cv_results_*.csv` | Performance of each model in each fold |
| `cv_predictions_*.csv` | Predicted probability for each patient in each fold |
| `cv_importance_*.csv` | Permutation importance of each feature in each fold |
| `top3_features_*.csv` | Three most important features of each model |
| `roc_cv_*.png`, `importance_cv_*.png` | ROC curves and importance figures |
