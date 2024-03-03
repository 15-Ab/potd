## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 03=03-24 [Problem Link](https://www.geeksforgeeks.org/problems/largest-number-formed-from-an-array1117/1)
## Largest Number formed from an Array

## Intuition
The goal of the code is to find the largest number by concatenating the given array of integers. The approach involves sorting the array in a custom order to maximize the resulting concatenated number.

## Approach

**I sorted the array using a custom comparator :**
   - The `Arrays.sort` method is applied to the array of integers.
   - A custom comparator is used to compare two integers based on their concatenation.
   - For integers `a` and `b`, the comparator compares `ba` with `ab`, ensuring a descending order.

**Concatenated the sorted integers :**
   - After sorting, concatenated the integers in the sorted order to form the largest possible number.
   - Concatenation is done using string concatenation to preserve leading zeros.

**Stored the result :**
   - The final concatenated result is stored in the static variable `jawab` for later retrieval.

**Result :**
   - The `printLargest` method returned the stored result.

My approach ensured that the integers are arranged in a way that maximizes the concatenated result, leading to the formation of the largest number.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $O( n * logn )$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ : length of the array
- Space complexity : $O( n + logn )$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code

```
// User function Template for Java

class Solution {
    // Static variable to store the result
    static String jawab;

    // Main function to print the largest number
    String printLargest(int n, String[] arr) {
        
        // Calling the helper function to perform the sorting and concatenation
        helper(arr);
        // Returning the result
        return jawab;
    }

    // Helper function to sort the array of strings in descending order
    static void helper(String[] arr) {
        // Using Arrays.sort with a custom comparator
        Arrays.sort(arr, new Comparator<String>() {
            @Override
            public int compare(String a, String b) {
                // Concatenating strings in different orders to compare
                String ab = a + b;
                String ba = b + a;
                // Comparing in descending order
                return ba.compareTo(ab);
            }
        });

        // Initializing the result string
        jawab = "";

        // Concatenating the sorted strings to form the final result
        for (int i = 0; i < arr.length; i++) {
            jawab += arr[i];
        }
    }
}
```
