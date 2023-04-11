# Time-Series-Analysis


Project Title: 
Air Passengers Forecasting Using SARIMAX
This project focuses on predicting the number of future air passengers by analyzing time-series data. The project involves data preprocessing and exploratory analysis to identify trends, seasonal patterns, and stationarity in the dataset. The ultimate goal is to build a SARIMAX model that can accurately predict the number of future air passengers.

Installation:
To run this project, you will need to have the following dependencies installed:

Python 3.x
NumPy
Pandas
Matplotlib
Statsmodels

Data Preprocessing and Exploratory Analysis:
The first step in the project is to preprocess the data and perform exploratory analysis. This includes plotting all columns (number of passengers) in the DataFrame against the DataFrame's index, which in this case is the 'Month' column. We then decompose the time series by both additive and multiplicative models to identify trends and seasonal patterns. We check stationarity in the dataset by performing ADF, apply log transformation to remove multiplicative seasonality, and take the first difference to remove trend and make the data stationary. However, the ADF test result was not in favor, so we remove seasonality using second-order differencing. We apply a seasonal differencing of 12 periods followed by a first-order difference to the original time series, which results in a new differenced series. The stationary data is stored in a pandas dataframe called 'diff_seasonal' and studied through time series plot. We also perform an auto-correlation plot.

SARIMAX Modeling:
We build the SARIMAX model by importing two time series models, ARIMA and SARIMAX, from the statsmodels library. We create a NumPy array 'x' containing the differenced values of data ts_df and split the numpy array into training and testing datasets. We then perform a grid search over all combinations of p, d, and q values using a SARIMAX model. We try to fit a SARIMAX model to the training data for each combination of p, d, and q values, and then evaluate the resulting model by computing its RMSE on the test data. However, we did not achieve any good fit or result, so we increase the range of (P,D,Q) and perform the same steps as above. We introduce the seasonal_order parameter to (0, 0, 0, 12, 'A'), which means that there is a seasonal component with a period of 12 (i.e., the data has a yearly seasonality) and the seasonal data is assumed to be additive (as denoted by the 'A' argument). We use Sarimax for p,d,q = 1,1,1 and seasonality = 12 and make predictions for the testing set using the fitted model.

Model Evaluation:
We evaluate the model's performance by calculating various metrics such as RMSE, MAE, MSE, and R2. We also perform a grid search over a defined range of parameter values to find the SARIMAX model with the lowest Akaike Information Criterion (AIC). We use the itertools.product() function to generate all possible combinations of the SARIMAX parameters, and then fit a SARIMAX model for each combination. If a model is successfully fit, its AIC value is calculated, and the model's parameters are compared to the current best model's parameters. If the current model has a lower AIC value, it is considered the new best model.

Overall, this project showcases the use of time series analysis and modeling techniques to predict future air passenger traffic.
