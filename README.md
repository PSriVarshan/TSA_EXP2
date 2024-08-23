### Developed By : Sri Varshan P
### Register No. 212222240104
###  Date:

# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
Date:
### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

### ALGORITHM:
Import necessary libraries (NumPy, Matplotlib)

Load the dataset

Calculate the linear trend values using least square method

Calculate the polynomial trend values using least square method

End the program

### PROGRAM:

```py
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import PolynomialFeatures
import numpy as np
```
```py
data = pd.read_csv('/content/russia_losses_equipment.csv')
```

```py
data['date'] = pd.to_datetime(data['date'])
```

```py
X = np.array(data.index).reshape(-1, 1)
y = data['tank']
```

```py
linear_regressor = LinearRegression()
linear_regressor.fit(X, y)
y_pred_linear = linear_regressor.predict(X)
```

```py
poly = PolynomialFeatures(degree=2)
X_poly = poly.fit_transform(X)
```

```py
poly_regressor = LinearRegression()
poly_regressor.fit(X_poly, y)
y_pred_poly = poly_regressor.predict(X_poly)
```

```py
plt.figure(figsize=(35, 5))
plt.subplot(1,3,1)
plt.plot(data['date'], data['tank'], label='Tank Losses')
plt.xlabel('Date')
plt.ylabel('Tank Losses')
plt.title('Year-wise Tank Losses Over Time')
plt.grid(True)

plt.figure(figsize=(35, 5))
plt.subplot(1,3,2)
plt.plot(data['date'], y, label='Actual Tank Losses')
plt.plot(data['date'], y_pred_linear, color='red',linestyle='--', label='Linear Trend')
plt.xlabel('Date')
plt.ylabel('Tank Losses')
plt.title('Linear Trend Estimation for Tank Losses')
plt.legend()
plt.grid(True)


plt.figure(figsize=(35, 5))
plt.subplot(1,3,3)
plt.plot(data['date'], y, label='Actual Tank Losses')
plt.plot(data['date'], y_pred_poly, color='green',linestyle='--', label='Polynomial Trend (Degree 2)')
plt.xlabel('Date')
plt.ylabel('Tank Losses')
plt.title('Polynomial Trend Estimation for Tank Losses')
plt.legend()
plt.grid(True)
plt.show()
```
### OUTPUT

![image](https://github.com/user-attachments/assets/5b26ec37-1fe5-4e89-ab92-0585b48a7828)


A - LINEAR TREND ESTIMATION

![image](https://github.com/user-attachments/assets/ef9551cb-d0a4-4c2c-be1c-58ca9851d316)


B- POLYNOMIAL TREND ESTIMATION

![image](https://github.com/user-attachments/assets/ee63f555-d422-402f-a5e0-47195893ce05)


### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
