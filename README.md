# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 13-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/insertion-sort-for-singly-linked-list/1)
## Insertion Sort for Singly Linked List

### Intuition
Insertion Sort is a simple sorting algorithm that builds the final sorted list one element at a time. It is much less efficient on large lists than more advanced algorithms such as quicksort, heapsort, or merge sort. However, it has the advantage of being easy to understand and implement.

### Approach
**Traversal and Extraction:**
   - Traverse the linked list and extract the values of each node, storing them in an ArrayList (`al`).
   
**Sorting:**
   - Sort the ArrayList in ascending order. The sorting is done using the `sort` method with the natural order comparator.

**Linked List Update:**
   - Traverse the linked list again.
   - Update the values of each node with the sorted values from the ArrayList.

### Implementation:
- The algorithm converts the linked list into an ArrayList to leverage its easy sorting capabilities.
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

/*class Node
    {
        int data;
        Node next;
        Node(int d) {data = d; next = null; }
    }
    */
class Solution
{
    public static Node insertionSort(Node head_ref){
        
        // Extracting values from the linked list and store them in an ArrayList.
        Node n = head_ref;
        ArrayList<Integer> al = new ArrayList<>();
        while( n != null){
            al.add(n.data);
            n = n.next;
        }
        
        // Sorting the ArrayList in ascending order.
        al.sort(Comparator.naturalOrder());
        
        // Traversing the linked list again and update the values with the sorted values.
        n = head_ref;
        int i = 0;
        while( n != null){
            n.data = al.get(i++);
            n = n.next;
        }
        return head_ref;
    }
}
```

