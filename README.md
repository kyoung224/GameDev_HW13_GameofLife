# GameDev_HW13_GameofLife

Starting code given by professor, Michael Weeks.

## Directions: https://hallertau.cs.gsu.edu/~mweeks/csc4821/HW13.html

Conway's "Game of Life" is a classic cellular automata demonstration. In it, each cell in a matrix comes to life or dies according to the number of neighbors. This assignment is similar, but different. It is similar in that it is also a cellular automata, with rules governing how the cells grow and die. However, the rules are different, and instead of a cell being either alive or dead, this assignment has the trees in many different stages.

Show a matrix of tiles, like you did in recent homeworks. Use the tileset "features_trees.png", and show trees randomly placed around the canvas (though limit the positions to tile locations). The "features_trees.png" tileset shows a blank, followed by many different tiles representing the life of a tree, aging from left to right. Each tile is 32x32. Use this to show the trees.

To keep this simple, let a 0 value mean that there is no tree at that location. A 1 or higher means that there is a tree there. You can "age" a tree by increasing the value, but when it goes beyond the last tile, set it to 0.

On the gamedev server, you can find the features_trees.png tileset.

Start with a randomly populated matrix of trees. Set up an interval (i.e. the Tick() function), but make it relatively slow at 1 second. For each cell, count the number of live cells around it. Take care about the edges, i.e. don't try to access a row of -1. According to the number of neighbors, do one of the possible actions. Keep this flexible, i.e. implement the rules with a switch statement. Implement the rules as follows.
0 or 1 neighbors: no change
2 neighbors: age the tree
3 neighbors: if the current cell does not have a tree, add one
4 or 5 neighbors: no change
6, 7, or 8 neighbors: age the tree

Aging the tree simply means incrementing the value and using the next image (to the right) from the tileset. Note that 8 is the maximum number of neighbors possible; the cell does not count itself.

Clear the canvas, and re-draw the trees.

Hint: to make this work correctly, you will need to duplicate some data. The easiest way is to have a copy of the matrix of trees, where you make updates, then copy it to the original matrix when the updates are finished. For example, consider a matrix with the following values:

1, 1, 1, 1
0, A, B, 0
0, 0, 0, 0

Let's suppose that A and B both start with the value 0. You can count the neighbors of A, and find it is 3. This means that a new tree will appear there, so A will be 1 on the next display. Now when you count the neighbors of B, is the answer 3 or 4? If you count A as 1, you would get 4, but this is wrong. A and B should be updated simultaneously, and the order that you process them should not to the result. That is, use the original A value of 0, and count 3 as the number of neighbors for B. This is why you may want to have a copy of the matrix for the updates.
