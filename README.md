## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 13-02-24 [Problem Link](https://www.geeksforgeeks.org/problems/clone-graph/1)
## Clone an Undirected Graph

## Intuition
The goal of this problem is to clone an undirected graph represented as a set of nodes. The graph is given as a collection of nodes, each having a value and a list of neighbors. 

The intuition behind my approach was to perform a Breadth-First Search (BFS) traversal of the original graph while creating a clone of each node and maintaining a mapping between the original nodes and their corresponding cloned nodes. This ensured that each node and its neighbors are cloned exactly once, preventing the creation of duplicate nodes.

## Approach

##### Clone Node Function (`cloneNode`) :

- The `cloneNode` function is my helper function that recursively cloned a single node and its neighbors.
- It checked if the original node is null or if it has already been cloned. If so, it returned the corresponding cloned node from the HashMap.
- Otherwise, it created a new cloned node with the same value and added the original and cloned nodes to the HashMap.
- It then recursively cloned each neighbor of the original node and addedd the cloned neighbors to the neighbors list of the cloned node.

##### Clone Graph Function (`cloneGraph`) :

- The `cloneGraph` function initialized a queue for BFS traversal (`q`) and a HashMap (`m`) to store the mapping between original and cloned nodes.
- It enqueued the original node into the queue and started the BFS traversal.
- During BFS, for each dequeued node, it called the `cloneNode` function to clone the node and its neighbors.
- The BFS ensured that each node and its neighbors are processed in a level-order fashion, ensuring the creation of the entire cloned graph.
- The function returned the cloned graph, which is the cloned node corresponding to the original node that was enqueued initially.

Overall, my approach involved using BFS to traverse the original graph, creating a clone of each node and its neighbors using the `cloneNode` function. The HashMap (`m`) ensured that each original node is cloned exactly once, preventing duplication. The time complexity is O(V + E), where V is the number of nodes (vertices) and E is the number of edges in the graph.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $O(V + E)$
<!-- Add your time complexity here, e.g. $$O())$$ -->

$V$ : number of nodes (vertices)

$E$ : number of edges in the graph

- Space complexity : $O(N)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$N$ : total number of nodes in the original graph

## Code 

```
// User function Template for Java

/*
    class Node{
        int val;
        ArrayList<Node> neighbors;
        public Node(){
            val = 0;
            neighbors = new ArrayList<>();
        }
    
        public Node(int val){
            this.val = val;
            neighbors = new ArrayList<>();
        }
    
        public Node(int val, ArrayList<Node> neighbors){
            this.val = val;
            this.neighbors = neighbors;
        }
    }
*/

class Solution {
    
    // HashMap to store the mapping between original nodes and their corresponding cloned nodes
    HashMap<Node, Node> m;
    // Queue for BFS traversal
    Queue<Node> q;

    // Helper function to clone a single node and its neighbors
    private Node cloneNode(Node originalNode) {
        // Checking if the original node is null
        if (originalNode == null) {
            return null;
        }

        // Checking if the original node is already cloned, if yes, returning the cloned node
        if (m.containsKey(originalNode)) {
            return m.get(originalNode);
        }

        // Creating a new cloned node with the same value
        Node clonedNode = new Node(originalNode.val);
        // Adding the original and cloned nodes to the HashMap
        m.put(originalNode, clonedNode);

        // Checking if the original node has neighbors
        if (originalNode.neighbors != null) {
            // Iterating through the neighbors
            for (Node neighbor : originalNode.neighbors) {
                // Recursively cloning each neighbor and adding the cloned neighbor to the cloned node's neighbors list
                clonedNode.neighbors.add(cloneNode(neighbor));
            }
        }

        // Returning the cloned node
        return clonedNode;
    }

    // Function to clone the entire graph
    public Node cloneGraph(Node node) {
        
        // Initializing the queue with the original node
        q = new LinkedList<>();
        q.add(node);

        // Initializing the HashMap to store the mapping between original and cloned nodes
        m = new HashMap<>();
        
        // Cloning the entire graph starting from the original node
        Node clonedGraph = cloneNode(node);

        // Returning the cloned graph
        return clonedGraph;
    }
}  
```
