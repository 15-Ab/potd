## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 02-03-24 [Problem Link](https://www.geeksforgeeks.org/problems/first-element-to-occur-k-times5150/1)
## First element to occur k times

## Intuition
The goal of the provided code is to find the first element in an array that occurs exactly k times. It employs a HashMap to keep track of the frequency of each element during a linear traversal of the input array.

## Approach

**I initialized a HashMap :**
   - Declared a static HashMap named `m` to store the frequency of elements.

**Iterated Through Array :**
   - Traversed the given array `a`.
   - For each element in the array :
     - Updated the frequency of the element in the HashMap using `m.put(a[i], m.getOrDefault(a[i], 0) + 1)`.

**Checked Frequency :**
   - After updating the frequency, checked if the frequency of the current element is equal to `k`.
     - If true, returned the current element as it occurs exactly `k` times.

- **Returned -1 if Not Found :**
   - If no element is found with frequency `k` after the traversal, returned -1.

My approach efficiently utilized a HashMap to keep track of element frequencies while traversing the array linearly. The code stops and returns the first element that satisfies the condition of occurring exactly `k` times.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $O( N )$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$N$ :  size of the input array

$U$ :  number of unique elements in the input array
- Space complexity : $O( U )$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code

```
// User function Template for Java

class Solution {

    // Declaring a static HashMap to store element frequencies
    static HashMap<Integer, Integer> m;

    // Method to find the first element occurring k times in an array
    public int firstElementKTime(int n, int k, int[] a) {
        
        // Initializing the HashMap
        m = new HashMap<>();

        // Iterating through the array
        for (int i = 0; i < a.length; i++) {
            // Updating the frequency of the current element in the HashMap
            m.put(a[i], m.getOrDefault(a[i], 0) + 1);

            // Checking if the frequency of the current element is equal to k
            if (m.get(a[i]) == k) {
                // Returning the element if the condition is met
                return a[i];
            }
        }

        // If no element is found with frequency k, returning -1
        return -1;
    }
}
```
