# Tries

## Core Concepts

### Basic Operations
- Insert: O(m) where m is word length
- Search: O(m) where m is word length
- Delete: O(m) where m is word length
- Prefix Search: O(m) where m is prefix length
- Space: O(ALPHABET_SIZE * N * M) where N is number of words, M is average length

### Trie Properties
- Prefix tree
- Character-based nodes
- Path represents word
- Common prefix sharing
- End of word marking

### Node Structure
- Children pointers
- End of word flag
- Value storage
- Frequency count
- Additional metadata

## Implementation Details

### Basic Trie Implementation
```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end = False
        self.frequency = 0

class Trie:
    def __init__(self):
        self.root = TrieNode()
    
    def insert(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end = True
        node.frequency += 1
    
    def search(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                return False
            node = node.children[char]
        return node.is_end
    
    def startsWith(self, prefix):
        node = self.root
        for char in prefix:
            if char not in node.children:
                return False
            node = node.children[char]
        return True
    
    def delete(self, word):
        def _delete_helper(node, word, index):
            if index == len(word):
                if not node.is_end:
                    return False
                node.is_end = False
                return len(node.children) == 0
            
            char = word[index]
            if char not in node.children:
                return False
            
            should_delete = _delete_helper(node.children[char], word, index + 1)
            if should_delete:
                del node.children[char]
                return len(node.children) == 0
            return False
        
        _delete_helper(self.root, word, 0)
```

## Common Use Cases

### String Operations
- Dictionary implementation
- Spell checking
- Autocomplete
- Word search
- Pattern matching

### Text Processing
- Word frequency
- Text compression
- String matching
- Prefix operations
- Suffix operations

### Word Games
- Word squares
- Boggle
- Crossword
- Word ladder
- Anagrams

## Memory Management

### Node Optimization
- Character compression
- Path compression
- Memory pooling
- Node sharing
- Space efficiency

### Dynamic Operations
- Insertion strategy
- Deletion strategy
- Balancing
- Cleanup
- Memory reclamation

## Related Notes
- [[../Algorithms/Trie_Problems|Trie Problems]]
- [[String_Algorithms|String Algorithms]]
- [[Word_Games|Word Games]]

## Notes
- Consider memory usage
- Handle edge cases
- Optimize node structure
- Practice implementation
- Understand time/space complexity 

#DSA