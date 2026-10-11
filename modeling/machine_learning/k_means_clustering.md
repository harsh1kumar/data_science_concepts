# k-means clustering

## Intro

Minimises within-cluster sum of squared distances, also known as inertia

$$
Objective function = Euclidean Distance = \sum_i^{k} \sum_j (x_{ij}-\mu_{i})^2
$$

**Limitations**:

- Number of clusters (K) has to be specified in advance
- Is sensitive to the initial placement of centroids and may converge to local optima
- It assumes clusters are spherical and equally sized, which may not always hold true

## Steps

1. **Initialisation:**
    
    Start by randomly initialising K centroids
    
2. **Assignment:**
    
    Each data point in the dataset is assigned to the nearest centroid based on some distance metric, typically the Euclidean distance.
    
3. **Update:**
    - Recalculate the centroids of the newly formed clusters
    - Each centroid is updated to be the mean of all data points assigned to its cluster
4. **Iteration:**
    
    Steps 2 and 3 are repeated until convergence criteria is met:
    
    - centroids no longer change significantly between iterations
    - or when a maximum number of iterations is reached

## Initialisation

1. **Random Initialisation:**
    - Randomly select K data points from the dataset as the initial centroids
    - Chosen uniformly at random from the dataset
2. **K-means++ Initialisation:**
    
    Improvement over random initialisation that aims to choose initial centroids that are well spread out in the feature space and leads to better convergence
    
    - Starts by selecting one data point randomly as the first centroid
    - Subsequent centroids are chosen with a probability proportional to the squared distance from the nearest already chosen centroid

**Importance of centroid initialisation**

1. Convergence Speed: Poor initialisation can lead to slower convergence
2. Avoiding Local Optima: K-means is sensitive to initial centroid positions and can converge to local optima. Proper initialisation methods like K-means++ can help 
3. Quality of Clusters: Well-initialised centroids can lead to better quality clusters by ensuring that the algorithm explores a diverse range of data points from the beginning

## Selecting K

1. **Domain Knowledge**
2. **Elbow Method:**
    - Running the K-means algorithm for a range of *k* values and plotting the within-cluster sum of squared distances (inertia) against *k*
    - The point where the rate of decrease in inertia starts to slow down (forming an "elbow" shape) can indicate the optimal number of clusters
3. **Silhouette Score:**
    - Silhouette score measures how similar an object is to its own cluster compared to other clusters
    - It ranges from -1 to +1, where a high silhouette score indicates that the object is well-matched to its own cluster and poorly matched to neighbouring clusters.
    - Silhouette score can be calculated for different values of *k*, and the value of *k* with the highest silhouette score is considered optimal.

### Limitations of k-means clustering

1. Sensitive to Initial Centroids
2. Requires Predefined Number of Clusters
3. Assumes Spherical Clusters
4. Generates approximately equal sized clusters
5. May perform poorly on high-dimensional data due to the curse of dimensionality, where distances become less meaningful in high-dimensional spaces
6. Prone to Outliers: K-means is sensitive to outliers, as they can disproportionately influence the positions of centroids and the formation of clusters
7. Doesn't Handle Non-Linear Data: K-means performs poorly on datasets with non-linear or irregularly shaped clusters
8. May Require Multiple Runs: To mitigate the sensitivity to initial centroids, K-means may need to be run multiple times with different initialisations

**Handling Outliers and Noisy Data Points**

1. Preprocessing**:** Outliers can be detected and removed or corrected
2. Normalisation the data before clustering can help mitigate the influence of outliers by scaling all features to a similar range
3. Robust Distance Measures: Using robust distance measures, such as the Mahalanobis distance or Manhattan distance, instead of the Euclidean distance

### Evaluation

1. **Inertia (Within-Cluster Sum of Squared Distances)**
2. **Silhouette Score:**
    - It ranges from -1 to +1, where a high silhouette score indicates that the object is well-matched to its own cluster and poorly matched to neighboring clusters.
    - Compute average silhouette score across all samples. A high average silhouette score suggests that the clustering configuration is appropriate.
    - $a_i$: Average distance from *i* to all other data points in the same cluster. This represents the cohesion of *i* with its own cluster
    - $b_i$: Average distance from *i* to all data points in the nearest neighboring cluster. This represents the separation of *i* from neighboring clusters
    
    $$
    silhouete\_score = \frac{b_i-a_i}{max(a_i, b_i)}
    $$
    
3. **Davies-Bouldin Index:**
    - Measures the average similarity between each cluster and its most similar cluster
    - Lower values = good
4. **Calinski-Harabasz Index (Variance Ratio Criterion):**
    - Computes the ratio of between-cluster dispersion to within-cluster dispersion
    - Higher values = good