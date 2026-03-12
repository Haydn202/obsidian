# Arrays

- [[#Static Arrays]]
- [[#Static array operations]]
- [[#Dynamic Arrays]]
- [[#Dynamic array operations]]
- [[#Example dynamic array implementation]]
- [[#Summary table]]

Arrays are stored in **contiguous memory** in RAM. We can use known indexes (or the offset from the start) to access or update items very efficiently.

---

## Static Arrays

Static arrays have a **fixed size**: you define the length when creating the array and cannot exceed it. Common in C/C++ and when you need predictable memory layout.

---

## Static array operations

| Operation                  | Time   | Space  |
| --------------------------|--------|--------|
| Read / write at index i   | O(1)   | O(1)   |
| Insert / remove at end    | O(1)   | O(1)   |
| Insert / remove in middle | O(n)   | O(1)   |
| Search by value           | O(n)   | O(1)   |
| Traverse all elements     | O(n)   | O(1)   |

### Read at index — O(1) time, O(1) space

```python
my_array = [1, 3, 5]

# Read item at index i
value = my_array[i]   # e.g. my_array[1] → 3
```

### Write at index — O(1) time, O(1) space

```python
my_array = [1, 3, 5]

# Overwrite item at index i
my_array[i] = 6       # e.g. my_array[1] = 6 → [1, 6, 5]
```

### Append (if supported) — O(1) time, O(1) space

```python
a = [2, 3, 4]

# Add 5 at the end
a.append(5)           # → [2, 3, 4, 5]
```

### Insert at position — O(n) time, O(1) space

Each element at or after the insert index must be shifted right, so up to n moves.

```python
a = [2, 3, 4]

# Insert 1 at index 0 (beginning)
a.insert(0, 1)        # → [1, 2, 3, 4]

# Insert 99 at index 2
a.insert(2, 99)      # → [1, 2, 99, 3, 4]
```

### Remove at position — O(n) time, O(1) space

Elements after the removed index must be shifted left to fill the gap.

```python
arr = [1, 2, 3, 4, 5]

# Remove and return element at index 2
val = arr.pop(2)      # val = 3, arr → [1, 2, 4, 5]

# Remove first occurrence of value (also O(n) — search + shift)
arr.remove(4)         # arr → [1, 2, 5]
```

### Search by value — O(n) time, O(1) space

No index to jump to; must scan until the value is found or the end is reached.

```python
arr = [10, 20, 30, 40]

# Find index of value (linear search)
index = arr.index(30)     # → 2

# Check membership
exists = 25 in arr        # → False
```

### Traverse — O(n) time, O(1) space

```python
arr = [1, 2, 3, 4]

# By index
for i in range(len(arr)):
    print(arr[i])

# By value
for x in arr:
    print(x)
```

---

## Dynamic Arrays

You do **not** set a length when creating a dynamic array. A default capacity is used under the hood. When you append and the array is full, the implementation typically:

1. Allocates a new array (often **twice** the current capacity),
2. Copies all elements into it,
3. Deallocates the old array.

That resize is **O(n)**, but **amortized** over many appends, push and pop at the end are still **O(1)** on average. Languages like Python (`list`), Java (`ArrayList`), and C++ (`std::vector`) use this idea.

---

## Dynamic array operations

| Operation                  | Time (avg/amortized) | Space |
| --------------------------|----------------------|--------|
| Read / write at index i   | O(1)                 | O(1)   |
| Insert / remove at end    | O(1) amortized       | O(1)   |
| Insert / remove in middle | O(n)                 | O(1)   |
| Search by value           | O(n)                 | O(1)   |
| Traverse all elements     | O(n)                 | O(1)   |

The same code examples as above apply; in Python, `list` is a dynamic array, so `append`, `insert`, `pop`, and indexing all behave as in the static section, with the complexity notes above (e.g. append O(1) amortized, insert in middle O(n)).

---

## Example: dynamic array implementation

Minimal dynamic array in Python: fixed-capacity backing list, **double on full** so amortized append is O(1).

```python
class DynamicArray:
    def __init__(self, initial_capacity=4):
        self._capacity = initial_capacity
        self._size = 0
        self._data = [None] * self._capacity

    def __len__(self):
        return self._size

    def _resize(self):
        """Double capacity and copy elements. O(n) but amortized O(1) per append."""
        self._capacity *= 2
        new_data = [None] * self._capacity
        for i in range(self._size):
            new_data[i] = self._data[i]
        self._data = new_data

    def append(self, value):
        """Amortized O(1)."""
        if self._size == self._capacity:
            self._resize()
        self._data[self._size] = value
        self._size += 1

    def get(self, index):
        """O(1)."""
        if not 0 <= index < self._size:
            raise IndexError("index out of range")
        return self._data[index]

    def set(self, index, value):
        """O(1)."""
        if not 0 <= index < self._size:
            raise IndexError("index out of range")
        self._data[index] = value

    def pop_end(self):
        """O(1)."""
        if self._size == 0:
            raise IndexError("pop from empty array")
        self._size -= 1
        return self._data[self._size]

    def __str__(self):
        return "[" + ", ".join(str(self._data[i]) for i in range(self._size)) + "]"


# Usage
arr = DynamicArray()
arr.append(10)
arr.append(20)
arr.append(30)
arr.append(40)   # fills capacity 4
arr.append(50)   # triggers resize to 8, then append
print(len(arr))  # 5
print(arr.get(2))  # 30
arr.set(2, 99)
print(arr)       # [10, 20, 99, 40, 50]
print(arr.pop_end())  # 50
print(arr)       # [10, 20, 99, 40]
```

**Why doubling?** If we grow by a fixed amount each time, n appends can cause O(n) copies on resize, so total cost is O(n²). Doubling (or any constant factor > 1) gives O(n) total copies over n appends, so **amortized O(1)** per append.

---

## Summary table

| Operation           | Static/Dynamic | Time        | Space |
| -------------------|----------------|------------|--------|
| Access by index     | Both           | O(1)       | O(1)   |
| Update by index     | Both           | O(1)       | O(1)   |
| Append (end)        | Both*          | O(1)†      | O(1)   |
| Insert (middle)     | Both           | O(n)       | O(1)   |
| Remove (middle)     | Both           | O(n)       | O(1)   |
| Search by value     | Both           | O(n)       | O(1)   |
| Traverse            | Both           | O(n)       | O(1)   |

\* Static arrays may not support growth; “append” then means “write next slot” if space exists.  
† O(1) amortized for dynamic arrays when using doubling growth.
