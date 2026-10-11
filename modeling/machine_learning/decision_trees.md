# Decision Trees

## Classification Trees

### **How to split nodes?**

Two approaches: Gini or Entropy reduction (information gain)

1. Gini
    - Gini impurity of leaf node = $1-\sum p_i^2 = 1-(prob \space of \space 1)^2-(prob \space of \space 0)^2$
    - Gini = $w_LG_L+w_RG_R$
    - Split the feature which has lowest gini
2. Entropy reduction/Information Gain
    
    $$
    Entropy = -\sum_{i=1}^{n} p_i \log_2 p_i
    $$
    
- Entropy ranges from 0 to 1, where:
    - If all instances belong to the same class (perfectly pure), the entropy is 0
    - If the instances are evenly distributed across all classes (completely impure), the entropy is 1
- Information Gain: We find the entropy before splitting and then weighted entropy after splitting
    
    $$
    Information \space Gain (X) = Entropy(Y) - \sum_{i=1}^k \frac{N_i}{N} \times Entropy(X_i)
    $$
    
    - Entropy(*Y*) is the entropy of the target variable before splitting
    - *k* is the number of unique values or categories in feature *X*
    - *N* is the total number of instances in the dataset
    - $N_i$ is the number of instances in the dataset with value *i* for feature *X*
    - Entropy($X_i$) is the entropy of the dataset after splitting based on value *i* of feature *X*

<aside>
⚡

For a classification decision, the leaf node can be assigned to the majority class i.e look at the majority class among all observations in training data coming to the leaf node

</aside>

### How to split features?

- Yes/No: Simply split at yes/no
- Numeric data: Try all avg. values between all numbers OR different percentiles
- Ranked data: ≤1, ≤2, ≤3
- Multiple choices: All combinations of choices

### **Feature selection**

Impurity reduction or information gain should be above a threshold

### **Missing values in a feature**

1. Put the most common value for that class → Mean/Median
2. Find another column with high correlation, use regression with that column to find value

## Regression Trees

### **How to split nodes?**

We can use different measures of variance reduction like **MSE or MAE**

- Value in leaf/child node = Avg. of observations in the leaf node
- Residuals = $actual -predicted$
- MSE or Sum of Squared Residuals = $\sum(actual - predicted)^2$

### Pruning Trees

Cost complexity pruning

1. Add a tree complexity penalty of $\alpha$ → $SSR + \alpha T$, where T= number of leaf nodes
2. Use validation data to find value of $\alpha$

## Questions

1. How is variable importance calculated for a decision tree?
    - Sum up Gini impurity reduction or MSE reduction across all nodes where a feature is being used
2. Why don’t we use decision trees?
    - Overfitting
3. What techniques to use to overcome the shortcoming for decision trees?
    - Boosting and bagging