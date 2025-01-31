## What is k-means clustering?

K-means clustering is an unsupervised learning algorithm used for data clustering, which groups unlabeled data points into groups or clusters.

It is one of the most popular clustering methods used in machine learning. Unlike supervised learning, the training data that this algorithm uses is unlabeled, meaning that data points do not have a defined classification structure.

While various types of clustering algorithms exist, including exclusive, overlapping, hierarchical and probabilistic, the k-means clustering algorithm is an example of an exclusive or "hard" clustering method. This form of grouping stipulates that a data point can exist in just one cluster. This type of cluster analysis is commonly used in data science for market segmentation, document clustering, image segmentation and image compression. The k-means algorithm is a widely used method in cluster analysis because it is efficient, effective and simple.

K-means is an iterative, [centroid-based clustering algorithm](https://www.ibm.com/topics/clustering) that partitions a dataset into similar groups based on the distance between their centroids. The centroid, or cluster center, is either the main or medial of all the points within the cluster depending on the characteristics of the data.

## How does k-means clustering work?

K-means clustering is an iterative process to minimize the sum of distances between the data points and their cluster centroids.

The k-means clustering algorithm operates by categorizing data points into clusters by using a mathematical distance measure, usually euclidean, from the cluster center. The objective is to minimize the sum of distances between data points and their assigned clusters. Data points that are nearest to a centroid are grouped together within the same category. A higher k value, or the number of clusters, signifies smaller clusters with greater detail, while a lower k value results in larger clusters with less detail.

#### Initialize K

The conventional k-means clustering algorithm requires a few steps. The first step is to initialize k centroids when k is equal to the number of clusters chosen for a specific dataset. This approach uses either random selection or initial centroid sampling methods.

#### Assign centroids

The next step includes a two-step iterative process based on the expectation maximization machine learning algorithm. The expectation step assigns each data point to its closest centroid based on distance (again, usually euclidean). The maximization step computes the mean of all the points for each cluster and reassigns the cluster center, or centroid. This process repeats until the centroid positions have reached convergence or the maximum number of iterations have been reached.

K-means clustering is simple yet sensitive to initial conditions and outliers. It is important to optimize the centroid initialization and the number of clusters k, to achieve the most meaningful clusters. There are several ways to evaluate and optimize clustering components of the algorithm by using [[notes/IOAI/evaluation metrics]] and initial centroid sampling methods.

## Cluster evaluation metrics

Quality clusters contain at least two properties:
1. All data points within a cluster should be similar.
2. Clusters should be distinct from each other.

These properties are achieved by minimizing the intracluster distance and maximizing the intercluster distance of all points in a dataset. In other words, the more compact and isolated a cluster is from other clusters, the better. The goal of the k-means clustering algorithm is to minimize the sum of squared errors (SSE). Computing the SSE of the squared euclidean distance of each point to its closest centroid evaluates the quality of the cluster assignments by measuring the total variation within each cluster.

Cluster evaluation metrics check the quality and provide different perspectives to analyze clustering results. This helps in selecting the optimal number of clusters and centroid initialization. The following evaluation metrics are common ways to measure the intra and intercluster distances in clustering.

#### Inertia

The k-means clustering algorithm aims to choose centroids, or cluster centers, that minimize inertia, an evaluation metric that measures how well a dataset has been clustered based on distance metrics. Inertia is calculated by measuring the distance between a datapoint and its centroid, squaring the distance and summing those squares for each data point in the cluster. The sum of inertial value is the intracluster distance. The lower the sum the better because it means that the datapoints within the cluster are compact or more similar.

#### The Dunn index

The second property is measured within the Dunn index. The Dunn index represents the relationship between the minimum intercluster distance and the maximum intracluster distance. Clusters with a high intercluster distance indicate better quality because it means that the clusters are as different from each other as possible.

## Optimizing k-means performance

Optimization is important when using k-means to achieve the best clustering results.

The k-means algorithm is nondeterministic due to its random initialization step. The method implies that if the algorithm is performed twice on identical data, the cluster assignments might differ. To achieve optimal clustering results, properly selecting the initial centroids and the optimum number of clusters improves the accuracy and the speed of the k-means algorithm.

#### Initializing the cluster centroids

Each cluster is represented by a centroid, a data point that represents the cluster center. K-means groups together similar data points into clusters by minimizing the distance between data points in a cluster with their centroid or k mean value. The primary goal of the k-means algorithm is to minimize the total distances between points and their assigned cluster centroid. The algorithm operates iteratively, and initial partition selection can greatly impact the resulting clusters.

Random initialization risks yielding inconsistent result. Centroid initialization methods exist to mitigate these risks. A study by NUS computing explains and compares methods such as the popular k-means++ to random initialization.

#### K-means++

K-means++ is a k-means algorithm that optimizes the selection of the initial cluster centroid or centroids. Developed by researchers Arthur and Vassilvitskii, k-means++ improves the quality of the final cluster assignment.

The first step to initialization by using the k-means++ method is to choose one centroid from the data set. For each subsequent centroid, calculate the distance of each data point from its closest cluster center. The subsequent centroid is selected by considering the likelihood that a point is at a proportional distance from the nearest centroid chosen earlier. The process executes iterations until the chosen number of cluster centers have been initialized.

Here is a [tutorial](https://developer.ibm.com/tutorials/awb-k-means-clustering-in-python/) from IBM developer that uses k-means++ method for initialization.

#### Choosing the optimal number of clusters

Ideally, the k-means algorithm iterates until the optimal number of clusters are reached. The maximum number of iterations are met once the centroids have achieved convergence.

#### The elbow method

One method to achieve the optimal number of clusters is the elbow method. The elbow method is a graphical method for finding the optimum number of clusters within a k-means clustering algorithm. It measures the euclidean distance between each data point and its cluster center and chooses the number of clusters based on where change in "within cluster sum of squares" (WCSS) levels off. This value represents the total variance within each cluster that gets plotted against the number of clusters.

The first step of the elbow method is to calculate the WCSS for each cluster (k). Then, the WCSS value is plotted along the y-axis and the number of clusters is plotted on the x-axis. As the number of clusters increases, the plot points should form a consistent pattern. From this pattern, results a range for the optimum number of clusters. When deciding on the number of clusters, consider the computational costs. The higher the number of clusters, the more processing power is needed especially with large datasets.

This method isn't necessarily the best, especially for datasets with high dimensionality or irregular shape. Another method for choosing the optimum number of clusters is the silhouette analysis.

![[notes/IOAI/k-means clustering elbow.png]]

## Applications in machine learning

The k-means clustering algorithm is used in almost every domain and industry. It's typically applied to machine learning data that has few dimensions, is numeric and can be easily portioned.

Researchers have integrated k-means clustering with deep learning methods such as [[notes/IOAI/cnns|CNNs]] and [[notes/IOAI/rnns|RNNs]] to enhance the performance of various machine learning tasks such as computer vision, NLP and many other domains.

See more at: https://www.ibm.com/think/topics/k-means-clustering