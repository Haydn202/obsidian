# Linked Lists

## Core Concepts

### Basic Operations
- Access: O(n)
- Search: O(n)
- Insert: O(1) at known position
- Delete: O(1) at known position
- Space: O(n)

### Types of Linked Lists
- Singly Linked List
- Doubly Linked List
- Circular Linked List
- Skip List
- XOR Linked List

### List Properties
- Head pointer
- Tail pointer
- Node structure
- Length tracking
- Cycle detection

## Implementation Details

### Node Structure
```python
class ListNode:
    def __init__(self, val=0):
        self.val = val
        self.next = None

class DoublyListNode:
    def __init__(self, val=0):
        self.val = val
        self.prev = None
        self.next = None
```

### Singly Linked List
```python
class LinkedList:
    def __init__(self):
        self.head = None
        self.size = 0
    
    def insert_at_head(self, val):
        new_node = ListNode(val)
        new_node.next = self.head
        self.head = new_node
        self.size += 1
    
    def insert_at_tail(self, val):
        new_node = ListNode(val)
        if not self.head:
            self.head = new_node
        else:
            curr = self.head
            while curr.next:
                curr = curr.next
            curr.next = new_node
        self.size += 1
    
    def delete_at_head(self):
        if not self.head:
            return
        self.head = self.head.next
        self.size -= 1
    
    def delete_at_tail(self):
        if not self.head:
            return
        if not self.head.next:
            self.head = None
        else:
            curr = self.head
            while curr.next.next:
                curr = curr.next
            curr.next = None
        self.size -= 1
    
    def search(self, val):
        curr = self.head
        while curr:
            if curr.val == val:
                return True
            curr = curr.next
        return False
```

## Common Use Cases

### List Operations
- Traversal
- Insertion
- Deletion
- Reversal
- Merging

### Special Operations
- Cycle detection
- Middle node
- Nth from end
- Intersection
- Partitioning

### Applications
- LRU Cache
- Polynomial addition
- Browser history
- Undo/Redo
- Memory management

## Memory Management

### Node Management
- Dynamic allocation
- Garbage collection
- Memory leaks
- Pointer safety
- Resource cleanup

### List Optimization
- Dummy nodes
- Fast/slow pointers
- Tail pointer
- Size tracking
- Memory efficiency

## Related Notes
- [[../Algorithms/LinkedList_Problems|Linked List Problems]]
- [[Two_Pointers|Two Pointers Technique]]
- [[Cycle_Detection|Cycle Detection]]

## Notes
- Handle edge cases
- Manage pointers
- Consider memory
- Practice implementation
- Understand time/space complexity 

#DSA