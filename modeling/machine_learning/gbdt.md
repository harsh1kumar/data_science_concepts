# GBDT (Boosting)

## General Concepts

- Combine weak learners
- All trees have equal weighting
- Each tree **corrects the errors** from the previous tree

## Regression

1. Initial prediction: Avg. value 
2. Build trees iteratively to predict the residuals (actual-predicted) from the previous tree
    1. Residual is the gradient of loss function w.r.t. predicted. This give the name gradient descent to this algo
    2. Remember the gradient descent formula for regression, we are doing kind of the similar thing:
        
        *New Prediction = Old Prediction - Alpha x Gradient w.r.t prediction*
        
3. Combine the output from trees using a learning rate

$$
Loss Function = \sum \frac{1}{2}(Actual - Predicted)^2
$$

Loss function is minimized when initial value is set as avg. value of all observations

- because if we solve $\frac{\delta Loss}{\delta Predicted} = 0$, we get Predicted = Actual

This is the same reason for value in the leaf node being average of all values

## Classification

$$
Odds = \frac{Count \ of \ Ones}{ Count \ of \ Zeros} \\
$$

$$
Prob = \frac{e^{log(odds)}}{1+e^{log(odds)}}
$$

1. Initial prediction: log(odds)
2. Build trees to predict residuals.  We fit trees to the **gradient of the loss function**
3. Leaf node would have `log(odds)` prediction

$$
 Loss Function = -\frac{1}{N} \sum_{i=1}^{N} \left[ y_i \log(p_i) + (1 - y_i) \log(1 - p_i) \right]
$$

## Light GBM

- Leaf-wise split instead of level-wise split
- Find the best leaf node at each split
- Results in better performance

## XGBoost

1. Approximately greedy algorithm
    1. Divide the data by quantiles
2. Parallel learning
3. More regularization parameters
    1. L1: `alpha`
    2. L2: `lambda`

### XGBoost: Regression

- First prediction is 0.5
- Build tree for residuals

### XGBoost: Classification

- First prediction is 0.5
- Leaf node has log(odds)