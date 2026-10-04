# Descriptive Statistics

### Measures of Central Tendency

- Mean (Arithmetic, Geometric, Harmonic), Median, Mode

### Measures of dispersion

- Population Variance:

$$
{\sigma}^2 = \frac{\sum_{i=1}^{N} {(x_{i} - \mu)}^2}{N}
$$

- Sample Variance:

$$
{S}^2 = \frac{\sum_{i=1}^{n} {(x_{i} - \bar{X})}^2}{n-1}
$$

- Standard Deviation is square root of variance

> NOTE: Sample variance is a unbiased estimator of population variance. However, sample standard deviation is not an unbiased estimator of population standard deviation
> 

> **Unbiased estimator**: An estimator of a given parameter is said to be unbiased if its expected value is equal to the true value of the parameter. In other words, an estimator is unbiased if it produces parameter estimates that are on average correct
> 

### **Covariance**

- Covariance measures the directional relationship between two variables
- A positive covariance means that both variables move together, while a negative covariance means they move inversely
- It’s value can be between $-\infty$ and $-\infty$

$$
Covariance = E[(x-\bar{x})[(y-\bar{y})]
$$

### Correlation

- Correlation is dimension-less and has value between -1 and 1. It is a scaled form of covariance.

$$
Correlation = \frac{Cov(x,y)}{\sigma_{x}\sigma_{y}}
$$

- p-value for correlation relates to following null hypothesis: “Randomly drawn points will have the same correlation”