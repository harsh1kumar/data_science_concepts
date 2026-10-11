# Causal Inference

## Book - **Causal Inference for The Brave and True**

[Summary: **Causal Inference for The Brave and True**](summary_causal_inference_book.md)

## Terminology

n: # of subjects or observations, where `i` is one suject

$T_i$: Treatment

$Y_i$: Response

$X_i$: Feature Vector

- Potential Outcomes: $Y_i(1)$ and $Y_i(0)$
- Actual Outcome: $Y_i$

- Causal Effect = $Y_i(1)-Y_i(0)$
- Avg. Treatment Effect (ATE) = $E[Y_i(1)-Y_i(0)]$
- Conditional Avg. Treatment Effect (CATE) = $E[Y_i(1)-Y_i(0) \ | \ X_i=x]$

## Need for causal analysis

**ATE Calculations**

- We only have one actual outcome, so can’t get the value of both potential outcomes
- So, we have a problem of missing counterfactuals

**Simpson's paradox**

- A trend appearing in groups disappears or reverses when the groups are combined
- This happens can happen due to confounders

## Randomised Control Trials

Since treatments are applied randomly…

$$
ATE = E[Y_i|T=1]-E[Y_i|T=0]
$$

## Controlling for X in observation data

$$
\begin{align*}
ATE &= E_x[E[Y_i|T=1,X_i]-E[Y_i|T=0,X_i]] \\
&= E_x[\mu_1(X_i)-\mu_0(X_i)]
\end{align*}
$$

$$
ATE = \sum_x E[Y_i|T=1,X_i]-E[Y_i|T=0,X_i] \ P(x)
$$

1. Learn $\hat{\mu}_o(X)$ by predicting Y from X on control data
2. Learn $\hat{\mu}_1(X)$ by predicting Y from X on treatment data

- If the relationship of $\hat{\mu}_T(X)$ is linear, then linear regression work best. If it is not linear, then this approach gives wrong results
- If we decide to use non-parametric ML algos like Random Forest, then the results are not completely wrong, but the results improve as $n \to \infty$

## Propensity Scores

Probability of being treated conditional on $X_i$

$$
e(X) = P[T_i=1|X_i]
$$

- In case of a randomised trial, propensity score is constant

### Inverse Propensity Weighting (IPW)

$$
ATE = E\left[\frac{T_iY_i}{e(X_i)}-\frac{(1-T_i)Y_i}{1-e(X_i)}\right]
$$

- `e(X)` can be estimated from a ML model
- However, error introduced by ML models won’t be low enough to make reliable conclusions

## Double Robustness

### Augmented IPW

$$
\begin{align*}
ATE &= \frac{1}{n}\sum_{i=1}^n [ \hat{\mu}_1(X_i) - \hat{\mu}_0(X_i) \\

&+ \frac{T_i}{\hat{e}(X_i)}(Y_i-\hat{\mu}_1(X_i))

- \frac{1-T_i}{1-\hat{e}(X_i)}(Y_i-\hat{\mu}_1(X_i))]
\end{align*}
$$

$$
ATE_{AIPW} = D+R
$$

D: Direct regression adjustment estimator using $\hat{\mu}_T(X)$

R: IPW estimator applied to residuals $Y_i-\hat{\mu}_T(X)$

### Confidence Interval

$$
ATE_{AIPW} = \frac{1}{n} \sum_{i=1}^n \hat{\Gamma_i}
$$

where $\hat{\Gamma_i}$ is the things inside summation of $ATE_{AIPW}$

To find confidence interval, think of above as gaussian distribution with $mean = ATE_{AIPW}$

## Cross-fitting

- When estimating $e(X_i)$, use a model that didn’t have access to $i^{th}$ training example
- You can divide data into k groups, train on all except $k^{th}$ fold and evaluate on $k^{th}$ fold data

## Assumption of Causal Inference

**1. Conditional Ignorability / Conditional Exchangeability / Unconfoundedness**

**Exachangeability**: If you make control group as the treatment, the output of this new treatment group is same as the old treatment group.

- **Identifiability**: A causal quantity is causal if we can compute it from purely statistical qualities

**2. Positivity / Overlap**

$$
0 < P(T=1|X=x) <1
$$

Propensity scores should be neither too close to 0 or 1 i.e $e(X_i)$ shouldn’t have very high certainity or being in test or in control

**Positivity-Unconfoundedness tradeoff:** We get better unconfoundedness by conditioning on more covariates (features X). However, that could increase positivity violations.

**3. No Interference**

$Y_i(T_i)$ is not influenced by treatments given to other subjects

**4. Consistency**

*If T=t, then Y = Y(t)*

This assumption can be violated if a particular subject sometimes generates Y=1 as outcome and Y=0 other times, if the same treatment is given

## Instrumental Variables

[A Beginner’s Guide to Using Instrumental Variables](https://towardsdatascience.com/a-beginners-guide-to-using-instrumental-variables-635fd5a1b35f)

### Assumptions

1. Relevance
2. Exclusion
3. Instrumental Unconfoundedness

### ATE with instruments in a linear setting

### Two-stage Least Square Estimates

### Non-parametric identification of local ATE

## Graphs

- Directed Acyclic Graphs (DAGs)
    - Chain: `A → B → C`
    - Fork: `A ← B → C`
    - Collider: `A → B ← C`
- d-separation:
    - Conditioning on a variable along a chain or fork blocks (d-separates) the path
    - Conditioning on a collider opens the path
    

## Terminology

1. **Split Testing**: Method used to evaluate the causal effect of an intervention or treatment by randomly assigning subjects or units into different groups and comparing their outcomes
2. **Difference-in-differences (DiD):** Method used in causal inference to estimate the causal effect of a treatment by comparing the changes in outcomes over time between a treatment group and a control group. It is particularly useful when randomized controlled trials are not feasible or ethical, such as in cases where policies are implemented at a broader level.
    1. Data are collected from treatment and control groups before and after the intervention is implemented
    2. By taking the difference between the post-intervention period and the pre-intervention period for both groups, and then taking the difference in those differences, the method estimates the causal effect of the intervention
3. **Matching estimators:** A class of statistical methods to estimate the causal effect of a treatment by comparing treated and untreated units that are similar in terms of observed covariates
    - The goal of matching estimators is to create a counterfactual scenario where the treated and untreated units are comparable, allowing researchers to isolate the causal effect of the treatment
    - Nearest-neighbor is one of the methods used for matching
4. **Regression discontinuity design (RDD):** A quasi-experimental research design used in causal inference to estimate the causal effect of a treatment by exploiting a natural or imposed cutoff point
    - Units on one side of the cutoff point receive the treatment, while units on the other side do not receive the treatment
    - The basic idea behind RDD is to compare outcomes for units that are just above and just below the cutoff point, assuming that units close to the cutoff are comparable except for the treatment status