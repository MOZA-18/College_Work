# C++ Competitive Programming Cheat Sheet

A comprehensive collection of algorithms, data structures, and theory for competitive programming.

---

## Table of Contents

- [Template & Macros](#template--macros)
- [Data Structures Implementation](#data-structures-implementation)
  - [Linear Structures](#linear-structures)
  - [Stacks & Queues](#stacks--queues)
  - [Non-Linear Structures](#non-linear-structures)
- [Mathematics & Number Theory](#mathematics--number-theory)
  - [Prime Checking](#prime-checking)
  - [Base Conversion](#base-conversion)
  - [General Formulas](#general-formulas)
- [Standard Template Library (STL)](#standard-template-library-stl)
  - [Vectors](#vectors)
  - [Deque](#deque)
  - [Pairs](#pairs)
  - [Sets](#sets)
  - [Ordered vs Unordered Containers](#ordered-vs-unordered-containers)
- [Algorithms](#algorithms)
  - [Sorting Implementation](#sorting-implementation)
  - [Searching](#searching)
  - [Sorting Theory & Complexity](#sorting-theory--complexity)
- [Logic Gates](#logic-gates)

---

## Template & Macros

Standard starter template for faster I/O and common definitions.

```cpp
#include <bits/stdc++.h>
using namespace std;

#define ll long long
#define nl "\n"
#define vi vector<int>
#define sp " "
#define all(x) (x).begin(), (x).end()
const double EPS = 1e-9;

void MOZA()
{
    ios::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);
#ifndef ONLINE_JUDGE
    freopen("input.txt", "r", stdin);
    freopen("output.txt", "w", stdout);
#endif
}

void solve()
{
    // Write your solution here
}

int main() {
    MOZA();
    solve();
    return 0;
}
```

---

## Data Structures Implementation

This section covers the custom data structures I've implemented from scratch in the [College_Work repository](https://github.com/Moza202/College_Work). Each implementation includes detailed operations and practical applications.

### Linear Structures

#### Singly Linked List

**File**: [Linked_list1.cpp](https://github.com/Moza202/College_Work/blob/main/Linked_list1.cpp)

A dynamic linear data structure where each node contains data and a pointer to the next node.

**Key Features**:
- Insert at head, tail, or position
- Delete by value or position
- Advanced operations: Reverse, Copy, Find Min/Max
- Display and traversal
- Time Complexity: O(n) for most operations

**Use Cases**: Dynamic memory allocation, implementing other data structures

#### Doubly Linked List

**File**: [Doublylinkedlist.cpp](https://github.com/Moza202/College_Work/blob/main/Doublylinkedlist.cpp)

Each node contains data and two pointers (next and previous), enabling bidirectional traversal.

**Key Features**:
- Bidirectional traversal
- Easier deletion (no need to track previous node)
- Insert and delete from both ends
- Time Complexity: O(n) for search, O(1) for insert/delete at known position

**Use Cases**: Browser history, undo/redo functionality, music playlists

#### Circular Linked List

**File**: [CLL.cpp](https://github.com/Moza202/College_Work/blob/main/CLL.cpp)

The last node points back to the head, forming a circle.

**Key Features**:
- No NULL pointers (tail points to head)
- Continuous traversal possible
- Useful for round-robin scheduling
- Time Complexity: Similar to singly linked list

**Use Cases**: Round-robin scheduling, multiplayer games, circular buffers

### Stacks & Queues

#### Stack (Array-Based)

**File**: [Stack_using_array.cpp](https://github.com/Moza202/College_Work/blob/main/Stack_using_array.cpp)

LIFO (Last In First Out) structure with fixed size.

**Key Operations**:
- `push()`: Add element to top
- `pop()`: Remove element from top
- `peek()`: View top element
- `isEmpty()` / `isFull()`: Check status

**Applications**:
- Expression evaluation (Infix to Postfix conversion)
- Palindrome checking
- Backtracking algorithms
- Function call stack

**Time Complexity**: O(1) for all operations

#### Stack (Dynamic - Linked List)

**File**: [Stack_using_linkedlist.cpp](https://github.com/Moza202/College_Work/blob/main/Stack_using_linkedlist.cpp)

LIFO structure with flexible memory usage.

**Advantages over Array-Based**:
- No size limit (dynamic growth)
- No wasted memory
- Better for unpredictable sizes

**Time Complexity**: O(1) for push/pop

#### Circular Queue

**File**: [Queue.cpp](https://github.com/Moza202/College_Work/blob/main/Queue.cpp)

FIFO (First In First Out) structure using circular array implementation.

**Key Operations**:
- `enqueue()`: Add element to rear
- `dequeue()`: Remove element from front
- Bulk operations support
- Efficient space utilization (circular wrapping)

**Applications**:
- CPU scheduling
- Printer queue management
- BFS traversal in graphs

**Time Complexity**: O(1) for enqueue/dequeue

### Non-Linear Structures

#### Binary Search Tree (BST)

**File**: [Tree.cpp](https://github.com/Moza202/College_Work/blob/main/Tree.cpp)

Hierarchical data structure where each node has at most two children, with left child < parent < right child.

**Key Operations**:
- `insert()`: Add new node maintaining BST property
- `search()`: Find element in O(log n) average case
- `delete()`: Remove node with three cases (leaf, one child, two children)
- `inorder()`, `preorder()`, `postorder()`: Different traversal methods
- `size()`: Count total nodes
- `depth()`: Find tree height

**BST Properties**:
- Inorder traversal gives sorted sequence
- Search, insert, delete: O(log n) average, O(n) worst case
- Self-balancing variants (AVL, Red-Black) guarantee O(log n)

**Applications**:
- Database indexing
- File system organization
- Expression parsing
- Auto-complete features

---

## Mathematics & Number Theory

### Prime Checking

Checks if a number is prime in O(√N) time.

```cpp
bool is_prime(int x)
{
    if (x < 2) return false;
    for (int i = 2; i * i <= x; ++i)
    {
        if (x % i == 0) return false;
    }
    return true;
}
```

### Base Conversion

#### Decimal to Base (Returns String)

```cpp
string decimal_to_base(int n, int base)
{
    string num = "";
    while (n)
    {
        int rem = n % base;
        num += char((rem < 10 ? rem + '0' : (rem - 10 + 'A')));
        n /= base;
    }
    reverse(num.begin(), num.end());
    return num;
}
```

#### Base to Decimal (Returns Integer)

```cpp
int base_to_decimal(string num, int base)
{
    int n = 0;
    for (int i = 0; i < num.size(); i++)
    {
        n *= base;
        n += (isdigit(num[i]) ? num[i] - '0' : num[i] - 'A' + 10);
    }
    return n;
}
```

### General Formulas

- **Odd numbers count**: `(n + 1) / 2` (Count of odd numbers from 1 to n)
- **Odd Number Expression**: `2k - 1` or `2k + 1`
- **Even Number Expression**: `2k`

---

## Standard Template Library (STL)

### Vectors

Dynamic arrays that handle memory automatically.

**Common Operations:**

- `push_back()` / `emplace_back()`: Add element to the end
- `pop_back()`: Delete the last element
- `front()` / `back()`: Access first / last element
- `size()`: Number of elements
- `empty()`: Returns 1 if empty, 0 otherwise
- `insert()`: Add element at a specific iterator
- `emplace()`: Like insert but faster (in-place construction)
- `erase()`: Delete element at iterator or range
- `reverse()`: Reverse the vector
- `*min_element()` / `*max_element()`: Find min/max in a range
- `find_if()`: Find element based on a condition

### Deque

Double-ended queue with fast insertion/deletion at both ends.

- `push_front()` / `emplace_front()`: Adds element to the beginning
- All vector operations also available

### Pairs

Container for two heterogeneous values.

```cpp
// Declaration
pair<string, int> p;
p.first = "ziad";  // Access first element
p.second = 123;    // Access second element

// Creation
auto p2 = make_pair(123, "ziad");

// Nested Pairs
pair<string, pair<int, double>> nas;
// nas.first          -> string
// nas.second.first   -> int
// nas.second.second  -> double
```

### Sets

Stores unique elements in sorted order using Red-Black Trees. No random access.

**Complexity**: Worst case O(log n)

**Common Operations:**

- `begin()` / `end()`: Iterators
- `insert(val)` / `emplace(val)`: Add element
- `erase(val)`: Remove element
- `count(val)`: Returns 1 if present (0 otherwise)
- `find(val)`: Returns iterator to element
- `clear()`: Empties the set
- `lower_bound(val)`: First element ≥ val
- `upper_bound(val)`: First element > val

**Optimization Hint:**

```cpp
auto it = s.begin();
s.emplace_hint(it, 5); // Reduces time from O(log n) to O(1)
```

### Ordered vs Unordered Containers

| Feature | Ordered (map, set) | Unordered (unordered_map) |
|---------|-------------------|---------------------------|
| **Data Structure** | Self-balancing BST | Hash Table |
| **Order** | Sorted by Key | Random/Undefined |
| **Time Complexity** | O(log n) | O(1) Avg, O(n) Worst |
| **Use Case** | Range queries, Sorted data | Fast lookups |

---

## Algorithms

### Sorting Implementation

#### Selection Sort (Ascending)

Time Complexity: O(n²)

```cpp
void mini(int arr[], int n) {
    int idx;
    for (int i = 0; i < n - 1; i++) {
        idx = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[idx])
                idx = j;
        }
        swap(arr[idx], arr[i]);
    }
}
```

### Searching

#### Find Maximum

```cpp
int findMax(int arr[], int n) {
    int max = arr[0];
    for (int i = 1; i < n; i++)
        if (arr[i] > max) max = arr[i];
    return max;
}
```

#### Find Minimum

```cpp
int findMin(int arr[], int n) {
    int min = arr[0];
    for (int i = 1; i < n; i++)
        if (arr[i] < min) min = arr[i];
    return min;
}
```

#### Manual Swap Logic

```cpp
int temp = a;
a = b;
b = temp;
```

### Sorting Theory & Complexity

#### Sorting Algorithms Comparison Table

| Algorithm | Best Case | Average Case | Worst Case | Space Complexity | Stable? | In-Place? |
|-----------|-----------|--------------|------------|------------------|---------|-----------|
| **Bubble Sort** | O(n) | O(n²) | O(n²) | O(1) | ✓ Yes | ✓ Yes |
| **Selection Sort** | O(n²) | O(n²) | O(n²) | O(1) | ✗ No | ✓ Yes |
| **Insertion Sort** | O(n) | O(n²) | O(n²) | O(1) | ✓ Yes | ✓ Yes |
| **Merge Sort** | O(n log n) | O(n log n) | O(n log n) | O(n) | ✓ Yes | ✗ No |
| **Quick Sort** | O(n log n) | O(n log n) | O(n²) | O(log n) | ✗ No | ✓ Yes |
| **Heap Sort** | O(n log n) | O(n log n) | O(n log n) | O(1) | ✗ No | ✓ Yes |
| **Counting Sort** | O(n+k) | O(n+k) | O(n+k) | O(k) | ✓ Yes | ✗ No |
| **Radix Sort** | O(d(n+k)) | O(d(n+k)) | O(d(n+k)) | O(n+k) | ✓ Yes | ✗ No |
| **Bucket Sort** | O(n+k) | O(n+k) | O(n²) | O(n) | ✓ Yes | ✗ No |

**Legend:**
- **k** = range of input values
- **d** = number of digits
- **Stable**: Maintains relative order of equal elements
- **In-Place**: Requires O(1) or O(log n) extra space

---

#### Detailed Algorithm Breakdown

##### 1. Comparison-Based Iterative Sorts

**Bubble Sort**
- **Method**: Repeatedly swaps adjacent elements if they're in wrong order
- **Best Case**: O(n) when array is already sorted (with optimization flag)
- **When to Use**: Small datasets, educational purposes, nearly sorted data
- **Key Feature**: Simple but inefficient for large datasets

**Selection Sort**
- **Method**: Finds minimum element from unsorted part and puts it at beginning
- **Why Always O(n²)**: Always scans remaining array regardless of order
- **When to Use**: Memory writes are costly (minimizes swaps)
- **Key Feature**: Makes minimum number of swaps (n-1)

**Insertion Sort**
- **Method**: Builds sorted array one item at a time
- **Best Case**: O(n) when array is already sorted
- **When to Use**: Small datasets, nearly sorted data, online sorting
- **Key Feature**: Efficient for small arrays and partially sorted data

---

##### 2. Divide & Conquer Sorts (Recursive)

**Merge Sort**
- **Method**: Divides array into halves, sorts them, then merges
- **Guaranteed Performance**: Always O(n log n)
- **When to Use**: Linked lists, external sorting, when stability is required
- **Key Feature**: Stable and predictable, but requires extra space
- **Drawback**: O(n) extra space needed

**Quick Sort**
- **Method**: Picks pivot, partitions array around it, recursively sorts partitions
- **Average Performance**: O(n log n) with good pivot selection
- **Worst Case**: O(n²) when pivot is always smallest/largest (sorted array)
- **When to Use**: General purpose sorting, in-place sorting needed
- **Optimization**: Use randomized pivot or median-of-three
- **Key Feature**: Fastest in practice for average cases



---

##### 3. Non-Comparison Sorts

**Counting Sort**
- **Method**: Counts occurrences of each value, reconstructs sorted array
- **Complexity**: O(n+k) where k is range of input
- **When to Use**: Small range of integers, k is not significantly larger than n
- **Key Feature**: Linear time for suitable data
- **Limitation**: Only works for integers or discrete values

**Radix Sort**
- **Method**: Sorts digit by digit using stable sort (like counting sort)
- **Complexity**: O(d(n+k)) where d is number of digits
- **When to Use**: Sorting integers, strings of fixed length
- **Key Feature**: Can be faster than O(n log n) for suitable data
- **Requirement**: Requires stable sub-sort algorithm



---

#### Sorting Algorithm Decision Guide

| Scenario | Recommended Algorithm | Reason |
|----------|----------------------|---------|
| Small array (n < 10) | Insertion Sort | Low overhead, simple |
| Nearly sorted data | Insertion Sort | O(n) best case |
| Large random data | Quick Sort | Best average performance |
| Guaranteed O(n log n) | Merge Sort or Heap Sort | No worst case degradation |
| Stability required | Merge Sort | Maintains relative order |
| Limited memory | Heap Sort or Quick Sort | In-place algorithms |
| Integer data, small range | Counting Sort | Linear time |
| Linked list | Merge Sort | No random access needed |
| External sorting | Merge Sort | Works well with sequential access |

---

#### Stability Explained

**Stable Sort**: Preserves the relative order of elements with equal keys.

Example: Sorting students by grade, then by name.
- **Stable** algorithms maintain the name order for students with same grade
- **Unstable** algorithms may change the relative positions

**Stable Algorithms**: Bubble, Insertion, Merge, Counting, Radix, Bucket  
**Unstable Algorithms**: Selection, Quick, Heap

---

#### C++ STL sort()

```cpp
#include <algorithm>
sort(arr, arr + n);           // Sort array
sort(v.begin(), v.end());     // Sort vector
sort(all(v));                 // Using macro: #define all(x) (x).begin(), (x).end()

// Custom comparator (descending)
sort(v.begin(), v.end(), greater<int>());

// Custom comparator function
bool cmp(int a, int b) { return a > b; }
sort(v.begin(), v.end(), cmp);
```

**STL sort() Details**:
- **Algorithm Used**: IntroSort (hybrid of Quick Sort, Heap Sort, and Insertion Sort)
- **Time Complexity**: O(n log n) average and worst case
- **Stability**: `sort()` is **not stable**, use `stable_sort()` if stability is needed
- **When to Use**: Default choice for most competitive programming problems

---

## Logic Gates

### XOR Gate Rule

For an XOR gate with >2 inputs:

- **Output is Logic 1** if the number of Logic 1 inputs is **Odd**
- **Output is Logic 0** otherwise

---

## Quick Reference

### Time Complexity Hierarchy

```
O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2^n) < O(n!)
```

### Common STL Time Complexities

| Operation | Vector | Set | Unordered Set |
|-----------|--------|-----|---------------|
| Access | O(1) | — | — |
| Insert | O(1) amortized | O(log n) | O(1) avg |
| Delete | O(n) | O(log n) | O(1) avg |
| Search | O(n) | O(log n) | O(1) avg |

---

*Happy Coding! 🚀*
