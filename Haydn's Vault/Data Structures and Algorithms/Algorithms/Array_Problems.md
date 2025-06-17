# Array Problems

## Common Techniques

### Two Pointers
- Opposite ends
- Same direction
- Fast and slow
- Window sliding

### Prefix Sums
- Cumulative sum
- Range queries
- Subarray problems
- Difference array

### Kadane's Algorithm
- Maximum subarray
- Dynamic programming
- Local and global max
- Negative numbers

## Practice Problems

### Easy
- [ ] Two Sum
- [ ] Valid Palindrome
- [ ] Reverse String
- [ ] Remove Duplicates
- [ ] Merge Sorted Arrays

### Medium
- [ ] 3Sum
- [ ] Longest Substring Without Repeating Characters
- [ ] Container With Most Water
- [ ] Rotate Array
- [ ] Product of Array Except Self

### Hard
- [ ] Trapping Rain Water
- [ ] Sliding Window Maximum
- [ ] Longest Consecutive Sequence
- [ ] Minimum Window Substring
- [ ] Median of Two Sorted Arrays

## Implementation Examples

### Two Sum
```python
def twoSum(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
        seen[num] = i
    return []
```

### Kadane's Algorithm
```python
def maxSubArray(nums):
    max_so_far = float('-inf')
    max_ending_here = 0
    
    for num in nums:
        max_ending_here = max(num, max_ending_here + num)
        max_so_far = max(max_so_far, max_ending_here)
    
    return max_so_far
```

## Problem-Solving Strategies

### Pattern Recognition
- Identify common patterns
- Map to known solutions
- Break down complex problems
- Look for invariants
- Consider edge cases

### Optimization Techniques
- Space-time tradeoffs
- In-place operations
- Cache utilization
- Memory efficiency
- Algorithm selection

## Progress Tracking

### Basic Techniques
- [ ] Two pointer technique
- [ ] Sliding window
- [ ] Prefix sums
- [ ] In-place operations
- [ ] Pattern matching

### Advanced Techniques
- [ ] Kadane's algorithm
- [ ] Dutch national flag
- [ ] Cyclic sort
- [ ] Dynamic programming
- [ ] Greedy approaches

## Related Notes
- [[../Data Structures/Arrays|Arrays Data Structure]]
- [[Two_Pointers|Two Pointers Technique]]
- [[Sliding_Window|Sliding Window Technique]]

## Notes
- Practice pattern recognition
- Master common techniques
- Understand time/space complexity
- Focus on edge cases
- Review solutions thoroughly 

#DSA