Instead of perfect information, there  is a host of unknown possibilities, ranging from missing information to deliberate deception.

Take self-driving car for example - you can set the goal to get from A to B in an efficient and safe manner that follows all laws. But what happens if the traffic gets worse than expected, maybe because of an accident ahead? Sudden bad weather? Random events like a ball bouncing in the street, or a piece of trash flying straight into the car's camera?

A self-driving car needs to use a variety of sensors, including sonar-like ones and cameras, to detect where it is and what is around it. These sensors are never perfect as the data from the sensors always includes some errors and inaccuracies called "noise". It is very common then that one sensor indicates that the road ahead turns left, but another sensor indicates the opposite direction. This needs to be resolved without always stopping the car in case of even a slightest amount of noise.

## Probability

One of the reasons why modern AI methods actually work in real-word problems - as opposed to most of the earlier "good old-fashioned" methods in the 1960-1980s - is their ability to deal with uncertainty.

> The history of dealing with uncertainty
> 
> The history of AI has seen various competing paradigms for handling uncertain and imprecise information. For example, you may have heard of fuzzy logic. Fuzzy logic was for a while a contender for the best approach to handle uncertain and imprecise information and used in many customer-applications such as washing machines where the machine could detect the dirtiness (a matter of degrees, not only dirty or clean) and adjust the program accordingly.
> 
> However, probability has turned out to be the best approach for reasoning under uncertainty, and almost all current AI applications are based, to at least some degree, on probabilities.


## Why probability matters

We are perhaps most familiar with applications of probability in games: what are the chances of getting three of a kind in poker (about 1 in 47), what are the chances of winning in the lottery (very small), and so on. However, far more importantly, probability can also be used to quantify and compare risks in everyday life: what are the chances of crashing your car if you exceed the speed limit, what are the chances that the interest rates on your mortgage will go up by five percentage points within the next five years, or what are the chances that AI will automate particular tasks such as detecting fractured bones in X-ray images or waiting tables in a restaurant.

> The key lesson about probability
> 
> The most important lesson about probability that we'd like you to take away is not probability calculus. Instead, it is the ability to think of uncertainty as a thing that can be quantified at least in principle. This means that we can talk about uncertainty as if it were a number: numbers can be compared ("is this thing more probable than that thing"), and they can often be measured.
> 
> Granted, measuring probabilities is hard: we usually need many observations about a phenomenon to draw conclusions. However, by systematically collecting data, we can critically evaluate probabilistic statements, and our numbers can sometimes be found to be right or wrong. In other words, the key lesson is that uncertainty is not beyond the scope of rational thinking and discussion, and probability provides a systematic way of doing just that.

The fact that uncertainty can be quantified is of paramount importance, for example, in decisions concerning vaccination or other public policies. Before entering the market, any vaccine is clinically tested, so that its benefits and risks have been quantified. The risks are never known to the minutest detail, but their magnitude is usually known to sufficient degree that it can be argued whether the benefits outweigh the risks.

> Why quantifying uncertainty matters
> 
> If we think of uncertainty as something that can't be quantified or measured, the uncertainty aspect may become and obstacle for rational discussion. We may for example argue that since we don't know exactly whether a vaccine may cause a harmful side-effect, it is too dangerous to use. However, this may lead us to ignore a life-threatening disease that the vaccine will eradicate. In most cases, the benefits and risks are known to sufficient precision to clearly see that one is more significant than the other.

The above lesson is useful in many everyday scenarios and professionally: for example, medical doctors, judges in a court of law, or investors have to process uncertain information and make rational decision based on them. Since this is an AI directory, I will discuss about how probability can be used to automate uncertain reasoning. The examples I will use include medical diagnosis (although it is usually not a task that we'd wish to fully automate), and identifying fraudulent email messages ("spam").

## Odds

probably the easiest way to represent uncertainty is through odds. They make it particularly easy to update beliefs when more information becomes available (we will return to this in the next note).

Before we proceed any further, we should make sure you are comfortable with doing basic manipulations on ratios (or fractions). As you probably recall, fractions are numbers like 3/4 or 9/11. We will need to multiply and divide such things, so it's good to refresh these operations if you feel unsure about them. A compact presentation for those who just need a quick reminder is [Wikibooks: multiplying fractions](https://en.wikibooks.org/wiki/Arithmetic/Multiplying_Fractions). Another fun animated presentation of the basic operations is [Math is Fun: using rational numbers](https://www.mathsisfun.com/algebra/rational-numbers-operations.html). Feel free to consult your favorite source if necessary.

By odds, we mean an expression like 3:1 (three to one), which means that we expect that for every three cases of an outcome, for example winning a bet, there is one case of the opposite outcome, not winning the bet. (In gambling terms, the odds are usually given from the bookmakers point of view, so 3:1 usually means that *your* chances of winning are 1:3). The other way to express the same would be to say that the chances of winning are 3/4 (three in four). These are called natural frequencies since they involve only whole numbers. With whole numbers, it is easy to imagine, for example, four people out of whom, three have brown eyes. Or four days out of which it rains on three (if you're in Helsinki).

> Why we use odds and not percentages
> 
> Three out of four is of course the same as 75% (mathematicians prefer to use fractions like 0.75 instead of percentages). It has been found that people get confused and make mistakes more easily when dealing with fractions and percentages than with natural frequencies or odds. This is why we use natural frequencies and odds whenever convenient.

An important thing to notice is that while expressed as two numbers, 3 and 1 for example, the odds can actually be thought of as single fraction or a ratio, for example 3/1 (three divided by one) which is equal to 3. Thus, the odds 3:1 is the same as the odds 6:2 or 30:10 since these ratios are also equal to 3. Likewise, the odds 1:5 can be thought of as 1/5 (one divided by five) which equals 0.2. Again, this is the same as the odds 2:10 or 10:50 because that's what you get by dividing 2 by 10 or 10 by 50. But be careful! The odds 1:5 (one win for every five losses), even if it can be expressed as the decimal number 0.2, it is different from 20% probability (or probability 0.2 using the mathematicians' notation). The odds 1:5 mean that you'd have to play the game six times to get one win on the average. The probability 20% means that you'd have to play five times to get one win on the average.

For odds that are greater than one, such as 5:1, it is easy to remember that we are not dealing with probabilities because no probability can be greater than 1 (or greater than 100%), but for odds that are less than one such as 1:5, the danger of confusion lurks around the corner.

So make sure you always know when we are talking about odds and when we are talking about probabilities.