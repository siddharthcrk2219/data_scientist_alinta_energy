# data_scientist_alinta_energy
Project Overview

This project investigates the use of machine learning to forecast electricity demand in the Australian energy sector. The project is developed in the context of a Data Scientist role in the energy industry, where predictive modelling can support demand planning, data-driven decision-making, and commercial strategies.

Two machine learning regression algorithms are implemented and compared:

Gradient Boosting Machine (GBM)
Multi-Layer Perceptron (MLP) Regressor

The models use weather, calendar, and historical demand features to forecast electricity demand.

Objectives

The main objectives of this project are to:

Analyse publicly available Australian energy data.
Prepare and integrate relevant energy-demand data.
Develop features suitable for electricity demand forecasting.
Apply two machine learning regression algorithms.
Compare the predictive performance of GBM and MLP.
Identify important factors associated with electricity demand.
Evaluate the models using appropriate forecasting metrics.
Datasets
Australian Energy Statistics (AES)

The Australian Energy Statistics dataset provides historical information about Australian energy consumption, production, and energy use across different sectors and fuel types.

Source:
https://www.energy.gov.au/government-priorities/energy-data/australian-energy-statistics

Australian Energy Market Operator (AEMO)

AEMO provides publicly available electricity-market data for Australia's National Electricity Market, including electricity demand and other electricity-market information.

Source:
http://nemweb.com.au

The datasets were selected because they are relevant to the energy-sector Data Scientist role, particularly for understanding energy consumption patterns and developing electricity demand forecasting models.

Methodology

The analysis follows a time-series forecasting workflow:

Load the Australian Energy Statistics and AEMO datasets.
Convert date fields to datetime format.
Sort the observations chronologically.
Integrate the relevant data.
Create lagged demand features.
Handle missing observations.
Define the predictor variables and demand target.
Split the data chronologically into training and testing sets.
Standardise the features for the MLP model.
Train the Gradient Boosting Machine.
Train the Multi-Layer Perceptron.
Evaluate both models using RMSE and MAPE.
Analyse GBM feature importance.
Analyse prediction and residual behaviour.

The temporal order of the observations is preserved throughout the forecasting process to reduce the risk of using future information to predict past observations.

Features

The models use the following predictor variables:

temperature
day_of_week
month
is_weekend
demand_lag_1
demand_lag_3
demand_lag_7
Target Variable
demand — electricity demand measured in MW.

The lagged demand variables provide historical information that allows the models to capture temporal patterns in electricity consumption.

Machine Learning Models
Gradient Boosting Machine (GBM)

Gradient Boosting is an ensemble learning method that sequentially builds decision trees, with each subsequent tree attempting to reduce the errors of the preceding trees.

GBM was selected because it can model nonlinear relationships and provides feature-importance information that helps interpret the factors contributing to the predictions.

Multi-Layer Perceptron (MLP)

The Multi-Layer Perceptron is a feedforward neural network capable of modelling nonlinear relationships between input features and the target variable.

MLP was selected because it provides a different modelling approach from the tree-based GBM and can capture nonlinear interactions between weather, calendar, and historical demand features.

Train-Test Strategy

The data was divided chronologically into:

80% training data
20% testing data

The temporal order of observations was preserved rather than randomly shuffling the dataset. This approach is appropriate for time-series forecasting because future observations should not be used to train a model that is evaluated on earlier observations.

Time-series splits were also examined to preserve temporal ordering during model validation.

Evaluation Metrics
Root Mean Squared Error (RMSE)

RMSE measures the magnitude of prediction errors while giving greater weight to larger errors.

A lower RMSE indicates better predictive performance.

RMSE is appropriate for energy demand forecasting because large forecasting errors can be particularly important when planning electricity demand and supply.

Mean Absolute Percentage Error (MAPE)

MAPE expresses prediction error as a percentage of the actual demand.

A lower MAPE indicates better forecasting accuracy.

MAPE is useful because percentage-based results are relatively straightforward to interpret and communicate.

Results

The final test-set results were:

Model	RMSE (MW)	MAPE
Gradient Boosting Machine	78.4	5.1%
Multi-Layer Perceptron (MLP)	78.2	5.0%
Interpretation

The MLP achieved slightly better performance than the GBM on both evaluation metrics.

MLP RMSE: 78.2 MW
GBM RMSE: 78.4 MW
MLP MAPE: 5.0%
GBM MAPE: 5.1%

The difference between the models is small. Therefore, both models demonstrated very similar predictive performance for this forecasting task.

The MLP provided a marginal improvement in predictive accuracy, while GBM provides the additional advantage of feature importance and greater interpretability.

Analysis and Insights

The models were used to investigate patterns associated with electricity demand.

The GBM model provides interpretable information about the relative importance of the input features, while the MLP provides a flexible nonlinear modelling approach.

The analysis focuses on:

Seasonal demand patterns
Weekly demand patterns
Temperature-related demand variation
The relationship between current and historical demand
Differences in predictive performance between GBM and MLP

The two models therefore provide complementary perspectives: GBM supports interpretation of feature importance, while MLP provides a flexible nonlinear modelling approach.
