# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 22-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/paths-from-root-with-a-specified-sum/1)
## Paths from root with a specified sum

## Intuition
A vertex cover of a graph is a set of vertices such that every edge in the graph is incident to at least one vertex from the set. This problem is to find the smallest possible size of such a vertex cover.

## Approach

#### Initialization
- I represented the graph using a 2D boolean array called `adjacencyMatrix`. `adjacencyMatrix[i][j]` is true if there is an edge between vertex `i` and vertex `j`.
- The function `addEdge` is used to fill the adjacency matrix based on the given edges.

#### Finding Minimum Vertex Cover Size
**Function `vertexCover`**
- It takes the number of nodes `n`, the number of edges `m`, and a 2D array `edges` representing the edges between nodes.
- Initializes and fills the adjacency matrix using the `addEdge` function.
- Calls the `findMinimumCoverSize` function to find the minimum size of the vertex cover.

**Function `findMinimumCoverSize`**
- It uses binary search to find the minimum size of the vertex cover.
- Calls the `isVertexCover` function to check if a vertex cover of a certain size is valid.
- The result is the minimum size of the vertex cover.

**Function `isVertexCover`**
- Checks whether a vertex cover of a given size covers all the edges in the graph.
- Utilizes bitmasking to represent the selected vertices.
- Iterates through all possible combinations of vertices to find a valid cover.
- Uses a 2D array `visited` to keep track of visited edges during the checking process.

**Function `initializeVisited`**
- Initializes a 2D array `visited` to keep track of visited edges during the checking process.

### Summary
My code employs an adjacency matrix, bitmasking, and binary search to efficiently find the minimum size of a vertex cover for the given graph. My approach involves checking the validity of vertex covers of different sizes until the minimum valid size is found.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(log n * 2^n)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ : number of nodese

- Space complexity : $O(max^2)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$max = MAX NODES$ : 30 ( I used )

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

