# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 12-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/reverse-first-k-elements-of-queue/1)
## Reverse First K elements of Queue

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My code is implementing a function to reverse the first k elements of a given queue.

# Approach
<!-- Describe your approach to solving the problem. -->
**Input Parameters:** My function takes a `Queue<Integer>` and an integer `k`.
**Calculated Unchanged Elements:** Determined the number of unchanged elements in the queue by subtracting `k` from its total size.
**Temporary Storage with Stack:**
   - Used a `Stack<Integer>` to temporarily store the first k elements of the queue.
   - Iterated over the first k elements, dequeuing each element and pushing it onto the stack, effectively reversing their order.
**Reversed Order Back to Queue:**
   - Iterated over the elements in the stack, dequeuing each element and enqueuing it back into the original queue, reversing their order again.
**Enqueued Remaining Unchanged Elements:**
   - Iterated over the remaining unchanged elements in the queue and enqueued them back.
**Returned Modified Queue:**
   - The modified queue is returned as the final result.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(k+(n-k)) = O(n)$
<!-- Add your time complexity here, e.g. $$O(k+(n-k))$$ -->
$n$ : size of queue
- Space complexity : $O(k)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
// User function Template for Java

class GfG {
    // Function to reverse first k elements of a queue.
    public Queue<Integer> modifyQueue(Queue<Integer> q, int k) {
        // Calculated the number of unchanged elements.
        int unchanged = q.size() - k;
    
        // Used a stack to temporarily store the first k elements.
        Stack<Integer> s = new Stack<>();
        for (int i = 0; i < k; i++) {
            s.push(q.poll());
        }
    
        // Reversed the order of the first k elements and enqueued them back.
        while (!s.isEmpty()) {
            q.offer(s.pop());
        }
    
        // Enqueued the remaining unchanged elements.
        for (int i = 0; i < unchanged; i++) {
            q.offer(q.poll());
        }
    
        // Returned the modified queue.
        return q;
    }
}
```

