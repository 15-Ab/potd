# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 24-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/is-it-a-tree/1)
## Check if a given graph is tree or not

## Intuition

The goal is to determine whether a given graph is a tree. A tree in graph theory is a connected acyclic graph, and to validate this, I checked for connected components and the absence of cycles.

## Approach

##### Built Graph :
   - Created an adjacency list to represent the graph using an array of ArrayLists. Populate the adjacency list based on the provided edges.

##### Connected Components :
   - Used Breadth-First Search (BFS) to traverse the graph and mark connected components.
   - Maintained an array to keep track of visited nodes during BFS.
   - Counted the number of connected components in the graph.

##### Checked for Multiple Components :
   - If the number of connected components is greater than 1, the graph is not a tree (as a tree should be a single connected component).

##### Checked for Cycles :
   - Used BFS to detect cycles in the graph.
   - Maintained an array to keep track of visited nodes during cycle detection.
   - If a visited node is encountered, checked if it is the parent of the current node. If not, a cycle exists.

##### Final Decision :
   - If the graph has multiple connected components or contains a cycle, it is not a tree. Returned false in such cases.
   - If no issues are found, the graph is a tree. Returned true.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(N + M)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$N$ : number of nodes

$M$ : number of edges

- Space complexity : $O(N)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code 
```
//User function Template for Java

class Solution {
    
    // Function to find the minimum number of flips required to transform Num1 to Num2
    int solve(int Num1, int Num2) {
        // If Num1 is already equal to Num2, no flips are needed
        if (Num1 == Num2) return 0;

        // Initializing a queue for BFS traversal
        Queue<Integer> queue = new LinkedList<>();
        queue.add(Num1);

        // Set to track visited number strings to avoid cycles
        Set<String> visitedNumStrings = new HashSet<>();

        // Variable to track the number of flips
        int flips = 0;

        // Performing BFS traversal
        while (!queue.isEmpty()) {
            int size = queue.size();
            while (size != 0) {
                int poppedNum = queue.remove();
                size--;

                String startNumString = String.valueOf(poppedNum);

                // Skipping if the number string is already visited
                if (!visitedNumStrings.add(startNumString.toString())) continue;

                // Iterating over each digit in the number string
                for (int i = 0; i < 4; i++) {
                    StringBuffer currString = new StringBuffer(startNumString);
                    // Trying to change the digit to every possible digit from '0' to '9'
                    for (char c = '0'; c <= '9'; c++) {
                        // Skipping if the digit doesn't change or the first digit becomes '0'
                        if (currString.charAt(i) == c || (i == 0 && c == '0')) {
                            continue;
                        }
                        currString.setCharAt(i, c);
                        int changedNum = Integer.parseInt(currString.toString());

                        // If the changed number becomes Num2, returning the number of flips
                        if (changedNum == Num2) {
                            return flips + 1;
                        }

                        // If the changed number is prime, adding it to the queue for further exploration
                        if (isPrime(changedNum)) {
                            queue.offer(changedNum);
                        }
                    }
                }
            }
            flips++; // Incrementing flips per level in BFS
        }

        // If no transformation is possible, returning -1
        return -1;
    }

    // Function to check if a number is prime
    static boolean isPrime(int num) {
        if (num <= 1) return false;

        for (int i = 2; i <= Math.sqrt(num); i++) {
            if (num % i == 0) return false;
        }

        return true;
    }
}

```

