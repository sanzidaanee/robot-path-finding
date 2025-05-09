# Robot Path Planning with A* Search Algorithm

## Problem Statement

This is a robot path planning problem on a grid with obstacles (cells colored black). The following figure shows such a 6 x6 grid with obstacles at 6 cell locations. Assume the robot can move to the cell up, down, left or right to the current cell in one move. The cost for moving is 1.


![heuristic model](https://github.com/user-attachments/assets/b6dc1408-7498-47e9-9514-68636f137d6d)




Suppose the robot wants to find the shortest cost path from start location S to the closest goal locations marked by G using A* search algorithm. If there were a single goal an admissible heuristic would be the Manhattan distance between the current location and the goal location (assuming there are no obstacles – this ensures the Manhattan distance will be smaller than the actual cost making the heuristic admissible). However, to solve the problem with more than one goal you need to have an admissible heuristic to the closest goal location. But you do not know which goal location is the closest. (hint: you can find the Manhattan distance to all the goal nodes and then construct a heuristic function from them)

Write a python program to find the shortest path to the closest goal location. Your code should work for any grid of size smaller than 10 x 10.

A sample input for the above grid will as follows:

5 6 // number of rows and number of columns of the grid
2 1 //sources (S) cell number
3 //number of goals locations, the locations are given below
2 6 //goal cell
4 3 //goal cell
5 5 //goal cell
6 // number of blocked cells. Locations of the blocked as given next
2 2
4 2
2 3
3 3

The output should be the sequence of moves (L,R,U,or D)

# Solution

Find the shortest path from a start position to the closest goal position on a grid with obstacles. The robot can move up, down, left, or right (no diagonals). I will use the A* search algorithm with an admissible heuristic.

## A* algorithm
A* algorithm is an informed search algorithm, leverages a heuristic function to guide its search towards the goal. This heuristic function estimates the cost of reaching the goal from a given node, allowing the algorithm to prioritize promising paths.

The A* algorithm's efficiency comes from its smart evaluation of paths using three key components: g(n), h(n), and f(n). These components work together to guide the search process toward the most promising paths.



# Step-by-Step Explanation

- Input Reading: The program reads the grid dimensions, start position, goal positions, and blocked cells.

- Admissible Heuristic: For multiple goals, we need a heuristic that underestimates the distance to the closest goal.

- Heuristic Function: For any cell (r, c), it calculates the Manhattan distance to all goals and returns the minimum value.

- A Search*:

-  Uses a priority queue (min-heap) to explore nodes with the lowest f(n) = g(n) + h(n) first.
-  g(n) is the actual cost from start to current node.
-  h(n) is the heuristic estimate to the closest goal.
-   or each move, checks if the new position is valid (within bounds and not blocked).

- Track the path: Use a parent dictionary to reconstruct the path once a goal is found.

- Termination: When a goal is reached, returns the path. If the queue is exhausted without finding a goal, returns an empty path (though the problem assumes a path exists)




