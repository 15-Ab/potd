# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 18-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/water-the-plants--170646/1)
## Water the plants

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
//User function Template for Java

class jora {
    int left;
    int right;
    int value;

    jora(int l, int r, int v) {
        this.left = l;
        this.right = r;
        this.value = v;
    }
}

class Solution {
    
    int min_sprinklers(int gallery[], int n) {
        // ArrayList to store the sprinklers' information
        ArrayList<jora> al = new ArrayList<>();

        // Filtering out invalid sprinklers and adding them to the ArrayList
        for (int i = 0; i < n; i++) {
            if (gallery[i] == -1) {
                continue;
            }
            int l = Math.max(i - gallery[i], 0);
            int r = Math.min(i + gallery[i], n - 1);
            int v = gallery[i];
            al.add(new jora(l, r, v));
        }

        // Sorting the sprinklers based on their left positions
        Collections.sort(al, (p, q) -> p.left - q.left);

        // Variables to keep track of current and last covered positions
        int in = 0;
        int minTap = 0;
        int suru = -1;
        int khtm = -1;

        // Iterating through sprinklers to find the minimum number of taps
        while (in < n && khtm < n - 1) {
            jora j = al.get(in);
            if (j.left <= suru + 1) {
                khtm = Math.max(khtm, j.right);
            } 
            else if (j.left > khtm + 1) {
                return -1;
            } 
            else {
                suru = khtm;
                khtm = j.right;
                minTap++;
            }
            in++;
        }

        // Returning the minimum number of taps + 1
        return minTap + 1;
    }
}
```

