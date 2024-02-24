## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 24-02-24 [Problem Link](https://www.geeksforgeeks.org/problems/maximum-sum-problem2211/1)
## Maximum Sum Problem

## Intuition
- This problem involves finding the maximum sum for a given number `n`.
- The decision at each step is to either include the current number or divide it into parts and consider the sum of those parts.

## Approach

- Initialized an array `a` to store the maximum sum for each index up to `n+1`.
- Set base cases `a[0] = 0` and `a[1] = 1`.
- Iterated from `2` to `n`, calculating the maximum sum as the maximum of `i`, `a[i/2] + a[i/3] + a[i/4]`.
- The final result is stored in `a[n]`, representing the maximum sum.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $O(n)$ 
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ : given

- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
   
## Code 

```
// User function Template for Java

class Solution {
    
    // Static array to store results for dynamic programming
    static int[] a;

    // Function to find the maximum sum
    public int maxSum(int n) { 
        
        if( n == 0){
            return 0;
        }
        
        // Initializing the array with size n+1
        a = new int[n+1];
        
        // Base cases
        a[0] = 0;
        a[1] = 1;

        // Dynamic programming approach to find the maximum sum
        for (int i = 2; i <= n; i++) {
            // The maximum sum at index i is the maximum of i, a[i/2] + a[i/3] + a[i/4]
            a[i] = Math.max(i, a[i/2] + a[i/3] + a[i/4]);
        }
        
        // Returning the maximum sum at index n
        return a[n];
    } 
}
```
