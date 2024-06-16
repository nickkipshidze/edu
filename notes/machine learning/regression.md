Our main learning objective in this section is another nice example of supervised learning methods, and almost as simple as the nearest neighbor classifier too: linear regression. We'll introduce its close cousin, logistic regression as well.

> The difference between classification and regression
> 
> There is a small but important difference in the kind of predictions that we should produce in different scenarios. While for example the nearest neighbor classifier chooses a class label for any item out of a give set of alternative (like spam/ham, or 0, 1, 2, ..., 9), linear regression produces a numerical predictions that is not constrained to be an integer. So linear regression is better suited in situations where the output variable can be any number like the price of a product, the distance to an obstacle, the box-office revenue of the next star wards movie, and so on.

The basic idea in linear regression is to add up the effects of each of the feature variables to produce the predicted value. The technical term for the adding up process is *linear combination*. The idea is very straightforward, and it can be illustrated by your shopping bill.

> Thinking of linear regression as a shopping bill
> 
> Suppose you go to the grocery store to buy 2.5kg potatoes, 1.0kg carrots, and two bottles of milk. If the price of potatoes is 2€ per kg, the price of carrots is 4€ per kg, and a bottle of milk costs 3€, then the bill, calculated by the cashier, totals 2.5 * 2€ + 1.0 * 4€ + 2 * 3€ = 15€. In linear regression, the amount of potatoes, carrots, and milk are the inputs in the data. The output is the cost of your shopping, which clearly depends on both the price and how much of each product you buy.

The word linear means that the increase in the output when one input feature is increased by some fixed amount is always the same. In other words, whenever you add, say, two kilos of carrots into your shopping basket, the bill goes up 8€. When you add another two kilos, the bill goes up another 8€, and if you add half as much, 1kg, the bill goes up exactly half as much, 4€.

> Coefficients or weights
> 
> In linear regression terminology, the prices of the different products would be called coefficients or weights (this may appear confusing since we measured the amount of potatoes and carrots by weight, but do not let yourself be tricked by this). One of the main advantages of linear regression is its easy interpretability: the learned weights may in fact be more interesting than the predictions of the outputs.
> 
> For example, when we use linear regression to predict the life expectancy, the weight of smoking (cigarettes per day) is about minus half a year, meaning that smoking one cigarette more per day takes you on the average half a year closer to termination. Likewise, the weight of vegetable consumption (handful of vegetables per day) has weight plus one year, so eating a handful of greens every day gives you on the average one more year.

## Learning linear regression

Above, we discussed how predictions are obtained from linear regression when both the weights and the input features are known. So we are given the inputs and the weight, and we can produce the predicted output.

When we are given the inputs and the outputs for a number of items, we can find the weights such that the predicted output matches the actual output as well as possible. This is the task solved by ML.

> Example
> 
> Continuing the shopping analogy, suppose we were given the contents of a number of shopping baskets and the total bill for each of them, and we were asked to figure out the price of each of the products (potatoes, carrots and so on). From one basket, say 1kg of sirloin steak, 2kg of carrots, and a bottle of Chianti, even if we knew that the total bill is 35€, we couldn't determine the prices because there are many sets of prices that will yield the same total bill. With many baskets, however, we will usually be able to solve the problem.

But the problem is made harder by the fact that in the real world, the actual output isn't always fully determined by the input, because of various factors that introduce uncertainty or "noise" into the process. You can think of shopping at a bazaar where the prices for any given product may vary from time to time, or a restaurant where the final damage includes a variable amount of tip. In such situations, we can estimate the prices but only with some limited accuracy.

Finding the weights that optimize the match between the predicted and the actual outputs in the training data is a classical statistical problem dating back to the 1800s and it can be easily solved even for massive data sets.

We will not go into the details of the actual weight-finding algorithms, such as the classical least squares technique, simple as they are.

## Visualizing linear regression

A good way to get a feel for what linear regression can tell us is to draw a chart containing our data and our regression results. As a simple toy example our data set has one variable, the number of cups of coffee an employee drinks per day, and the number of lines of code written per day by that employee as the output. (LOL) This is **a real** data set as obviously there are no other factors having an effect on the productivity of an employee other than coffee that interact in complex ways. The increase in productivity by increasing the amount of coffee will also hold only to a certain point after which the jitters distract too much.

![[notes/machine learning/linear regression.png]]

When we present our data in the chart above as points where one point represents one employee, we can see that there is obviously a trend that drinking more coffee results in more lines of code being written (recall that this is completely real data). From this data set we can learn the coefficient, or the weight, related to coffee consumption, and by eye we can already say that it seems to be somewhere close to five, since for each cup of coffee consumed the number of lines programmed seems to go up roughly by five. For example, employees who drink around two cups of coffee per day seem to produce around 20 lines of code per day, and similarly at four cups of coffee, the amount of lines produced is around 30.

It can also be noted that employees who do not drink coffee at all also produce code, and is shown by the graph to be about ten lines. This number is the intercept term that we mentioned earlier. The intercept is another parameter in the model just like the weights are, that can be learned from the data. Just as in life expectancy example it can be thought of as the starting point of our calculations before we have added in the effects of the input variable, or variables if we have more than one, be it coffee cups in this example, or cigarettes and vegetables in the previous one.

The line in the chart represents our predicted outcome, where we have estimated the intercept and the coefficient by using an actual linear regression technique called least squares. This line can be used to predict the number of lines produced when then input is the number of cups of coffee. Note that we can obtain a prediction even if we allow only partial cups (like half, 1/4 cups, and so on).

## ML applications of linear regression

Linear regression is truly the workhorse of many AI and date science applications. It has its limits but they are often compensated by its simplicity, interpretability and efficiency. Linear regression has been successfully used in the following problems to give a few examples.

- Predictions of click rates in online advertising
- Prediction of retail demand for products
- Prediction of box-office revenue of Hollywood movies
- Prediction of software cost
- Prediction of insurance cost
- Prediction of crime rates
- Prediction of real estate prices

## Could we use regression to predict labels?

As we discussed above, linear regression and the nearest neighbor method produce different kinds of predictions. Linear regression outputs numerical outputs while the nearest neighbor method produces labels from a fixed set of alternatives.

Where linear regression excels compared to nearest neighbors is interpretability. What do I mean by this? You could say that in a way, the nearest neighbor method and any single prediction that is produces are easy to interpret, It's just the nearest training data element! This is true, but when it comes to interpretability of the learned model, there is a clear difference. Interpreting the trained model in the nearest neighbors in a similar fashion as the weights in linear regression is impossible: the learned model is basically the whole data, and it is usually way too big and complex to provide us with much insight. So what if we'd like to have a method that produces the same kind of outputs as the nearest neighbor, labels, but is interpretable like linear regression?

## Logistic regression to the rescue

Well there is good news for you: we can turn the linear regression method's outputs into predictions about labels. The technique for doing this is called logistic regression. We will not go into the technicalities, suffice to say that in simplest case, we take the output from linear regression, which is a number, and predict one label A if the output is greater than zero, and another label B if the output is less than or equal to zero. Actually, instead of just predicting one class or another, logistic regression can also give us a measure of uncertainty of the prediction. So if we are predicting whether a customer will buy a new smartphone this year, we can get a prediction that customer A will buy a phone with probability 90%, but for another, less predictable customer, we can get a prediction that they will *not* buy a phone with 55% probability (or in other words, that they will buy one with 45% probability).

It is also possible to use the same trick to obtain predictions over more than two possible labels, so instead of always predicting either yes or no (buy a new phone or not, fake news or real news, and so forth), we can use logistic regression to identify, for example, handwritten digits, in which case there are ten possible labels.

## An example of logistic regression

Let's suppose that we collect data of students taking an introductory course in cookery. In addition to the basic information such as the student ID, name and so on, we also ask the students to report how many hours they studied for the exam (however you study for a cookery exam, probably cooking? Eating?) - and hope that they are more or less honest in their reports. After the exam, we will know whether each students passed the course or not. Some data points are presented below.

| Student ID | Hours studied | Pass/fail |
| ---------- | ------------- | --------- |
| 24         | 15            | Pass      |
| 41         | 9.5           | Pass      |
| 58         | 2             | Fail      |
| 101        | 5             | Fail      |
| 103        | 6.5           | Fail      |
| 215        | 6             | Pass      |
Based on the table, what kind of conclusion could you draw between the hours studied and passing the exam? We could think that if we have data from hundreds of students, maybe we could see the amount needed to study in order to pass the course. We can present this data in a chart as you can see below.

![[notes/machine learning/logistic regression.png]]