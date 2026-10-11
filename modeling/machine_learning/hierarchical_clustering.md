# Hierarchical Clustering

- Organises the data into a tree-like structure, known as a dendrogram, where clusters at the bottom level represent individual data points, and clusters at higher levels represent combinations of lower-level clusters
- Doesn't require the user to specify the number of clusters beforehand, unlike partitioning algorithms like K-means
- **Flexibility in Cluster Shapes and Sizes: C**an handle clusters of arbitrary shapes and sizes, making it more flexible than some other algorithms that assume spherical or convex clusters
- **Interpretability:** Provides a hierarchical structure that can be visually interpreted through dendrograms, making it easier to understand the relationships between clusters and subclusters.

**Agglomerative vs divisive**

Agglomerative clustering starts with individual data points as separate clusters and merges them iteratively, while divisive clustering starts with all data points in a single cluster and splits them recursively.

Agglomerative is more commonly used.

## Approach

1. **Initialisation:** Begin by treating each data point as a separate cluster
2. **Compute Pairwise Distances:** Calculate the distance between each pair of clusters (initially, individual data points are considered as clusters). Common distance metrics include Euclidean distance, Manhattan distance, and others.
3. **Merge Closest Clusters:**
    - Identify the two closest clusters based on a chosen linkage criterion. The linkage criterion determines how the distance between clusters is calculated. (Details in separate section)
    - Merge the two closest clusters into a single cluster
4. **Update Distance Matrix:** Update the distance matrix to reflect the distances between the newly formed cluster and the remaining clusters using the chosen linkage criterion
5. **Repeat Until Termination:** Repeat steps 3 and 4 until only a single cluster containing all data points remains
6. **Construct Dendrogram:**
7. **Select Number of Clusters:** Determine the number of clusters by cutting the dendrogram at an appropriate level. The choice of the number of clusters depends on the specific problem and the desired granularity of the clustering.

## **Linkage criteria**

Used to measure the distance between clusters during the clustering process.

1. **Single Linkage (Minimum Linkage):**
    - Single linkage defines the distance between two clusters as the shortest distance between any two points in the two clusters
    - It tends to merge clusters based on the closest pair of points, resulting in elongated clusters.
    - Single linkage is sensitive to chaining effects and can be affected by outliers and noise.
2. **Complete Linkage (Maximum Linkage):**
    - Complete linkage defines the distance between two clusters as the maximum distance between any two points in the two clusters.
    - It merges clusters based on the farthest pair of points, resulting in more compact clusters.
    - Complete linkage is less sensitive to outliers compared to single linkage but may struggle with uneven cluster sizes.
3. **Average Linkage:**
    - Average linkage defines the distance between two clusters as the average distance between all pairs of points in the two clusters
    - It considers the overall similarity between clusters and is less affected by outliers compared to single linkage
    - Average linkage tends to produce balanced clusters and is less sensitive to noise
4. **Centroid Linkage:**
    - Centroid linkage defines the distance between two clusters as the distance between their centroids, i.e., the mean points of the clusters
    - It measures the overall distance between clusters and can produce well-separated clusters
    - However, centroid linkage can be sensitive to outliers and varying cluster shapes
5. **Ward's Linkage:**
    - Ward's linkage minimises the variance when merging two clusters
    - It aims to minimise the increase in total within-cluster variance after merging clusters, resulting in compact and spherical clusters
    - Ward's linkage is often used when the goal is to find clusters of approximately equal size and variance

## Limitations

1. **Computational Complexity and Memory Requirements:** especially for large datasets, due to the need to compute pairwise distances between all data points
2. **Difficulty in interpreting Dendrograms:** especially in datasets with many data points or clusters
3. **Sensitivity to Noise and Outliers:** which can affect the structure of the resulting dendrogram and cluster assignments
4. **Assumption of Hierarchical Structure:** which may not always be the case in real-world datasets
5. **Subjectivity in Determining the Number of Clusters:** Hierarchical clustering does not inherently determine the number of clusters, requiring users to interpret dendrograms and manually select the number of clusters.