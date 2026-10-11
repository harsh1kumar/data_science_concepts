# Assumptions of Linear Regression

## Assumptions

| Related to Observations | Independence |
| --- | --- |
| Related to Independent Variables | Linearity |
| Related to Independent Variables | No Perfect Multicollinearity |
| Related to Residuals | Normality of Residuals |
| Related to Residuals | Homoscedasticity |
| Related to Residuals | No Autocorrelation of Residuals |
1. **Independence:** Observations should be independent of each other. In other words, the value of the dependent variable for one observation should not be influenced by the values of the other observations
2. **Linearity:** The relationship between the independent and dependent variables is assumed to be linear.
3. **No Perfect Multicollinearity:** Independent variables are not correlated with each other. There can’t be a linear relationship between a variable and a group of variables
4. **Normality of Residuals:** Residuals are assumed to be normally distributed. This assumption is important for hypothesis testing and confidence interval estimation.
5. **Homoscedasticity:** Residuals have constant variance across all values of the independent variables.
6. **No Autocorrelation of Residuals:** Residuals do not exhibit patterns or correlations over time. Residuals are independent of each other

## **Consequences of Violation**

1. Independence: Biased standard errors affecting the reliability of hypothesis tests and confidence intervals
2. Linearity: Coefficients are not accurately estimated, thus inaccurate predictions
3. No Perfect Multicollinearity: Imprecise coefficient estimates
4. Normality of Residuals: Accuracy of hypothesis tests and confidence intervals impacted

## **Detection**

### 1. Independence

### 2. Linearity

Scatter plots 

### 3. No Perfect Multicollinearity

1. **Correlation** between all features
2. **Variance Inflation Factor (VIF)**: The larger the value of VIF, the more correlated the variable is with other regressors. If there is no collinearity between two variables, VIF will be 1.
    
    It is calculated by taking a predictor and regressing it against every other predictor in the model. This gives the R² value which is then used in the VIF formula.
    
    Usually a variable with VIF greater than 10 is considered to be troublesome, some people consider value above 5 to be problematic
    
    $$
    VIF = \frac{1}{1-R^2}
    $$
    

### **4. Normality of residuals**

1. **KDE (Histogram) plot** of residuals
2. **Quantile-Quantile (q-q) plot**: Compares the quantiles of the observed data with the quantiles of a normal distribution. If the data is normally distributed, the points will fall on a straight diagonal line

### **5. Homoscedasticity**

1. **Scatter plot** of residuals vs predictors
2. **Breusch-pagan test:** 
    
    Ho: Error variances are equal (Homoscedasticity)
    
    Ha: Error variances are not equal (Heteroscedasticity)
    

### **6. No autocorrelation of residuals**

**Durbin Watson Test**: The value of the statistic will lie between 0 to 4. Values between 0 and 2 indicating positive autocorrelation, 2 indicating zero autocorrelation, and values between 2 and 4 indicating negative autocorrelation

Ho : No autocorrelation of errors
Ha : Autocorrelation of errors

## Fixes

### 1. Linearity

- Apply transformations to variable like square, root, log, etc
- Use other approaches like tree-based algorithms

### 3. No Perfect Multicollinearity

- Remove highly correlated predictors
- Use L1 (lasso) regression

### **4. Normality of residuals**

- If non-normal due to outliers, try robust regression

**Robust regression** is a type of regression that is less sensitive to outliers and violations of assumptions (especially normality and homoscedasticity) compared to ordinary least squares (OLS) regression. It down-weights the influence of extreme observations.

**Approaches**:

- **Huber**: Optimizes the squared loss for small residuals and the absolute loss for large residuals
- **Tukey's biweight**: Similar to huber for small residuals, but loss for large residuals is constant
- **Least Absolute Deviations (LAD) Regression**: Minimizes the sum of absolute residuals instead of squared residuals

### **5. Homoscedasticity**

- If variance increases with Y, use **log or sqrt transformation** of Y
- If variance structure is predictable, use **Weighted Least Squares** (WLS). WLS assigns different weights to different observations, giving less weight to data points with high variance and more weight to those with low variance.