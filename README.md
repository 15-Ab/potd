# Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 09-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/search-pattern0205/1)
## Search Pattern (KMP-Algorithm)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My code aims to find all occurrences of a given pattern within a given text using the Knuth-Morris-Pratt (KMP) pattern matching algorithm. The KMP algorithm efficiently handles pattern matching by utilizing information from previous matching attempts.

# Approach
<!-- Describe your approach to solving the problem. -->
- Initialization :
- - Initialized an ArrayList (al) to store the starting indices of pattern occurrences.
- - Initialized an array (a) to store information related to the KMP algorithm.
- KMP Prefix Array Construction (helperKMP) :
- - The helperKMP method constructs the prefix array (a) for the given pattern.
- - The prefix array represents the length of the proper prefix that is also a proper suffix for each position in the pattern.
- Pattern Search (search) :
- - Iterated through the text (txt) and the pattern (pat) using indices i and ia respectively.
- - If characters at the current positions matched, incremented both indices (i and ia).
- - If the entire pattern is matched, added the starting index of the occurrence to the ArrayList (al), and adjusted the pattern index (ia) based on the prefix array.
- - If there is a mismatch between characters:
- - - If 'ia' is zero, incremented the text index (i).
- - - If 'ia' is non-zero, adjusted 'ia' based on the prefix array.
- Result :
- - My ArrayList 'al' contains the starting indices of all occurrences of the pattern in the text. 

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $O(p+t)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
 
- Space complexity : $O(p+k)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

$p$ : length of pattern  

$t$ : length of text 

$k$ : represents the number of occurrences of the pattern in the text.

# Code
```
//User function Template for Java

class Solution {
    // Created static arrays to store information for KMP algorithm
    static int[] a;
    static ArrayList<Integer> al;

    // Main method for pattern search in text using KMP algorithm
    ArrayList<Integer> search(String pat, String txt) {
        // Initialized an ArrayList to store the starting indices of pattern occurrences
        al = new ArrayList<>();

        // Length of the pattern
        int l = pat.length();

        // Initialized the prefix array for the KMP algorithm
        a = new int[l];

        // Built the prefix array using the helper method
        helperKMP(pat);

        // Initialized indices for pattern (ia) and text (i)
        int ia = 0;
        int i = 0;

        // Iterated through the text
        while (i < txt.length()) {
            // If characters matched, moved to the next characters in both pattern and text
            if (txt.charAt(i) == pat.charAt(ia)) {
                i++;
                ia++;
            }

            // If the entire pattern is matched, added the starting index to the result list
            if (ia == l) {
                al.add(i - ia + 1);
                ia = a[ia - 1]; // Moved the pattern index based on the prefix array
            } else if (i < txt.length() && txt.charAt(i) != pat.charAt(ia)) {
                // Mismatch between characters

                if (ia == 0) {
                    i++;
                } else {
                    // Move the pattern index based on the prefix array
                    ia = a[ia - 1];
                }
            }
        }

        // Returned the list of starting indices of pattern occurrences
        return al;
    }

    // Helper method to build the prefix array using the KMP algorithm
    static void helperKMP(String pattern) {
        a[0] = 0;
        int s = 0;

        // Iterated through the pattern to build the prefix array
        for (int i = 1; i < pattern.length(); i++) {
            if (pattern.charAt(s) == pattern.charAt(i)) {
                s++;
                a[i] = s;
            } else if (s == 0) {
                a[i] = s;
            } else {
                s = a[s - 1];
                i--;
            }
        }
    }
}

```

