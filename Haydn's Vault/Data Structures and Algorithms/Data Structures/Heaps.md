# Heaps

## Core Concepts

### Basic Operations
- Insert: O(log n)
- Extract Max/Min: O(log n)
- Peek: O(1)
- Heapify: O(n)
- Space: O(n)

### Types of Heaps
- Binary Heap
- Min Heap
- Max Heap
- Fibonacci Heap
- Binomial Heap

### Heap Properties
- Complete binary tree
- Heap property
- Parent-child relationship
- Level ordering
- Array representation

## Implementation Details

### Binary Heap Implementation
```python
class BinaryHeap:
    def __init__(self, heap_type='min'):
        self.heap = []
        self.heap_type = heap_type
    
    def parent(self, i):
        return (i - 1) // 2
    
    def left_child(self, i):
        return 2 * i + 1
    
    def right_child(self, i):
        return 2 * i + 2
    
    def swap(self, i, j):
        self.heap[i], self.heap[j] = self.heap[j], self.heap[i]
    
    def insert(self, key):
        self.heap.append(key)
        self._sift_up(len(self.heap) - 1)
    
    def extract(self):
        if not self.heap:
            return None
        
        if len(self.heap) == 1:
            return self.heap.pop()
        
        root = self.heap[0]
        self.heap[0] = self.heap.pop()
        self._sift_down(0)
        
        return root
    
    def _sift_up(self, i):
        parent = self.parent(i)
        if i > 0 and self._compare(self.heap[i], self.heap[parent]):
            self.swap(i, parent)
            self._sift_up(parent)
    
    def _sift_down(self, i):
        min_index = i
        left = self.left_child(i)
        right = self.right_child(i)
        
        if left < len(self.heap) and self._compare(self.heap[left], self.heap[min_index]):
            min_index = left
        
        if right < len(self.heap) and self._compare(self.heap[right], self.heap[min_index]):
            min_index = right
        
        if i != min_index:
            self.swap(i, min_index)
            self._sift_down(min_index)
    
    def _compare(self, a, b):
        return a < b if self.heap_type == 'min' else a > b
```

## Common Use Cases

### Priority Queue
- Task scheduling
- Event handling
- Graph algorithms
- Simulation
- Real-time systems

### Sorting
- Heap sort
- Partial sorting
- K-sorted arrays
- External sorting
- In-place sorting

### Selection
- Kth largest/smallest
- Running median
- Top K elements
- Percentile calculation
- Order statistics

## Memory Management

### Array Representation
- Parent: (i-1)/2
- Left child: 2i+1
- Right child: 2i+2
- Level ordering
- Space efficiency

### Dynamic Resizing
- Growth strategy
- Shrink strategy
- Amortized cost
- Memory efficiency
- Performance impact

## Related Notes
- [[../Algorithms/Heap_Problems|Heap Problems]]
- [[Priority_Queue|Priority Queue Implementation]]
- [[Heap_Sort|Heap Sort Algorithm]]

## Notes
- Maintain heap property
- Handle edge cases
- Consider space complexity
- Optimize operations
- Practice implementation 

#DSA