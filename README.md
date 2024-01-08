# Problem Of The Day Solutions

This is my attemp to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 08-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/merge-2-sorted-linked-list-in-reverse-order/1)
## Merge 2 sorted linked list in reverse order

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My code aims to merge two sorted linked lists into a new sorted linked list. It should also leverages the properties of sorted lists, where the smallest element is at the beginning. The merging process involves comparing the current elements of both lists and inserting the smaller element into the new list. This process continues until one of the lists is exhausted. Any remaining elements in the non-empty list are then appended to the merged list.

# Approach
<!-- Describe your approach to solving the problem. -->
- Initialization :
- - Created a dummy node (jawab) to simplify the merging process.
- - Initialized a pointer p to point to the dummy node, which will be used to build the merged list.
- Merging Process :
- - Iterated through both linked lists (node1 and node2) as long as both lists have elements.
- - Compared the data of the current nodes in node1 and node2.
- - If the data of the node in node1 is smaller, created a new node with that data and inserted it at the beginning of the merged list.
- - If the data of the node in node2 is smaller, created a new node with that data and inserted it at the beginning of the merged list.
- - Move to the next node in the respective list.
- Appending Remaining Nodes :
- - After the above loop, there might be remaining nodes in one of the lists.
- - If there are remaining nodes in node1, append them to the merged list.
- - If there are remaining nodes in node2, append them to the merged list.
- Result :
- - Returned the merged list, excluding the dummy node.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $$O(m+n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$$m : length of first linked list  $$

$$n : length of second linked list  $$

- Space complexity : $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->


# Code
```
class GfG {
    
    Node mergeResult(Node node1, Node node2) {
        // Created a dummy node to start the merged list
        Node jawab = new Node(0);
        Node p = jawab;

        // Iterated while both lists have elements
        while (node1 != null && node2 != null) {
            // Compared the data of the current nodes in both lists
            if (node1.data < node2.data) {
                // If node1's data is smaller, create a new node with node1's data
                // Inserted the new node at the beginning of the merged list
                Node in = new Node(node1.data);
                in.next = p.next;
                p.next = in;

                // Moved to the next node in list1
                node1 = node1.next;
            } else {
                // If node2's data is smaller, create a new node with node2's data
                // Inserted the new node at the beginning of the merged list
                Node in = new Node(node2.data);
                in.next = p.next;
                p.next = in;

                // Moved to the next node in list2
                node2 = node2.next;
            }
        }

        // If there are remaining nodes in list1, append them to the merged list
        while (node1 != null) {
            Node in = new Node(node1.data);
            in.next = p.next;
            p.next = in;
            node1 = node1.next;
        }

        // If there are remaining nodes in list2, append them to the merged list
        while (node2 != null) {
            Node in = new Node(node2.data);
            in.next = p.next;
            p.next = in;
            node2 = node2.next;
        }

        // Returned the merged list (excluding the dummy node)
        return jawab.next;
    }
}

```

