# Linked lists


A linked list is a series of connected nodes, where each node stored the data and a pointer to the next node.

Head of linked list: The first node in the list.
Tail of the linked list: Last node in the list which has a pointer to NULL.

### Single linked list
Each node contains a pointer to the next node, and the only way to traverse this list is in a forward direction.

    HEAD
     |
     v
+-------+      +-------+      +-------+
| Data1 |----->| Data2 |----->| Data3 |----->NULL
+-------+      +-------+      +-------+
