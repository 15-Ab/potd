# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 15-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/grinding-geek/1)
## Grinding Geek

### Intuition
My code aims to find the maximum number of courses that Geek can complete within a specific time frame, considering a certain total budget. Geek has to buy courses each day, and if he completes 90% of the course on the same day, he receives a 90% refund. This involves dynamic programming, where my goal is to maximize the number of completed courses.

### Approach

**Dynamic Programming:**
   - My code utilizes a dynamic programming approach to solve the problem.
   - It maintains an array `gp` to store the maximum number of courses that can be completed with a given total budget.
   - The outer loop iterates over the courses in reverse order, starting from the last day.
   - The inner loop iterates over the total budget, considering different budget scenarios.
   - If the current budget is sufficient to buy the current course, the code calculates the remaining budget after enrolling in the course with a 10% refund.
   - The `gp` array is updated to maximize the number of courses that can be completed at the current budget.

**Result:**
   - After the dynamic programming process, my function returns `gp[total]`, which represents the maximum number of courses that can be completed with the total budget.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(n*total)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ : number of courses

$total$ : total budget

$n$ : number of column(s)
- Space complexity : $O(total)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code
```
// User function Template for Java
class Solution {
    public int max_courses(int n, int total, int[] cost) {
        // Array to store the maximum number of courses that can be completed with a given total budget
        int[] gp = new int[1 + total];
        int t;

        // Iterated over courses in reverse order (from the last day to the first)
        for (int i = cost.length - 1; i >= 0; i--) {
            // Iterated over the total budget
            for (int j = total; j >= 0; j--) {
                // Checked if the budget is sufficient to buy the current course
                if (j >= cost[i]) {
                    // Calculated the remaining budget after enrolling in the course with a 10% refund
                    t = j - cost[i] + (9 * cost[i]) / 10;
                    
                    // Updated gp[j] to maximize the number of courses that can be completed
                    gp[j] = Math.max(gp[j], gp[t] + 1);
                }
            }
        }

        // Returned the maximum number of courses that can be completed with the total budget
        return gp[total];
    }
}
```

