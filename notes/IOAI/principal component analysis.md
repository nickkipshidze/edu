## What is principal component analysis?

Principal component analysis (PCA) reduces the number of dimensions in large datasets to principal components that retain the most of the original information. It does this by transforming potentially correlated variables into a smaller set of variables, called principal components.

Karl Pearson is credited with the development of PCA in 1901, but it gained popularity with the increased availability of computers, which allowed datasets, or data with many features, as it can easily identify trends, patters, or outliers.

PCA is commonly used for data preprocessing for use with machine learning algorithms. It can extract the most informative features from large datasets with preserving the most relevant information from the initial dataset. This reduces model complexity as the addition of each new feature negatively impacts the model performance, which is also commonly referred to as the "curse of dimensionality". By projecting a high-dimensional dataset into a smaller feature space, PCA also minimizes, or altogether eliminates, common issues such as multicollinearity and [[notes/IOAI/overfitting|overfitting]]. Multicollinearity occurs when two or more independent variables are highly correlated with one another, which can be problematic for casual modeling. Overfit models will generalize poorly to new data, diminishing their value altogether. PCA is a commonly used approach within regression analysis but it is also leveraged for a variety of use cases, such as pattern recognition, signal processing, image processing, and more.

While there are other variations of PCA, such as principal component regression and kernel PCA, the scope of this article will focus on the primary method within current literature.

## PCA vs LDA vs factor analysis

PCA is a dimension reduction technique like [linear discriminant analysis](https://www.ibm.com/topics/linear-discriminant-analysis) (LDA). In contrast to LDA, PCA is not limited to supervised learning tasks. For unsupervised learning tasks, this means PCA can reduce dimensions without having to consider class labels or categories. PCA is also closely related to factor analysis. They both reduce the number of dimensions or variables is a dataset while minimizing information loss. PCA breaks down variables into a subset of linearly independent principal components. Factor analysis, however, is generally used to understand underlying data structures, focusing on latent variables, or unmeasured factors, that capture a variable's spread.

### PCA vs K-means clustering

PCA and [[notes/IOAI/k-means clustering|k-means clustering]] are both unsupervised machine learning techniques used for data analysis, but they have different goals and methods. PCA is used to reduce the dimensionality of the data, while k-means clustering groups data points together based on similarity. The technique you select depends on the specific dataset and goals of your analysis.

PCA creates new variables, such as principal components, that are linear combinations of the original variables. PCA takes a dataset with multiple variables as input, and it produces a dataset into a lower subspace, that is, a reduced dataset with fewer variables. It is often used in [exploratory data analysis](https://www.ibm.com/topics/exploratory-data-analysis) for building predictive models, but it is also used in data preprocessing for dimensionality reduction.

K-means is a clustering algorithm that assigns data points to clusters based on their distance from the cluster centers. It takes a dataset with one or more variables as input, and it produces a set of clusters with similar data points. It is often used to cluster data for a variety of use cases, such as image segmentation, customer segmentation, and anomaly detection.

## How principal component analysis works

PCA summarizes the information content of large datasets into a smaller set of uncorrelated variables known as principal components. These principal components are linear combinations of the original variables that have the maximum variance compared to the other linear combinations. These components capture as much information from the original dataset as possible.

This statistical technique involves both linear algebra and matrix operations, and it transforms the original dataset into a new coordinate system that is structured by the principal components. The eigenvectors and eigenvalues from the covariance matrix that underpin the principal components allow for the analysis of these linear transformations.

Imagine you have mapped out a dataset with multiple features, resulting in a multi-dimensional scatterplot. Eigenvectors provide the direction of variance in the scatterplot. Eigenvalues are the coefficients of the eigenvectors; these denote the importance of this directional data. Therefore, a high eigenvalue means that the corresponding eigenvector is more critical. Since principal components represent the directions of maximum variance in the data, they are also the eigenvectors of the covariance matrix.

Two major components are calculated in PCA: the first principal component (PC1) and the second principal component (PC2).

#### First principal component

We calculate the second principal component (PC2) in the same way as PC1. PC2 accounts for the next highest variance in the dataset and must be uncorrelated with PC1. This is, PC2 must be orthogonal, that is perpendicular, to PC1. This relationship can also be expressed as the correlation between PC1 and PC2 equals zero.

A scatterplot is typically used to show the relationship between PC1 and PC2 when PCA is applied to a dataset. PC1 and PC2 axis will be perpendicular to each other.

![[notes/IOAI/principal component analysis diagram.png]]

If there are any subsequent components, then they would also retain the same properties, where they would not be correlated with other components and explain any remaining variation.

## Calculating principal components

The PCA computation process is summarized in the steps below, showing that how the principal components are calculated and how they relate to the original data.

#### Standardize the range of continuous initial variables

Since PCA can bias towards specific features, it is important to evaluate whether normalization of data is needed. Data should reflect a normal distribution with a mean of zero and a standard deviation of one.

In this step, the mean values of the variables are calculated and subtracted from the original dataset so that each variable contributes equally to the analysis. This value is then divided by the standard deviation for each variable so that all variables use the same scale.

#### Compute the covariance matrix to identify correlations

Covariance (cov) measures how strongly correlated two or more variables are. The covariance matrix summarizes the covariances associated with all pair combinations of the initial variables in the dataset. Computing the covariance matrix helps identify the relationships between the variables - that is, how the variables vary from the mean with respect to each other. This data matrix is a symmetric matrix, meaning the variable combinations can be represented as d x d, where d is the number of dimensions. For example, for a 3-dimensional dataset, there would be 3 x 3 or 9 variable combinations in the covariance matrix.

The sign of the variable in the matrix tells us whether combinations are correlated:

- Positive (the variables are correlated and increase or decrease at the same time)
- Negative (the variables are not correlated, meaning that one decreases while the other increases)
- Zero (the variables are not related to each other)

#### Compute the eigenvectors and eigenvalues of the covariance matrix

Here, we calculate the eigenvector (principal components) and eigenvalues of the covariance matrix. As eigenvectors, the principal components represent the directions of maximum variance in the data. The eigenvalues represent the amount of variance in each component. Ranking the eigenvectors by eigenvalue identifies the order of principal components.

#### Select the principal components

Here, we decide which components to keep and those to discard. Components with low eigenvalues typically will not be as significant. Scree plots usually plot the proportion of total variance explained as the cumulative proportion of variance. These metrics help one to determine the optimal number of components to retain. The point at which the Y axis of eigenvalues or total variance explained creates an "elbow" will generally indicate how many PCA components that we want to include.

#### Transform the data into the new coordinate system

Finally, the data is transformed into the new coordinate system defined by the principal components. That is, the feature vector created from the eigenvectors of the covariance matrix projects the data onto the new axes defined by the principal components. This creates new data, capturing most of the information but with fewer dimensions than the original dataset.

## Interpreting PCA results

A PCA plot is a scatter plot created by using the first two principal components as axes. The first principal components (PC1) is the x-axis, and the second principal component (PC2) is the y-axis. The scatter plot shows the relationships between observations (data points) and the new variables (the principal components). The position of each point shows the values of PC1 and PC2 for that observation.

The direction and length of the plot arrows indicate the loadings of the variables, that is, how each variable contributes to the principal components. If a variable has a high loading for a particular component, it is strongly correlated with that component. This can highlight which variables have a significant impact on data variations.

The number of principal components that remain after applying PCA can help you interpret the data output. The first principal component explains the most data variance, and each later component accounts for less variance. Thus, the number of components can indicate the amount of information retained from the original dataset. Fewer components after applying PCA could mean that you didn't capture much data variation. More components indicate more data variation, but the results may be harder to interpret. You can decide the optimal number of components to retain using either a scree plot or the cumulative explained variance.

More information at: https://www.ibm.com/think/topics/principal-component-analysis