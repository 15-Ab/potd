# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 16-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/sequence-of-sequence1155/1)
## Sequence of Sequence

### Intuition
My code aims to find the maximum number of courses that Geek can complete within a specific time frame, considering a certain total budget. Geek has to buy courses each day, and if he completes 90% of the course on the same day, he receives a 90% refund. This involves dynamic programming, where my goal is to maximize the number of completed courses.

### Approach

**Initialization:**
   - Initialized a 2D array `h` of size `(m + 1) x (n + 1)` to store intermediate results.
   - Looped through each combination of `i` and `j` where `i` represents the length of the sequence, and `j` represents the number of elements in each sequence.

**Base Cases:**
   - If `j` is greater than `i` or if `i` is 0 or `j` is 0, set `h[i][j]` to 0 since it's not possible to form a sequence in these cases.
   - If `j` is 1, set `h[i][j]` to `i` since there is only one element in each sequence.

**Recursive Relation:**
   - For other cases, used the recursive relation `h[i][j] = h[i/2][j-1] + h[i-1][j]`.
   - This relation indicates that the number of sequences of length `i` with `j` elements can be obtained by either taking the first half of a sequence of length `i` with `j-1` elements or by adding one more element to a sequence of length `i-1` with `j` elements.

**Filled the 2D Array:**
   - Looped through each combination of `i` and `j` and filled in the values of `h` based on the calculated results.

**Returned the Result:**
   - The final result is stored in `h[m][n]`, representing the number of sequences of length `m` with `n` elements.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(m*n)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$m$ : given

$n$ : given
- Space complexity : $O(m*n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code
```
// User function Template for Java

class Solution {
    // Created a helper 2D array to store intermediate results for dynamic programming
    static int[][] h;

    static int numberSequence(int m, int n) {
        // Initializing the 2D array to store results
        h = new int[m + 1][n + 1];

        // Looping through each combination of m and n
        for (int i = 0; i <= m; i++) {
            for (int j = 0; j <= n; j++) {
                // Base cases:
                // If j is greater than i or if i is 0 or j is 0
                if (j > i || i == 0 || j == 0) {
                    h[i][j] = 0; // Set result to 0
                } else if (j == 1) {
                    // If j is 1, set the result to i
                    h[i][j] = i;
                } else {
                    h[i][j] = h[i / 2][j - 1] + h[i - 1][j];
                }
            }
        }

        // Returning the final result for the given m and n
        return h[m][n];
    }
}
```

