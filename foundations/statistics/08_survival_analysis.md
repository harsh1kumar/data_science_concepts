# Survival Analysis

Survival analysis is a statistical method where the focus is on estimating the time until an event of interest occurs (e.g., customer churn, machine failure, patient survival).

## **Censoring**

Censoring occurs when we do not observe the event of interest (e.g., death, churn, failure) for some subjects during the study period. This means we have **incomplete data** on their event times, but we still know something about them (e.g., they survived at least until a certain time).

1. **Right Censoring (Most Common):** The event hasn't happened yet by the end of the study or observation period
2. **Left Censoring:** The event **already happened** before the subject entered the study, but we don’t know when
3. **Interval Censoring:** The event happened in a time range, but we don’t know the exact time

## **Kaplan-Meier Estimator (KM Estimator)**

- A **non-parametric** method
- Calculate the probability that an event has **not** occurred by a given time i.e the probability of survival
    - You can understand it as % of individuals who survive at time $t_i$, but it gets complicated with censored variables

$$
S(t)= \prod_{t_i \leq t} \left( 1 - \frac{d_i}{n_i} \right)
$$

- where…
    - S(t) = Estimated survival probability at time t
    - $t_i$ = Time points where events occur
    - $d_i$ = Number of events (failures) at time $t_i$
    - $n_i$ = Number of individuals at risk just before $t_i$

![In this image, m is number of failure events, q is the number of censored events and n is the number of individuals at risk just before time t](Survival%20Analysis/image.png)

In this image, m is number of failure events, q is the number of censored events and n is the number of individuals at risk just before time t

**Kaplan-Meier Curve**

- **Y-axis** (Survival Probability S(t)): Probability of survival beyond time t.
- **X-axis** (Time to Event): Duration (e.g., time to death, churn, failure).
- **Steps in the Curve**: Drops occur at event times (when an event happens).
- **Censored Observations**: Indicated with markers (e.g., crosses or ticks).

## Log Rank Test

The **Log-Rank Test** is a statistical test used in survival analysis to compare the **survival distributions** of two or more groups (e.g., treatment vs. control in clinical trials). It is a **non-parametric test** that checks whether survival times differ significantly between groups.

The log-rank test compares the **observed** vs. **expected** number of events (e.g., deaths, churns) at each time point.

$$
Test Statistic = \sum \frac{(O_i - E_i)^2}{V_i}
$$

- where…
    - $O_i$ = Observed number of events in group i
    - $E_i$ = Expected number of events in group i (assuming no difference in survival)
    - $V_i$ = Variance of the expected events.

The test follows a **chi-square distribution**

## **Cox Proportional Hazards Model (Cox Regression)**

- Estimates the effect of **covariates (predictors)** on survival time.
- It does not assume a specific distribution for survival times.

**Hazard function** in the Cox model is:

$$
h(t | X) = h_0(t) \cdot e^{(\beta_1 X_1 + \beta_2 X_2 + ... + \beta_p X_p)}
$$

- where…
    - $h(t∣X)$ = Hazard rate at time t given predictors X.
    - $h_0(t)$ = **Baseline hazard function** (unknown function).
    - $e^{(\beta_1 X_1 + \beta_2 X_2 + ... + \beta_p X_p)}$= Effect of covariates.
    - $\beta_i$ = Regression coefficient for predictor Xi (determines its impact).

**Interpretation**

- If HR ($e^{\beta}$) > 1: **Higher risk** of the event happening.
- If HR ($e^{\beta}$) < 1: **Lower risk** (protective effect).
- If HR = 1: No effect.

**Example**

| **Covariate** | **Coefficient (β)** | **Hazard Ratio ($e^{\beta}$**) | **Interpretation** |
| --- | --- | --- | --- |
| Age | 0.05 | 1.051 | Each 1-year increase in age increases risk by 5.1%. |
| Treatment | -0.3 | 0.74 | New treatment reduces risk by 26% compared to old treatment. |