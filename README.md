### Developed by Vaishnav Nanda
### Reg.no: 212222240112
### Date: 
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION

### AIM:
To Illustrates how to perform time series analysis and decomposition on the Meta Stock price predictions

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose


df = pd.read_csv('NVIDIA_stock.csv') 

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
#### FIRST FIVE ROWS:
![image](https://github.com/user-attachments/assets/546b2835-f0f4-48a9-87b8-ef100cc35c5f)



#### PLOTTING THE DATA:

![image](https://github.com/user-attachments/assets/fdcf2eff-0f43-4d1a-bfc5-effa68bb29d3)


#### SEASONAL PLOT REPRESENTATION :


![image](https://github.com/user-attachments/assets/82596b2e-4c56-439a-83c9-e70caa151c4d)

#### TREND PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/31add1b6-6c83-43b7-b0c4-3e254e51bc7c)



#### OVERAL REPRESENTATION:

![image](https://github.com/user-attachments/assets/2c4c3e17-e2c7-41cf-9712-a4e777ab1d6e)


### RESULT:
Thus the python code for the time series analysis and decomposition was created successfully.
