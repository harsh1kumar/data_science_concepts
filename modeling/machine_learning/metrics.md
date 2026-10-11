# Metrics

## Classification Problem

- **Precision**

$$
\frac{TP}{TP+FP}
$$

- **Recall (Sensitivity)**: What % of positives are correctly identified?
    
    $$
    \frac{TP}{TP+FN}
    $$
    
- **Specificity:** What % of negatives are correctly identified?
    
    $$
    \frac{TN}{TN+FP}
    $$
    
- **Accuracy**

$$
\frac{TP+TN}{All \space Observations}
$$

- **F1 score**

$$
\frac{2 \times Precision \times Recall}{Precision + Recall}
$$

- **Confusion Matrix**
    
    
    |  | Actual
    1 | Actual
    0 |
    | --- | --- | --- |
    | Predicted 1 | TP | FP |
    | Predicted 0 | FN | TN |
- **ROC AUC (Receiver Operator Characteristics)**
    
    Plot `True Positive Rate` vs `False Positive Rate`
    
    OR `Sensitivity` vs `1-Specificity`
    

- **PR AUC (Precision Recall)**
    
    Plot `Recall/Sensitivity` vs `Precision`
    
    If % of zeros is high, we can use precision instead of false +ve rate
    
- **Information value**

$$
IV = \sum(\%Goods - \%Bads)\times ln(\frac{\%Good}{\%Bads})
$$

## Regression Problem

1. **Mean Absolute Error (MAE): $\frac{1}{n}\sum|y_i - \hat{y_i}|$**
    - less sensitive to outliers compared to the mean squared error.
2. **Mean Squared Error (MSE): $\frac{1}{n}\sum(y_i - \hat{y_i})^2$**
    - gives higher weight to large errors and is sensitive to outliers.
3. **Root Mean Squared Error (RMSE): $\sqrt{\frac{\sum(y_i - \hat{y_i})^2}{n}}$**
    - is in the same unit as the target variable
    - provides a more interpretable measure of error compared to MSE.
4. **R-squared**
5. **Adjusted R-squared:**
6. **Mean Absolute Percentage Error (MAPE): $\frac{1}{n}\sum|\frac{y_i-\hat{y_i}}{y_i}| \times 100$**
    - expresses the error as a percentage of the actual values
    - commonly used when the scale of the target variable is important.

## Distance Measures

- **L1 (Manhattan) Distance**: calculated by taking the sum of distances between the *x* and *y* coordinates

$$
Distance(x,y) = \sum_{i=1}^n |x_i - y_i|
$$

- **L2 (Euclidean) Distance**: the length of a line segment between the two points

$$
Distance(x,y) = \sqrt{\sum_{i=1}^n(x_i-y_i)^2}
$$

- **Cosine similarity**: A measure of similarity between two non-zero vectors defined in an inner product space. Cosine similarity is the cosine of the angle between the vectors; that is, it is the dot product of the vectors divided by the product of their lengths

$$
Cosine Similarity = \frac{X.Y}{||X|| \times ||Y||} = \frac{\sum_{i=1}^n x_i y_i}{\sqrt{\sum x_i^2 \sum y_i^2}}
$$

- **Chebyshev Distance:** Chebyshev distance measures the maximum absolute difference between corresponding coordinates of two points.
    
    $$
    d = max(|x_1-y_1|, |x_2-y_2|....|x_n-y_n|)
    $$
    
- **Minkowski Distance:** Generalisation of Euclidean distance and Manhattan distance.
    - *p*=2 reduces to Euclidean distance, *p*=1 reduces to Manhattan distance
    
    $$
    d=(\sum|x_i-y_i|^p)^{1/p}
    $$