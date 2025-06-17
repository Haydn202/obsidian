# Tree Problems

## Common Techniques

### Tree Traversal
- Pre-order (Root, Left, Right)
- In-order (Left, Root, Right)
- Post-order (Left, Right, Root)
- Level-order (BFS)
- Morris Traversal

### Graph Traversal
- Depth-First Search (DFS)
- Breadth-First Search (BFS)
- Topological Sort
- Union-Find
- Dijkstra's Algorithm

### Tree Properties
- Height calculation
- Depth tracking
- Balance checking
- Diameter finding
- Path sum problems

## Practice Problems

### Easy
- [ ] Maximum Depth of Binary Tree
- [ ] Validate Binary Search Tree
- [ ] Symmetric Tree
- [ ] Path Sum
- [ ] Invert Binary Tree

### Medium
- [ ] Binary Tree Level Order Traversal
- [ ] Construct Binary Tree from Preorder and Inorder
- [ ] Lowest Common Ancestor
- [ ] Number of Islands
- [ ] Course Schedule

### Hard
- [ ] Binary Tree Maximum Path Sum
- [ ] Word Ladder
- [ ] Alien Dictionary
- [ ] Reconstruct Itinerary
- [ ] Redundant Connection

## Implementation Examples

### Binary Tree Traversal
```python
def inorderTraversal(root):
    result = []
    stack = []
    curr = root
    
    while curr or stack:
        while curr:
            stack.append(curr)
            curr = curr.left
        
        curr = stack.pop()
        result.append(curr.val)
        curr = curr.right
    
    return result
```

### Graph DFS
```python
def dfs(graph, start):
    visited = set()
    stack = [start]
    
    while stack:
        vertex = stack.pop()
        if vertex not in visited:
            visited.add(vertex)
            stack.extend(graph[vertex] - visited)
    
    return visited
```

## Problem-Solving Strategies

### Pattern Recognition
- Identify traversal patterns
- Map to known solutions
- Break down complex problems
- Look for invariants
- Consider edge cases

### Optimization Techniques
- Space-time tradeoffs
- Iterative vs recursive
- Memory efficiency
- Algorithm selection
- Data structure choice

## Progress Tracking

### Basic Techniques
- [ ] Tree traversal methods
- [ ] Graph traversal methods
- [ ] Tree property calculations
- [ ] Path finding
- [ ] Tree construction

### Advanced Techniques
- [ ] Morris traversal
- [ ] Topological sorting
- [ ] Union-Find
- [ ] Shortest path algorithms
- [ ] Cycle detection

## Related Notes
- [[../Data Structures/Trees|Trees Data Structure]]
- [[Tree_Traversal|Tree Traversal Techniques]]
- [[Graph_Algorithms|Graph Algorithms]]

## Notes
- Draw trees for visualization
- Handle edge cases (null, cycles)
- Consider space complexity
- Use appropriate data structures
- Practice recursive solutions 

#DSA