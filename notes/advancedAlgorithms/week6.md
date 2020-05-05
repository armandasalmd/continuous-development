## Week 6. Greedy algorithms

Table of contents

-   Optimal greedy algorithm
    -   Shortest path
    -   Scheduling
    -   Knapsack problem
    -   Optimal Knapsack
        maximum value given capacity of knapsack and weight of items
        drawback that is takes time: O(n!) and more code to write

Optimal solution and backtracking

> The knapsack problem can be solved by finding one solution, saving it, then going back (backtracking) to the start of the process and looking for another solution

> This is repeated until there are no more solutions

> Then the best solution is selected

-   Optimal greedy algorithm
    -   Maximum root to leaf sum
        1. Greedy - fast, inaccurate
        1. Optimal - check all of the sums, return the best, expensive
    -   Maximum root to leaf path
        1. Optimal - algorithm is recursive

#### Summary

-   Greedy algorithms always make the choice that looks best at the moment
-   Optimal solutions can be complex because they involve backtracking
