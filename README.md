🚀 Enjoy exploring my solution and keep the coding spirit alive! Happy coding ! ✨

## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 02-04-24 [Problem Link](https://www.geeksforgeeks.org/problems/minimum-absolute-difference-in-bst-1665139652/1)
## Minimum Absolute Difference In BST

## Intuition
Count the number of pairs of nodes violating the BST property.

## Approach
- Traversed the BST in inorder to obtain a sorted array of its elements.
- While traversing, count inversions, i.e., the number of times a smaller value appears after a larger value.
- Used a modified merge sort to count inversions during merging of sorted subarrays.
- Returned the inversion count as the result.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $O(n*logn)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ : number of nodes in the BST

- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code

```
//  User function Template for Java

/*The Node structure is defined as
struct Node {
    int data;
    Node *left;
    Node *right;

};
*/
class Solution {
    
    int p = Integer.MAX_VALUE; // Initializing previous node value with max value
    int a = Integer.MAX_VALUE; // Initializing minimum absolute difference with max value
    
    // Method to find the minimum absolute difference between adjacent node values
    int absolute_diff(Node root) {
        inorder(root);  // Performing inorder traversal
        return a;       // Returning the minimum absolute difference
    }
    
    // Inorder traversal to visit nodes in non-decreasing order
    void inorder(Node root) {
        if(root==null){
            return;
        }
        inorder(root.left);          // Traversing left subtree
        if(p != Integer.MAX_VALUE){  // Checking if p is not initialized (first node)
            a = Math.min(a,root.data-p); // Calculating absolute difference and update a
        }
        p = root.data;       // Updating previous node value
        inorder(root.right); // Traversing right subtree
    }
}
```