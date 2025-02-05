## Overfitting VS underfitting

When data scientists and engineers train machine learning models, they risk using an algorithm that is too simple to capture the underlying patterns in the data, leading to underfitting, or on that is too complex, leading to overfitting. Managing [overfitting](https://www.ibm.com/topics/overfitting) and [underfitting](https://www.ibm.com/topics/underfitting) is a core challenge in data science workflows and developing reliable artificial intelligence systems.

## Bias and variance in machine learning

![[notes/IOAI/overfitting diagram.png]]

Bias and variance explain the balance engineers need to strike to help ensure a good fit in their machine learning models. As such, the bias-variance tradeoff is central to addressing underfitting and overfitting.

A biased model makes strong assumptions about the training data to simplify the learning process, ignoring subtleties or complexities it cannot account for. Variance refers to the model's sensitivity to learning fluctuations in the training data.

Examples of high-bias models include linear regression algorithms or shallow decision trees, which assume simple linear or binary relationships even when the data patterns are more complex

Using linear regression model for data with a quadratic relationship will result in underfitting because the linear model cannot capture the inherent curvature. As a result, the model performs poorly on the training set and unseen test data because it cannot generalize well to new data.

Generalization is the model's ability to understand and apply learned patterns to unseen data. Models with low variance also tend to underfit as they are too simple to capture complex patterns. However, low-bias models might overfit if they are too flexible.

High variance indicates that the model capture noise, idiosyncrasies and random details within the training data. High-variance models are overly flexible, resulting in low training error, but when tested on new data, the learned patterns fail to generalize, leading to high test error.

## How to recognize overfitting and underfitting

#### The rules
- **Overfitting:** Training error is low, but testing error is significantly higher.
- **Underfitting:** Errors are consistently high across training and testing data sets.

An **overfit model** can result in high model accuracy on training data but low accuracy on new data due to memorization instead of generalization. Overfitting happens  when engineers use a machine learning model with too many parameters or layers, such as deep learning neural network, making it highly adaptable to the training data.

When trained on a small or noisy data set, the model risks memorizing specific data points and noise rather than learning the general patterns. If the data contains errors or inconsistencies, the model might incorrectly learn these as meaningful patterns.

Engineers look for a performance gap between training and testing, but they can also detect overfitting in learning curves, where training loss decreases toward zero while validation loss increases, indicating poor generalization.

Another sign of an overfit model is its decision boundaries, the model's learned rules for classifying data points. The decision boundary comes overly complex and erratic in overfit models, as it adapts to noise in the training set rather than capturing true underlying structures, further indicating overfitting.

![[notes/IOAI/underfitting diagram.png]]

In addition, high-dimensional data sets can lead to overfitting due to the "curse of dimensionality". As the number of features increases, data points become sparse, making it harder for models to find meaningful patters, increasing variance and the risk of overfitting.

An **underfit model** performs poorly on training data and testing data because it fails to capture the dominant patterns in the data set. Engineers typically identify underfitting through consistently poor performance across both data sets.

Underfit models also tend to show high errors in learning curves, return suboptimal evaluation metrics and exhibit systematic residual patterns, all of which indicate an inability to learn the underlying relationships in the data effectively.

Underfitting in machine learning often occurs due to simplistic models, poor [feature engineering](https://www.ibm.com/topics/feature-engineering) or excessive [regularization](https://www.ibm.com/topics/regularization) that overly restricts the model's flexibility. Similarly, poor feature selection - such as omitting interaction terms or polynomial features - can prevent the model from understanding hidden relationships in the data. Inadequate preprocessing, insufficient training time or a lack of sufficient data to train the model can also contribute to underfitting.

## Examples of overfitting and underfitting

#### Overfitting

- **Medical diagnosis model:** A machine learning model is trained to classify medical images as "healthy" or "diseased" on a small data set. The model memorizes the training images, achieving near-perfect accuracy but performs poorly on new images because it has learned specific noise or artifacts in the training data instead of general disease features.
- **Stock price prediction:** A financial model uses a complex neural network with many parameters to predict stock prices. Instead of learning trends or patterns, it captures random fluctuations in historical data, leading to highly accurate training predictions but poor performance when tested on future stock prices.
- **Customer churn prediction:** A customer retention model includes too many specific features, such as highly detailed demographic data, causing it to overfit the training data. It struggles to generalize and identify patterns across different demographics when applied to a broader customer base.

#### Underfitting

- **Housing price prediction:** A linear regression model predicts house prices based solely on square footage. The model fails to account for other important features such as location, number of bedrooms or age of the house, leading to poor performance on training and testing data.
- **Weather forecasting:** A model uses a small set of simple features, such as average temperature and humidity to predict rainfall. It fails to capture more complex relationships, such as seasonal patterns or interactions between multiple atmospheric factors, resulting in consistently poor accuracy.
- **Image recognition:** A shallow decision tree is used to classify images of cats and dogs. Due it its simplicity, it fails to differentiate between the two species, performing poorly on training images and new, unseen ones.

## How to avoid overfitting and underfitting

Machine learning algorithms train models to recognize patterns in data, enabling engineers to use them for forecasting future outcomes for unseen inputs. Hyperparameter tuning plays a large role in balancing overfitting and underfitting, ensuring a predictive model generalizes effectively to unseen data.

By using hyperparameters, engineers can fine-tune the learning rate, regularization strength, the number of layers in a neural network or the maximum depth of a decision tree. Proper tuning can prevent a model from being too rigid or overly adaptable.

### Overfitting

**Regularization**

Regularization for regression models or dropout in neural networks, is a technique used in machine learning by discouraging the model from relying too heavily on any single feature or from fitting noise in the training data.

Common types of regularization include L1, which encourages sparsity by shrinking some coefficients to zero and L2, which reduces the size of all coefficients to make the model simpler and more generalizable. Regularization helps the model focus on the underlying patterns rather than memorizing the data.

**Data augmentation**

Data augmentation is another effective strategy, especially in tasks such as computer vision, where artificially expanding the training data by flipping, rotating or cropping images helps the model generalize better. Simplifying the model by reducing the number of parameters or layers in a neural network also limits its ability to memorize training data details.

**K-fold cross-validation**

Engineers can use techniques such as k-fold cross-validation for evaluating model generalization as well. K-fold cross-validation splits the data into subsets, trains on some and tests on the remaining.

Similarly, engineers can use a holdout set, information from the training set to be reserved as unseen data to provide another means to assess generalization performance. The results are then averaged to provide an overall performance score.

![[notes/IOAI/k-fold cross-validation.png]]

**Evaluation frameworks**

In addition to these techniques, robust model evaluation frameworks are essential for ensuring that a machine learning model generalizes well. One advanced evaluation technique is nested cross-validation, which is particularly useful for hyperparameter tuning. In nested cross-validation, an outer loop splits the data into training and testing subsets to evaluate the model's generalization ability.

At the same time, an inner loop performs hyperparameter tuning on the training data to help ensure that the tuning process does not overfit the validation set. This approach separates hyperparameter optimization from model evaluation, providing a more accurate estimate of the model's performance on unseen data.

Another effective framework combines train-test splits with early stopping to monitor validation loss during training. By evaluating the model's performance on a dedicated validation set, engineers can halt training when validation performance plateaus or degrades, preventing overfitting.

Evaluation frameworks should include stratified sampling for classification problems with imbalanced data sets to help ensure that each data split maintains the same class distribution as the original data set. This prevents overfitting to majority classes while providing a fair assessment of the performance of minority classes.

**Ensemble methods**

Ensemble methods, such as bagging and boosting, combine multiple models to mitigate individual weaknesses and improve overall generalization. For instance, random forests, a popular ensemble technique, reduces overfitting by aggregating predictions from multiple decision trees, effectively balancing bias and variance.

### Underfitting

**More complex models**

To address underfitting, engineers often increase the model's complexity to better capture the underlying patters in the data. For instance, switching form simple linear regression to a polynomial regression can help is cases where the relationship features and the target variable are nonlinear. While more complex models can address underfitting, they risk overfitting if not regularized properly.

**Regularization**

Reducing regularization penalties can also allow the model more flexibility to fit the data without being overly constrained. For example, L1 and L2 parameters are types of regularization used to check the complexity of a model. L1 ([lasso](https://www.ibm.com/topics/lasso-regression)) adds a penalty to encourage the model to select only the most important features. L2 ([ridge](https://www.ibm.com/topics/ridge-regression)) helps lead the model to a more evenly distributed importance across features.

**Feature engineering**

Feature engineering and selection play a role in creating or transforming features - such as adding interaction terms, polynomial features or encoding categorical variables - to provide the model with more relevant information.

**Training time**

Allowing the model more training time by increasing the number of epochs helps ensure that it has an adequate opportunity to learn from the data. An epoch represents one complete pass through the training data set and multiple epochs allow the model to learn patterns more effectively.

Multiple epochs are often used to allow the model to learn patterns in the data more effectively. Also, increasing the size of the training data set helps the model identify more diverse patterns, reducing the risk of oversimplification and improving generalization.

**Data quality**

Holistically, engineers should thoroughly assess training data for accuracy, completeness and consistency, cross-verifying it against reliable sources to address any discrepancies. Techniques such as normalization (scaling values between 0 and 1) or standardization (scaling to a mean of 0 and standard deviation of 1) help ensure that the model does not favor certain variables over others due to differing scales.

With time, input data distributions might shift - a phenomenon known as data drift - which can cause models to underfit or overfit the new data. To counter this, regular monitoring and periodic retraining with updated data sets are essential. Removing outliers can also help prevent skewed results and improve the model's robustness.

Tools such as [AutoML](https://www.ibm.com/topics/automl) can further streamline process by automating hyperparameter tuning, feature selection and the creation of model evaluation frameworks, enabling engineers to focus on higher-level insights and decision-making.

## Achieving the optimal model fit

A good model fit lies at the optimal balance between underfitting and overfitting. It describes a model that accurately captures the underlying patters in the data without being overly sensitive to noise or random fluctuations.

- The tradeoff between model complexity and generalization is about finding the right balance between a model being too simple or too complex.
- Engineers must balance bias and variance to achieve optimal model performance. One way to do this is by tracking learning curves, which will show training and validation errors over time.
- Analyzing validation metrics such as accuracy, precision, recall or mean squared error helps evaluate how well the model generalizes to unseen data.
- A good fit model carefully balances model complexity, training data and regularization techniques to generalize well to new data and provide accurate predictions.

See more at: https://www.ibm.com/think/topics/overfitting-vs-underfitting