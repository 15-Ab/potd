# Celebrating Unity in Diversity: Happy Republic Day ! :india:

## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 26-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/fractional-knapsack-1587115620/1)
## Fractional Knapsack

## Intuition

The Fractional Knapsack problem revolves around optimizing the total value of items placed in a knapsack with a specified weight capacity. Each item has both a weight and a value, and the objective is to strategically select items, allowing for fractional parts, to maximize the overall value within the given constraints.


## Approach

**Sorted by Value-to-Weight Ratio :**
   - Created a new Comparator class for this
   - Sorted the items in descending order based on their value-to-weight ratio.
   - Prioritized items that offer more value per unit of weight.

**Greedy Selection :**
   - Iterated through sorted items.
   - Included items in the knapsack if there's sufficient capacity.
   - If an item doesn't fit entirely, included a fraction to maximize overall value.

**Optimal Solution :**
   - Continued greedy selection until the knapsack is full.
   - Achieved the maximum total value through strategic inclusion of items, considering both entire items and fractional parts.

By employing a greedy strategy and sorting based on value-to-weight ratio, I systematically selected more valuable items early on, leading to an efficient solution for the Fractional Knapsack problem.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(nlogn)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ : number of items

- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code 
```
//User function Template for Java

// Custom Comparator class for sorting items based on value-to-weight ratio in descending order.
class MyComparator implements Comparator<Item> {
    @Override
    public int compare(Item a, Item b) {
        // Calculating value-to-weight ratio for both items.
        double ka = (double) a.value / (double) a.weight;
        double kb = (double) b.value / (double) b.weight;

        // Sorting in descending order based on the ratio.
        if (ka < kb) {
            return 1;
        }
        return -1;
    }
}

class Solution {
    // Function to get the maximum total value in the knapsack.
    double fractionalKnapsack(int W, Item arr[], int n) {
        
        // Sorting the items based on the value-to-weight ratio using MyComparator.
        Arrays.sort(arr, new MyComparator());

        double jawab = 0d;  // Variable to store the final result.
        
        // Iterating through the sorted items.
        for (Item i : arr) {
            int v = i.value;     // Value of the current item.
            int w = i.weight;    // Weight of the current item.

            // Check if the entire item can be included in the knapsack.
            if (W >= w) {
                jawab += v;         // Adding the value of the entire item to the result.
                W -= w;            // Reducing the available space in the knapsack.
            } 
            else {
                // Calculating the fraction of the item that can be included.
                double tukra = (double) W / (double) w;
                jawab += (v * tukra);                   // Adding the fractional value to the result.
                W -= (int) (w * tukra);                 // Updating the available space in the knapsack.
                break;                                  // Breaking the loop as the knapsack is full.
            }
        }

        return jawab;  // Returning the final result.
    }
}
```

