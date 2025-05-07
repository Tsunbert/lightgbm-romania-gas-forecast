# Natural Gas Consumption Forecasting Using LightGBM

This project presents a time series forecasting model for Romania's monthly inland natural gas consumption. Utilizing the LightGBM gradient boosting framework, the model incorporates seasonality and various exogenous factors to generate accurate predictions. This research was accepted, presented at the International Conference on Business and Economics (ICBE) 2025 (Data Science section), and is currently awaiting publication in the conference proceedings.

## Project Overview

The analysis pipeline includes:
- Data preprocessing and time series feature engineering
- Model training and hyperparameter optimization using Bayesian search
- Feature selection using recursive feature elimination
- Model validation through backtesting
- Prediction intervals using bootstrapping
- Model interpretability using SHAP values

## Data 

The model uses:
- Monthly natural gas consumption data (`raw_data.csv`)
- Exogenous variables (`exog_data.csv`) including:
  - COVID-19 impact indicator
  - European Energy Crisis indicator  
  - Russian-Ukraine Conflict indicator

Data is split into:
- Training set: Up to December 2019
- Validation set: January 2020 - August 2022 
- Test set: After August 2022

## Model Architecture

The forecasting model uses:
- LightGBM regressor as the base model
- Recursive multi-step forecasting strategy
- Rolling window features (means and standard deviations)
- First-order differencing for stationarity
- 12 months of lagged values as features

## Feature Engineering

The model incorporates:
- Lagged values of the target variable
- Rolling statistics (mean, std) with different window sizes (3, 6, 12 months)
- External regressors capturing major market events

## Model Evaluation

Performance metrics include:
- Mean Absolute Error (MAE)
- Mean Absolute Percentage Error (MAPE)
- Root Mean Squared Scaled Error (RMSSE)

## Model Interpretability

The analysis includes:
- Feature importance analysis
- SHAP (SHapley Additive exPlanations) values
- Decision tree visualization
- Residual analysis

## Results

The model provides:
- Point forecasts up to 36 months ahead
- Confidence intervals through bootstrapping
- Quantile predictions (5%, 25%, 50%, 75%, 95%)
- Visual analysis of predictions vs actual values

## Dependencies

- lightgbm
- skforecast
- scikit-learn
- pandas
- numpy
- matplotlib
- plotly
- shap

## Usage

The notebook is structured to be run sequentially, with each section building on previous results. Make sure to modify file paths to match your local environment before running.

## Notes

This implementation includes careful handling of:
- Seasonality in gas consumption
- External shocks
- Model validation through multiple approaches
- Uncertainty quantification in predictions