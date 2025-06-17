# Hash Tables

## Core Concepts

### Basic Operations
- Insert: O(1) average, O(n) worst
- Search: O(1) average, O(n) worst
- Delete: O(1) average, O(n) worst
- Space: O(n)

### Hash Functions
- Deterministic
- Uniform distribution
- Fast computation
- Collision handling
- Load factor management

### Collision Resolution
- Separate Chaining
- Open Addressing
  - Linear Probing
  - Quadratic Probing
  - Double Hashing
- Robin Hood Hashing

## Implementation Details

### Hash Table Implementation
```python
class HashTable:
    def __init__(self, size=1000):
        self.size = size
        self.table = [[] for _ in range(size)]
        self.count = 0
        self.load_factor = 0.75
    
    def _hash(self, key):
        return hash(key) % self.size
    
    def insert(self, key, value):
        if self.count / self.size >= self.load_factor:
            self._resize()
        
        index = self._hash(key)
        for i, (k, v) in enumerate(self.table[index]):
            if k == key:
                self.table[index][i] = (key, value)
                return
        
        self.table[index].append((key, value))
        self.count += 1
    
    def get(self, key):
        index = self._hash(key)
        for k, v in self.table[index]:
            if k == key:
                return v
        return None
    
    def delete(self, key):
        index = self._hash(key)
        for i, (k, v) in enumerate(self.table[index]):
            if k == key:
                self.table[index].pop(i)
                self.count -= 1
                return
    
    def _resize(self):
        old_table = self.table
        self.size *= 2
        self.table = [[] for _ in range(self.size)]
        self.count = 0
        
        for bucket in old_table:
            for key, value in bucket:
                self.insert(key, value)
```

## Common Use Cases

### Dictionary Operations
- Key-value storage
- Fast lookups
- Frequency counting
- Duplicate detection
- Set operations

### Caching
- LRU Cache
- LFU Cache
- Memoization
- Result caching
- State tracking

### Applications
- Database indexing
- Symbol tables
- Spell checking
- Network routing
- Distributed systems

## Memory Management

### Collision Handling
- Separate chaining
- Open addressing
- Load factor
- Rehashing
- Memory efficiency

### Optimization
- Hash function design
- Table size
- Load factor
- Resizing strategy
- Memory usage

## Related Notes
- [[../Algorithms/HashTable_Problems|Hash Table Problems]]
- [[Caching_Techniques|Caching Techniques]]
- [[Hash_Functions|Hash Function Design]]

## Notes
- Choose hash function
- Handle collisions
- Monitor load factor
- Consider resizing
- Understand tradeoffs 

#DSA