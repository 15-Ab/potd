## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 30-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/lcs-of-three-strings0028/1)
## LCS of three strings

## Intuition

The task is to find the length of the Longest Common Subsequence (LCS) of three strings: A, B, and C. The LCS is a subsequence that is common to all three strings and is not necessarily contiguous.

This problem can be efficiently solved using dynamic programming. My idea is to break down the problem into smaller subproblems and use memoization to avoid redundant computations.

## Approach

**Defined the Variables :**
   - Declared three static String variables `a`, `b`, and `c` to store the input strings.
   - Created a 3D array `gp` to store the results of subproblems. `gp[i][j][k]` will represent the length of LCS of substrings A[0...i], B[0...j], and C[0...k].

**Initialized the Array :**
   - Initialized the `gp` array with -1 to indicate that the result for a particular subproblem has not been computed yet.

**Recursive Helper Function :**
   - Implemented a recursive helper function `helper(i, j, k)` that computes the length of the LCS for substrings A[0...i], B[0...j], and C[0...k].
   - Base case: If any of the strings becomes empty (`i == -1`, `j == -1`, or `k == -1`), return 0.
   - If the result for the current subproblem is already computed, returned it.
   - If the characters at the current positions in all three strings are equal, incremented the result and move to the previous positions in all three strings.
   - If the characters are not equal, found the maximum length by considering all possibilities :
     - `helper(i - 1, j, k)`
     - `helper(i, j - 1, k)`
     - `helper(i, j, k - 1)`

**Main Function:**
   - In the main function `LCSof3`, assigned the input strings to the static variables.
   - Called the helper function with the lengths of the input strings as arguments.

**Returned the Result:**
   - The result of the main function is the length of the LCS of the three input strings.

My dynamic programming approach helps optimize the solution by avoiding redundant computations and efficiently finding the length of the Longest Common Subsequence of three strings.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(n1 * n2 * n3)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
n1, n2, and n3 are the lengths of the input strings.

- Space complexity : $O(n1 * n2 * n3)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code 
```
//User function Template for Java
class Solution 
{ 
    // Declaring three static String variables
    static String a;
    static String b;
    static String c;
    
    // Creating a 3D array to store the results of subproblems
    static int[][][] gp = new int[26][26][26];
    
    // Main function to find the length of the Longest Common Subsequence of three strings
    int LCSof3(String A, String B, String C, int n1, int n2, int n3) { 
        // Assigning input strings to the static variables
        a = A;
        b = B;
        c = C;
        
        // Initializing the 3D array with -1
        for (int[][] m : gp){
            for (int[] r : m){
                Arrays.fill(r, -1);
            }
        }
        
        // Calling the helper function to compute the result
        return helper(n1 - 1, n2 - 1, n3 - 1);
    }
    
    // Helper function to compute the length of the Longest Common Subsequence
    static int helper(int i, int j, int k) {
        // Base case: if any of the strings is empty, return 0
        if (i == -1 || j == -1 || k == -1) {
            return 0;
        }
        
        // If the result for the current subproblem is already computed, returning it
        if (gp[i][j][k] != -1) {
            return gp[i][j][k];
        }
 
        // If the characters at the current positions in all three strings are equal
        if (a.charAt(i) == b.charAt(j) && b.charAt(j) == c.charAt(k)) {
            // Incrementing the result and move to the previous positions in all three strings
            return gp[i][j][k] = 1 + helper(i - 1, j - 1, k - 1);
        } else {
            // If the characters are not equal, finding the maximum length by considering all possibilities
            return gp[i][j][k] = Math.max(Math.max(helper(i - 1, j, k), helper(i, j - 1, k)), helper(i, j, k - 1));
        }
    }
}
```

