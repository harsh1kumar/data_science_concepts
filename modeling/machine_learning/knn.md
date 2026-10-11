# kNN

- Makes predictions by finding the *k* nearest neighbors of a given data point in the feature space and using their labels or values to determine the label or value of the new data point
- Used for both classification and regression tasks

**Steps**

1. When a new data point needs to be classified or predicted, the algorithm calculates the distances between the new data point and all the data points in the training dataset
2. The distance metric used is typically Euclidean distance, or maybe Manhattan distance or cosine similarity
3. After calculating the distances, the algorithm selects the *k* data points with the smallest distances to the new data point
4. For **classification tasks**, the algorithm assigns the label that is most frequent among the *k* nearest neighbours to the new data point
5. For **regression tasks**, the algorithm assigns the average or weighted average of the target values of the *k* nearest neighbours to the new data point. The weights can be inversely proportional to the distance from the new data point, giving more weight to closer neighbours.
6. *k* is typically chosen through **cross-validation** to avoid overfitting or underfitting