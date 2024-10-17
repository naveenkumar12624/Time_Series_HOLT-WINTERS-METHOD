# Ex.No: 6 HOLT WINTERS METHOD

## Date:
## Developed by : Naveen Kumar S
## Register Number : 212221240033

## AIM:
To analyze walmart sales dataset using the Holt-Winters exponential smoothing method.
## ALGORITHM:

1.Select Relevant Data: Import Required Libraries and Extract the relevant column for forecasting, typically 'Adj Close' or a similar column that reflects the values you wish to forecast from the DataFrame.

2.Data Resampling: Resample the extracted time series data to a monthly frequency, aggregating the values to calculate the mean for each month, which helps in smoothing out daily fluctuations.

3.Fit Holt-Winters Model: Initialize and fit the Holt-Winters Exponential Smoothing model to the resampled monthly data, specifying the seasonal type (additive or multiplicative) and setting the seasonal period (e.g., 12 for monthly data).

4.Make Future Predictions: Define the number of future periods you wish to forecast (e.g., 12 months) and generate forecast values using the fitted Holt-Winters model, which captures the underlying trends and seasonality in the data.

5.Plot Results: Create a visualization that includes the original resampled data along with the forecasted values, ensuring to clearly differentiate between historical data and the predicted future values for better interpretation and analysis.

## PROGRAM:
```py
# Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.holtwinters import ExponentialSmoothing

# Load Nvidia CSV file into DataFrame
df = pd.read_csv('C:/Users/lenovo/Downloads/archive (2)/NVIDIA/NvidiaStockPrice.csv', parse_dates=['Date'], index_col='Date')

# Select the 'Adj Close' column for time series analysis
adj_close_data = df['Adj Close']

# Group the data by date and resample it to a monthly frequency
monthly_data = adj_close_data.resample('M').mean()

# Fit Holt-Winters model to the monthly dataset
holt_winters_model = ExponentialSmoothing(monthly_data, seasonal='additive', seasonal_periods=50)
holt_winters_fit = holt_winters_model.fit()

# Make future predictions (next 12 months)
future_months = 48
forecast = holt_winters_fit.forecast(future_months)

# Create a date range for the forecast
future_index = pd.date_range(start=monthly_data.index[-1] + pd.DateOffset(months=1), periods=future_months, freq='M')

# Plot original adjusted close data and Holt-Winters forecast
plt.figure(figsize=(12, 6))
plt.plot(monthly_data, label='Original Monthly Adjusted Close', color='blue')
plt.plot(future_index, forecast, label='Holt-Winters Forecast', color='orange')
plt.title('Holt-Winters Forecasting of Adjusted Close Prices')
plt.xlabel('Date')
plt.ylabel('Adjusted Close Price')
plt.legend()
plt.show()
```
## OUTPUT:
![download](https://github.com/user-attachments/assets/5fc70ea0-4813-4998-ab6e-73344b726021)

## RESULT:
Thus the program run successfully based on the Holt Winters Method model.
