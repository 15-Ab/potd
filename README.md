🚀 Enjoy exploring my solution and keep the coding spirit alive! Happy coding ! ✨


## Problem Of The Day Solutions

This is my attempt to make the coding experience easier for you guys so that you can easily learn what to do in today's problem of the day.

## Today's 16-03-24 [Problem Link](https://www.geeksforgeeks.org/problems/delete-without-head-pointer/1)
## Delete without head pointer

## Intuition
The goal is to delete a node from a singly linked list given only access to that node (`del_node`). Deleting a node usually requires access to the previous node as well, but in this case, we only have access to the node to be deleted. 

## Approach

**Special Cases Handling :**
   - First, I checked if the given node to be deleted (`del_node`) is null. If it is null, it implied that the linked list is empty, so there's nothing to delete.
   - Next, I checked if the next node of `del_node` is null. If it is null, it means `del_node` is the last node of the linked list. In this case, I cannot directly delete `del_node`, so I returned without performing any deletion.

**Copy Data and Update Pointers :**
   - If neither of the above special cases holds true, it meant `del_node` is neither null nor the last node of the linked list.
   - To delete `del_node`, I copied the data from its next node to `del_node`. This effectively maked `del_node` contain the data of its next node.
   - Next, I updated the `next` pointer of `del_node` to skip the next node and point directly to the node after the next node. This effectively removed the next node from the linked list.

My approach allows to delete a node from a singly linked list given only access to that node, without needing access to the previous node.

---
Have a look at the code , still have any confusion then please let me know in the comments

Keep Solving.:)

## Complexity
- Time complexity : $O( 1 )$
<!-- Add your time complexity here, e.g. $$O())$$ -->

- Space complexity : $O( 1 )$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

## Code

```
//  User function Template for Java

/*
class Node
{
	int data ;
	Node next;
	Node(int d)
	{
		data = d;
		next = null;
	}
}
*/

//Function to delete a node without any reference to head pointer.
class Solution
{
    void deleteNode(Node del_node)
    {
        // Your code here
        
        // Checking if the linked list is empty
        if(del_node == null)
            return; 
        
        // Checking if del_node is the last node
        if(del_node.next == null)
            return; 

        // Copying data from the next node to del_node
        del_node.data = del_node.next.data;

        // Updating pointers to delete the next node
        del_node.next = del_node.next.next;
    }
}
```
