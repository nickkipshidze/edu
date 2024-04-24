Many problems can be phrased as search problems. This requires that we start by formulating the alternative choices and their outcomes.

## Search in practice: getting from A to B

Imagine you're in a foreign city, at some address (say a hotel) and want to use public transport to get to another address (a nice restaurant, perhaps). What do you do? If you are like many people, you pull out your phone, type in the destination and start following the instructions.

This question belongs to the class of search and planning problems. Similar problems need to be solved by self-driving cars, and (perhaps less obviously) AI for playing games. In the game of chess, for example, the difficulty is not so much in getting a piece from A to B as keeping your pieces safe from the opponent.

Often there are many different ways to solve the problem, some of which may be more preferable in terms of time, effort, cost or other criteria. Different search techniques may lead to different solutions, and developing advanced search algorithms is an established research area.

We will not focus on the actual search algorithms. Instead, we emphasize the first stage of the problem solving process: defining the choices and their consequences, which is often far from trivial and can require careful thinking. We also need to define what our goal is, or in other words, when we can consider the problem solved. After this has been done, we can look for a sequence of actions that leads from the initial state to the goal.