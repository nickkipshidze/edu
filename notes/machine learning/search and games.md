## Game trees

To solve games using AI, we will introduce the concept of a game tree. The different states of the game are represented by nodes in the game tree. The idea is just slightly different. In the game tree, the nodes are arranged in levels that correspond to each player's turns in the game so that the "root" node of the tree (usually depicted at the top of the diagram) is the beginning position in the game. In tic-tac-toe, this would be empty grid with no Xs or Os played yet. Under root, on the second level, there are the possible states that can result from the first player's moves, be it X or O. We call these nodes the "children" of the root node.

Each node on the second level, would further have as its children nodes the states that can be reached from it by the opposing player's moves. This is continued, level by level, until reaching states where the game is over. In tic-tac-toe, this means that either one of the players gets a line of three and wins, or the board is full and the game ends in a tie.

## Minimizing and maximizing value

In order to be able to create game AI that attempts to win the game, we attach a numerical value to each possible end result. To the board positions where X has a line of three so that maximizing player wins, we attach the value +1, and likewise, to the position where minimizing player wins with three Os in a row we attach the value -1. For the positions where the board is full and neither player wins, we use the neutral value 0.

## The Minimax algorithm

We can exploit the concept of the value of the game to obtain an algorithm called the Minimax algorithm. It guarantees optimal game play in, theoretically speaking, any deterministic, two-person, perfect-information zero-sum game. Giver a state of the game, the algorithm simply computes the values of the children of the given state and chooses the one that has the maximum value if it is maximizing player's turn, and the one that has the minimum value if it is minimizing player's turn.

The algorithm can be implemented using a few lines of code. However, we will be satisfied with having grasped the main idea.