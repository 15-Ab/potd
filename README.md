🚀 Enjoy exploring my solution and keep the coding spirit alive! Happy coding ! ✨

## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 27-03=24 [Problem Link](https://www.geeksforgeeks.org/problems/find-shortest-safe-route-in-a-matrix/1)
## Find shortest safe route in a matrix

## Intuition
An additive sequence is a series of numbers in which each number in the sequence is the sum of the two preceding numbers. The idea behind the algorithm is to explore all possible combinations of the first two numbers in the sequence and then recursively check if the remaining string forms a valid additive sequence.

## Approach

**Input Validation :** I checked if the length of the input string is less than or equal to 2. If so, return false as an additive sequence must contain at least three numbers.
- **Initialization :** Initialized two static variables `jawab` (result) and `sequence` (to store the current sequence being checked).
- **Recursion :** Defined a recursive function `checkAdditive` that takes the input string and the starting index as parameters.
- **Base Case :** If the starting index equals the length of the input string and the size of the sequence is greater than 2, set the result to true.
- **Updated Variables :** Updated variables `first`, `second`, and `current` based on the current state of the sequence.
- **Iterated :** Iterated through the remaining characters in the input string starting from the current index.
- **Backtracking :** Added the current number to the sequence if the sequence size is less than 2 and the result is not true. Recursively call the `checkAdditive` function with the updated parameters. Removed the current number from the sequence to backtrack and explore other possibilities.
- **Checked Conditions :** Checked if the current number violates the additive property or if it satisfies the additive property. Return or continue accordingly.
- **Result :** After exploring all possibilities, returned the final result.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $O( N^2 )$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$N$ : length of the input string
- Space complexity : $O( N )$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code

```
//  User function Template for Java

class Solution {
    
    // Inner class to represent a cell in the grid
    static class Cell {
        int row, col;
        
        // Constructor to initialize row and column values of a cell
        Cell(int r, int c) {
            row = r;
            col = c;
        }
    }
    
    // Static variables to store the number of rows and columns in the grid
    static int ROWS;
    static int COLS;
    
    // Arrays to store possible moves in rows and columns (up, left, right, down)
    static int[] rowMoves = {-1, 0, 0, 1};
    static int[] colMoves = {0, -1, 1, 0};
    
    // Method to check if a given cell is within the grid boundaries
    static boolean isValid(int x, int y) {
        return (x >= 0 && y >= 0 && x < ROWS && y < COLS);
    }
    
    // Method to find the shortest path in the grid
    static int findShortestPath(int[][] grid) {
        ROWS = grid.length;
        COLS = grid[0].length;
        
        // Marking adjacent cells of landmines as -1
        for (int i = 0; i < ROWS; i++) {
            for (int j = 0; j < COLS; j++) {
                if (grid[i][j] == 0) {
                    for (int k = 0; k < 4; k++) {
                        int nextRow = i + rowMoves[k];
                        int nextCol = j + colMoves[k];
                        if (isValid(nextRow, nextCol))
                            grid[nextRow][nextCol] = -1;
                    }
                }
            }
        }
        
        // Converting -1 cells back to 0
        for (int i = 0; i < ROWS; i++) {
            for (int j = 0; j < COLS; j++) {
                if (grid[i][j] == -1)
                    grid[i][j] = 0;
            }
        }
        
        // Initializing a 2D array to store distances from the starting point
        int[][] distance = new int[ROWS][COLS];
        for (int i = 0; i < ROWS; i++) {
            for (int j = 0; j < COLS; j++)
                distance[i][j] = -1;
        }
        
        // Initializing a queue for BFS traversal
        Queue<Cell> queue = new LinkedList<>();
        
        // Adding cells from the first column with value 1 to the queue and set their distance to 0
        for (int i = 0; i < ROWS; i++) {
            if (grid[i][0] == 1) {
                queue.add(new Cell(i, 0));
                distance[i][0] = 0;
            }
        }
        
        // Performing BFS to find shortest path
        while (!queue.isEmpty()) {
            Cell current = queue.poll();
            int d = distance[current.row][current.col];
            int x = current.row;
            int y = current.col;
            
            // Exploring neighboring cells
            for (int k = 0; k < 4; k++) {
                int newX = x + rowMoves[k];
                int newY = y + colMoves[k];
                
                // Checking if the neighboring cell is valid, unvisited, and reachable
                if (isValid(newX, newY) && distance[newX][newY] == -1 && grid[newX][newY] == 1) {
                  
                    // Updating distance and add the cell to the queue
                    distance[newX][newY] = d + 1;
                    queue.add(new Cell(newX, newY));
                }
            }
        }
        
        // Finding minimum distance to reach the last column
        int minDistance = Integer.MAX_VALUE;
        for (int i = 0; i < ROWS; i++) {
            if (grid[i][COLS - 1] == 1 && distance[i][COLS - 1] != -1) {
                minDistance = Math.min(minDistance, distance[i][COLS - 1]);
            }
        }
        
        // If destination cannot be reached, return -1; otherwise, returning the minimum distance plus 1
        if (minDistance == Integer.MAX_VALUE){
            return -1;
        } 
        else {
            return minDistance + 1;
        }
    }
}
```