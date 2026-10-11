# DBSCAN

Density-Based Spatial Clustering of Applications with Noise

1. **Density-Based Approach:** It groups together points that are closely packed, identifying regions of high density separated by regions of low density
    
    Does not assume that clusters have a specific shape or size, making it more flexible in identifying clusters of arbitrary shapes and sizes
    
2. **No Predefined Number of Clusters**
3. **Robust to Noise and Outliers:** It can identify and disregard points that do not belong to any cluster, classifying them as noise
4. **Cluster Representation:** DBSCAN represents clusters as dense regions separated by areas of low density. It does not assign each point to a single cluster but rather identifies core points, border points, and noise points based on their density and proximity to other points.
5. **Parameter Selection:** DBSCAN requires two main parameters
    1. **epsilon (*ϵ*):** defines the radius within which to search for neighboring points
    2. **MinPts**: specifies the minimum number of points required to form a dense region

## Approach

1. **Core Points:**
    - In density-based clustering, a core point is a data point that has at least a specified number of neighboring points within a given radius (*ϵ*)
    - Core points are considered to be at the heart of clusters and represent regions of high density in the dataset.
2. **Border Points:**
    - A border point is a data point that is within the neighborhood (*ϵ*radius) of a core point but does not have enough neighbors to be considered a core point itself.
    - Border points lie on the outskirts of clusters and are often included in clusters due to their proximity to core points.
3. **Noise Points:**
    - Noise points are data points that are neither core points nor border points and do not belong to any cluster.
    - Noise points are typically isolated points that do not fit well into any cluster due to their low density or distance from other points.
4. **Density-Reachability:**
    - A data point *P* is density-reachable from another data point *Q* if there is a chain of core points connecting them, such that each successive core point is within the neighborhood (*ϵ*radius) of the previous core point
    - Density-reachability captures the notion of density-based connectivity between points in the dataset
5. **Density-Connectivity:**
    - Two data points are density-connected if there exists a common core point from which they are both density-reachable.
    - Density-connectivity allows clusters to form even if they are not directly connected but are reachable through a series of core points.

**Steps**

1. The algorithm starts by randomly selecting a data point and determining whether it is a core point based on the number of neighboring points within the specified radius (*ϵ*)
2. If a core point is found, DBSCAN recursively expands the cluster by adding density-reachable points to it
3. Border points that are within the neighborhood of a core point are added to the cluster, and their neighborhood is explored to find additional core and border points
4. Data points that are not density-reachable from any core point are labeled as noise points and do not belong to any cluster
5. DBSCAN continues this process until all data points have been assigned to clusters or labeled as noise.