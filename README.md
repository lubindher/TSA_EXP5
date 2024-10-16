# NAME: LUBINDHER S
# REG NO: 212222240056
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the NVIDIA Stock Pice dataset.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose


df = pd.read_csv('Meta_stock.csv') 

print(df.head())

df['Date'] = pd.to_datetime(df['Date'])
df.set_index('Date', inplace=True)

stock_data = df['Open']

new_index = pd.date_range(start=stock_data.index.min(), periods=len(stock_data), freq='B')[:len(stock_data)]
stock_data.index = new_index

decomposition = seasonal_decompose(stock_data, model='additive', period=30) 

trend = decomposition.trend
seasonal = decomposition.seasonal
residuals = decomposition.resid

plt.figure(figsize=(12, 6))
plt.plot(stock_data, label='Original Stock Prices')
plt.title('Original Stock Prices')
plt.legend()
plt.show()

plt.figure(figsize=(12, 6))
plt.plot(seasonal, label='Seasonal Component', color='orange')
plt.title('Seasonal Component')
plt.legend()
plt.show()

plt.figure(figsize=(12, 6))
plt.plot(trend, label='Trend Component', color='green')
plt.title('Trend Component')
plt.legend()
plt.show()

plt.plot(residuals, label='Residuals', color='red')
plt.legend(loc='best')
plt.tight_layout()
plt.show()

```

### OUTPUT:
# Original Time Series
![image](https://github.com/user-attachments/assets/db7c49d4-8df9-449a-b72a-5665dbd0180a)
# Trend Component
![image](https://github.com/user-attachments/assets/69e32470-2ece-4f85-8359-a54d6817458a)
# Seasonal Component
![image](https://github.com/user-attachments/assets/b354e4a4-aa12-443a-80d8-dfbb264bfa9d)
# Residual Component
![image](https://github.com/user-attachments/assets/d8244af5-432d-42b6-9a91-dd33bb1a897a)




### RESULT:
Thus, the python code for the time series analysis and decomposition on NVIDIA Stock Pice dataset is Executed.
