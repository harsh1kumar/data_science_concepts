# Linear Regression

### General Ideas

([Video of some derivations from Khan Academy](https://www.youtube.com/watch?v=6OvhLPS7rj4&list=PL1328115D3D8A2566&index=51))

- To find the best fitting line for some points, we find the squared error and try to minimize it
- Let’s assume that the best fitting line is $y=mx+b$
- Squared error which we minimize will be:

$$
MSE = \frac{1}{n}\sum_{i=1}^{N}(y_i-(mx_i + b))^2
$$

where $(x_i, y_i)$  is the $i^{th}$ observation and $mx_i +b$ is the predicted value of $y$

- Interesting fact: Mean of x and mean of y will be a point on this best fitting line
    
    

### Assumptions of Linear Regression

[Assumptions of Linear Regression](linear_regression/assumptions_of_linear_regression.md)

### R-squared (Coefficient of Determination)

([Video from Khan Academy](https://www.youtube.com/watch?v=lng4ZgConCM&list=PL1328115D3D8A2566&index=57))

**Question**: What % of the variation in y is described by the variation in x?

**Alternate question**: If we fit a line on the data points, how good is the fit of that line?

- Total variation in y is the distance of each value of y from the mean of y. It is also called SST.

$$
SST = \sum(y_i - \bar{y})^2
$$

- What % of the total variation is **NOT** explained by the regression line?
    
    Numerator will be **SSE** since this the error which is not explained by the regression line. If the regression line doesn’t fit the data well, then residuals will be high and so SSE would be high.
    

$$
\frac{Sum of Squares of Error(SSE)}{Sum of Squares Total(SST)} = \frac{\sum(y_i-\hat{y_i})^2}{\sum(y_i - \bar{y})^2}
$$

- What % of the variation in y is described by the variation in x? **OR** what % of variation in y is described by the regression line

$$
R^2 = 1-\frac{SSE}{SST}
$$

- R in R2 is the correlation coefficient

**What is the shortcoming of $R^2$**

1. # of Independent variables: It increases as number of independent variables increase.
2. Sample Size: It tends to increase with the sample size which makes it challenging to compare R2 values across datasets with different sample sizes
3. Assumes Linearity: R2 is most meaningful where the relationship between the independent and dependent variables is assumed to be linear
4. No Information on Prediction Accuracy: R2 does not provide information about the accuracy of predictions for new, unseen data. It measures the goodness of fit for the observed data but does not assess the model's generalization performance.

$$
Adjusted \space R^2 = 1-\frac{(1-R^2)(n-1)}{n-k-1}
$$

where:

- n: # of observations
- k: # of predictors (independent variables)

### Feature Importance

1. **Coefficients Magnitude**: Magnitude of the coefficient indicates the strength and direction of the relationship between feature and predicted outcome. Larger magnitudes imply a more significant impact. Feature scaling should be done for using this.
2. **p-values:** Lower p-values suggest a more significant relationship between the feature and the target variable. However, be cautious with using p-values
3. **Stepwise Selection: I**teratively add or remove features based on their impact on the model's performance

### Regularization

L1 = Lasso

L2 = Ridge

**How regularization works**:

- Naive way to reduce loss would be make the coefficients ($\beta$) to very low values
- However, that increases loss from squared errors as model doesn’t fit
- Best way would be to set beta high enough for features which add value by keeping squared errors low and set beta to be very low (or zero) for features which don’t add any value

**Feature selection**: L1 regularization helps in feature selection, since it shrinks coefficient of less important features to zero

### Feature Normalization

**Why is this needed?**

1. impact of one feature on the regression model may dominate over others, if not normalized
2. accelerate the convergence of optimization algorithms like gradient descent
3. makes it easier to interpret the coefficients of the regression model
4. regularization methods penalize large coefficients. If features are on different scales, the regularization term may unfairly penalize some features more than others

**Methods**

1. Min-max normalization
2. Z-score normalization
3. Robust Scaling: $\frac{X-median(X)}{InterQuartileRange}$
    - is less sensitive to outliers
4. Max abs scaling: $\frac{X}{max(|X|)}$
    - range [-1, 1]

### ANOVA for regression

Used to assess the overall significance of the regression model and the individual significance of each predictor variable

**Stage 1:**

<aside>
💡 Ho: All the coefficients of the predictor variables are equal to zero

Ha: At least one coefficient is not equal to zero

</aside>

$SSR = \sum(\hat{y_i}-\bar{y_i})^2$      and       df = k                  where k=number of predictors

$SSE = \sum(y_i-\hat{y_i})^2$      and       df = n-k-1           where n=number of observations

Note: *df for SST is (k) + (n-k-1) = n-1*

$MSR = \frac{\sum(\hat{y_i}-\bar{y_i})^2}{k}$

$MSE = \frac{\sum(y_i-\hat{y_i})^2}{n-k-1}$

$F = \frac{MSR}{MSE} = \frac{Variations \space explained \space by \space regression}{Variations \space not \space explained \space by \space regression}$

**Stage 2:**

<aside>
💡 Ho: One coefficient is zero
Ha: One coefficient is non-zero

</aside>

We run t-test here for all predictors as well as the intercept.

The actual t-test is a bit complicated, so you should know how to interpret the results

### How good is the model?

1. **Model performance:** Check model performance using metrics like MAPE, etc
2. **Cross-Validation:** Perform cross-validation to assess the model's generalization performance. Check overfitting and under-fitting
3. **Model Benchmarking:** Compare the linear regression model with alternative models or simpler baseline model. Do we even need a model.
4. **Model Summary:** Review the summary statistics, including coefficients, standard errors, t-statistics, *R*2, and p-values. Ensure that the model statistically significant insights
5. **Assumptions of linear regression check**
6. **Outliers and Influential Points:**
    - Identify outliers and influential points that may have a significant impact on the model. Consider leverage, Cook's distance, and other diagnostic measures to identify points that disproportionately influence the regression coefficients.
7. **Feature Importance**
8. **Feature Scaling**