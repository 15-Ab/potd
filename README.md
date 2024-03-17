🚀 Enjoy exploring my solution and keep the coding spirit alive! Happy coding ! ✨


## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 17-03-24 [Problem Link](https://www.geeksforgeeks.org/problems/count-pairs-whose-sum-is-equal-to-x/1)
## Count Pairs whose sum is equal to X

## Intuition
The task is to count pairs from two linked lists `head1` and `head2` that sum up to a given integer `x`. To achieve this, I can use a HashMap to store the frequencies of elements in the first linked list. Then, for each element in the second linked list, I check if its complement (i.e., `x - element`) exists in the HashMap. If it exists, I increment the count by the frequency of the complement.

## Approach

- I initialized a HashMap to store the frequency of elements from `head1`.
- Iterated through `head1` and populated the HashMap with the frequency of each element.
- Iterated through `head2`.
  - For each element `num` in `head2`, checked if `x - num` exists in the HashMap.
  - If it existed, incremented the count by the frequency of `x - num`.
- After iterating through `head2`, returned the count as the result.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $O( n )$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ :  total number of elements in both linked lists
- Space complexity : $O( n )$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code

```
//  User function Template for Java

// your task is to complete this function

/*
class Node
{
    int data;
    Node next;

    Node(int key)
    {
        data = key;
        next = null;
    }
}
*/

class Solution {
    
    static HashMap<Integer, Integer> m;

    public static int countPairs(LinkedList<Integer> head1, LinkedList<Integer> head2, int x) {
        // add your code here
        m = new HashMap<>();
        int jawab = 0;
        
        // Counting occurrences of elements in head1
        for (int num : head1) {
            m.put(num, m.getOrDefault(num, 0) + 1);
        }
        
        // Checking for pairs in head2
        for (int num : head2) {
            if (m.containsKey(x - num)) {
                jawab += m.get(x - num);
            }
        }
        
        return jawab;
    }
}
```
