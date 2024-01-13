# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 13-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/insertion-sort-for-singly-linked-list/1)
## Insertion Sort for Singly Linked List

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My code is implementing a function to reverse the first k elements of a given queue.

# Approach
<!-- Describe your approach to solving the problem. -->
**Input Parameters:** My function takes a `Queue<Integer>` and an integer `k`.
**Calculated Unchanged Elements:** Determined the number of unchanged elements in the queue by subtracting `k` from its total size.
**Temporary Storage with Stack:**
   - Used a `Stack<Integer>` to temporarily store the first k elements of the queue.
   - Iterated over the first k elements, dequeuing each element and pushing it onto the stack, effectively reversing their order.
**Reversed Order Back to Queue:**
   - Iterated over the elements in the stack, dequeuing each element and enqueuing it back into the original queue, reversing their order again.
**Enqueued Remaining Unchanged Elements:**
   - Iterated over the remaining unchanged elements in the queue and enqueued them back.
**Returned Modified Queue:**
   - The modified queue is returned as the final result.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(nlogn)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ : size of queue
- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
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

