## Credit Card Fraud Detection

### Introduction
The datasets contains transactions made by credit cards in September 2013 by european cardholders. This dataset presents transactions that occurred in two days, where we have 492 frauds out of 284,807 transactions. The dataset is highly unbalanced, the positive class (frauds) account for 0.172% of all transactions.

It contains only numerical input variables which are the result of a PCA transformation.

Due to confidentiality issues, there are not provided the original features and more background information about the data.

Features V1, V2, ... V28 are the principal components obtained with PCA;
The only features which have not been transformed with PCA are Time and Amount. Feature Time contains the seconds elapsed between each transaction and the first transaction in the dataset. The feature Amount is the transaction Amount, this feature can be used for example-dependant cost-senstive learning.
Feature Class is the response variable and it takes value 1 in case of fraud and 0 otherwise.

### Isolation Forest Algorithm :
Isolation Forests is a relatively novel technique used for detecting anomalies in data. Here's a deeper dive into its principles and workings:

#### Principles:
Anomaly Detection: The core premise of Isolation Forests is based on the idea that anomalies are typically rare instances that are significantly different from the majority of the data points. These anomalies are more 'isolated' compared to normal data points.

Isolation Mechanism: Anomalies are deemed easier to isolate due to their uniqueness and rarity. This is in contrast to normal data points, which require more conditions or splits to separate them from the rest of the data.

#### Key Features:
Efficiency: Isolation Forests are highly efficient. They have a low linear time complexity and a minimal memory requirement, making them suitable for processing large datasets.

Random Sub-sampling: The algorithm builds multiple random decision trees (isolation trees) using small sub-samples of fixed size from the dataset. This process remains consistent regardless of the size of the dataset.

#### Working Mechanism:
Feature and Split Selection: The algorithm randomly selects a feature and then chooses a split value within the range of the selected feature's maximum and minimum values.

Isolation Tree Construction: Isolation trees are constructed by repeatedly partitioning the dataset based on random feature selections and split values. This process creates a collection of random decision trees.

Anomaly Score Calculation: The anomaly score for each data point is determined by the path length required to isolate that observation in the constructed isolation trees. Anomalies are expected to have shorter path lengths, indicating easier isolation.

#### Advantages:
Effectiveness: Isolation Forests are particularly effective at detecting anomalies, especially in scenarios where anomalies are rare and distinctly different from normal data points.

Robustness: The method is robust to the presence of noise and outliers in the data, making it suitable for various real-world applications.

Scalability: Isolation Forests are scalable to large datasets due to their efficient algorithmic design and minimal memory requirements.

Overall, Isolation Forests offer a promising approach to anomaly detection, leveraging the concept of isolation and random partitioning to efficiently identify rare and unusual instances in data.

### Local Outlier Factor(LOF) Algorithm:
TThe LOF (Local Outlier Factor) algorithm is a popular unsupervised outlier detection method that evaluates the local density deviation of a data point compared to its neighboring points. Here's a more detailed explanation of its principles and workings:

#### Principles:
Local Density Estimation: LOF assesses the density of a data point within its local neighborhood. It measures how densely packed the data points are around a given point.

Outlier Identification: Anomalies are identified as data points with significantly lower local density compared to their neighbors. These points are considered outliers as they deviate from the expected density pattern.

#### Key Features:
Parameter: n_neighbors: This parameter specifies the number of neighbors considered when calculating the local density of a data point. It's typically chosen based on certain considerations:
It should be greater than the minimum number of objects a cluster has to contain, ensuring that outliers can be identified relative to clusters.
It should be smaller than the maximum number of nearby objects that could potentially be outliers.
In practice, choosing n_neighbors=20 is often found to be effective when these considerations are not explicitly available.
Working Mechanism:
Local Density Computation: For each data point, LOF computes the local density based on the distance to its nearest neighbors. Points in dense regions have higher local densities, while points in sparse regions have lower local densities.

Outlier Score Calculation: The LOF score for each data point quantifies its deviation from the local density of its neighbors. Lower LOF scores indicate potential outliers, as they suggest a significant drop in density compared to neighboring points.

Threshold Determination: An appropriate threshold is set to classify data points as outliers based on their LOF scores. Points exceeding this threshold are flagged as anomalies.

#### Advantages:
Flexibility: LOF is adaptable to various types of datasets and can handle data with irregular shapes and varying densities effectively.

Parameter Robustness: While the choice of n_neighbors can impact the algorithm's performance, LOF tends to be robust to parameter variations, making it suitable for practical applications.

Scalability: LOF is relatively scalable to large datasets, although computational complexity increases with the dataset size.

#### Limitations:
Sensitive to Parameter Settings: While LOF is generally robust to parameter variations, suboptimal parameter choices can impact its performance.

Computationally Intensive: Calculating LOF scores for each data point can be computationally intensive, especially for large datasets with high dimensionality.

Overall, LOF offers a powerful approach to outlier detection by leveraging local density estimation. It provides a flexible and effective method for identifying anomalies in various real-world datasets.
