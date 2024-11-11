NAME: DEEPIKA P
REG NO: 212223240024
# EX.NO.09        A project on Time series analysis on weather forecasting using ARIMA model 

### AIM:
To create a project on time series analysis for Daily Delhi Climate prediction using the ARIMA model in Python and evaluate its performance.

### ALGORITHM:
1. Explore the dataset of weather 
2. Check for stationarity of time series time series plot
   ACF plot and PACF plot
   ADF test
   Transform to stationary: differencing
3. Determine ARIMA models parameters p, q
4. Fit the ARIMA model
5. Make time series predictions
6. Auto-fit the ARIMA model
7. Evaluate model predictions
### PROGRAM:
import pandas as pd

# Load the dataset
file_path = '/mnt/data/DailyDelhiClimateTest.csv'\
data = pd.read_csv(file_path)

# Display the first few rows of the dataset
data.head()\
import matplotlib.pyplot as plt

# Convert 'date' column to datetime and set it as the index
data['date'] = pd.to_datetime(data['date'])\
data.set_index('date', inplace=True)

# Plot the 'meantemp' time series
plt.figure(figsize=(12, 6))\
plt.plot(data['meantemp'], color='blue')\
plt.title('Daily Mean Temperature in Delhi')\
plt.xlabel('Date')\
plt.ylabel('Mean Temperature (°C)')\
plt.show()\
from statsmodels.tsa.stattools import adfuller

# Perform the Augmented Dickey-Fuller test
adf_test = adfuller(data['meantemp'])\
adf_results = {\
    'ADF Statistic': adf_test[0],\
    'p-value': adf_test[1],]\
    'Critical Values': adf_test[4]\
}
adf_results\
data['meantemp_diff'] = data['meantemp'].diff().dropna()\
from statsmodels.tsa.stattools import adfuller\
adf_test_diff = adfuller(data['meantemp_diff'].dropna())\
print('ADF Statistic:', adf_test_diff[0])\
print('p-value:', adf_test_diff[1])\
# Apply first-order differencing to make the series stationary
data['meantemp_diff'] = data['meantemp'].diff().dropna()\

# Perform the ADF test again on the differenced series
adf_test_diff = adfuller(data['meantemp_diff'].dropna())\
adf_results_diff = {\
    'ADF Statistic': adf_test_diff[0],\
    'p-value': adf_test_diff[1],\
    'Critical Values': adf_test_diff[4]\
}
adf_results_diff\
train_size = int(len(df) * 0.8)\
train_data, test_data = df['Log_Close_diff'][:train_size], df['Log_Close_diff'][train_size:]

plt.figure(figsize=(10, 6))\
plt.plot(df['Close'])\
plt.title('Yahoo Stock Price')\
plt.xlabel('Date')\
plt.ylabel('Closing Price')\
plt.show()
### OUTPUT:

![Screenshot 2024-11-11 082227](https://github.com/user-attachments/assets/d17f50d6-c7ef-4315-be8c-523932ab63fd)
![Screenshot 2024-11-11 082034](https://github.com/user-attachments/assets/db656a67-b0e0-4471-a72b-31d680574f7c)
![Screenshot 2024-10-16 105106](https://github.com/user-attachments/assets/e8795dfa-3600-4c25-9e4c-12ac29042cd0)

### RESULT:
Thus the program run successfully based on the ARIMA model using python.
