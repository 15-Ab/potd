## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 16-02-24 [Problem Link](https://www.geeksforgeeks.org/problems/flatten-bst-to-sorted-list--111950/1)
## Flatten BST to sorted list

## Intuition
The goal is to flatten a Binary Search Tree (BST) into a sorted doubly linked list. My Java code used an in-order traversal to achieve this. During the traversal, I maintained a previous node (`pichla`) to properly link the nodes in the doubly linked list.


## Approach

- Initialized a dummy node (`tatkal`) to serve as the head of the resulting doubly linked list. Also, initialized `pichla` as the dummy node.
- Implement an in-order traversal of the BST.
   - Recursively traversed the left subtree.
   - Set the left and right pointers of the current node, updating `pichla` accordingly.
   - Recursively traversed the right subtree.
- After the traversal, set the left and right pointers of the last node to null to complete the doubly linked list.
- Returned the head of the flattened BST, which is `tatkal.right`.

My in-order traversal ensured that the nodes are visited in ascending order, and by appropriately updating pointers, the BST is flattened into a doubly linked list.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $O(r * c)$
<!-- Add your time complexity here, e.g. $$O())$$ -->

$r$ : number of rows in the 2D `paths` array 

$c$ : number of columns in the 2D `paths` array 

- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
## Code 

```
// User function Template for Java
class Solution {
    
    // Declaring static variables to keep track of the previous and current nodes
    static Node pichla;
    static Node tatkal;

    // Function to flatten a BST
    public Node flattenBST(Node root) {
        // Code here

        // Initializing the 'tatkal' node as a dummy node
        tatkal = new Node(-1);
        // Initializing the 'pichla' node as the dummy node
        pichla = tatkal;

        // Performing inorder traversal to flatten the BST
        inorder(root);

        // Set the left and right pointers of the last node to null
        pichla.left = null;
        pichla.right = null;

        // Returning the head of the flattened BST
        return tatkal.right;
    }

    // Helper function for inorder traversal
    static void inorder(Node r) {
        // Base case : If the current node is null, return
        if (r == null) {
            return;
        }

        // Recursively traversing the left subtree
        inorder(r.left);

        // Set the left and right pointers of the current node
        pichla.left = null;
        pichla.right = r;

        // Updating 'pichla' to the current node
        pichla = r;

        // Recursively traversing the right subtree
        inorder(r.right);
    }
}
```
