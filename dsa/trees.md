# Trees


## Binary Tree
A type of tree where each node can have a maximum of two child nodes, a left and a right child node.

#### Breadth First Search(BFS)
All nodes on the same level are visited before going to the next level on the tree.

#### Depth First Search(DFS)
Tree traversal goes all the way down the tree leafs.

#### Implementation
```python
Class TreeNode:
	def __init__(self, data):
		self.data = data
		self.left = None
		self.right = None

root = TreeNode('R')
nodeA = TreeNode('A')
nodeB = TreeNode('B')

root.left = nodeA
root.right = nodeB
```

## Binary Search Tree
Is a binary tree where the left child is less than the right child.
