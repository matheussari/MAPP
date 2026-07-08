# MAPP - Military Aircraft Performance Prediction

MAPP is a data science project focused on predicting military aircraft performance using machine learning models and publicly available aircraft specification data.

## Version

Current version: **v1.0**

## Project Objective

The objective of version 1.0 is to predict the **combat radius** of military aircraft using supervised machine learning regression models.

Target variable: `Combat_Radius_km`

## Dataset

The dataset contains technical specifications of military fighter aircraft, including weight, speed, range, engine characteristics, radar information, combat record variables, and operational details.

Dataset source: Kaggle - Military Aircraft Dataset by OXCART.

## Models Tested

Version 1.0 evaluates the following regression models:

- K-Nearest Neighbors
- Support Vector Regression
- Decision Tree Regressor
- Random Forest Regressor
- XGBoost Regressor
- Multiple Linear Regression
- Lasso Regression
- Ridge Regression

## Best Model in v1.0

Based on the test RMSE, the best-performing model in version 1.0 was: **Random Forest Regressor**

Main test metrics:

- RMSE Test: approximately 484 km
- MAE Test: approximately 356 km
- R2 Test: approximately 0.296

## Main Limitation

Version 1.0 uses a single train-test split on a small dataset of 48 aircraft. Because of this, model performance should be interpreted with caution.

## Next Version

Version 1.1 will improve the evaluation process by adding:

- Baseline models
- Cross-validation
- Feature set comparison
- Redundancy control
- More robust model comparison

## Disclaimer

This project is for educational and portfolio purposes only. It uses publicly available data and does not represent classified, operational, or official military performance information.
