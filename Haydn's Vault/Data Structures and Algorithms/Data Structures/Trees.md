# Trees

## Core Concepts

### Basic Operations
- Access: O(log n) for balanced
- Search: O(log n) for balanced
- Insert: O(log n) for balanced
- Delete: O(log n) for balanced
- Space: O(n)

### Types of Trees
- Binary Tree
- Binary Search Tree
- AVL Tree
- Red-Black Tree
- B-Tree
- Trie
- Heap

### Tree Properties
- Height
- Depth
- Balance
- Diameter
- Path length

## Implementation Details

### Binary Tree Node
```python
class TreeNode:
    def __init__(self, val=0):
        self.val = val
        self.left = None
        self.right = None
```

### Binary Search Tree
```python
class BST:
    def __init__(self):
        self.root = None
    
    def insert(self, val):
        if not self.root:
            self.root = TreeNode(val)
            return
        
        def _insert(node, val):
            if val < node.val:
                if not node.left:
                    node.left = TreeNode(val)
                else:
                    _insert(node.left, val)
            else:
                if not node.right:
                    node.right = TreeNode(val)
                else:
                    _insert(node.right, val)
        
        _insert(self.root, val)
    
    def search(self, val):
        def _search(node, val):
            if not node:
                return False
            if node.val == val:
                return True
            if val < node.val:
                return _search(node.left, val)
            return _search(node.right, val)
        
        return _search(self.root, val)
    
    def delete(self, val):
        def _delete(node, val):
            if not node:
                return None
            
            if val < node.val:
                node.left = _delete(node.left, val)
            elif val > node.val:
                node.right = _delete(node.right, val)
            else:
                if not node.left:
                    return node.right
                if not node.right:
                    return node.left
                
                temp = self._find_min(node.right)
                node.val = temp.val
                node.right = _delete(node.right, temp.val)
            
            return node
        
        self.root = _delete(self.root, val)
    
    def _find_min(self, node):
        while node.left:
            node = node.left
        return node
```

## Common Use Cases

### Binary Search Tree
- Ordered data storage
- Range queries
- Successor/predecessor
- Balanced operations
- Sorting

### Tree Traversal
- Pre-order (Root, Left, Right)
- In-order (Left, Root, Right)
- Post-order (Left, Right, Root)
- Level-order (BFS)
- Morris Traversal

### Tree Operations
- Height calculation
- Balance checking
- Path finding
- Subtree operations
- Tree construction

## Memory Management

### Node Structure
- Value storage
- Child pointers
- Parent pointer
- Additional metadata
- Memory efficiency

### Tree Balancing
- AVL rotations
- Red-Black rules
- B-tree splitting
- Rebalancing
- Performance impact

## Related Notes
- [[../Algorithms/Tree_Problems|Tree Problems]]
- [[Tree_Traversal|Tree Traversal Techniques]]
- [[Balanced_Trees|Balanced Tree Types]]

## Notes
- Consider tree type
- Handle balancing
- Optimize operations
- Practice implementation
- Understand time/space complexity 

#DSA