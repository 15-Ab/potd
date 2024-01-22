# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 22-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/paths-from-root-with-a-specified-sum/1)
## Paths from root with a specified sum

## Intuition
As the goal of this algorithm is to find all paths in a binary tree where the sum of node values along the path is equal to a given target sum, I used a recursive approach to explore all possible paths in the binary tree.

## Approach

- I Initialized global variables `chahiye` (target sum), `rasta` (current path), and `jawab` (result paths).
- Called the helper function `helper` with the initial sum `0` and the root of the binary tree.

**In the `helper` function :**
- Checked if the current node is `null`. If true, return.
- Updated the current sum (`abhitak`) by adding the value of the current node.
- Added the value of the current node to the current path (`rasta`).
- Checked if the current path sums up to the target sum (`chahiye`).
- - If true, add a new copy of the current path to the result paths (`jawab`).
- Recursively explored the left and right subtrees.
- Backtrack: Remove the last element from the current path to explore other paths.

- Return the result paths (`jawab`).

### Summary
My algorithm utilizes a recursive depth-first search (DFS) approach to traverse the binary tree and explore all possible paths. The result paths are stored in the `jawab` ArrayList.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ : number of nodes in the binary tree

- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
## Code 
```
//User function Template for Java

/*Tree Node
class Node {
    int data;
    Node left;
    Node right;
    Node(int data) {
        this.data = data;
        left = null;
        right = null;
    }
} 
*/

class Solution {
    
    // Global variables to store target sum, current path, and result paths
    static int chahiye;
    static ArrayList<Integer> rasta;
    static ArrayList<ArrayList<Integer>> jawab;

    public static ArrayList<ArrayList<Integer>> printPaths(Node root, int sum) {
        
        // Initializing global variables
        chahiye = sum;
        rasta = new ArrayList<>();
        jawab = new ArrayList<>();

        // Calling helper function to explore paths
        helper(0, root);

        // Returning the result paths
        return jawab;
    }

    // Helper function to recursively explore paths
    static void helper(int abhitak, Node n) {
        // Base case: if the node is null, return
        if (n == null) {
            return;
        }

        // Updating the current sum and path
        abhitak += n.data;
        rasta.add(n.data);

        // Checking if the current path sums up to the target sum
        if (abhitak == chahiye) {
            // Adding a new copy of the current path to the result paths
            jawab.add(new ArrayList<>(rasta));
        }

        // Recursively exploring left and right subtrees            
        helper(abhitak, n.left);
        helper(abhitak, n.right);

        // Backtracking : removing the last element from the current path
        rasta.remove(rasta.size() - 1);
    }
}

```

