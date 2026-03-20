


## Why Regression ? 
Regression aims at predicting a *numerical target feature* based on another one or more numerical features 

	Example : Predict fuel consumption of a car based on the horse power


## 2.1 Ordinary Least Squares 

> How can we predict the value of a numerical feature **y** based on the value of another numerical feature **x** ?

1. Make Assumptions about their Relationship 
$$
\hat{y} = w_0 + w_1 x
$$
2. Our model thus assumes the Realtionship is linear 
3. How can we determine the coefficients $w_0$ and $w_1$ ? 

Here, $y$ is a *Dependent Feature* (Target), $w_0$ and $w_1$ are coefficients and $x$ is a Independent Variable 

### The Mean
The Mean is the average Set of Values 

### The Variance 
The Variance describes how spread out the values of a variable are around the mean 

### The Standard Deviation 
The Standard Deviation is the quare Root of the Variance.
Its in the Same Units as the Original Variable, making it easy to interpret

### The Covariance 
The Covariance is the statistical measure to indicate how two variables change together
Its shows whether a change in one variable corresponds to an increase or decrease in the other variable 

>Large ovariacne suggests that two features vary Jointly. 

>A positive value indicates that they tend to deviate from their respective mean in the same direction

>A negative value indicates that they tend to deviate
from their respective mean in opposite directions

### The Pearson Correlation Coefficient 
The **Pearson Correlation Coefficient** (often denoted as r) is a measure of the **strength and direction of the linear relationship** between two continuous variables.

### The Loss Function 

Loss function measures how well our model, for a specific choice of coefficients $w_0$ and $w_1$, describes the training data (i.e., how much we loose by using the model)


### The Residual
Residual for data point ($x_i$, $y_i$) measures how much the observed value $y_i$ differs from the prediction of our model

### Ordinary Least Squared 
Uses the sum of squared residuals, as a loss function 

### R2 Coefficient of Determination

The $R^2$ value, or **Coefficient of Determination**, is a key metric in **regression analysis**. It tells you how well your **model explains the variability** in the target variable $Y$.

It measures how well the determined regression line approximates the data, or put differently, how much of the variation observed in the data is explained by it







