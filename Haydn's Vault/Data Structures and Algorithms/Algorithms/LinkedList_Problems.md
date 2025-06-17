# Linked List Problems

## Common Techniques

### Two Pointers
- Fast and slow pointers
- Finding middle node
- Cycle detection
- Finding intersection
- Nth node from end

### Pointer Manipulation
- Reversing lists
- Merging sorted lists
- Partitioning lists
- Reordering nodes
- Swapping nodes

### Dummy Nodes
- Handling edge cases
- Simplifying operations
- Avoiding null checks
- Clean code structure
- Head node management

## Practice Problems

### Easy
- [ ] Reverse Linked List
- [ ] Merge Two Sorted Lists
- [ ] Linked List Cycle
- [ ] Remove Duplicates
- [ ] Middle of Linked List

### Medium
- [ ] Add Two Numbers
- [ ] Remove Nth Node From End
- [ ] Swap Nodes in Pairs
- [ ] Rotate List
- [ ] Partition List

### Hard
- [ ] Merge K Sorted Lists
- [ ] Reverse Nodes in K-Group
- [ ] LRU Cache
- [ ] Copy List with Random Pointer
- [ ] Sort List

## Implementation Examples

### Reverse Linked List
```python
def reverseList(head):
    prev = None
    curr = head
    
    while curr:
        next_temp = curr.next
        curr.next = prev
        prev = curr
        curr = next_temp
    
    return prev
```

### Detect Cycle
```python
def hasCycle(head):
    if not head or not head.next:
        return False
        
    slow = head
    fast = head.next
    
    while slow != fast:
        if not fast or not fast.next:
            return False
        slow = slow.next
        fast = fast.next.next
    
    return True
```

## Problem-Solving Strategies

### Pattern Recognition
- Identify pointer patterns
- Map to known solutions
- Break down complex operations
- Look for invariants
- Consider edge cases

### Optimization Techniques
- Space-time tradeoffs
- In-place operations
- Memory efficiency
- Algorithm selection
- Pointer manipulation

## Progress Tracking

### Basic Techniques
- [ ] Two pointer technique
- [ ] Pointer manipulation
- [ ] Dummy node usage
- [ ] Cycle detection
- [ ] List reversal

### Advanced Techniques
- [ ] Merge operations
- [ ] Partition operations
- [ ] Random pointer handling
- [ ] K-group operations
- [ ] LRU cache implementation

## Related Notes
- [[../Data Structures/LinkedLists|Linked Lists Data Structure]]
- [[Two_Pointers|Two Pointers Technique]]
- [[Dummy_Nodes|Dummy Nodes Technique]]

## Notes
- Draw diagrams for complex operations
- Handle edge cases carefully
- Use dummy nodes when needed
- Practice pointer manipulation
- Understand memory management 

#DSA