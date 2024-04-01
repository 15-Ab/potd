🚀 Enjoy exploring my solution and keep the coding spirit alive! Happy coding ! ✨

## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 01-04-24 [Problem Link](https://www.geeksforgeeks.org/problems/pairs-violating-bst-property--212515/1)
## Pairs violating the BST property

## Intuition
Count the number of pairs of nodes violating the BST property.

## Approach
- Traversed the BST in inorder to obtain a sorted array of its elements.
- While traversing, count inversions, i.e., the number of times a smaller value appears after a larger value.
- Used a modified merge sort to count inversions during merging of sorted subarrays.
- Returned the inversion count as the result.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $O(n*logn)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$n$ : number of nodes in the BST

- Space complexity : $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code

```
//  User function Template for Java

/*

Definition for Binary Tree Node
class Node
{
    int data;
    Node left;
    Node right;

    Node(int data)
    {
        this.data = data;
        left = null;
        right = null;
    }
}
*/

class Solution {
    static int inversionCount;
    
    public static int pairsViolatingBST(int n, Node root) {
        inversionCount = 0;
        int[] arr = new int[n];
        inorderTraversal(root, arr);
        return mergeSortAndCount(arr, 0, n - 1);
    }
    
    static void inorderTraversal(Node root, int[] arr) {
        if (root == null) {
            return;
        }

        inorderTraversal(root.left, arr);
        arr[inversionCount++] = root.data;
        inorderTraversal(root.right, arr);
    }
    
    static int mergeSortAndCount(int[] arr, int l, int r) {
        int count = 0;
        if (l < r) {
            int m = (l + r) / 2;
            count += mergeSortAndCount(arr, l, m);
            count += mergeSortAndCount(arr, m + 1, r);
            count += mergeAndCount(arr, l, m, r);
        }
        return count;
    }

    static int mergeAndCount(int[] arr, int l, int m, int r) {
        int n1 = m - l + 1;
        int n2 = r - m;
        int[] left = new int[n1];
        int[] right = new int[n2];

        for (int i = 0; i < n1; i++) {
            left[i] = arr[l + i];
        }
        for (int i = 0; i < n2; i++) {
            right[i] = arr[m + 1 + i];
        }

        int count = 0, i = 0, j = 0, inversionCount = l;

        while (i < n1 && j < n2) {
            if (left[i] <= right[j]) {
                arr[inversionCount] = left[i];
                i++;
            } else {
                arr[inversionCount] = right[j];
                j++;
                count += (n1 - i);
            }
            inversionCount++;
        }

        while (i < n1) {
            arr[inversionCount] = left[i];
            i++;
            inversionCount++;
        }
        while (j < n2) {
            arr[inversionCount] = right[j];
            j++;
            inversionCount++;
        }
        return count;
    }
}
```