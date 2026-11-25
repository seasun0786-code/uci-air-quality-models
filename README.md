# UCI Air Quality — Regression & Classification Models

**Project Deliverable 2** | UCI Air Quality dataset | Python / Google Colab

## Purpose
This project analyzes the cleaned UCI Air Quality dataset from Deliverable 1 and demonstrates two machine-learning methods: **regression** to predict a numerical NO2 ground-truth reading, and **classification** to predict whether the reading is at or above the median in the training set. The binary classification category is a *teaching example*, not an official air-quality threshold.

## Repository files

| Item | Purpose |
| --- | --- |
| `UCI_Air_Quality_Models_Colab.ipynb` | Runnable Python notebook, training/evaluation/graphs |
| `AirQualityUCI_clean.csv` | Cleaned input dataset from Deliverable 1; upload separately |
| `model_outputs/regression_actual_vs_predicted.png` | Regression plot generated in Colab |
| `model_outputs/classification_confusion_matrix.png` | Classification confusion matrix generated in Colab |
| `model_outputs/regression_feature_importance.png` | Feature importance plot generated in Colab |
| `model_outputs/model_predictions.csv` | Model predictions on the held-out data |
| `model_outputs/model_metrics.json` | Numerical performance statistics |
| `model_outputs/MODEL_RESULTS.md` | Full measured results and discussion |
| `requirements.txt` | Python packages |

## Dependencies
- Python 3.10+
- `numpy`, `pandas`, `matplotlib`, `scikit-learn`
- Google Colab for the easiest no-install execution

## How to run
1. Open https://colab.research.google.com/ and upload `UCI_Air_Quality_Models_Colab.ipynb` using **File → Upload notebook**.
2. Choose **Runtime → Run all**.
3. When prompted, select `AirQualityUCI_clean.csv` from your Downloads folder (the CLEAN dataset from Deliverable 1).
4. Let both models train and review the printed results/plots.
5. Download `UCI_Air_Quality_Model_Results.zip`, unzip it, and upload the `model_outputs` files to GitHub, together with the notebook, README, dependencies, and clean input CSV.

## Technical methodology
- Sort records by `DateTime`; exclude records with missing NO2 target.
- Eight features: five PT08 sensor readings plus T, RH, AH.
- Chronological 80% training / 20% held-out testing split.
- Impute missing features using the training-set median (inside each model pipeline).
- Train 120-tree Random Forest regression and classification models.
- For classification, use a target category determined by the median NO2 ground-truth value in the **training** observations; the same threshold is used for the test set.
- Report regression MAE, RMSE, R² and classification accuracy, precision, recall, F1, and confusion matrix.

## Outputs and interpretation
After running the notebook, see [`model_outputs/MODEL_RESULTS.md`](model_outputs/MODEL_RESULTS.md) for observed metrics, charts, and limitations. No model performance values are claimed before the full dataset has been processed.

## Limitations
The UCI data is historical and from a single monitoring location. Results do not establish general performance on other sites or years; missingness and changes over time can affect scores. The classification category is not a regulatory or health-related air-quality standard. Feature importance is associative, not causal.

## Dataset credit
Vito, S. (2008). *Air Quality* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C59K5F. License: CC BY 4.0.
