NAME: DEEPIKA P\
REG NO: 212223240024
# EX.NO.09        A project on Time series analysis on weather forecasting using ARIMA model 

### AIM:
To Create a project on Time series analysis on forecasting using ARIMA model in  Python and compare with other models.

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
import pandas as pd\
import numpy as np\
import matplotlib.pyplot as plt\
from statsmodels.tsa.arima.model import ARIMA\
from sklearn.metrics import mean_squared_error

def arima_model(data, target_variable, order):\
    # Split data into training and testing sets (80% train, 20% test)
    train_size = int(len(data) * 0.8)\
    train_data, test_data = data[:train_size], data[train_size:]

    # Fit the ARIMA model on the training data
    model = ARIMA(train_data[target_variable], order=order)\
    fitted_model = model.fit()

    # Forecast for the length of the test data
    forecast = fitted_model.forecast(steps=len(test_data))

    # Calculate RMSE
    rmse = np.sqrt(mean_squared_error(test_data[target_variable], forecast))

    # Plot the results
    plt.figure(figsize=(10, 6))\
    plt.plot(train_data.index, train_data[target_variable], label='Training Data')\
    plt.plot(test_data.index, test_data[target_variable], label='Testing Data')\
    plt.plot(test_data.index, forecast, label='Forecasted Data', color='red')
    
    # Format the x-axis to show only the year
    plt.gca().xaxis.set_major_formatter(plt.matplotlib.dates.DateFormatter('%Y'))
    
    plt.xlabel('Year')\
    plt.ylabel(target_variable)\
    plt.title('ARIMA Forecasting for ' + target_variable)\
    plt.legend()\
    plt.show()

    # Print the RMSE value
    print("Root Mean Squared Error (RMSE):", rmse)

# Load the dataset
data = pd.read_csv('OnionTimeSeries - Sheet1.csv')

# Convert 'Date' to datetime and set it as the index
data['date'] = pd.to_datetime(data['Date'])\
data.set_index('date', inplace=True)

# Run the ARIMA model function with the specified target and order
arima_model(data, 'Min', order=(5, 1, 0))
### OUTPUT:

![Screenshot 2024-11-11 182524](https://github.com/user-attachments/assets/c9b500a2-8fe1-490d-9b7c-c9a122b68e97)

### RESULT:
Thus the program run successfully based on the ARIMA model using python.
