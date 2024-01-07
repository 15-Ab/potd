# Problem Of The Day Solutions

This is my attemp to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 07-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/split-array-largest-sum--141634/1)
## Split Array Largest Sum

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal of this question is to split an array into at most K partitions in a way that minimizes the maximum sum of elements in each partition. Basically this involves finding the maximum sum for a given number of partitions.

# Approach
<!-- Describe your approach to solving the problem. -->
- Initialization :
- - I initialized a variable 'm' to store the maximum element in the array.
- - I iterated through the array to find the maximum element and calculate the sum of all elements in the array (jor).
- Binary Search :
- - I performed binary search to find the maximum possible sum of elements in a partition.
- - Initialized the left boundary (l) with the maximum element in the array (m) and the right boundary (r) with the total sum of elements in the array (jor).
- Binary Search Loop :
- - While 'l' is less than or equal to 'r', calculate the mid-point (mid) between l and r.
- - Initialize variables :
- - - 'tatkal' to store the current number of partitions.
- - - 'j' to store the sum of elements in the current partition.
- Check Partitions :
- - Iterated through the array and check how many partitions can be formed with the current mid value:
- - - If the sum j exceeds the current mid value, increase the partition count (tatkal) and reset j to the current element.
- - Then I compared the partition count tatkal with the allowed number of partitions K.
- Adjust Boundaries :
- - If the current partition count 'tatkal' is greater than K, it means the mid value is too small, so I adjusted the left boundary (l) to mid + 1.
- - If the current partition count is less than or equal to K, update the result variable (jawab) with the current mid value and adjusted the right boundary (r) to mid - 1.
- Return Result :
- - After the binary search loop, the result variable jawab contains the maximum sum for at most K partitions.
- - Returned the final result.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $$O(nlogd)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
- Space complexity : $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$n : length of array  $$
$$d : difference between the maximum element and the sum of the array.  $$

# Code
```
class Solution {
    static int m; // Static variable to store the maximum element in the array
    
    // Function to split the array into at most K partitions
    static int splitArray(int[] arr, int N, int K) {
        int jor = 0; // Variable to store the sum of array elements
        m = Integer.MIN_VALUE; // Initialize m to the minimum integer value

        // Iterate through the array to find the maximum element (m) and calculate the sum (jor)
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] > m) {
                m = arr[i];
            }
            jor += arr[i];
        }

        int jawab = 0;
        jawab = helper(arr, jor, K); // Call the helper function to find the maximum sum for at most K partitions
        return jawab; // Return the result
    }

    // Helper function to perform binary search to find the maximum sum for at most K partitions
    static int helper(int[] a, int jor, int K) {
        int l = m; // Initialize the left boundary with the maximum element in the array
        int r = jor; // Initialize the right boundary with the sum of array elements
        int jawab = 0; // Variable to store the final result

        // Perform binary search to find the maximum sum for at most K partitions
        while (l <= r) {
            int mid = (l + r) / 2; // Calculate the mid-point

            int tatkal = 1; // Variable to store the current number of partitions
            int j = 0;

            // Iterate through the array to check how many partitions can be formed with the current mid value
            for (int i = 0; i < a.length; i++) {
                j += a[i];
                if (j > mid) {
                    tatkal++; // Increase the partition count
                    j = a[i];
                }
            }

            // Adjust the boundaries based on the current number of partitions
            if (tatkal > K) {
                l = mid + 1; // Need to increase the sum, move to the right half
            } else {
                jawab = mid; // Update the result with the current mid value
                r = mid - 1; // Explore the left half for a potentially smaller maximum sum
            }
        }

        return jawab; // Return the final result
    }
};


```

