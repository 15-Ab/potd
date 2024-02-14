# बसंत पंचमी की हार्दिक शुभकामनाएं। 
# I'm bowing to the goddess of knowledge without whom I'm nothing.

## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 14-02-24 [Problem](https://www.geeksforgeeks.org/problems/critical-connections/1)
## Find all Critical Connections in the Graph

## Intuition
This problem aimed to find critical connections (bridges) in a network represented as an undirected graph. Critical connections are edges that, if removed, would increase the number of connected components in the graph.

## Approach

**Depth-First Search (DFS) :**
   - Initialized arrays to store node ranks (`nodeRanks`), visited nodes (`visitedNodes`), and critical connections (`criticalConnections`).
   - Started DFS from the first node (`0`) to discover critical connections in the graph.

**DFS Function (`dfs`) :**
   - For each node, set its rank and mark it as visited.
   - Explored its neighbors:
     - If a neighbor is already visited, updated the minimum depth.
     - If the neighbor is not visited, recursively called DFS on it.
   - Checked for critical connections:
     - If the rank of the current node is less than the minimum depth, added the edge to `criticalConnections`.

**Sorted :**
   - After DFS, sorted each edge in ascending order of nodes.
   - Sorted the list of critical connections.

**Returned the Result :**
   - Returned the sorted list of critical connections.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $O(V + E)$
<!-- Add your time complexity here, e.g. $$O())$$ -->

$V$ : number of vertices

$E$ : number of edges in the graph

- Space complexity : $O(V + E)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$N$ : total number of nodes in the original graph

## Code 

```
// User function Template for Java

class Solution {
    private static final int MAX_DEPTH = Integer.MAX_VALUE;
    private static ArrayList<ArrayList<Integer>> criticalConnections;
    private static int[] nodeRanks;
    private static int[] visitedNodes;

    public ArrayList<ArrayList<Integer>> criticalConnections(int v, ArrayList<ArrayList<Integer>> adj) {
        // Initialization
        criticalConnections = new ArrayList<>();
        nodeRanks = new int[v];
        Arrays.fill(nodeRanks, -1);
        visitedNodes = new int[v];

        // Starting DFS to find critical connections
        dfs(0, -1, 0, adj);

        // Sorting each edge in ascending order of nodes
        for (ArrayList<Integer> edge : criticalConnections) {
            Collections.sort(edge);
        }

        // Sorting the list of edges
        criticalConnections.sort((a, b) -> {
            if (a.get(0).equals(b.get(0))) {
                return a.get(1) - b.get(1);
            }
            return a.get(0) - b.get(0);
        });

        return criticalConnections;
    }

    // Depth-first search to find critical connections
    private static int dfs(int currentNode, int parent, int currentRank,
                           ArrayList<ArrayList<Integer>> adjacencyList) {
        // Set node rank and mark as visited
        nodeRanks[currentNode] = currentRank;
        visitedNodes[currentNode] = 1;
        int minDepth = MAX_DEPTH;

        // Exploring neighbors
        for (int child : adjacencyList.get(currentNode)) {
            if (child != parent) {
                // If neighbor is visited, updating minDepth
                if (visitedNodes[child] == 1) {
                    minDepth = Math.min(minDepth, nodeRanks[child]);
                } else {
                    // Continuing DFS for unvisited neighbor
                    int minRank = dfs(child, currentNode, currentRank + 1, adjacencyList);

                    // Checking for critical connection
                    if (nodeRanks[currentNode] < minRank) {
                        ArrayList<Integer> edge = new ArrayList<>();
                        edge.add(currentNode);
                        edge.add(child);
                        criticalConnections.add(edge);
                    }

                    // Updating minDepth
                    minDepth = Math.min(minRank, minDepth);
                }
            }
        }
        return minDepth;
    }
}
```
