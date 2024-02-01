## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 01-02-24 [Problem Link](https://www.geeksforgeeks.org/problems/pangram-checking-1587115620/1)
## Panagram Checking

## Intuition

The goal of this problem is to determine whether a given string is a pangram or not. A pangram is a sentence containing every letter of the alphabet at least once.


## Approach

**Converted to Lowercase :**
   - Converted the input string `s` to lowercase to make the check case-insensitive.

**HashSet for Unique Alphabets :**
   - Used a `HashSet` (`h`) to store unique lowercase alphabets encountered in the string.

**Iterated Through Characters :**
   - Iterated through each character (`c`) in the lowercase string.
   - Checked if the character is a lowercase alphabet (`'a'` to `'z'`).

**Added to HashSet:**
   - If the character is a lowercase alphabet, added it to the `HashSet` to ensure uniqueness.

**Check for Pangram :**
   - After processing the entire string, checked if the size of the `HashSet` is 26.
   - If the size is 26, it indicates that all lowercase alphabets are present in the string.

**Result :**
   - Returned `true` if the size is 26, indicating a pangram.
   - Returned `false` otherwise.

My code employs a HashSet to keep track of unique lowercase alphabets in the given string. After iterating through the string and adding alphabets to the HashSet, I checked if the size of the HashSet is 26 to determine whether the string is a pangram or not. The conversion to lowercase ensures case-insensitivity.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(s)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$s$ :  length of the input string.

- Space complexity : $O(26) = O(1) : Constant$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code 
```
//User function Template for JAVA

class Solution {
    // Function to check if a string is Pangram or not.
    public static boolean checkPangram(String s) {
        
        // Converting the input string to lowercase
        s = s.toLowerCase(); 

        // HashSet to store unique lowercase alphabets encountered
        HashSet<Character> h = new HashSet<>();

        // Iterating through each character in the string
        for (char c : s.toCharArray()) {
            // Checking if the character is a lowercase alphabet
            if (c >= 'a' && c <= 'z') {
                // Adding the lowercase alphabet to the HashSet
                h.add(c);
            }
        }

        // Checking if the size of the HashSet is 26, indicating all lowercase alphabets are present
        return h.size() == 26;
    }
}
```

