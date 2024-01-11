# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 11-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/remove-k-digits/1)
## Remove K Digits

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
A this code aims to find the minimum number that can be obtained by removing K digits from the given string. My approach involves using a stack to keep track of the digits and ensuring that the resulting number is minimal.

# Approach
<!-- Describe your approach to solving the problem. -->
**Base Case:**
   - If the length of the string `S` is less than or equal to `K`, return "0" since all digits can be removed.

**Stack to Build Minimum Number:**
   - Use a stack (`s`) to build the minimum number.
   - Iterate through each character in the string.
   - While the stack is not empty, the current character is smaller than the top of the stack, and there are still digits to be removed (`K > 0`):
      - Pop elements from the stack.
      - Decrement `K`.
   - Push the current character onto the stack.

**Remove Remaining Digits:**
   - After the iteration, if there are remaining digits to be removed (`K > 0`), pop elements from the end of the stack.

**Build Minimum Number from Stack:**
   - Use a `StringBuilder` (`min`) to build the minimum number from the elements in the stack.
   - Ignore leading zeros by skipping them.

**Result:**
   - If the resulting number is empty, return "0"; otherwise, return the string representation of the minimum number.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$n$ : number of elements
- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
    public String removeKdigits(String S, int K) {

        // Check if the length of the string is less than or equal to K
        if (S.length() <= K) {
            return "0";
        }

        // Use a stack to build the minimum number by removing larger digits
        Stack<Character> s = new Stack<>();
        for (int i = 0; i < S.length(); i++) {
            // Pop elements from the stack if a larger digit is encountered and K > 0
            while (!s.isEmpty() && s.peek() > S.charAt(i) && K > 0) {
                s.pop();
                K--;
            }
            // Push the current character onto the stack
            s.push(S.charAt(i));
        }

        // Remove remaining K digits from the end, if necessary
        while (K-- > 0) {
            s.pop();
        }

        // Build the minimum number from the stack, ignoring leading zeros
        StringBuilder min = new StringBuilder();
        for (char c : s) {
            // Ignore leading zeros
            if (c == '0' && min.length() == 0) {
                continue;
            }
            min.append(c);
        }

        // If the resulting number is empty, return "0"
        return min.length() == 0 ? "0" : min.toString();
    }
}

```

