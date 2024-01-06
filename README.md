# Problem Of The Day Solutions

This is my attemp to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.

## Today's 06-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/techfest-and-the-queue1044/1)
## Techfest and the Queue

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My intuition is to breaking down each number into its prime factors and summing up the powers of those prime factors.

# Approach
<!-- Describe your approach to solving the problem. -->
- Prime Factorization (primeFactorization method) :
- - I initialized a Map<Integer, Integer> named 'bhajak' to store prime factors and their counts.
- - I startes with the smallest prime divisor (2) and iterate until the given number is reduced to 1.
- - While iterating, divide the number by the divisor:
- - - If the division is successful (remainder is 0), count how many times the divisor divides the number.
- - - If the count is greater than 0, add an entry to the map with the divisor as the key and the count as the value.
- - Move to the next divisor and repeat until the number is completely factored.
- - Return the bhajak map representing the prime factorization.
- Sum of Powers (sumhelper method) :
- - Take a number as input and calculate the sum of powers of its prime factorization.
- - Call the primeFactorization method to obtain the prime factors and their counts (bhajak map).
- - Iterate over the values (counts) in the bhajak map and add them to the sum.
- - Return the final sum representing the sum of powers of prime factorization for the given number.
- Range Calculation (sumOfPowers method) :
- - Take two parameters, a and b, representing the range of numbers [a, b].
- - Initialize a variable sum to store the cumulative sum of powers for all numbers in the range.
- - Iterate over each integer in the range [a, b] (inclusive).
- - For each number, call the sumhelper method to calculate the sum of powers of its prime factorization.
- - Add the result to the sum.
- - Return the final sum representing the sum of powers for all numbers in the specified range.
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

# Complexity
- Time complexity : $$O((b-a)*$\sqrt{k}$)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
- Space complexity : $$O(p)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$p$$ : number of prime factors

# Code
```
import java.util.HashMap;
import java.util.Map;

public class Solution {
    // Method to calculate the sum of powers for each number in the range [a, b]
    public static long sumOfPowers(long a, long b) {
        long sum = 0;

        // Iterate over the range [a, b] and calculate the sum of powers using sumhelper
        for (int i = (int) a; i <= (int) b; i++) {
            sum += sumhelper(i);
        }

        return sum;
    }

    // Method to find the sum of powers of prime factorization for a given number
    public static long sumhelper(int number) {
        long sum = 0;

        // Calculate the prime factorization for the given number
        Map<Integer, Integer> primebhajak = primeFactorization(number);

        // Iterate over the values (exponents) in the prime factorization and add them to the sum
        for (int v : primebhajak.values()) {
            sum += v;
        }

        return sum;
    }

    // Method to calculate the prime factorization of a number
    public static Map<Integer, Integer> primeFactorization(int n) {
        Map<Integer, Integer> bhajak = new HashMap<>();
        int divisor = 2;

        while (n > 1) {
            int count = 0;

            // Divide by the divisor and count the number of times it divides
            while (n % divisor == 0) {
                n /= divisor;
                count++;
            }

            // If the count is greater than 0, add the divisor and count to the map
            if (count > 0) {
                bhajak.put(divisor, count);
            }

            divisor++;

            // If the square of the divisor is greater than n and n is still greater than 1, add n to the map
            if (divisor * divisor > n && n > 1) {
                bhajak.put(n, 1);
                break;
            }
        }

        return bhajak;
    }
}

```

