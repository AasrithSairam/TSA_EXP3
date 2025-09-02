# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 02-09-2025
### NAME: Ponguru Aasrith Sairam
### REGISTER NUMBER: 212223240116
### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import pandas, numpy, matplotlib.
2. Load CSV and extract 'High' values.
3. Compute mean and variance.
4. Calculate autocorrelation for each lag and store in a list.
5. Plot lag vs. autocorrelation using a stem graph.
### PROGRAM:
```PYTHON
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load CSV
file_path = "TSLA.csv"
df = pd.read_csv(file_path)

# Ensure Date is parsed (optional)
df['Date'] = pd.to_datetime(df['Date'])

# Use 'High' column
data = df['High'].values
lags = range(35)

autocorr_values = []
mean_data = np.mean(data)
variance_data = np.var(data)
N = len(data)

for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)

# Plot
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)   # <-- fixed line
plt.axhline(y=0, color='r', linestyle='-')
plt.title('Autocorrelation of Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()

```
### OUTPUT:

<img width="846" height="547" alt="image" src="https://github.com/user-attachments/assets/a1781cca-0f58-4cee-a0ec-f59f99575574" />



### RESULT:
Thus we have successfully implemented the auto correlation function in python.
