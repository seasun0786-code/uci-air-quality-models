# Model results — UCI Air Quality

## Project purpose
Analyze the cleaned historical UCI Air Quality dataset with a numeric prediction model (regression)
and a binary category model (classification).

## Dataset and approach
- Source: https://archive.ics.uci.edu/dataset/360/air+quality
- Input file: `AirQualityUCI_clean.csv`
- Rows in cleaned input: 9,357
- Rows usable after excluding missing targets/dates: 7,715
- Chronological split: 6,172 train / 1,543 test (first 80% / last 20%)
- Training dates: 2004-03-10 18:00:00 to 2005-01-28 10:00:00
- Testing dates: 2005-01-28 11:00:00 to 2005-04-04 14:00:00
- Predictors: PT08.S1(CO), PT08.S2(NMHC), PT08.S3(NOx), PT08.S4(NO2), PT08.S5(O3), T, RH, AH
- Missing feature values filled using medians learned from training only
- Models: RandomForestRegressor and RandomForestClassifier, 120 trees each

## Regression (predict numerical NO2(GT))
- Mean Absolute Error (MAE): 26.1022
- Root Mean Squared Error (RMSE): 37.6267
- R²: 0.5127

## Classification (categorize NO2(GT))
- Category 1: at or above training median (102.00 dataset units)
- Category 0: below training median
- Accuracy: 0.8963
- Precision: 0.9617
- Recall: 0.9023
- F1: 0.9310
- Confusion matrix, actual rows / predicted columns: [[303, 43], [117, 1080]]

## Generated outputs
- `regression_actual_vs_predicted.png`: comparison of observed/predicted test values
- `classification_confusion_matrix.png`: correct versus incorrect category predictions
- `regression_feature_importance.png`: model's relative predictor importance
- `model_predictions.csv`: each held-out observation's actual and predicted values/classes
- `model_metrics.json`: machine-readable score summary

## Interpretation and limitations
The regression errors describe deviations between predicted and observed NO2 measurements.
Classification metrics describe agreement with a category defined from **the training median**.
This category is for demonstration only, not a regulatory air-quality or health threshold.
The dataset comes from one historical monitoring location, so performance may not generalize to
other places, periods, or sensors. Some predictors and targets are missing; exclusion and
imputation can affect the evaluation. Random Forest feature importance is not evidence of causality.
The chronological holdout tests later observations but does not replace external validation.

## Source citation
Vito, S. (2008). *Air Quality* [Dataset]. UCI Machine Learning Repository.
https://doi.org/10.24432/C59K5F (CC BY 4.0).
