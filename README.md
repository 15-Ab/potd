# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 19-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/top-k-numbers3425/1)
## Top k numbers in a stream

### Intuition
This problem involves finding the minimum number of sprinklers needed to cover the entire gallery. To approach this problem, I used the following strategy :

**Identifed valid sprinklers :** Filtered out the valid sprinklers based on their range (ignoring the ones with `-1` range).

**Sorted the sprinklers :** Sorted the sprinklers based on their left positions.

**Iterated through sprinklers :** Started iterating through the sorted sprinklers. For each sprinkler, check if its left position is covered. If not, return `-1`. Otherwise, update the covered range based on the current sprinkler's right position.

**Counted minimum taps :** Counted the number of taps used during the iteration.

### Approach

- Created an `ArrayList` to store the sprinklers' information, where each element is an object containing left, right, and value (range) of the sprinkler.
- Filtered out the invalid sprinklers (ones with `-1` range) and add them to the ArrayList.
- Sorted the ArrayList based on the left positions of the sprinklers.
- Initialized variables to keep track of the current and last covered positions.
- Iterated through the sorted sprinklers :
- - If a sprinkler's left position is beyond the current covered range + 1, returned `-1`.
- - If a sprinkler's left position is within or equal to the current covered range + 1, update the covered range based on the sprinkler's right position.
- - If a sprinkler's left position is greater than the current covered range + 1, updated the last covered position and covered range based on the current sprinkler, and increment the tap count.
- Returned the minimum number of taps + 1.
- - The final result is the minimum number of sprinklers needed to cover the entire gallery.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(s log s)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$s$ : number of valid sprinklers
- Space complexity : $O( s)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code
```
import java.util.*;

class Solution {
    // Function to determine the top K elements based on frequency at each iteration
    public static ArrayList<ArrayList<Integer>> kTop(int[] arr, int N, int K) {
        // Resultant array of arrays to store the top K elements at each iteration
        ArrayList<ArrayList<Integer>> result = new ArrayList<>();

        // Array to maintain the current top K elements along with an extra slot
        int[] jada = new int[K + 1];

        // HashMap to store the frequency of each element
        HashMap<Integer, Integer> m = new HashMap<>();

        // Initialize the frequency map with zeros for each element from 0 to K
        for (int i = 0; i <= K; i++) {
            m.put(i, 0);
        }

        // Iterate over the input array
        for (int i = 0; i < arr.length; i++) {
            // Update the last slot of jada with the current element
            jada[K] = arr[i];

            // Update the frequency map for the current element
            if (m.containsKey(arr[i])) {
                m.put(arr[i], m.get(arr[i]) + 1);
            } else {
                m.put(arr[i], 1);
            }

            // Find the position of the current element in jada
            int in = -1;
            for (int j = 0; j < jada.length; j++) {
                if (jada[j] == arr[i]) {
                    in = j;
                    break;
                }
            }
            in--;

            // Move the current element to its correct position in jada based on frequency
            while (in >= 0) {
                if (m.get(jada[in]) < m.get(jada[in + 1])) {
                    int t = jada[in];
                    jada[in] = jada[in + 1];
                    jada[in + 1] = t;
                } else if ((jada[in] > jada[in + 1]) && (m.get(jada[in]) == m.get(jada[in + 1]))) {
                    int t = jada[in];
                    jada[in] = jada[in + 1];
                    jada[in + 1] = t;
                } else {
                    break;
                }
                in--;
            }

            // Populate the current array with the top K elements and add it to the result
            ArrayList<Integer> aa = new ArrayList<>();
            for (int e = 0; e < K && jada[e] != 0; e++) {
                aa.add(jada[e]);
            }
            result.add(aa);
        }

        // Return the final result
        return result;
    }
}

```

