# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date : 22/9/2025

### AIM :
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM :
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
Name : Rehan Jeyan
Reg No : 212223040167
```
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the dataset
file_path = 'used_car_listings.csv'
data = pd.read_csv(file_path)

print("Column names in the dataset:", data.columns)

# --- Create a fake date index if no date column ---
# For example, assume monthly data:
date_index = pd.date_range(start='2020-01-01', periods=len(data), freq='M')

# Attach it to the dataframe
data.index = date_index

# Use the correct column for decomposition
series = data['price']  # not 'Price Today'

# Perform decomposition (adjust period as needed, e.g., 12 for yearly seasonality)
decomposition = seasonal_decompose(series, model='additive', period=12)

# Plotting the decomposition
plt.figure(figsize=(12, 8))
decomposition.plot()
plt.suptitle('Seasonal Decomposition of Price Series', fontsize=16)
plt.show()

# Display components
trend = decomposition.trend
seasonal = decomposition.seasonal
residual = decomposition.resid

print("Trend Component:")
print(trend.dropna().head())

print("\nSeasonal Component:")
print(seasonal.dropna().head())

print("\nResidual Component:")
print(residual.dropna().head())

```
### OUTPUT:
<img width="1189" height="790" alt="image" src="https://github.com/user-attachments/assets/5cc4ce1e-e8b7-4854-8a24-59c96cb22b4a" />



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
