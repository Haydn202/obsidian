# Stacks and Queues

## Core Concepts

### Stack Operations
- Push: O(1)
- Pop: O(1)
- Peek/Top: O(1)
- IsEmpty: O(1)
- Space: O(n)

### Queue Operations
- Enqueue: O(1)
- Dequeue: O(1)
- Front: O(1)
- IsEmpty: O(1)
- Space: O(n)

### Deque Operations
- AddFirst: O(1)
- AddLast: O(1)
- RemoveFirst: O(1)
- RemoveLast: O(1)
- Space: O(n)

## Implementation Details

### Stack Implementation
```python
class Stack:
    def __init__(self):
        self.items = []
    
    def push(self, item):
        self.items.append(item)
    
    def pop(self):
        if not self.is_empty():
            return self.items.pop()
        return None
    
    def peek(self):
        if not self.is_empty():
            return self.items[-1]
        return None
    
    def is_empty(self):
        return len(self.items) == 0
    
    def size(self):
        return len(self.items)
```

### Queue Implementation
```python
from collections import deque

class Queue:
    def __init__(self):
        self.items = deque()
    
    def enqueue(self, item):
        self.items.append(item)
    
    def dequeue(self):
        if not self.is_empty():
            return self.items.popleft()
        return None
    
    def front(self):
        if not self.is_empty():
            return self.items[0]
        return None
    
    def is_empty(self):
        return len(self.items) == 0
    
    def size(self):
        return len(self.items)
```

## Common Use Cases

### Stack Applications
- Function call stack
- Expression evaluation
- Parentheses matching
- Backtracking
- DFS implementation

### Queue Applications
- Task scheduling
- BFS implementation
- Print queue
- Message queue
- Level order traversal

### Deque Applications
- Sliding window
- Double-ended operations
- Cache implementation
- Work stealing
- Task management

## Memory Management

### Stack Memory
- LIFO order
- Fixed size
- Fast allocation
- Automatic cleanup
- Stack overflow

### Queue Memory
- FIFO order
- Dynamic size
- Circular buffer
- Memory efficiency
- Overflow handling

## Related Notes
- [[../Algorithms/StackQueue_Problems|Stack and Queue Problems]]
- [[Monotonic_Stack|Monotonic Stack Technique]]
- [[Expression_Evaluation|Expression Evaluation]]

## Notes
- Consider size limitations
- Handle overflow/underflow
- Choose appropriate type
- Understand memory usage
- Practice implementation 

#DSA