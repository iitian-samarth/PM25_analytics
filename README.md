# PM25_analytics
AirCast is a machine learning project for PM2.5 air pollution prediction using multi-station air quality and meteorological data. It explores data analysis, feature engineering, regression models, time-series validation, and model evaluation to understand pollution patterns and improve predictive performance.
# 🌫️ AirCast: Predicting Urban Air Quality Using Machine Learning

AirCast is a machine learning project focused on predicting **PM2.5 concentrations** using historical air-quality and meteorological data. The project explores pollution patterns, develops regression models, and evaluates their ability to predict particulate matter concentrations across multiple monitoring stations.

## Objectives

* Explore air-quality data and identify patterns in PM2.5 concentrations.
* Perform data cleaning, missing-value treatment, and outlier analysis.
* Engineer meaningful temporal and seasonal features.
* Train and compare multiple regression models.
* Evaluate model performance using chronological validation.
* Investigate prediction errors, particularly during high-pollution periods.

## Dataset

The project uses the **Beijing Multi-Site Air-Quality Dataset**, containing hourly air-quality and meteorological observations from multiple monitoring stations.

The dataset includes variables such as:

* PM2.5 and other pollutant measurements
* Temperature and dew point
* Atmospheric pressure
* Wind speed and direction
* Rainfall
* Date, time, and monitoring-station information

**Target variable:** PM2.5 concentration.

## Methodology

The project follows a structured machine learning workflow:

1. **Exploratory Data Analysis:** Statistical summaries, distribution plots, correlation analysis, and temporal visualizations.
2. **Data Preprocessing:** Missing-value imputation, categorical encoding, and numerical feature scaling.
3. **Outlier Analysis:** Comparison of Interquartile Range (IQR) and Z-score methods.
4. **Feature Engineering:** Cyclical encoding of hour and month, day-of-week features, and a heating-season indicator.
5. **Model Development:** Training and comparison of multiple regression algorithms.
6. **Model Evaluation:** Chronological train-validation-test splitting and evaluation using MAE, RMSE, and R².
7. **Error Analysis:** Residual analysis, permutation feature importance, and investigation of performance across different pollution levels.

## Models Implemented

* Linear Regression
* Ridge Regression
* Lasso Regression
* Decision Tree Regressor
* Random Forest Regressor

A mean-only baseline is also used to assess whether the models provide meaningful predictive improvements.

## Results

Performance on the held-out test set:

| Model              |   MAE |  RMSE |     R² |
| ------------------ | ----: | ----: | -----: |
| Linear Regression  | 47.33 | 65.46 |  0.374 |
| Ridge Regression   | 47.33 | 65.46 |  0.374 |
| Lasso Regression   | 47.29 | 65.51 |  0.373 |
| Decision Tree      | 46.67 | 66.76 |  0.349 |
| Random Forest      | 46.17 | 66.93 |  0.346 |
| Mean-only Baseline | 61.24 | 82.94 | -0.005 |

Linear Regression was selected based on validation RMSE. Although Random Forest achieved a slightly lower test MAE, Linear Regression performed better on test RMSE and explained a larger proportion of the target's variance.

The results demonstrate improvement over the mean-only baseline, while also highlighting the difficulty of accurately predicting extreme pollution events.

## Tech Stack

* **Language:** Python
* **Data Processing:** Pandas, NumPy
* **Visualization:** Matplotlib
* **Machine Learning:** Scikit-learn
* **Environment:** Jupyter Notebook

## Getting Started

1. Clone this repository.

2. Install the required libraries:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn scipy jupyter
   ```

3. Download the Beijing Multi-Site Air-Quality Dataset and configure the notebook's dataset paths.

4. Open the notebook in Jupyter or Google Colab.

5. Run the analysis and model evaluation cells.

> **Note:** Dataset paths may need to be updated for your local environment. Ensure all notebook cells execute successfully before reproducing the reported results.

## Key Findings

* Meteorological and seasonal features provide useful predictive information.
* Chronological validation provides a more appropriate evaluation for time-ordered observations than a randomly shuffled split.
* Linear Regression provides competitive performance despite its simplicity.
* Prediction errors increase substantially at very high PM2.5 concentrations, revealing a weakness in the current modelling approach.

## Limitations

* Predictive performance remains limited, particularly during extreme pollution events.
* The current feature set does not include lagged or rolling PM2.5 measurements.
* The analysis uses historical data from Beijing, so the results may not generalize directly to other cities.
* The models identify predictive associations, not causal relationships.

## Future Improvements

* Engineer lagged and rolling-window PM2.5 features.
* Perform systematic hyperparameter optimization.
* Investigate methods for reducing errors during high-pollution periods.
* Evaluate alternative target transformations and model configurations.
* Improve reproducibility and document the dataset source and experimental setup.

---

**AirCast** — Exploring air pollution patterns and machine learning-based PM2.5 prediction.
