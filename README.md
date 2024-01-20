# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 20-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/distribute-candies-in-a-binary-tree/1)
## Distribute candies in a binary tree

## Intuition
As the goal is to distribute candies among nodes in a binary tree, ensuring each node receives at least one candy. My recursive approach calculates the minimum additional candies needed for the left and right subtrees of each node. The absolute values of these candies are added to a global variable, representing the total additional candies required for fair distribution.

## Approach

**Base Case :**
   - If the current node is `null`, returned 0 (no candies needed for an empty subtree).

**Recursive Calls :**
   - Recursively calculated candies needed for the left subtree (`l`).
   - Recursively calculated candies needed for the right subtree (`r`).

**Updated Answer (`jawab`) :**
   - Added the absolute values of `l` and `r` to `jawab`, representing additional candies for the current subtree.

**Calculated Total Candies :**
   - Calculated total candies needed for the current subtree by adding the data value of the current node, `l`, and `r`. Subtracted 1 to avoid double-counting.

**Returned Total Candies :**
   - Returned the total candies needed for the current subtree.

**Wrapper Function (`distributeCandy`) :**
   - I initialized `jawab` and calls the helper function for the actual calculation.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(N)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$N$ : number of nodes in the binary tree

$H$ :  height of the binary tree
- Space complexity : $O(H)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code
```
//User function Template for Java

/*
class Node {
    int data;
    Node left;
    Node right;
    Node(int data) {
        this.data = data;
        left = null;
        right = null;
    }
}*/

class Solution
{
    static int jawab;
    
    // Function to distribute candy among nodes in a binary tree
    public static int distributeCandy(Node root){
        jawab = 0;
        helper(root);
        return jawab;
    }
    
    // Helper function to calculate the candies distributed and return the extra candies
    static int helper(Node n){
        // Base case: If the node is null, returning 0
        if(n == null){
            return 0;
        }
        
        // Recursively calculating the extra candies for left and right subtrees
        int l = helper(n.left);
        int r = helper(n.right);
        
        // Updating the total candies distributed by adding the absolute values of left and right extra candies
        jawab += Math.abs(l) + Math.abs(r);
        
        // Returning the total candies distributed for the current subtree
        return n.data + l + r - 1;
    }
}

```

