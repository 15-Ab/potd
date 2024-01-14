# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 14-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/find-duplicate-rows-in-a-binary-matrix/1)
## Find duplicate rows in a binary matrix

### Intuition
Insertion Sort is a simple sorting algorithm that builds the final sorted list one element at a time. It is much less efficient on large lists than more advanced algorithms such as quicksort, heapsort, or merge sort. However, it has the advantage of being easy to understand and implement.

### Approach
**Traversal and Extraction:**
   - I traversed the linked list and extract the values of each node, storing them in an ArrayList (`al`).
   
**Sorting:**
   - Sorted the ArrayList in ascending order. The sorting is done using the `sort` method with the natural order comparator.

**Linked List Update:**
   - Traversed the linked list again.
   - Updated the values of each node with the sorted values from the ArrayList.

### Implementation:
- My algorithm converts the linked list into an ArrayList to leverage its easy sorting capabilities.
- After sorting, it updates the linked list nodes with the sorted values.

### Example:
Consider an unsorted linked list: `5 -> 2 -> 8 -> 1`
1. Extract values: `[5, 2, 8, 1]`
2. Sort values: `[1, 2, 5, 8]`
3. Update linked list: `1 -> 2 -> 5 -> 8`

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(nlogn)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ : number of elements in linked list
- Space complexity : $O(n)$
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

