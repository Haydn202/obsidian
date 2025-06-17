# Hash Table Problems

## Common Techniques

### Frequency Counting
- Character counts
- Word frequencies
- Element occurrences
- Pattern matching
- Anagrams

### Two Sum Variations
- Pair finding
- Complement tracking
- Range queries
- Subarray sums
- Target matching

### Caching
- LRU Cache
- LFU Cache
- Memoization
- Result caching
- State tracking

## Practice Problems

### Easy
- [ ] Two Sum
- [ ] Valid Anagram
- [ ] First Unique Character
- [ ] Contains Duplicate
- [ ] Intersection of Two Arrays

### Medium
- [ ] Group Anagrams
- [ ] Longest Substring Without Repeating Characters
- [ ] Top K Frequent Elements
- [ ] LRU Cache
- [ ] Design HashMap

### Hard
- [ ] Minimum Window Substring
- [ ] Substring with Concatenation of All Words
- [ ] Word Ladder II
- [ ] All O(1) Data Structure
- [ ] LFU Cache

## Implementation Examples

### Custom HashMap
```python
class MyHashMap:
    def __init__(self):
        self.size = 1000
        self.buckets = [[] for _ in range(self.size)]
    
    def put(self, key: int, value: int) -> None:
        bucket = self.buckets[key % self.size]
        for i, (k, v) in enumerate(bucket):
            if k == key:
                bucket[i] = (key, value)
                return
        bucket.append((key, value))
    
    def get(self, key: int) -> int:
        bucket = self.buckets[key % self.size]
        for k, v in bucket:
            if k == key:
                return v
        return -1
    
    def remove(self, key: int) -> None:
        bucket = self.buckets[key % self.size]
        for i, (k, v) in enumerate(bucket):
            if k == key:
                bucket.pop(i)
                return
```

### LRU Cache
```python
from collections import OrderedDict

class LRUCache:
    def __init__(self, capacity: int):
        self.capacity = capacity
        self.cache = OrderedDict()
    
    def get(self, key: int) -> int:
        if key not in self.cache:
            return -1
        self.cache.move_to_end(key)
        return self.cache[key]
    
    def put(self, key: int, value: int) -> None:
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.capacity:
            self.cache.popitem(last=False)
```

## Problem-Solving Strategies

### Pattern Recognition
- Identify hash patterns
- Map to known solutions
- Break down complex problems
- Look for invariants
- Consider edge cases

### Optimization Techniques
- Space-time tradeoffs
- Collision handling
- Load factor management
- Memory efficiency
- Algorithm selection

## Progress Tracking

### Basic Techniques
- [ ] Frequency counting
- [ ] Two sum variations
- [ ] Anagram detection
- [ ] Substring problems
- [ ] Cache implementations

### Advanced Techniques
- [ ] Custom hash functions
- [ ] Dynamic resizing
- [ ] Collision resolution
- [ ] Load balancing
- [ ] Distributed hashing

## Related Notes
- [[../Data Structures/HashTables|Hash Tables Data Structure]]
- [[Caching_Techniques|Caching Techniques]]
- [[String_Algorithms|String Algorithms]]

## Notes
- Consider collision handling
- Monitor load factor
- Choose appropriate hash function
- Handle edge cases
- Optimize for specific use cases 

#DSA