## What is logistic regression?

Logistic regression estimates the probability of an event occurring, such as voted or didn't vote, based on a given set of independent variables.

This type of statistical model (also known as logit model) is often used for classification and predictive analytics. Since the outcome is a probability, the dependent variable is bounded between 0 and 1. In logistic regression, a logit transformation is applied on the odds - that is, the probability of success divided by the probability of failure. This is also commonly known as the log odds, or the natural logarithm of odds, and this logistic function is represented by the following formulas:

> Logit(pi) = 1/(1 + exp(-pi))
> ln(pi/(1 - pi)) = Beta_0 + Beta_1 * X_1 + ... + B_k * K_k

In this logistic regression equation, logit(pi) is the dependent or response variable and x is the independent variable. The beta parameter, or coefficient, in this model is commonly estimated through maximum likelihood estimation (MLE). This method tests different values of beta through multiple iterations to optimize for the best fit of log odds. All of these iterations produce the log likelihood function, and logistic regression seeks to maximize this function to find the best parameter estimate. Once the optimal coefficient (or coefficients if there is more than one independent variable) is found, the conditional probabilities for each observation can be calculated, logged, and summed together to yield a predicted probability. For binary classification, a probability less than 0.5 will predict 0 while a probability greater than 0 will predict 1. After the model has been computed, it's best practice to evaluate the how well the model predicts the dependent variable, which is called goodness of fit. The Hosmer-Lemeshow test is a popular method to assess model fit.

## Interpreting logistic regression

Log odds can be difficult to make sense of within a logistic regression data analysis. As a result, exponentiating the beta estimates is common to transform the results into an odds ratio (OR), easing the interpretation of results. The OR represents the odds that an outcome will occur given a particular event, compared to the odds of the outcome occurring in the absence of that event. If the OR is less than 1, then the event is associated with a lower odds of that outcome occurring. Based on the equation from above, the interpretation of an odds ratio can be denoted as the following: the odds of a success changes by exp(cB_1) times for every c-unit increase in x. To use an example, let's say that we were to estimate the odds of survival on the Titanic given that the person was male, and  the odds ratio for males was 0.0810. We'd interpret the odds ratio as the odds of survival of males decreased by a factor of 0.0810 when compared to females, holding all other variables constant.

## Linear regression vs logistic regression

Both linear and logistic regression are among the most popular models within data science, and open-source tools, such as Python and R, make the computation for them quick and easy.

[[notes/IOAI/linear regression|Linear regression models]] are used to identify the relationship between a continuous dependent variable and one or more independent variables. When there is only one independent variable and one dependent variable, it is known as simple linear regression, but as the number of independent variables increases, it is referred to as multiple linear regression. For each type of linear regression, it seeks to plot a line of best fit through a set of data points, which is typically calculated using the least squares method.

Similar to linear regression, logistic regression is also used to estimate the relationship between a dependent variable and one or more independent variables, but it is used to make a prediction about a categorical variable versus a continuous one. A categorical variable can be true or false, yes or no, 1 or 0, et cetera. The unit of measure also differs from linear regression as it produces a probability, but the logit function transforms the S-curve into a straight line.

While both models are used in regression analysis to make predictions about future outcomes, linear regression is typically easier to understand. Linear regression also does not require as large of a sample size as logistic regression needs an adequate sample to represent values across all the response categories. Without a larger, representative sample, the model may not have sufficient statistical power to detect a significant effect.

## Types of logistic regression

There are three types of logistic regression models, which are defined based on categorical response.

- **Binary logistic regression:** In this approach, the response or dependent variable is dichotomous in nature - that is, it has only two possible outcomes (for example 0 or 1). Some popular examples of its use include predicting if an email is spam or not spam or if a tumor is malignant of not malignant. Within logistic regression, this is the most commonly used approach, and more generally, it is one of the most common classifiers for binary classification.
- **Multinomial logistic regression:** In this type of logistic regression model, the dependent variable has three or more possible outcomes; however, these values have no specified order. For example, movie studios what to predict what genre of film a moviegoer is likely to see to market films more effectively. A multinomial logistic regression model can help the studio to determine the strength of influence a person's age, gender and dating status may have on the type of film that they prefer. The studio can then orient an advertising campaign of a specific movie toward a group of people likely to go see it.
- **Ordinal logistic regression:** This type of logistic regression model is leveraged when the responsive variable has three or more possible outcomes, but in this case, these values do have a defined order. Examples of ordinal responses include grading scales from A to F or rating scales from 1 to 5.

## Logistic regression and machine learning

Withing machine learning, logistic regression belongs to the family of supervised machine learning models. It is also considered a discriminative model, which means that it attempts to distinguish between classes (or categories). Unlike a generative algorithm, such as naive bayes, it cannot, as the name implies, generate information, such as an image, of the class that it is trying to predict (for example a picture of a cat).

Previously, we mentioned how logistic regression maximizes the log likelihood function to determine the beta coefficients of the model. This changes slightly under the context of machine learning. Within machine learning, the negative log likelihood used as the loss function, using the process of gradient descent to find the global maximum. This is just another way to arrive at the same estimations discussed above.

Logistic regression can also be prone to [[notes/IOAI/overfitting|overfitting]], particularly when there is a high number of predictor variables within the model. Regularization is typically used to penalize parameters large coefficients when the model suffers from high dimensionality.

Scikit-learn provides valuable documentation to learn more about logistic regression machine learning models.