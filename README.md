## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 05-02-24 [Problem Link](https://www.geeksforgeeks.org/problems/sorted-insert-for-circular-linked-list/1)
## Sorted insert for circular linked list

## Intuition

The goal of my code is to insert a new node with the given data into a sorted circular linked list while maintaining the sorting order.

## Approach

**Checked if Linked List is Empty :**
   - If the linked list is empty (head is null), created a new node with the given data and make it circular by pointing to itself.
   - Returned the new node as the new head.

**Traversed the Linked List :**
   - Initialized two pointers, `h` (current node) and `p` (previous node), both initially pointing to the head.
   - Traversed the circular linked list until reaching back to the head.

**Find Insertion Point :**
   - While traversing, found the correct position (`p` and `h`) to insert the new node based on the sorting order.
   - If `h.data` is less than the new data, moved the pointers to the next nodes.
   - Broke the loop if the correct position is found.

**Insert the New Node :**
   - Created a new node (`in`) with the given data.

**Three Cases for Insertion :**
   - **Case 1 : Inserted at the Head :**
      - If `h` is equal to the head and `h.data` is greater than the new data, inserted the new node at the head.
   - **Case 2 : Inserted at the Last :**
      - If `h.next` is equal to the head and both `p.data` and `h.data` are less than the new data, inserted the new node at the last.
   - **Case 3 : Inserted in the Middle :**
      - Otherwise, inserted the new node in the middle between `p` and `p.next`.

**Return Updated Head :**
   - Returned the updated head of the circular linked list.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O())$$ -->

$n$ : number of nodes in the circular linked list.

- Space complexity : $O(1)$ 
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code 

```
//User function Template for Java
class Solution {
    // Function to insert a node with the given data in a sorted circular linked list
    public Node sortedInsert(Node head, int data) {
        // If the linked list is empty, creating a new node and returning it as the new head
        if (head == null) {
            Node n = new Node(data);
            n.next = n;
            return n;
        }
        
        // Initializing pointers for traversal
        Node h = head;  // Current node
        Node p = head;  // Previous node
        
        // Traversing the circular linked list
        while (h.next != head) {
            // Moving pointers until finding the correct position to insert the new node
            if (h.data < data) {
                p = h;
                h = h.next;
            } else {
                // Breaking the loop if the correct position is found
                break;
            }
        }
        
        // Creating a new node with the given data
        Node in = new Node(data);
        
        // Inserting the new node based on different cases
        
        // Case 1 : Inserting at the head
        if (h == head && h.data > data) {
            Node last = head;
            // Traversing to the last node of the circular linked list
            while (last.next != head) {
                last = last.next;
            }
            // Updating pointers to insert the new node at the head
            last.next = in;
            in.next = head;
            head = in;
        }
        // Case 2 : Inserting at the last
        else if (h.next == head && p.data < data && h.data < data) {
            // Updating pointers to insert the new node at the last
            h.next = in;
            in.next = head;
        }
        // Case 3 : Inserting in the middle
        else {
            // Updating pointers to insert the new node in the middle
            in.next = p.next;
            p.next = in;
        }
        
        // Returning the updated head of the circular linked list
        return head;
    }
}
```

