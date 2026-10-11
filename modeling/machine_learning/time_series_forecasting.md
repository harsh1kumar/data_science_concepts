# Time Series Forecasting

## General Concepts

### Lag Operator

$$
LX_t = X_{t-1}\\
L^{k}X_t = X_{t-k}
$$

### **Stationary**

Constant statistical properties:

1. Constant mean over time
2. Constant variance over time
3. No seasonality

**How to check:**

- Global vs local test
- Augmented Dicky-Fuller Test

**How to make a time series stationary?** 

Take difference of value at time `t` with value at time `t-1`

## Auto Regressive Model - AR(p) model

Represents the linear regression of the current value of the time series on its past values. 

`$\epsilon_t$` is white noise

$$
X_t = \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t\\
X_t = \sum_{i=1}^p \phi_i L^i X_t + \epsilon_t\\
$$

## **Moving Average Model - MA(q) model**

Represents linear regression of the current value of the time series on the past prediction errors

$$
X_t = \mu+\epsilon_t+\sum_{i=1}^q \theta_i \epsilon_{t-i}\\
X_t = \mu+\epsilon_t+\sum_{i=1}^q \theta_i L^i \epsilon_t\\
$$

## ARMA(p,q) Model

$$
X_t = \epsilon_t + \sum_{i=1}^{p}\phi_i X_{t-i} + \sum_{i=1}^{q}\theta_i \epsilon_{t-i}
$$

With lag operator:

- AR(p) model

$$
\epsilon_t = (1-\sum_{i=1}^p\phi_iL^i)X_t
$$

- MA(q) model

$$
X_t-\mu = (1-\sum_{i=1}^{q}\theta_i L^i)\epsilon_t
$$

- ARMA(p,q) model

$$
(1-\sum_{i=1}^p\phi_iL^i)X_t = (1-\sum_{i=1}^{q}\theta_i L^i)\epsilon_t
$$

### Choosing p and q

**For p**

Partial Autocorrelation Function (PACF): Measures the correlation between a time series and its lagged values, while controlling for the effects of intermediate lags

**For q**

Autocorrelation Function (ACF): Measures correlation between a time series and its lagged values

$$
ACF(k) = \frac{\sum_{t=k+1}^{n}(y_t-\bar{y})(y_{t-k}-\bar{y})}{\sum_{t=1}^{n}(y_t-\bar{y})^2}
$$

## ARIMA (p,d,q) model

ARIMA models are based on the assumption that the time series data is stationary or can be transformed into a stationary series through differencing

$$
(1-\sum_{i=1}^p\phi_iL^i) (1-L)^d X_t = (1-\sum_{i=1}^{q}\theta_i L^i)\epsilon_t
$$

**Integrated (I) component:** Represents differencing of the time series data to make it stationary. Differencing involves subtracting each observation from its previous observation

## Seasonal ARIMA (p,d,q)(P,D,Q)m

m: Number of periods in each season

## Other Concepts

**White Noise:** Time series which has…

- Zero mean
- Constant variance over time
- No seasonality or patterns

**Unit Roots:** Implies that a time series variable is non-stationary, meaning that it does not revert to a constant mean over time and exhibits a long-term trend or drift

**Dicky-Fuller Test:** Used to determine whether a univariate time series has a unit root, indicating non-stationarity

$H_0$: Time series is non-stationary; it has a unit root

$H_a$: Time series is stationary; it does not have a unit root

**Rolling window validation:** Instead of predicting values too much into the future, predict for a fixed window and keep on moving it.

Reason: Predictions tend to get less accurate when we predict too far into future

## Residual Diagnostics

In ARIMA modelling, the residuals are assumed to be white noise

1. **Plotting Residuals:**
    - The first step in residual diagnostics is to plot the residuals against time to visually inspect their behavior.
    - The plot should show random fluctuations around zero, with no discernible patterns or trends. Any systematic patterns in the residuals may indicate model misspecification or inadequacy.
2. **Autocorrelation Function (ACF) of Residuals:**
    - The autocorrelation function (ACF) of the residuals is used to examine whether there is any remaining autocorrelation in the residuals after fitting the ARIMA model.
    - Significant autocorrelation in the residuals suggests that the model has not adequately captured the temporal dependencies present in the data.
3. **Histogram and Q-Q Plot of Residuals:**
    - Histogram and quantile-quantile (Q-Q) plot of the residuals can be used to assess whether the residuals follow a normal distribution.
    - The histogram should show a bell-shaped distribution, and the Q-Q plot should display the residuals along a straight line, indicating normality.
4. **Residuals vs. Fitted Values:**
    - Plotting the residuals against the fitted values helps identify any systematic patterns or heteroscedasticity (changing variance) in the residuals.
    - Ideally, the residuals should be evenly distributed around zero, with no discernible pattern in their relationship with the fitted values.

## Assumption/Limitations of ARIMA

1. **Linear Relationships:**
    - ARIMA models assume that the relationships between the current observation and its lagged values, as well as the forecast errors, are linear. In real-world data, nonlinear relationships may exist, which ARIMA models may not capture effectively.
2. **Stationarity:**
    - ARIMA models assume that the time series data is stationary or can be made stationary through differencing. While stationarity is often achieved in practice, some time series may exhibit non-stationary behavior that is difficult to transform into a stationary series.
3. **Constant Parameters:**
    - ARIMA models assume that the parameters of the model (autoregressive coefficients, moving average coefficients, and the mean) remain constant over time. In practice, the underlying parameters of a time series may change over time, leading to model instability.
4. **Normality of Residuals:**
    - ARIMA models assume that the residuals (forecast errors) follow a normal distribution with constant mean and variance. While this assumption is often reasonable for large sample sizes, violations of normality can affect the accuracy of parameter estimates and forecast intervals.
5. **Seasonality:**
    - ARIMA models are not explicitly designed to handle seasonal patterns in time series data. While seasonal ARIMA (SARIMA) models can be used to incorporate seasonal components, they may not always capture complex seasonal patterns effectively.
6. **Lack of External Factors:**
    - ARIMA models do not explicitly incorporate external factors or explanatory variables that may influence the time series being modeled. This limitation can restrict the model's ability to capture the full complexity of real-world phenomena.
7. **Forecast Horizon:**
    - ARIMA models are most suitable for short- to medium-term forecasting horizons. For longer-term forecasts, the accuracy of ARIMA models may degrade due to the inherent uncertainty and variability in longer time horizons.
8. **Data Quality and Outliers:**
    - ARIMA models are sensitive to outliers and unusual observations in the time series data. Extreme values or data irregularities can distort parameter estimates and affect the model's predictive performance.

## Other approaches for time series forecasting

1. XGBoost
2. Neural Network (like LSTM)
3. Prophet