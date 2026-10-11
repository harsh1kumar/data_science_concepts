# Random Forest (Bagging)

### Approach

1. Bootstrapped dataset: Randomly select rows **with replacement**
2. Create tree with randomly selected columns at each node
    1. Number of variables to select: Try square root of # of variables
3. Track out of bag error

### Final Decision

Regression: Averaging predictions from all trees

Classification: Majority vote

## Overfitting

Individual decision trees can overfit the data. However, by averaging many trees, the variance is reduced

### Proximity matrix

- To compute the proximity matrix, each sample in the dataset is exposed to all decision trees in the forest.
- For every pair of samples, the proximity between them is calculated based on their relative positions in the decision trees.
- If two samples end up in the same leaf node of a decision tree, their proximity is increased by a certain amount (e.g., 1).
- The process is repeated for all decision trees in the forest, accumulating proximity values for each pair of samples.

In the proximity matrix, higher values indicate greater similarity or closeness between pairs of samples. Samples that are frequently grouped together in the same leaf nodes across different decision trees tend to have higher proximity values