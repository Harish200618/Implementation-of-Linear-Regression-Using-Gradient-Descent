# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
Algorithm for Linear Regression Model

Import Libraries: Import numpy, pandas, and StandardScaler from sklearn.preprocessing.

Read Data: Read '50_Startups.csv' into a DataFrame (data) using pd.read_csv().

Data Preparation:

Extract features (X) and target variable (y) from the DataFrame.
Convert features to a numpy array (x1) and target variable to a numpy array (y).
Scale the features using StandardScaler().
Linear Regression Function:

Define linear_regression(X1, y) function for linear regression.
Add a column of ones to features for the intercept term.
Initialize theta as a zero vector.
Implement gradient descent to update theta.
Model Training and Prediction:

Call linear_regression function with scaled features (x1_scaled) and target variable (y).
Prepare new data for prediction by scaling and reshaping.
Use the optimized theta to predict the output for new data.
Print Prediction:

Inverse transform the scaled prediction to get the actual predicted value.
Print the predicted value.

## Program:

/*
Program to implement the linear regression using gradient descent.
Developed by: HARISH.S
RegisterNumber: 212224240052
*/

Linear Regression Function
```
import numpy as np
import pandas as pd
from sklearn.preprocessing import StandardScaler
def linear_regression(X1,y,learning_rate=0.1,num_iters=1000):
    X=np.c_[np.ones(len(X1)),X1]

    theta=np.zeros(X.shape[1]).reshape(-1,1)

    for _ in range(num_iters):
        #calculate predictions
        predictions=(X).dot(theta).reshape(-1,1)

        #calculate errors
        errors=(predictions-y).reshape(-1,1)
        #Update theta using gradient descent
        theta-=learning_rate*(1/len(X1))*X.T.dot(errors)
    return theta
```
Read Data
```
data=pd.read_csv("/content/50_Startups.csv")
data.head()
```
Scaling
```
x=(data.iloc[1:,:-2].values)
x1=x.astype(float)

scaler=StandardScaler()
y=(data.iloc[1:,-1].values).reshape(-1,1)
x1_scaled=scaler.fit_transform(x1)
y1_scaled=scaler.fit_transform(y)
print(x)
print(x1_scaled)
```
Predicting
```
theta=linear_regression(x1_scaled,y1_scaled)
new_data=np.array([165349.2,136897.8,471784.1]).reshape(-1,1)
new_scaled=scaler.fit_transform(new_data)
prediction=np.dot(np.append(1,new_scaled),theta)
prediction=prediction.reshape(-1,1)
pre=scaler.inverse_transform(prediction)
print(prediction)
print(f"Predicted valeue: {pre}")
```


## Output:
![1ML](https://github.com/rohithprem18/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/146315115/9bf60fa0-af77-42cf-a31d-ea158d181abb)

![2ML](https://github.com/rohithprem18/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/146315115/3be61adc-d7e3-4d8c-97b4-3e0ac9547133)

![3ML](https://github.com/rohithprem18/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/146315115/c0b84bd5-3d9e-45f2-8f24-7908acecff74)

![4ML](https://github.com/rohithprem18/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/146315115/9d167518-03cc-4e2c-b206-93ac4cf31ba6)

![5ML](https://github.com/rohithprem18/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/146315115/9c78ef45-c44a-4873-8ff1-262becf88045)



## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
