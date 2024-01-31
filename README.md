## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 31-01-24 [Problem Link](https://www.geeksforgeeks.org/problems/trie-insert-and-search0651/1)
## Insert and Search in a Trie

## Intuition

My code implements the basic operations of a Trie data structure, specifically, inserting a string into the Trie and searching for a string in the Trie. A Trie is a tree-like data structure used for efficient retrieval of strings, making it suitable for tasks like autocomplete.


## Approach

### Insert Function

**Initialization :**
- Initialized a TrieNode variable `currentNode` to traverse the Trie starting from the root.
    
**Iteration :**
- Iterated through each character in the input string (`key`).
- Calculated the index for the current character in the Trie node's children array (`index = key.charAt(layer) - 'a'`).
    
**Insertion :**
- If the child node corresponding to the current character is null, created a new TrieNode (`if (currentNode.children[index] == null)`).
- Moved to the next TrieNode in the Trie for the current character (`currentNode = currentNode.children[index]`).

**Mark End of Word:**
- Marked the last TrieNode as the end of the inserted word (`currentNode.isEndOfWord = true`).

### Search Function

**Initialization :**
- Initialized a TrieNode variable `currentNode` to traverse the Trie starting from the root.

**Iteration :**
- Iterated through each character in the input string (`key`).
- Calculated the index for the current character in the Trie node's children array (`index = key.charAt(layer) - 'a'`).
    
**Search :**
- If the child node corresponding to the current character is null, the word is not present, and the search fails (`if (currentNode.children[index] == null)`).
- Moved to the next TrieNode in the Trie for the current character (`currentNode = currentNode.children[index]`).

**Checked End of Word :**
- Checked if the last TrieNode in the path represents the end of a word (`return currentNode.isEndOfWord`).

My approach efficiently inserts words into the Trie and searches for words with a time complexity proportional to the length of the words being inserted or searched for.

---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)

## Complexity
- Time complexity : $O(k)$
<!-- Add your time complexity here, e.g. $$O())$$ -->
$k$ :  length of the input string `key`

If there are `N` words with an average length of `L` inserted into the Trie, the overall time complexity for building the Trie is $O(N * L)$.

- Space complexity : $O(N*L)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code 
```
//User function Template for Java

/*
static final int ALPHABET_SIZE = 26;

    // trie node
    static class TrieNode {
        TrieNode[] children = new TrieNode[ALPHABET_SIZE];

        // isEndOfWord is true if the node represents
        // end of a word
        boolean isEndOfWord;

        TrieNode() {
            isEndOfWord = false;
            for (int i = 0; i < ALPHABET_SIZE; i++) children[i] = null;
        }
    };
*/

// Function to insert a string into the TRIE.
static void insert(TrieNode root, String key) {
    // Initialized a TrieNode variable to traverse the TRIE starting from the root.
    TrieNode t = root;

    // Iterated through each character in the input key.
    for (int layer = 0; layer < key.length(); layer++) {
        // Calculated the index for the current character in the TRIE node's children array.
        int index = key.charAt(layer) - 'a';

        // If the child node corresponding to the current character is null, created a new TrieNode.
        if (t.children[index] == null) {
            t.children[index] = new TrieNode();
        }

        // Moved to the next TrieNode in the TRIE for the current character.
        t = t.children[index];
    }

    // Marked the last TrieNode as the end of the inserted word.
    t.isEndOfWord = true;
}

// Function to use the TRIE data structure and search for the given string.
static boolean search(TrieNode root, String key) {
    
    // Initialized a TrieNode variable to traverse the TRIE starting from the root.
    TrieNode t = root;

    // Iterated through each character in the input key.
    for (int layer = 0; layer < key.length(); layer++) {
        // Calculated the index for the current character in the TRIE node's children array.
        int index = key.charAt(layer) - 'a';

        // If the child node corresponding to the current character is null, the word is not present.
        if (t.children[index] == null) {
            return false;
        }

        // Moved to the next TrieNode in the TRIE for the current character.
        t = t.children[index];
    }

    // Checked if the last TrieNode in the path represents the end of a word.
    return t.isEndOfWord;
}
```

