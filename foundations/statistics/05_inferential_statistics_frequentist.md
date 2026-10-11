# Inferential statistics - Frequentist

## Statistical Tests

[Statistical Tests](resources/inferential_statistics_frequentist/statistical_tests.md)

## Confidence Interval/Margin of error

[(Video)](https://www.youtube.com/watch?v=OwPSuHXmiPw&list=PL1328115D3D8A2566&index=32)

We try to answer the following question:  

> Find an interval such that we are “reasonably confident” that there is a 95% chance that the true population mean is in the interval
> 

To calculate confidence interval, we require population standard deviation. However, since we can’t compute that, we use sample standard deviation as an estimator for population standard deviation

$$
Confidence \: Interval = \bar{s} \pm z\frac{s}{\sqrt{n}} \\

where \; \bar{s} := sample \: mean \\ 
and \; s := sample \: stddev \\
and \; z := z \: score  \\
and \; n := sample \: size
$$

It is important to note that a 95% confidence interval does not mean that there is a 95% chance that the population mean is within the interval. Rather, it means that if we were to repeat the sampling process many times and calculate a 95% confidence interval each time, then approximately 95% of the intervals would contain the true population mean.

## Hypothesis testing

[(Video)](https://www.youtube.com/watch?v=-FtlH4svqx4&list=PL1328115D3D8A2566&index=36)

We assume that null hypothesis is true. Given that null hypothesis is true, we try to find the probability of observing the results which we saw.

### Generic Steps

**Context**: We have a population mean without treatment. We also have the mean and standard deviation from a sample from the treatment group

1. Imagine a sampling distribution of sample means. We need to find the mean and std. deviation of this distribution
    1. The mean of this distribution would be same as population mean and standard deviation would be population standard deviation divided by square root of sample size
    2. Since we assume that null hypothesis is true, the mean of treatment population is same as the control population
    3. The same mean would be the mean of the sampling distribution of sample means
    4. We don’t have population standard deviation, but we know that standard deviation of sample is an unbiased estimator of population standard deviation
    5. Using sample std. deviation, we find the std. deviation of distribution of sample means by dividing by sq. root of sample size
2. Now, we need to find how far is the treatment mean from mean of the sampling distribution. For that, we calculate z-score. This will allow us to estimate the chances of observing the treatment mean given null hypothesis is true
3. Calculate the p-value
4. If p-value is less than some significance level (eg. 0.05), then we can reject the null hypothesis. Why? Look at the definition of p-value below

### p-value

p-value indicates the likelihood of observing the sampled data OR something more extreme if we assume that the null hypothesis is true. In other words, what is the likelihood of data occurring by a random chance

If p-value is 0.05, we can conclude that there is a probability of 5% that the experiment results occurred by chance.

Or we can say that there is a 5% probability of observing results more extreme than the experiment results if the null hypothesis is true

p-value has 3 parts:

1. Probability that random chance will result in the observation
2. Probability of observing something else that is equally rare or equally extreme
3. Probability of observing something rarer or more extreme

NOTE: A small p-value doesn’t mean that the difference between two groups is large. Effect size can be small or large irrespective of p-value

### Type I and Type II errors

[(Video)](https://www.youtube.com/watch?v=EowIec7Y8HM&list=PL1328115D3D8A2566&index=40)

A type 1 error occurs when the null hypothesis is rejected even if it is true. It is also known as **false positive**. This is equal to **p-value**

A type 2 error occurs when the null hypothesis fails to get rejected, even if it is false. It is also known as a **false negative**. It is equal to 1-Power

### 3 ways of testing hypothesis

1. Confidence interval
2. Z-score
3. p-value

### Power of a test

The power of a test is the likelihood of rejecting a null hypothesis when it is false. In other words it indicates the likelihood of detecting a true effect if it exists.

Here are the key components for calculating power:

1. Effect Size (*δ*): The magnitude of the difference or effect you expect to detect. It quantifies the practical significance of the test. We can use Cohen's d (see below)
2. Sample Size (*n*)
3. Significance Level ($\alpha$): Probability of making a Type I error, usually set at 0.05.
4. Standard Deviation (*σ*): Variability in the data
5. Mean ($\mu$): Mean of data

### Hypothesis testing on difference of 2 random variables

[(Video)](https://www.youtube.com/watch?v=N984XGLjQfs&list=PL1328115D3D8A2566&index=47)

Let X and Y be two random variables. Z is a random variable which is the difference between X and Y

$$
\mu_{x-y} = \mu_{x} - \mu_{y}
$$

$$
\sigma_{x-y} = \sqrt{\sigma_{x}^2 + \sigma_{y}^2}
$$

- So mean is difference of both means, but variance in the summation of both variances
- For hypothesis testing, we are looking at the sampling distribution of Z random variable. Mean and standard deviation of sampling distribution of samples means for Z can be calculated as described above
- Next, we can calculate z-score. Note the division by samples sizes here, which is because we are getting variance of sampling distribution from variance of population

$$
z = \frac{(X - Y) - (\mu_{x} - \mu_{y})}{\sqrt{\frac{\sigma_{x}^2}{n_x} + \frac{\sigma_{y}^2}{n_y}}}
$$

- Degree of freedom: $(n_x-1)-(n_y-1)$

### Hypothesis testing on difference of 2 proportions

([Video](https://www.youtube.com/watch?v=dvSa_tx04hw&list=PL1328115D3D8A2566&index=50))

Example: Is there a statistical difference between proportion of men voting for republican party vs proportion of women voting for republicans,

Since there the two proportions, these will be Bernoulli distributions with mean $p_1$ and $p_2$ and standard deviation of $p_1(1-p_1)$ and $p_2(1-p_2)$

- For calculating Z score, we need the mean and standard deviation of sampling distribution
- Mean of sampling distribution is assumed as part of null hypothesis and will be $μ_1-μ_2$

$$
z = \frac{(p_1 - p_2) - (\mu_{x} - \mu_{y})}{\sqrt{\frac{p_1(1-p_1)}{n_1} + \frac{p_2(1-p_2)}{n_2}}}
$$

- If our null hypothesis assumes that there is no difference in means i.e $μ_1-μ_2=0$ then, we can simplify z-value to

$$
z = \frac{(p_1 - p_2)}{\sqrt{\frac{2p(1-p)}{n}}}
$$

where p can be calculated by combining all observations of the two proportions. For details, see the video

## Effect Size

Effect size can be calculated in various ways depending on the type of data and research design:

- Cohen's d
- Pearson's r
- Odds ratio (OR)
- Partial eta-squared (η²)

**Cohen's d**

Used to measure the standardized difference between two group means with independent groups.

$$
d = \frac{\mu_1 - \mu_2}{Pooled \space Standard \space Deviation}
$$

$$
\sigma_{pooled} = \sqrt{\frac{(n_1-1) \times \sigma^2_1+(n_2-1) \times \sigma^2_2}{n_1+n_2-2}}
$$

Pooled standard deviation is weighted average of the standard deviations of the two groups, weighted by their sample sizes.

- Small effect size: *d*≈0.2
- Medium effect size: *d*≈0.5
- Large effect size: *d*≈0.8

**Hedge's g**: An alternative to Cohen's d for small sample sizes, providing a bias-corrected estimate of effect size

**Odds Ratio (OR):** is a measure of effect size commonly used in studies involving binary outcomes. It quantifies the strength and direction of association between two binary variables

The formula to calculate the Odds Ratio (OR) is as follows:

$$
OR = \frac{Odds \space of \space event \space in \space Group1}{Odds \space of \space event \space in \space Group2}
$$

- **OR = 1**: The odds of the event are the same in both groups, indicating no association between the groups and the event.
- **OR > 1**: The event is more likely to occur in Group 1 than in Group 2.
- **OR < 1**: The event is less likely to occur in Group 1 than in Group 2.

## p-hacking

It involves conducting multiple tests, selectively reporting results, or adjusting statistical analyses until a p-value of less than 0.05 is achieved. It also includes stopping data collection when results become significant or collecting more data until significance is reached.

Multiple testing problem: Doing a lot of tests and ending up with false positives

**How to avoid p-hacking?**

1. User power analysis to **calculate sample size before** running the experiment. Don’t add more datapoints when p-value is close to 0.05 hoping to get to 0.05
2. Benjamini-Hochberg procedure [[video](https://youtu.be/K8LQSvtjcEo)]

## Early Stopping or peeking data

Early stopping—the act of peeking at the data before the experiment reaches the planned sample size and making decisions based on interim results. Early stopping can significantly inflate the false positive rate, leading to incorrect conclusions.

When we perform multiple interim analyses, each one provides an additional opportunity to cross the significance threshold due to random fluctuations in the data.

Haybittle–Peto boundary: Sets a very stringent significance level (e.g., α=0.001) for interim analyses and retains the standard α=0.05 for the final analysis.

## Variance Reduction Techniques

([Source](https://arxiv.org/html/2411.06701v1))

1. **Increase sample size**: As per central limit theorem, as sample size increase, the variance (standard error) reduces
2. **Equal split**: If sample size is limited, 50%-50% split between treatment and control minimizes the variance since 
    1. variance is higher for smaller samples
    2. overall variance is sum of variance of treatment and control
3. **Winsorizing or trimming outliers**: Extreme values can inflate variance
4. **Focusing on subpopulations**: Segmenting users into more homogeneous groups can reduce within-group variance. This can yield more precise estimates when these subgroups are analyzed separately.
5. **Stratified sampling**: Ensuring that each strata are equally represented in both control and treatment groups
6. **Incorporating covariates**: Variables that are correlated with the outcome metric. CUPED adjusts for variance using covariates measured before the experiment begins

## CUPED

[[reference](https://matteocourthoud.github.io/post/cuped/)]

CUPED uses pre-experiment data to control for natural variation in an experiment’s north star metric

**1) Pick a pre-experiment covariate (*X*)**: Often, the best covariate is the north star metric prior to the experiment period

**2) Calculate the CUPED-adjusted metric (*Ŷ*) for each experimental condition.** So, instead of using a metric average (*Y*) to calculate lift, we use the CUPED-adjusted metric: *Ŷ*.

`Y_HAT = avg(Y) - (cov(X,Y)/var(X)) * avg(X)`

**3) Calculate the CUPED-adjusted variance for each experimental condition**

`VAR_Y_HAT = var(Y) * (1 - corr(X,Y)**2)`

Alternatively

2) Find Y_cuped for each observation (both control and treatment)

`Y_cuped = Y - (cov(X,Y)/var(X)) * X` 

3) Use `Y_cuped` to find difference between control and treatment