# Logistic Regression

Logistic regression model is expressed as

$$
P(y=1|X) = \frac{1}{1+e^{-(linear\_regression\_equation)}} \\

P(y=1|X) = \frac{1}{1+e^{-(\beta_{0}+\beta_{1}X_{1}+....+\beta_{n}X_{n})}}
$$

Sigmoid function or logit function

$$
p = \frac{1}{1+e^{-y}} = \frac{e^y}{1+e^{y}}
$$

or it can be written in a different way as log of odds 

$$
y = log(\frac{p}{1-p})
$$

### Estimate parameters of a logistic regression model

1. We do this by maximum likelihood. First, lets write the equation for likelihood

$$
L(\beta_{0}, \beta_{1}...| y_{i}, X_{i}) = \prod_{i=1}^{N}P(y_{i}|X_{i})^{y_{i}}(1-P(y_{i}|X_{i})^{(1-y_{i})})
$$

where

- $P(y_{i}|X_{i})$ is the predicted probability for observation i computed using logistic regression function
- $y_{i}$ is the actual observed outcome (0 or 1)

1. Our objective is to maximize this likelihood i.e. find the model parameters which makes the observed data most probable under the model
2. We maximize log likelihood instead of likelihood since both are maximized at the same point

$$
log L(\beta_{0}, \beta_{1}...| y_{i}, X_{i}) = \sum_{i=1}^{N}y_{i}logP(y_{i}|X_{i})+(1-y_{i})log(1-P(y_{i}|X_{i}))
$$

1. There is no closed form solution for this, so we use gradient descent
2. Cost function for logistic regression is negative of log-likelihood a.k.a. cross-entropy loss

<aside>
⚡

The maximum value of likelihood is 1 and log-likelihood is 0. This can only happen if we find the best model that fits the observed data perfectly. 

In reality, likelihood would be between 0 and 1, while log likelihood would be between -infinity and 0

</aside>

### R-squared

$$
R^2 = 1 - \frac{LL(fit)}{LL(event\_rate)}
$$

- `LL(fit)` is the log likelihood of the fitted model
- `LL(event_rate)` is the log likelihood when all predicted values are equal to the event rate of the observed data

## Other concepts

### Class weights

Add weights in loss functions to apply a larger penalty for misclassifications of the minority class

## Regularization

You can use regularization with logistic regression in same way as linear regression

### Multiclass Classification

- **One-vs-Rest (OvR) / One-vs-All (OvA):** Train one classifier per class where each classifier predicts whether a sample belongs to its respective class or not
- **One-vs-One (OvO):** Train a binary classifier for every possible pair of classes. For *K* classes, this results in $\binom{K}{2}$ classifiers
- **Softmax Regression:**
    - Model calculates a score for each class
    - Apply the **softmax function** to convert these scores into probabilities

### Problem of Separation

The outcome variable can be perfectly predicted by the predictor variables. In other words, one or more of the predictor variables completely separate the two classes (0 and 1 in binary classification). 

Leads to infinitely large coefficients, causing instability and making the model unable to converge.

### How would you evaluate the calibration of a logistic regression model, i.e., whether the predicted probabilities match the true probabilities? What techniques would you use?