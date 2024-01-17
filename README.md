# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 17-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/all-unique-permutations-of-an-array/1)
## All Unique Permutations of an array

### Intuition
This problem requires finding all possible unique permutations of the given array in sorted order. A permutation is an arrangement of elements in a specific order. Here, uniqueness refers to avoiding duplicate permutations, and sorted order indicates arranging the permutations in ascending order.

### Approach

**Sort the Input Array :** 
Start by sorting the given array in ascending order. Sorting helps in avoiding duplicates during the permutation generation process.

**Backtracking Permutation Generation :**
   - Used backtracking to generate permutations.
   - Maintained a boolean array to keep track of used elements during the backtracking process.
   - Iterated through the sorted array elements and consider each element for the current permutation.
   - Ensured uniqueness by skipping duplicate elements (same as the previous element) unless the previous occurrence is already used.
   - Recursively explored all possibilities by adding the current element to the permutation, marking it as used, and making a recursive call.
   - Backtracked by removing the last added element and marking it as unused for the next iteration.

**Store Result :**
   - Stored each unique permutation in the result array.

**Return Result :**
   - Returned the array containing all unique permutations in sorted order.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(n log n + n!)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ : length of the input array
- Space complexity : $O( n + n!)$
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

