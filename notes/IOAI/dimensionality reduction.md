## What is dimensionality reduction?

Dimensionality reduction techniques such as PCA, LDA and t-SNE enhance machine learning models. They preserve essential features of complex data sets by reducing the number of predictor variables for increased generalizability.

Dimensionality reduction is a method for representing a given dataset using a lower number of features (that is, dimensions) while still capturing the original data's meaningful properties. This amounts to removing irrelevant or redundant features, or simply noisy data, to create a model with a lower number of variables. Dimensionality reduction covers an array of feature selection and data compression methods used during preprocessing. While dimensionality reduction methods differ in operation, they all transform high-dimensional spaces into low-dimensional spaces through variable extraction or combination.

## Why use dimensionality reduction?

In machine learning, dimensions (or features) are the predictor variables that determine a model's output. They may also be called input variables. High-dimensional data denotes any dataset with a large number of predictor variables. Such datasets can frequently appear in biostatistics, as well as social science observational studies, where the number of data points (that is, observations) outweighs the number of predictor variables.

High-dimensional datasets pose a number of practical concerns for machine learning algorithms, such as increased computation time, storage space for big data, and so on. But the biggest concern is perhaps decreased accuracy in predictive models. Statistical and machine learning models trained on high-dimensional datasets often generalize poorly.

## Curse of dimensionality

The curse of dimensionality refers to the inverse relationship between model dimensions and decreasing generalizability. As the number of model input variables increase, the model's space increases. If the number of data points remains the same, however, the data becomes sparse. This means the majority of the model's feature space is empty, that is, without observable data points. As data sparsity increases, data points become so dissimilar that predictive models become less effective at identifying explanatory patterns.

In order to adequately explain patters in sparse data, models may [[notes/IOAI/overfitting|overfit]] on training data. In this way, increases in dimensionality can lead to poor generalizability. High-dimensionality can further inhibit model interpretability by inducing multicollinearity. As the quantity of model variables increase, so does the possibility that some variables are redundant or correlated.

Collecting more data can reduce data sparsity and thereby offset the curse of dimensionality. As the number of dimensions in a model increase, however, the number of data points needed to impede the curse of dimensionality increases exponentially. Collecting sufficient data is, of course, not always feasible. Thus, the need for dimensionality reduction to improve data analysis.

![[notes/IOAI/curse of dimensionality diagram.png]]

## Dimensionality reduction methods

Dimensionality reduction techniques generally reduce models to a lower-dimensional space by extracting or combining model features. Beyond this base similarity, however, dimensionality reductions algorithms vary.

#### Principal components analysis.

[[notes/IOAI/principal component analysis|Principal component analysis]] (PCA) is perhaps the most common dimensionality reduction method. It is a form of feature extraction, which means it combines and transforms the dataset's original features to produce new features, called principal components. Essentially, PCA selects a subset of variables from a model that together comprise the majority or all the variance present in the original set of variables. PCA then projects data onto a new space defined by this subset of variables.

#### Linear discriminant analysis

[Linear discriminant analysis](https://www.ibm.com/topics/linear-discriminant-analysis) (LDA) is similar to PCA in that it projects data onto a new, lower dimensional space, the dimensions for which are derived from the initial model. LDA differs from PCA in its concern for retaining classification labels in the dataset. While PCA produces new component variables meant to maximize data variance, LDA produces component variables that also maximize class difference in data.

Steps for implementing LDA are similar to those for PCA> The chief exception is that the former uses the scatter matrix whereas the latter uses the covariance matrix. Otherwise, much as in PCA, LDA computes linear combinations of the data's original features that corresponded to the largest eigenvalues from the scatter matrix. One goal of LDA is to maximize interclass difference while minimizing intraclass difference.

#### T-distributed stochastic neighbor embedding

LDA and PCA are types of linear dimensionality reduction algorithms. T-distributed stochastic neighbor embedding (t-SNE), however, is a form of non-linear dimensionality reduction (or, manifold learning). In aiming to principally preserve model variance, LDA and PCA focus on retaining distance between dissimilar datapoints in their lower dimensional representations. In contrast, t-SNE aims to preserve the local data structure with reducing model dimensions, so long as their generated model has less dimensions that the original data. t-SNE, however, visualizes all datasets in either three or two dimensions.

As a non-linear transformation methods, t-SNE foregoes data matrices. Instead, t-SNE utilizes a Gaussian kernel to calculate pairwise similarity of datapoints. Points near one another in the original dataset have a higher probability of being near one another than those further away. t-SNE then maps all of the datapoints onto a three or two-dimensional space while attempting to preserve data pairs.

There are a number of additional dimensionality reduction methods, such as kernel PCA, factor analysis, random forests, and singular value decomposition (SVD). PCA, LDA and t-SNE are among the most widely used and discussed. Note that several package and libraries, such as scikit-learn, come preloaded with functions for implementing these techniques.