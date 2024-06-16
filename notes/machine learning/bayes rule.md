I will not go too far into the details of probability calculus and all the ways in which it can be used in various AI applications, but we will discuss one very important formula.

We will do this because this particular formula is both simple and elegant as well as incredibly powerful. It can be used to weigh conflicting pieces of evidence in medicine, in a court of law, and in many (if not all) scientific disciplines. **The formula is called the Bayes rule (or the Bayes formula).**

We will start by demonstrating the power of the Bayes rule by means of a simple medical diagnosis problem where it highlights how poorly our intuition is suited for combining conflicting evidence. We will then show how the Bayes rule can be used to build AI methods that can cope with conflicting and noisy observations.

> Prior and posterior odds
> 
> The Bayes rule can be expressed in many forms. The simplest one is in terms of odds. The idea is to take odds for something happening (against it not happening), which we'll call prior odds. The word prior refers to our assessment of the odds before obtaining some new information that may be relevant. The purpose of the formula is to update the prior odds when new information becomes available, to obtain the posterior odds, or the odds after obtaining the information (the dictionary meaning of posterior is "something that comes after, later").

## How odds change

In order to weigh the new information and decide how the odds change when it becomes available, we need to consider how likely we would be to encounter this information in alternative situations. Let's take as an example, the odds that it will rain later today. Imagine getting up in the morning in Finland. The chances of rain are 206 in 365 (including rain, snow, and hail). The number of days without rain is therefore 159. This converts to prior odds of 206:159 for rain, so the cards are stacked against you already before you open your eyes.

However, after opening your eyes and taking a look outside, you notice it's cloudy. Suppose the chances of having a cloudy morning on a rainy day are 9 out of 10 - that means that only one out of 10 rainy days start out with blue skies. But sometimes there are also clouds without rain: the chances of having clouds on a rainless day are 1 in 10. Now how much higher are the chances of clouds on a rainy day compared to a rainless day? Think about this carefully as it will be important to be able to comprehend the question and obtain the answer in what follows.

The answer is that the chances of clouds on a rainy day are **nine times** as high as the chances of clouds on a rainless day: on a rainy day the chances are 9 out of 10, whereas on a rainless day the chances are 1 out of 10, which is nine times as high.

Note that even though the two probabilities 9/10 and 1/10 sum up to 1, this is by no means always the case. In some other town, the mornings of rainy days could be cloudy eight times out of ten. This, however, would not mean that the rainless days are cloudy two times out of ten. You'll have to be careful to get the calculations right.