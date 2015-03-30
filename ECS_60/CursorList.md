## Cursor List FAQ ##

### What is a cursor list, anyway? ###
You can think of a cursor list as an array version of a linked list. A cursor list's memory is preallocated in an array, while a linked list grows and shrinks dynamically. If the programming language you are using does not support pointers, you can use a cursor list as a way to implement a linked list.

### But if there are no pointers, how can we keep all the nodes together? ###
Basically, your "pointers" are integers that store the values of the array indices of the list nodes that are next in the list. For example, the head "pointer" is an integer variable containing the index of the first node of the list. To indicate the end of the list, we can use a sentinal value for the next "pointer" of the last node in the list.

### What is the free list? ###
The free list contains a bunch of list nodes (unoccupied array indices) that the cursor list can use whenever a new piece of data needs to be inserted. When you delete a node from the cursor list, the node becomes part of the free list. The free list is pretty much a heap for the cursor list, just like your program has a heap for dynamic memory allocation. It is also a linked list, just of unallocated list nodes.

### And the question everyone wants to know the answer to: why is the cursor list slower than the linked list? ###

You thought I was going to give you the answer here, didn't you? I'll give a hint: it's in the code.