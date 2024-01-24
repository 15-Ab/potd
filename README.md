# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 24-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/is-it-a-tree/1)
## Check if a given graph is tree or not

## Intuition
As this problem is about finding the order in which courses can be taken given a list of prerequisites, it is essentially a topological sorting problem.

My idea is to represent the courses as nodes in a graph, and the prerequisites as directed edges between the nodes, as the problem asks for an order in which we can take the courses, considering the prerequisites.

## Approach

**Initialized Data Structures :**
- Declared arrays and data structures for in-degrees (`in`), the final answer (`jawab`), an adjacency list (`al`), and a queue (`q`).
   
**Built Graph :**
- Created an adjacency list representing the directed edges between courses based on prerequisites.
- Calculated the in-degree of each course, i.e., the number of prerequisites it has.

**Initialized Queue :**
- Added courses with in-degree 0 to the queue initially.

**BFS Topological Sort :**
- Processed the courses in a Breadth-First Search (BFS) manner:
  - Poll a course from the queue.
  - Added the course to the answer (`jawab`).
  - Updated the in-degrees of its neighbors and add them to the queue if their in-degree becomes 0.

**Checked for Valid Order :**
- After processing all courses, checked if all courses have in-degree 0. If not, return an empty array since a valid order is not possible.

**Returned Result:**
- Returned the final answer (`jawab`) representing the order in which courses can be taken.

The BFS ensures that I processed courses with no prerequisites first, gradually moving to courses with all prerequisites satisfied. If a valid topological order exists, I returned it; otherwise, it returned an empty array.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(m + n)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ : number of courses

$m$ : number of prerequisites

- Space complexity : $O(m + n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code 
```
//User function Template for Java

class Solution {

    public boolean isTree(int n, int m, ArrayList<ArrayList<Integer>> edges) {
        
        // Creating an adjacency list to represent the graph
        ArrayList<Integer>[] graph = new ArrayList[n];
        for (int i = 0; i < n; i++) {
            graph[i] = new ArrayList<>();
        }

        // Populating the adjacency list based on the provided edges
        for (int i = 0; i < m; i++) {
            graph[edges.get(i).get(0)].add(edges.get(i).get(1));
            graph[edges.get(i).get(1)].add(edges.get(i).get(0));
        }

        // Array to keep track of visited nodes during BFS
        int[] visited = new int[n];

        // Counting the number of connected components in the graph
        int components = 0;
        for (int i = 0; i < n; i++) {
            if (visited[i] == 0) {
                components++;
                bfs(graph, visited, i);
            }
        }

        // If there is more than one connected component, it's not a tree
        if (components > 1) {
            return false;
        }

        // Checking for cycle in the graph
        if (hasCycle(graph, n)) {
            return false;
        }

        // If no issues are found, the graph is a tree
        return true;
    }

    // BFS helper function to traverse the graph and mark connected components
    static void bfs(ArrayList<Integer>[] graph, int[] visited, int start) {
        Queue<Integer> queue = new LinkedList<>();
        queue.add(start);
        visited[start] = 1;

        while (!queue.isEmpty()) {
            int node = queue.poll();

            for (int neighbor : graph[node]) {
                if (visited[neighbor] == 0) {
                    queue.add(neighbor);
                    visited[neighbor] = 1;
                }
            }
        }
    }

    // Helper function to check if the graph has a cycle
    static boolean hasCycle(ArrayList<Integer>[] graph, int n) {
        int[] visited = new int[n];
        Queue<int[]> queue = new LinkedList<>();
        queue.add(new int[]{0, -1});
        visited[0] = 1;

        while (!queue.isEmpty()) {
            int node = queue.peek()[0];
            int parent = queue.peek()[1];
            queue.poll();

            for (int neighbor : graph[node]) {
                if (visited[neighbor] == 1) {
                    if (parent == neighbor) {
                        // Skipping the edge to the parent in case of undirected graph
                        continue;
                    } else {
                        // If a node is already visited and not the parent, a cycle exists
                        return true;
                    }
                } else {
                    queue.add(new int[]{neighbor, node});
                    visited[neighbor] = 1;
                }
            }
        }
        return false;
    }
}

```

