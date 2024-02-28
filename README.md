## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 28-02-24 [Problem Link](https://www.geeksforgeeks.org/problems/check-if-a-number-is-divisible-by-83957/1)
## Check if a number is divisible by 8

## Intuition
The goal of the function `DivisibleByEight` is to determine whether a given string is divisible by 8.

## Approach

**Checked Length :**
   - If the length of the string (`s`) is less than or equal to 3 :
     - Converted the entire string to an integer.
     - Checked if the integer is divisible by 8.
     - Returned 1 if divisible, -1 otherwise.

**Considered Last Three Digits :**
   - If the length of the string is greater than 3 :
     - Considered the last three characters of the string.
     - Converted this substring to an integer.
     - Checked if the integer is divisible by 8.
     - Returned 1 if divisible, -1 otherwise.


- My approach leveraged the fact that a number is divisible by 8 if its last three digits are divisible by 8.
- If the string is short (length <= 3), the entire string is checked for divisibility.
- If the string is longer, only the last three characters are considered.
- The function returned 1 if the condition is met, and -1 otherwise.

My approach optimally handled both short and long strings, making use of the divisibility rule for 8.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $O(1)$ OR $O(2)$ OR $O(3)$ ${\equiv}$ $O(1)$
<!-- Add your time complexity here, e.g. $$O())$$ -->

- Space complexity : $O(1)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
   
## Code 

```
// User function Template for Java

class Solution{
    
    // Function to check if a substring or the whole string is divisible by 8
    int DivisibleByEight(String s){
        // Code here
        
        // Checking if the length of the string is less than or equal to 3
        if( s.length() <= 3){
            // If yes, converting the string to an integer and checking if it's divisible by 8
            if( Integer.parseInt(s) % 8 == 0 ){
                return 1; // Returning 1 if divisible by 8
            }
            return -1; // Returning -1 if not divisible by 8
        }
        else{
            // If the length is greater than 3, considering the last three characters of the string
            if( Integer.parseInt( s.substring(s.length()-3) ) % 8 == 0 ){
                return 1; // Returning 1 if the last three characters are divisible by 8
            }
            return -1; // Returning -1 if the last three characters are not divisible by 8
        }
    }
}
```
