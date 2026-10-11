# Other Topics

### Resampling (Bootstrapping)

Resampling methods are statistical techniques that involve repeatedly drawing samples from the observed data to make statistical inferences, estimate parameters, and assess the robustness of statistical procedures. 

Two common types of resampling methods are bootstrapping and cross-validation.

**Bootstrapping:**

- **Purpose:** Involves drawing multiple samples with replacement from the observed data to estimate the sampling distribution of a statistic
- **Procedure:**
    1. Draw a random sample (with replacement) from the observed data.
    2. Calculate the statistic of interest (e.g., mean, median, standard deviation) based on the resampled data.
    3. Repeat the process to create a large number of bootstrap samples.
- **Applications:**
    - Confidence interval estimation: Bootstrapping can be used to obtain confidence intervals for a parameter without relying on distributional assumptions.
    - Hypothesis testing: It can be used to perform hypothesis tests and assess the statistical significance of parameters.
- **Calculating p-value for hypothesis testing**
    - Let’s say that we have a sample with mean=0.5, we want to test the null hypothesis that mean=0
    - First shift the mean of the sample to 0 by shifting all sample points by -0.5
    - Take multiple bootstrapped samples from this shifted distribution and plot the means
    - From the distribution, we can find the probability of observing a mean as 0.5 or more extreme give that the mean was zero. This will be our p-value

### Standard Error

- In practice, standard error refers to the standard deviation of sample means. It is also known as standard error of means.
- In general, we can have standard error of any statistic. For example, we can have a standard error of sample standard deviation. In this case, we plot the standard deviations of different samples and that is called standard error.
- More broadly, you take multiple samples and calculate your desired statistic (mean, s.d., median, etc). Then you find the standard deviation of the metric from each sample and that is called the standard error. As you can see, this is related to bootstrapping.

### Technical and Biological Replicates

- **Technical replicates** are repeated measurements of the same sample under the same experimental conditions. They help assess the consistency and precision of the measurement process, identifying variability introduced by technical aspects of the experiment (e.g., pipetting, machine errors, or environmental fluctuations)
- **Biological replicates** involve independent samples that are biologically distinct but represent the same experimental conditions. These replicates help capture biological variability, which includes genetic, physiological, and environmental differences.

### Effective Sample Size

**Effective Sample Size (ESS)** refers to the number of independent data points that carry meaningful information in a statistical analysis, particularly in situations where data points may be correlated, clustered, or otherwise not fully independent. It adjusts for the loss of statistical power due to dependencies or other factors affecting the independence of observations.

For example, if you have 4 people, but 2 of these are twins. Samples from the twins will be correlated, so effective sample size will be between 3 and 4

### **LOWESS** and **LOESS**

[[video](https://www.youtube.com/watch?v=Vf7oJ6z2LCc)]

- LOESS: Locally Estimated Scatterplot Smoothing
- LOWESS: Locally Weighted Scatterplot Smoothing".

Non-parametric regression methods used for smoothing data. They are particularly useful for modeling relationships between variables when the underlying relationship is complex or unknown, allowing for a flexible, data-driven fit to the observed data without assuming a specific global functional form.

- involve fitting **local regressions** to subsets of the data to create a smooth curve that approximates the relationship between variables
- fits **local models** to small subsets of the data around each point
- for each point where the fit is computed, a **weighted least squares** regression is applied to neighboring data points. Points closest to the target get the most weight, while points farther away contribute less to the local fit