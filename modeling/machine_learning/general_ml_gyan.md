# General ML Gyan

## Steps before starting any model training

1. Understand data
    1. Look for missing values
    2. Look for outliers, range of values in each column
2. Prepare features:
    1. Feature scaling
    2. One-hot encoding
    3. Feature transformations including multiplication of features
3. Check for feature correlation
4. Fix imbalanced data

## Q: Do class imbalance impacts decision trees and other tree based models?

Yes, class imbalance can cause **bias toward the majority class**, leading to poor classification of the minority class.

## Q: What are common ways to address class imbalance?

1. **Adjust Class Weights:** Many ML algos support class weighting to balance the impact of classes
2. **Resampling:**
    1. Oversampling Minority Class (e.g., SMOTE): Generates synthetic minority samples
    2. Undersampling Majority Class: Reduces the size of the majority class (randomly or stratified)
3. **Change Evaluation Metrics**: Instead of accuracy, use precision, recall, f1, ROC-AUC

## Q: How does SMOTE works?

- SMOTE (Synthetic Minority Over-sampling Technique)
- Traditional oversampling methods duplicate minority class samples, which can cause overfitting
- SMOTE works by generating synthetic points using K-nearest neighbors (KNN).
    
    🔹 **Step 1:** Select a random minority class sample
    
    🔹 **Step 2:** Find its **K-nearest neighbors** (other minority samples)
    
    🔹 **Step 3:** Randomly pick one of these neighbors
    
    🔹 **Step 4:** Create a new synthetic sample **along the line connecting them**
    

💡 The new synthetic point is **not a duplicate** but a **linear interpolation** between two real minority samples

🚫 **Avoid SMOTE with k-NN and clustering algorithms** (since it creates synthetic neighbors that can affect distance-based calculations).

## Q: How does perform missing value treatment?

1. Impute with Mean, Median, or Mode
2. Impute using KNN: Use the values of the nearest data points 
3. Impute Using Regression: If there is a strong correlation with another feature
4. Deleting Rows or Columns with Missing Values