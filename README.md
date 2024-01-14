# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 14-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/find-duplicate-rows-in-a-binary-matrix/1)
## Find duplicate rows in a binary matrix

### Intuition
As, the goal of the code is to find and return the indices of the rows in a given matrix that are repeated. A row is considered repeated if there is another identical row in the matrix.
### Approach
- My function takes a 2D matrix matrix along with its dimensions `m` (number of rows) and `n` (number of columns).
- It uses a HashSet named `hl` to store unique rows encountered during the iteration.
- My function iterates through each row of the matrix using a for loop.
- For each row, it creates an ArrayList named `r` to store the elements of that row.
- If `r` is already present in the HashSet, it means the row is repeated, and the index of the repeated row is added to the result ArrayList named `jawab`.
- If `r` is not present in the HashSet, it is added to the HashSet to keep track of unique rows.
- After processing all rows, the function returns the ArrayList `jawab` containing indices of repeated rows.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(m*n)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$m$ : number of row(s)
$n$ : number of column(s)
- Space complexity : $O(m*n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code
```
//User function Template for Java

class Solution
{
    public static ArrayList<Integer> repeatedRows(int matrix[][], int m, int n){
        //code here
        HashSet<ArrayList<Integer>> hl = new HashSet<>();
        ArrayList<Integer> jawab = new ArrayList<>();
        
        // Iterating through each row of the matrix
        for( int i = 0; i < matrix.length; i++){
            ArrayList<Integer> r = new ArrayList<>();
            
            // Adding elements of the current row to an ArrayList
            for( int j = 0; j < matrix[0].length; j++){
                r.add(matrix[i][j]);
            }
            
            // If the ArrayList is already present in the HashSet, it means the row is repeated
            if( hl.contains(r)){
                jawab.add(i); // Adding the index of the repeated row to the result ArrayList
            }
            else{
                hl.add(r); // Adding the ArrayList to the HashSet
            }
        }
        
        return jawab; // Returning the ArrayList containing indices of repeated rows
    }
}
```

