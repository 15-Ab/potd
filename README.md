# 🔱 Embracing the cosmic energy this Mahashivratri ! 
## Wishing everyone a day filled with devotion, introspection, and coding adventures. Let the blessings of Lord Shiva guide our paths in the coding realm. 🖥️🕉️ #Mahashivratri #CodeWithDevotion #GitHubDiaries

🚀 Enjoy exploring my solution and keep the coding spirit alive! Happy coding ! ✨


## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 10-03-24 [Problem Link](https://www.geeksforgeeks.org/problems/remove-all-duplicates-from-a-given-string4321/1)
## Remove all duplicates from a given string

## Intuition
The objective is to remove duplicate characters from a given string and return the modified string. The code utilizes a HashSet to efficiently track unique characters and build the resulting string without duplicates.

## Approach

**Initialization **
   - Initialized an empty string (`jawab`) to store the result.
   - Initialized a HashSet (`h`) to keep track of unique characters encountered.

**Character Iteration **
   - Iterated through each character (`c`) in the input string (`str`).

**Duplicate Check **
   - Checked if the HashSet (`h`) does not contain the current character (`c`).
     - If true, proceeded to the next step.
     - If false, skipped the current iteration as the character is a duplicate.

**Result String Update **
   - Added the non-duplicate character (`c`) to the result string (`jawab`).

**HashSet Update **
   - Added the character (`c`) to the HashSet (`h`) to mark it as encountered.

**Result **
   - Returned the final string (`jawab`) with duplicates removed.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $O( n )$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ : length of the input string `s`

$u$ : number of unique characters encountered during the iteration
- Space complexity : $O( u )$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code

```
//  User function Template for Java

class Solution {
    
    // Static variables for storing the result and a HashSet for efficient duplicate checking.
    static String jawab;
    static HashSet<Character> h;

    // Method to remove duplicates from the input string.
    String removeDuplicates(String str) {
        // Initializing an empty string to store the result.
        jawab = "";

        // Initializing a HashSet to keep track of unique characters.
        h = new HashSet<>();

        // Iterating through each character in the input string.
        for (char c : str.toCharArray()) {
            // Check if the character is not already in the HashSet (duplicate check).
            if (!h.contains(c)) {
                // Adding the character to the result string.
                jawab += c;

                // Adding the character to the HashSet to mark it as encountered.
                h.add(c);
            }
        }

        // Returning the string with duplicates removed.
        return jawab;
    }
}
```
