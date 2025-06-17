# Stack and Queue Problems

## Common Techniques

### Stack Operations
- LIFO (Last In, First Out)
- Parentheses matching
- Expression evaluation
- Backtracking
- DFS simulation

### Queue Operations
- FIFO (First In, First Out)
- Level order traversal
- BFS simulation
- Sliding window
- Task scheduling

### Monotonic Stacks
- Next greater element
- Previous smaller element
- Stock span problem
- Histogram problems
- Temperature problems

## Practice Problems

### Easy
- [ ] Valid Parentheses
- [ ] Implement Queue using Stacks
- [ ] Implement Stack using Queues
- [ ] Min Stack
- [ ] Moving Average from Data Stream

### Medium
- [ ] Evaluate Reverse Polish Notation
- [ ] Basic Calculator
- [ ] Daily Temperatures
- [ ] Next Greater Element
- [ ] Asteroid Collision

### Hard
- [ ] Largest Rectangle in Histogram
- [ ] Basic Calculator III
- [ ] Sliding Window Maximum
- [ ] Design Circular Queue
- [ ] Design Circular Deque

## Implementation Examples

### Min Stack
```python
class MinStack:
    def __init__(self):
        self.stack = []
        self.min_stack = []
    
    def push(self, val: int) -> None:
        self.stack.append(val)
        if not self.min_stack or val <= self.min_stack[-1]:
            self.min_stack.append(val)
    
    def pop(self) -> None:
        if self.stack[-1] == self.min_stack[-1]:
            self.min_stack.pop()
        self.stack.pop()
    
    def top(self) -> int:
        return self.stack[-1]
    
    def getMin(self) -> int:
        return self.min_stack[-1]
```

### Monotonic Stack
```python
def nextGreaterElement(nums):
    result = [-1] * len(nums)
    stack = []
    
    for i in range(len(nums)):
        while stack and nums[stack[-1]] < nums[i]:
            result[stack.pop()] = nums[i]
        stack.append(i)
    
    return result
```

## Problem-Solving Strategies

### Pattern Recognition
- Identify LIFO/FIFO patterns
- Map to known solutions
- Break down complex problems
- Look for invariants
- Consider edge cases

### Optimization Techniques
- Space-time tradeoffs
- In-place operations
- Memory efficiency
- Algorithm selection
- Data structure choice

## Progress Tracking

### Basic Techniques
- [ ] Stack operations
- [ ] Queue operations
- [ ] Parentheses matching
- [ ] Expression evaluation
- [ ] Level order traversal

### Advanced Techniques
- [ ] Monotonic stacks
- [ ] Circular queues
- [ ] Deque operations
- [ ] Sliding window
- [ ] Calculator implementation

## Related Notes
- [[../Data Structures/Stacks_Queues|Stacks and Queues Data Structure]]
- [[Monotonic_Stack|Monotonic Stack Technique]]
- [[Expression_Evaluation|Expression Evaluation]]

## Notes
- Consider stack/queue limitations
- Handle edge cases (empty, full)
- Use appropriate data structure
- Practice implementation
- Understand time/space complexity 

#DSA