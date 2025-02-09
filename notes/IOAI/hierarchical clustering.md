## What is hierarchical clustering?

Hierarchical clustering is an unsupervised machine learning algorithm that groups data into a tree of nested clusters. The main types include agglomerative and divisive. Hierarchical cluster analysis helps find patterns and connections in datasets. Results are presented in a dendrogram diagram showing the distance relationships between clusters.

Clustering is an unsupervised machine learning technique used in data analysis to detect and group similar objects. Hierarchical clustering analysis (HCA), or hierarchical clustering, groups objects into a cluster hierarchy without enforcing a linear order within them. Many disciplines, such as biology, imagine analysis and the social sciences, use hierarchical clustering methods to explore and recognize patterns in datasets. Use cases include categorizing populations in clinical research, customer segmentation and detecting communities of nodes in network models.

There are two types of hierarchical clustering:

- Agglomerative or bottom-up approach that repeatedly merges clusters into larger ones until a single cluster emerges.
- Divisive or top-down approach that starts with all data in a single cluster and continues to split out successive clusters until all clusters are singletons.

Hierarchical clustering analysis has high computational costs. While using a heap can reduce computation time, memory requirements are increased. Both the divisive and agglomerative types of clustering are "greedy", meaning that the algorithm decides which clusters to merge or split by making the locally optimal choice at each stage of the process. It is also possible to apply a stop criterion, where the algorithm stops agglomeration or splitting clusters when it reaches a predetermined number of clusters.

A tree-like diagram called a dendrogram is often used to visualize the hierarchy of clusters. It displays the order in which clusters have been merged or divided and shows the similarity or distance between data points. Dendrograms can also be understood as nested lists of lists with attributes.

More at: https://www.ibm.com/think/topics/hierarchical-clustering