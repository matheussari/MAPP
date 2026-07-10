# MAPP - Military Aircraft Performance Prediction

MAPP is a data science project focused on predicting military aircraft performance using machine learning models and publicly available aircraft specification data.

## Version

Current version: **v1.1**

## Project Objective

The current objective is to predict the **combat radius** of military aircraft using supervised machine learning regression models.

Target variable: `Combat_Radius_km`

## Dataset

The dataset contains technical specifications of military fighter aircraft, including weight, speed, range, engine characteristics, radar information, combat record variables, and operational details.

Dataset source: Kaggle - Military Aircraft Dataset by OXCART.

## Version 1.0 Summary

Version 1.0 created the first machine learning pipeline for predicting `Combat_Radius_km`.

The following regression models were evaluated:

- K-Nearest Neighbors
- Support Vector Regression
- Decision Tree Regressor
- Random Forest Regressor
- XGBoost Regressor
- Multiple Linear Regression
- Lasso Regression
- Ridge Regression

In version 1.0, the best-performing model based on a single train-test split was:

**Random Forest Regressor**

Main v1.0 test metrics:

- RMSE Test: approximately 484 km
- MAE Test: approximately 356 km
- R2 Test: approximately 0.296

## Version 1.1 Update

Version 1.1 improves the evaluation process by adding:

- Baseline models
- Ferry Range Linear Baseline
- Feature set comparison
- Cross-validation
- More robust model comparison

The feature sets evaluated in v1.1 were:

- Engineering Only
- Engineering + Operational
- All Features

## Best Model in v1.1

Based on cross-validation RMSE, the best-performing model in version 1.1 was:

**XGBoost with the Engineering Only feature set**

Main v1.1 cross-validation metrics:

- RMSE CV Mean: approximately 365 km
- MAE CV Mean: approximately 276 km
- R2 CV Mean: approximately 0.356

## Main Findings

- The Ferry Range Linear Baseline performed better than simple mean and median baselines.
- `Ferry_Range_km` is a strong individual predictor of `Combat_Radius_km`.
- Engineering-only features produced the strongest model results.
- Using all available features did not improve performance and often made models less stable.
- XGBoost achieved the lowest cross-validation RMSE, but showed signs of overfitting.
- Random Forest remained a strong and more stable candidate model.

## Main Limitation

The dataset contains only 48 aircraft. Because of this, model performance should still be interpreted with caution, even with cross-validation.

## Next Steps

Future versions of MAPP may focus on:

- Expanding the dataset with more aircraft and verified sources
- Creating aviation-related engineered features
- Testing feature selection methods
- Applying light hyperparameter tuning
- Comparing model stability across repeated validation strategies

## Disclaimer

This project is for educational and portfolio purposes only. It uses publicly available data and does not represent classified, operational, or official military performance information.
