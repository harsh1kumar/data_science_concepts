# Descriptive Statistics

### Measures of Central Tendency

- Mean
    - Arithmetic
    $$
    \frac{1}{n} \sum_{i=1}^{n} x_i = \frac{x_1 + x_2 + \dots + x_n}{n}
    $$
    
    - Geometric
    $$
    \left( \prod_{i=1}^{n} x_i \right)^{\frac{1}{n}} = \sqrt[n]{x_1 \cdot x_2 \cdots x_n}
    $$

    - Harmonic
    $$
    H = \frac{n}{\sum_{i=1}^{n} \frac{1}{x_i}} = \frac{n}{\frac{1}{x_1} + \frac{1}{x_2} + \dots + \frac{1}{x_n}}
    $$
- Median
- Mode

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
Covariance = E[(x-\bar{X})[(y-\bar{Y})]
$$

### Correlation

- Correlation is dimension-less and has value between -1 and 1. It is a scaled form of covariance.

$$
Correlation = \frac{Cov(x,y)}{\sigma_{x}\sigma_{y}}
$$

- p-value for correlation relates to following null hypothesis: “Randomly drawn points will have the same correlation”