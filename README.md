# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 17-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/all-unique-permutations-of-an-array/1)
## All Unique Permutations of an array

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
//User function Template for Java

class Solution {
    // Function to find all unique permutations of the array in sorted order.
    static ArrayList<ArrayList<Integer>> uniquePerms(ArrayList<Integer> arr, int n) {
        // Sorting the input array
        Collections.sort(arr);
        // ArrayList to store the result (unique permutations)
        ArrayList<ArrayList<Integer>> result = new ArrayList<>();
        // Boolean array to keep track of used elements during backtracking
        boolean[] used = new boolean[arr.size()];
        // Generating permutations
        generatePermutations(arr, new ArrayList<>(), used, result);
        // Returning the result
        return result;
    }

    // Backtracking function to generate permutations
    private static void generatePermutations(ArrayList<Integer> arr, ArrayList<Integer> current, boolean[] used, ArrayList<ArrayList<Integer>> result) {
        // Base case: If the current permutation is of the same size as the input array, add it to the result
        if (current.size() == arr.size()) {
            result.add(new ArrayList<>(current));
            return;
        }

        // Iterating through the array elements
        for (int i = 0; i < arr.size(); i++) {
            // Checking if the current element is not used and is unique (to avoid duplicates)
            if (!used[i] && (i == 0 || arr.get(i) != arr.get(i - 1) || used[i - 1])) {
                // Adding the current element to the current permutation
                current.add(arr.get(i));
                // Marking the current element as used
                used[i] = true;
                // Recursive call to generate permutations
                generatePermutations(arr, current, used, result);
                // Backtracking: removing the last element to explore other possibilities
                current.remove(current.size() - 1);
                // Marking the current element as unused for the next iteration
                used[i] = false;
            }
        }
    }
};

```

