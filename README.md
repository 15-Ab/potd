🚀 Enjoy exploring my solution and keep the coding spirit alive! Happy coding ! ✨


## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 20-03-24 [Problem Link](https://www.geeksforgeeks.org/problems/possible-paths--141628/1)
## Possible Paths in a Tree

## Intuition
The given code implements a solution to find the maximum weighted edge for each query in a disjoint set data structure (also known as union-find or merge-find data structure). The problem involves processing a series of weighted edges and answering queries based on a weight threshold.


## Approach

**Disjoint Set Initialization** :
- I initialized the parent and size arrays for the disjoint set.
- Each node is initially its own parent, and the size of each set is set to 1.

**Processing Weighted Edges** :
- Sorted the given edges based on their weights in ascending order.
- For each edge in the sorted list :
  - Finded the roots of the two nodes connected by the edge using the `findRoot` method.
  - If the roots are different, performed union of the two nodes using the `union` method.
  - Updated the `result` variable with the sum of squares of sizes of the merged sets.

**Stored Results** :
- Used a TreeMap to store the result for each weight threshold encountered during the processing of edges.
- For each query weight :
  - Finded the closest weight threshold less than or equal to the query weight using the `floorEntry` method of TreeMap.
  - If no such weight threshold exists, added 0 to the result list; otherwise, add the corresponding result to the list.

**Results** :
- Returned the list containing the results for each query.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $ O(n log n + q log n)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ :  number of edges 

$q$ : number of queries
- Space complexity : $O( n )$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code

```
//  User function Template for Java

/*
node class of binary tree
class Node {
    int data;
    Node left, right;
    
    public Node(int data){
        this.data = data;
    }
}
*/
class Solution{
    public int sumOfLongRootToLeafPath(Node root) {
        maxHeight = longestPathSum = 0;
        // Call the recursive method to calculate the longest path sum 
        calculateLongestRootToLeafPathSum(root, 0, 0);
        return longestPathSum;
    }

    int maxHeight, longestPathSum;
    
    // Define a method named calculateLongestRootToLeafPathSum
    void calculateLongestRootToLeafPathSum(Node currentNode, int currentHeight, int currentSum) {
        // Base case: If the current node is null, return 
        if (currentNode == null)
            return;
        
        // If the current node is a leaf node, calculate the sum of the path from the root to this leaf node
        if (currentNode.left == null && currentNode.right == null) {
            currentSum += currentNode.data;
            
            // Update maxHeight and longestPathSum if the current path is longer than the previously found longest path
            if (currentHeight > maxHeight) {
                maxHeight = currentHeight;
                longestPathSum = currentSum;
            } else if (currentHeight == maxHeight) {
                longestPathSum = Math.max(longestPathSum, currentSum);
            }
                
            return;
        }
        
        // Recursively call the method for the left and right children of the current node 
        currentSum += currentNode.data;
        calculateLongestRootToLeafPathSum(currentNode.left, currentHeight + 1, currentSum);
        calculateLongestRootToLeafPathSum(currentNode.right, currentHeight + 1, currentSum);
    }
    
}
```