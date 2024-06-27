# Hash Tables


In a hash table, each data value has its own unique index value. The index value is calculated using a hash function.

### Hash Collitions
To avoid hash collisions, a linked list is appended to each index in the table. This way, each value can be stored in the same index using as a linked list node.

### Time Complexity
Lookup, Insertion, and Deletion: O(1) on average
