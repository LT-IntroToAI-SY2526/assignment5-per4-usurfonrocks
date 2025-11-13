# Assignment 5 Write up

Assignment 5 can be broken up into the following parts:
1. Import the Necessary Modules:
- `copy`: For creating deep copies of objects
- `Stack` and `Queue`: Custom implementations for DFS and BFS operations
2. Utility Functions: 
- `remove_if_exists`: Removes a specified element from a list if it exists, which is used to remove the possibilites from a cell
3. Board Class:
- Represents the Sudoku board
- Consists of functions that will find the most constrained cell, and update the board, which eliminates possible solutions
4. DFS & BFS Functions:
- `DFS`: Uses depth-first search to solve the Sudoku puzzle. It works by trying to fill the most constrained cell with potential values until a solution is found or backtracks if a mistake is made
- `BFS`: Uses breadth-first search to solve the Sudoku puzzle in a similar fashion to DFS but explores nodes level by level
5. Main Execution:
- Defines two different sets of initial moves for Sudoku puzzles
- Uses both DFS and BFS to solve each puzzle and prints the results


After completing the assignment, answer the following reflection questions:

## Reflection Questions

1. What are some things that you learned through this assignment? Think about the concepts of backtracking, constraint satisfaction, and search algorithms. Were there any particular challenges you faced while implementing the Board class methods or the DFS/BFS functions? How did you overcome them?
 i gained a much deeper understanding of backtracking, constraint satisfaction, and search algorithms. backtracking taught me how to systematically explore possible states, back up when a choice led to a dead end, and try alternative paths. one of the main challenges i faced was implementing the board class methods, especially making sure that each state transition correctly followed the game’s rules. i overcame these challenges by breaking the problem into smaller parts and testing each one separately.



2. How can you apply what you learned in this assignment to future programs or projects? Consider other types of problems that involve searching through possibilities, making decisions, and backtracking when those decisions don't work out. Can you think of real-world scenarios where DFS or BFS might be useful? What about other constraint satisfaction problems?
the ideas from this assignment can be applied to many future programs or projects that involve exploring options, making choices, and adjusting when something doesn’t work. understanding backtracking and search algorithms helps me think about how to structure problems that require finding solutions among many possibilities.



3. Explain how the Stack and Queue classes work and why they are important for DFS and BFS algorithms. Describe the difference between LIFO (Last In First Out) and FIFO (First In First Out) data structures. How does using a Stack versus a Queue change the way the search algorithm explores possible solutions? Why is one data structure better suited for depth-first search and the other for breadth-first search?
the stack and queue classes are essential tools for controlling the order in which a search algorithm explores possible solutions. dfs relies on a stack to move deeper into one path before backtracking, while bfs uses a queue to explore all options level by level. the main difference is that dfs focuses on depth first, and bfs focuses on breadth first. using a stack causes the search to dive into one branch quickly, while using a queue keeps the search balanced across all branches. this difference makes the stack better suited for depth-first search and the queue better suited for breadth-first search.