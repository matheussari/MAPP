# MAPP - Military Aircraft Performance Prediction

MAPP is a long-term Data Science project focused on analyzing and predicting military aircraft performance using machine learning and publicly available aircraft specification data.

## Current Version

**MAPP v1.2 - Feature Engineering, Model Tuning and Stability**

The current prediction target is:

`Combat_Radius_km`

The project currently uses a dataset containing 48 military aircraft and 45 variables.

## Project Evolution

### Version 1.0 - Initial Modeling

Version 1.0 created the first machine learning workflow for combat radius prediction.

The following regression models were evaluated:

- K-Nearest Neighbors
- Support Vector Regression
- Decision Tree Regressor
- Random Forest Regressor
- XGBoost Regressor
- Multiple Linear Regression
- Lasso Regression
- Ridge Regression

Random Forest achieved the best result using a single train-test split.

### Version 1.1 - Validation and Baselines

Version 1.1 improved model evaluation by introducing:

- Mean and median baseline models
- Ferry Range Linear baseline
- Feature set comparison
- Cross-validation
- Training and validation performance comparison

XGBoost with the Engineering Only feature set achieved the best average cross-validation RMSE, but showed strong signs of overfitting.

### Version 1.2 - Feature Engineering, Tuning and Interpretation

Version 1.2 introduced:

- Independent version setup
- Data quality audit
- Aviation-related feature engineering
- Repeated cross-validation
- Derived feature comparison
- Controlled hyperparameter tuning
- Model stability analysis
- Feature importance
- Repeated out-of-fold predictions
- Aircraft-level error analysis
- Interactive Plotly visualizations

## Feature Engineering

Seven derived engineering features were created:

- `Weight_Ratio`
- `Fuel_Fraction`
- `Weapon_Load_Fraction`
- `Total_Thrust_kN`
- `Thrust_to_Weight_Ratio_Approx`
- `Ferry_Range_per_Fuel_kg`
- `Development_Time_years`

The Derived Only feature set was not sufficient to outperform the original engineering variables.

However, derived features improved performance when combined with the original specifications.

For Random Forest, `Weight_Ratio` and `Ferry_Range_per_Fuel_kg` were the most useful derived features during feature removal comparison.

## Validation Strategy

Version 1.2 uses repeated cross-validation:

- 5 folds
- 10 repetitions
- 50 validation results per experiment

The main evaluation metrics are:

- Root Mean Squared Error (RMSE)
- Mean Absolute Error (MAE)
- Coefficient of Determination (R²)
- Metric standard deviation
- Training-validation performance gap

## Baseline

The strongest baseline was a linear regression using only `Ferry_Range_km`.

Baseline results:

- RMSE CV Mean: approximately 424 km
- MAE CV Mean: approximately 361 km
- R² CV Mean: approximately 0.05

## Final Model

The final selected model for MAPP v1.2 was:

**Tuned XGBoost with Engineering + Derived features**

Final repeated cross-validation results:

- RMSE CV Mean: approximately **350 km**
- RMSE CV Standard Deviation: approximately **86 km**
- MAE CV Mean: approximately **294 km**
- R² CV Mean: approximately **0.385**
- Training R² CV Mean: approximately **0.886**

Compared with the Ferry Range Linear baseline, Tuned XGBoost reduced average RMSE by approximately:

- **74 km**
- **17.5%**

Hyperparameter tuning also substantially reduced the XGBoost training-validation gap.

## Main Feature Importance Findings

The most important variables for Tuned XGBoost included:

- `Ferry_Range_km`
- `Cruise_Speed_kmh`
- `Empty_Weight_kg`
- `Fuel_Consumption_Cruise_kg_h`
- `Ferry_Range_per_Fuel_kg`
- `MTOW_kg`

The derived feature `Ferry_Range_per_Fuel_kg` appeared among the five most important variables.

Feature importance does not represent causality, and correlated features may share importance.

## Aircraft-Level Error Analysis

Repeated out-of-fold evaluation generated 10 predictions for each aircraft, resulting in 480 predictions.

Some of the lowest mean absolute percentage errors were achieved for:

- J-16 Flanker: approximately 3.4%
- F-35A Lightning II: approximately 4.4%
- MiG-35 Fulcrum-F: approximately 6.2%
- Su-27 Flanker: approximately 7.7%

The model performed better within the central range represented in the dataset.

It tended to:

- Underestimate aircraft with unusually high combat radius values
- Overestimate several aircraft with relatively low combat radius values

## Main Limitations

- The dataset contains only 48 aircraft.
- Some specifications may be estimated, unavailable, or classified.
- Model development and evaluation use the same small dataset.
- No independent external test dataset is currently available.
- Related aircraft variants may appear in both training and validation folds.
- Derived engineering features are approximations.
- Results should be interpreted as exploratory.

The model should not be used for operational, engineering, or military decision-making.

## Future Development

Future versions of MAPP may focus on:

- Expanding the dataset
- Recording data sources and confidence levels
- Separating unknown values from valid zeros
- Creating aircraft family labels
- Applying grouped validation by aircraft family
- Evaluating additional prediction targets
- Reorganizing the project into reusable modules

Deep Learning is not recommended for the current tabular dataset due to its limited number of observations.

Future Deep Learning applications may use different data modalities, such as aircraft image classification with transfer learning.

## Dataset

Dataset source:

**Military Aircraft Dataset by OXCART - Kaggle**

The dataset contains aircraft specifications related to:

- Speed
- Range
- Weight
- Engines
- Fuel
- Weapons
- Radar
- Cost
- Operational status
- Combat record

## Repository Files

- `military_aircraft_performance_prediction.ipynb` - Complete analysis through MAPP v1.2
- `fighter_aircraft_dataset_v10.csv` - Aircraft dataset
- `README.md` - Project documentation

## Disclaimer

This project is intended for educational and portfolio purposes only.

It uses publicly available data and does not represent classified, operational, official, or guaranteed military aircraft performance information.
