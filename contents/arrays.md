# Arrays

## Table of Contents

1. [Definition](#1-definition)
2. [How It Works](#2-how-it-works)
   - [Memory Layout](#memory-layout)
   - [Basic Operations](#basic-operations)
   - [Traversal](#traversal)
   - [Language-Specific Features](#language-specific-features)
3. [Mathematical Explanation](#3-mathematical-explanation)
4. [Problem Lists and Why Arrays Are Better](#4-problem-lists-and-why-arrays-are-better)
5. [Practice Problems](#5-practice-problems)
6. [Third Party Resources](#third-party-resources)
7. [Key Takeaways](#key-takeaways)

---

## 1. Definition

An **Array** is a linear data structure that stores elements in contiguous memory locations. It represents a collection of elements of the same data type, organized in a sequential order. Each element in an array can be accessed directly using its index position.

### Key Characteristics:
- **Homogeneous**: All elements are of the same type
- **Contiguous Memory**: Elements stored in adjacent memory locations
- **Fixed or Dynamic Size**: Can be static or resizable depending on language
- **Zero-based Indexing**: First element typically at index 0
- **Direct Access**: Can access any element in O(1) time via index

### Example Declarations:
```python
# Python - Dynamic Array
arr = [1, 2, 3, 4, 5]
```

```java
// Java - Static Array
int[] arr = {1, 2, 3, 4, 5};
// or
int[] arr = new int[5];
```

```cpp
// C++ - Static Array
int arr[] = {1, 2, 3, 4, 5};
// or
int arr[5] = {1, 2, 3, 4, 5};
// or dynamic
vector<int> arr = {1, 2, 3, 4, 5};
```

---

## 2. How It Works

### Memory Layout

Arrays allocate memory contiguously, meaning each element is stored right after the previous one:

```
Memory Address:  1000    1004    1008    1012    1016
Array Index:       0       1       2       3       4
Value:             10      20      30      40      50
```

### Basic Operations

#### **Access** - Get element at index
```python
# Python
arr = [10, 20, 30, 40, 50]
element = arr[2]  # Returns 30
```

```java
// Java
int[] arr = {10, 20, 30, 40, 50};
int element = arr[2];  // Returns 30
```

```cpp
// C++
int arr[] = {10, 20, 30, 40, 50};
int element = arr[2];  // Returns 30
```

#### **Update** - Modify element at index
```python
# Python
arr[2] = 35  # arr becomes [10, 20, 35, 40, 50]
```

```java
// Java
arr[2] = 35;  // arr becomes {10, 20, 35, 40, 50}
```

```cpp
// C++
arr[2] = 35;  // arr becomes {10, 20, 35, 40, 50}
```

#### **Insertion** - Add element at index
```python
# Python - insert() O(n)
arr.insert(2, 25)  # Insert 25 at index 2
```

```java
// Java - Requires shifting elements O(n)
// For ArrayList:
ArrayList<Integer> arr = new ArrayList<>(Arrays.asList(10, 20, 30, 40, 50));
arr.add(2, 25);  // Insert 25 at index 2
```

```cpp
// C++ - vector
vector<int> arr = {10, 20, 30, 40, 50};
arr.insert(arr.begin() + 2, 25);  // Insert 25 at index 2
```

#### **Deletion** - Remove element at index
```python
# Python - pop() or remove()
arr.pop(2)  # Remove element at index 2
```

```java
// Java - ArrayList
arr.remove(2);  // Remove element at index 2
```

```cpp
// C++ - vector
arr.erase(arr.begin() + 2);  // Remove element at index 2
```

#### **Search** - Find element
```python
# Python - index() O(n)
index = arr.index(30)  # Returns 2
```

```java
// Java - Linear search O(n)
for (int i = 0; i < arr.length; i++) {
    if (arr[i] == 30) {
        // found at index i
    }
}
```

```cpp
// C++ - Linear search O(n)
for (int i = 0; i < arr.size(); i++) {
    if (arr[i] == 30) {
        // found at index i
    }
}
```

### Traversal

```python
# Python
# By index
for i in range(len(arr)):
    print(arr[i])

# Direct iteration
for element in arr:
    print(element)
```

```java
// Java
// Traditional for loop
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}

// Enhanced for loop
for (int element : arr) {
    System.out.println(element);
}
```

```cpp
// C++
// Traditional for loop
for (int i = 0; i < arr.size(); i++) {
    cout << arr[i] << endl;
}

// Range-based for loop (C++11)
for (int element : arr) {
    cout << element << endl;
}
```

### Language-Specific Features

#### **Python - List Features**

```python
# List Comprehensions
squares = [x**2 for x in range(10)]  # [0, 1, 4, 9, 16, 25, ...]
evens = [x for x in range(20) if x % 2 == 0]

# Slicing - [start:end:step]
arr = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
arr[2:6]    # [2, 3, 4, 5]
arr[:5]     # [0, 1, 2, 3, 4] (first 5)
arr[5:]     # [5, 6, 7, 8, 9] (from 5 onwards)
arr[::2]    # [0, 2, 4, 6, 8] (every 2nd element)
arr[::-1]   # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0] (reverse)

# List Methods
arr = [3, 1, 4, 1, 5]
arr.append(6)       # Add to end
arr.extend([7, 8])  # Add multiple elements
arr.insert(2, 10)   # Insert at index
arr.remove(1)       # Remove first occurrence
arr.pop()           # Remove and return last
arr.pop(0)          # Remove and return first
arr.reverse()       # Reverse in place
arr.sort()          # Sort in place
arr.count(1)        # Count occurrences
arr.index(4)        # Find index

# Unpacking
first, second, *rest = [1, 2, 3, 4, 5]
# first=1, second=2, rest=[3, 4, 5]

# Concatenation and Repetition
arr1 + arr2  # Concatenate
arr * 3      # Repeat 3 times

# Built-in Functions
len(arr)     # Length
max(arr)     # Maximum
min(arr)     # Minimum
sum(arr)     # Sum
any(arr)     # True if any is true
all(arr)     # True if all are true
sorted(arr)  # Return sorted copy
enumerate(arr)  # Get (index, value) pairs
zip(arr1, arr2)  # Combine two lists
```

#### **Java - Array Features**

```java
// Arrays Class - Utility Methods
import java.util.Arrays;

int[] arr = {3, 1, 4, 1, 5};

// Fill
Arrays.fill(arr, 0);           // Set all to 0
Arrays.fill(arr, 2, 5, 10);    // Set indices 2-4 to 10

// Sorting
Arrays.sort(arr);               // Sort in place
Arrays.sort(arr, 1, 4);         // Sort range

// Searching (requires sorted)
Arrays.binarySearch(arr, 4);    // Returns index or -(insertion point - 1)

// Comparison
Arrays.equals(arr1, arr2);      // Element-wise equality
Arrays.deepEquals(arr1, arr2);  // For 2D arrays

// Copying
int[] copy = Arrays.copyOf(arr, 10);        // Copy first 10 elements
int[] copy = Arrays.copyOfRange(arr, 2, 5); // Copy range [2, 5)

// String representation
Arrays.toString(arr);           // "[3, 1, 4, 1, 5]"

// ArrayList - Dynamic Arrays
import java.util.ArrayList;
import java.util.Collections;

ArrayList<Integer> list = new ArrayList<>();
list.add(10);                   // Append
list.add(0, 5);                 // Insert at index
list.get(0);                    // Access
list.set(0, 20);                // Update
list.remove(0);                 // Remove at index
list.remove(Integer.valueOf(10)); // Remove by value
list.size();                    // Length
list.contains(10);              // Check existence
list.indexOf(10);               // Find index
Collections.sort(list);         // Sort
Collections.reverse(list);      // Reverse

// Stream API (Java 8+)
int[] arr = {3, 1, 4, 1, 5};
Arrays.stream(arr)
    .filter(x -> x > 2)
    .map(x -> x * 2)
    .sum();                     // Chain operations

// Multidimensional Arrays
int[][] matrix = new int[3][4]; // 3x4 matrix
int[][] jagged = new int[3][];   // Jagged array
```

#### **C++ - Array Features**

```cpp
#include <array>
#include <vector>
#include <algorithm>

// C-style Arrays
int arr[5] = {1, 2, 3, 4, 5};
sizeof(arr) / sizeof(arr[0]);  // Array size (compiler-dependent)

// std::array (C++11) - Better than C-style
#include <array>
std::array<int, 5> arr = {1, 2, 3, 4, 5};
arr.size();       // Size
arr.front();      // First element
arr.back();       // Last element
arr.fill(10);     // Fill all with 10
arr.empty();      // Check if empty
arr.at(2);        // Safe access with bounds checking

// std::vector - Dynamic Array
#include <vector>
std::vector<int> vec = {1, 2, 3, 4, 5};

// Basic Operations
vec.push_back(6);      // Add to end
vec.pop_back();        // Remove from end
vec.insert(vec.begin() + 2, 10);  // Insert at index
vec.erase(vec.begin() + 2);       // Erase at index
vec.size();            // Current size
vec.capacity();        // Allocated capacity
vec.empty();           // Check if empty
vec.clear();           // Clear all elements

// Access
vec[0];                // No bounds check
vec.at(0);             // Bounds check, throws exception
vec.front();           // First element
vec.back();            // Last element

// Resize
vec.resize(10);        // Resize to 10
vec.reserve(100);      // Reserve capacity for 100 elements

// STL Algorithms
std::vector<int> vec = {3, 1, 4, 1, 5};

// Sorting and Searching
std::sort(vec.begin(), vec.end());
std::reverse(vec.begin(), vec.end());
std::binary_search(vec.begin(), vec.end(), 4);

// Find
auto it = std::find(vec.begin(), vec.end(), 4);  // Returns iterator
std::count(vec.begin(), vec.end(), 1);          // Count occurrences

// Transform
std::transform(vec.begin(), vec.end(), vec.begin(), 
               [](int x) { return x * 2; });    // Lambda transform

// Useful Functions
std::max_element(vec.begin(), vec.end());  // Maximum
std::min_element(vec.begin(), vec.end());  // Minimum
std::accumulate(vec.begin(), vec.end(), 0); // Sum

// Two-Dimensional Vectors
std::vector<std::vector<int>> matrix(3, std::vector<int>(4, 0));  // 3x4
std::vector<std::vector<int>> jagged(3);  // Jagged array

// Range-based for loop (C++11)
for (const auto& element : vec) {
    std::cout << element << std::endl;
}

// Initialization (C++11)
std::vector<int> vec1(10, 0);  // 10 zeros
std::vector<int> vec2{1, 2, 3, 4, 5};  // Initializer list
```

#### **JavaScript - Array Features**

```javascript
// Array Creation
let arr = [1, 2, 3, 4, 5];
let arr = new Array(5);        // Empty array of length 5
let arr = Array.from({length: 5}, (_, i) => i * 2);  // [0, 2, 4, 6, 8]

// Mutating Methods
arr.push(6);           // Add to end
arr.pop();             // Remove from end
arr.shift();           // Remove from beginning
arr.unshift(0);        // Add to beginning
arr.splice(2, 1, 10);  // At index 2, remove 1, insert 10
arr.reverse();         // Reverse in place
arr.sort();            // Sort in place

// Non-Mutating Methods
arr.slice(2, 5);       // Copy range
arr.concat([6, 7]);    // Concatenate
arr.indexOf(3);        // Find index
arr.lastIndexOf(3);    // Find last index
arr.includes(3);       // Check existence
arr.join(', ');        // Join to string

// Functional Methods (ES6+)
arr.map(x => x * 2);           // Transform
arr.filter(x => x > 2);        // Filter
arr.reduce((acc, x) => acc + x, 0);  // Reduce
arr.forEach(x => console.log(x));    // Iterate
arr.some(x => x > 10);         // Any match
arr.every(x => x > 0);         // All match
arr.find(x => x > 2);          // Find first match
arr.findIndex(x => x > 2);     // Find first index

// Spread Operator (ES6)
let arr2 = [...arr, 6, 7];     // Copy and add
let max = Math.max(...arr);    // Spread as arguments

// Destructuring
let [first, second, ...rest] = arr;

// Fill and Copy
arr.fill(0, 2, 5);             // Fill range with 0
let copy = Array.from(arr);    // Shallow copy
let copy2 = arr.slice();       // Alternative copy
```

---

## 3. Mathematical Explanation

### Memory Addressing

For an array starting at base address `B`, with element size `S` bytes:

**Address of element at index i:**
```
Address[i] = B + (i × S)
```

**Example:**
- Base address = 1000
- Integer size = 4 bytes
- Index = 3
- Address[3] = 1000 + (3 × 4) = 1012

### Time Complexity Analysis

| Operation | Time Complexity | Explanation |
|-----------|----------------|-------------|
| Access | O(1) | Direct calculation: `B + (i × S)` |
| Update | O(1) | Same as access |
| Search | O(n) | May need to check all n elements |
| Insertion at end | O(1) | Direct assignment (amortized for dynamic arrays) |
| Insertion at position | O(n) | Need to shift n-i elements |
| Deletion from end | O(1) | Simple removal |
| Deletion from position | O(n) | Need to shift remaining elements |

### Space Complexity

**Static Array:** O(n) - where n is the array size (fixed)

**Dynamic Array:** O(n) - where n is current capacity
- Amortized O(1) for append operations
- May need resizing when capacity exceeded

### Resizing in Dynamic Arrays

When a dynamic array is full and needs to grow:

**Copy Strategy:** Allocate new array of size `2 × current_capacity`, then copy all elements.

**Amortized Cost:** 
- Most operations: O(1)
- Occasional resize: O(n)
- Amortized over sequence: O(1) per operation

**Mathematical Proof:**
- Let n be the number of elements
- Copy cost at resize: O(n)
- Next resize happens after n more operations
- Amortized cost: O(n) / n = O(1)

### Two-Dimensional Arrays

**Memory Layout (Row-major order):**
```
Base address: B
Row size: R
Column size: C

Address[i][j] = B + (i × R + j) × S
```

**Example:**
- 3×4 array (3 rows, 4 columns)
- Address[1][2] = B + (1 × 4 + 2) × S = B + 6S

---

## 4. Problem Lists and Why Arrays Are Better

### Problem 1: Finding Maximum/Minimum Element

**Why Arrays are Better:**
- Direct sequential access enables efficient single-pass algorithm
- No extra overhead like hash tables or trees
- O(1) space complexity
- Simple and intuitive implementation

**Example:**
```python
# Python
def find_max(arr):
    if not arr:
        return None
    max_val = arr[0]
    for num in arr[1:]:
        if num > max_val:
            max_val = num
    return max_val

# Time: O(n), Space: O(1)
```

```java
// Java
public static int findMax(int[] arr) {
    if (arr.length == 0) return Integer.MIN_VALUE;
    int max = arr[0];
    for (int i = 1; i < arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}
// Time: O(n), Space: O(1)
```

```cpp
// C++
int findMax(vector<int>& arr) {
    if (arr.empty()) return INT_MIN;
    int max = arr[0];
    for (int i = 1; i < arr.size(); i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}
// Time: O(n), Space: O(1)
```

---

### Problem 2: Reversing an Array

**Why Arrays are Better:**
- Two-pointer technique works perfectly with sequential memory
- In-place reversal requires O(1) extra space
- O(n/2) time with constant factor optimization
- Natural fit for direct element swapping

**Example:**
```python
# Python
def reverse_array(arr):
    left, right = 0, len(arr) - 1
    while left < right:
        arr[left], arr[right] = arr[right], arr[left]
        left += 1
        right -= 1
    return arr

# Time: O(n), Space: O(1)
```

```java
// Java
public static void reverseArray(int[] arr) {
    int left = 0, right = arr.length - 1;
    while (left < right) {
        int temp = arr[left];
        arr[left] = arr[right];
        arr[right] = temp;
        left++;
        right--;
    }
}
// Time: O(n), Space: O(1)
```

```cpp
// C++
void reverseArray(vector<int>& arr) {
    int left = 0, right = arr.size() - 1;
    while (left < right) {
        swap(arr[left], arr[right]);
        left++;
        right--;
    }
}
// Time: O(n), Space: O(1)
```

---

### Problem 3: Array Rotation

**Why Arrays are Better:**
- Multiple in-place rotation algorithms possible
- Direct manipulation of indices enables efficient solutions
- Can reverse subarrays to achieve rotation without extra space
- Essential for many array manipulation problems

**Example (Rotate Right by k):**
```python
# Python - Array Rotation
def rotate_right(arr, k):
    n = len(arr)
    k = k % n
    if k == 0:
        return arr
    
    # Reverse entire array
    arr.reverse()
    # Reverse first k elements
    arr[:k] = arr[:k][::-1]
    # Reverse remaining elements
    arr[k:] = arr[k:][::-1]
    
    return arr

# Time: O(n), Space: O(1)
```

```java
// Java - Array Rotation
public static void rotateRight(int[] arr, int k) {
    int n = arr.length;
    k = k % n;
    if (k == 0) return;
    
    // Reverse entire array
    reverse(arr, 0, n - 1);
    // Reverse first k elements
    reverse(arr, 0, k - 1);
    // Reverse remaining elements
    reverse(arr, k, n - 1);
}

private static void reverse(int[] arr, int start, int end) {
    while (start < end) {
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}
// Time: O(n), Space: O(1)
```

```cpp
// C++ - Array Rotation
void rotateRight(vector<int>& arr, int k) {
    int n = arr.size();
    k = k % n;
    if (k == 0) return;
    
    // Reverse entire array
    reverse(arr.begin(), arr.end());
    // Reverse first k elements
    reverse(arr.begin(), arr.begin() + k);
    // Reverse remaining elements
    reverse(arr.begin() + k, arr.end());
}
// Time: O(n), Space: O(1)
```

---

## 5. Practice Problems

### Easy Level

1. **Best Time to Buy and Sell Stock** - Find maximum profit
   - LeetCode: [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
   - Why: Single pass optimization

2. **Contains Duplicate** - Check if array has duplicates
   - LeetCode: [217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)
   - Why: Hash set or sorting

### Medium Level

1. **Next Permutation** - Find next lexicographically greater permutation
   - LeetCode: [31. Next Permutation](https://leetcode.com/problems/next-permutation/)
   - Why: In-place algorithm, understanding permutations

---

## Third Party Resources

### Visualizations
- **VisuAlgo - Array**: [https://visualgo.net/en/array](https://visualgo.net/en/array)
  - Interactive array visualization
  - Various operations demonstrated

- **Algorithm Visualizer - Arrays**: [https://algorithm-visualizer.org/brute-force/linear-search](https://algorithm-visualizer.org/brute-force/linear-search)
  - Step-by-step algorithm execution
  - Visual feedback for operations

### Tutorials
- **GeeksforGeeks - Arrays**: [https://www.geeksforgeeks.org/array-data-structure/](https://www.geeksforgeeks.org/array-data-structure/)
  - Comprehensive tutorial
  - Multiple language examples

- **Programiz - Arrays**: [https://www.programiz.com/python-programming/array](https://www.programiz.com/python-programming/array)
  - Beginner-friendly explanations
  - Python-focused

### Practice Platforms
- **LeetCode - Array Tag**: [https://leetcode.com/tag/array/](https://leetcode.com/tag/array/)
  - 2000+ array problems
  - Difficulty levels from Easy to Hard

- **HackerRank - Arrays**: [https://www.hackerrank.com/domains/data-structures/arrays](https://www.hackerrank.com/domains/data-structures/arrays)
  - Practical array problems
  - Real-world applications

### Books
- **"Cracking the Coding Interview"** - Chapter 1 (Arrays and Strings)
- **"Elements of Programming Interviews"** - Chapter 5 (Arrays)

### Video Resources
- **NeetCode - Arrays**: [YouTube - NeetCode Array Playlist](https://www.youtube.com/@NeetCode)
  - Problem-solving walkthroughs
  - Optimized solutions

- **Back To Back SWE - Arrays**: [YouTube - Back To Back SWE](https://www.youtube.com/@BackToBackSWE)
  - Detailed explanations
  - Interview-focused

---

## Key Takeaways

✅ **Arrays are the foundation**: Most problems start with arrays as input  
✅ **Direct access is powerful**: O(1) random access enables efficient algorithms  
✅ **Language-specific features**: Each language offers powerful array operations  
✅ **In-place operations**: Save space with careful index manipulation  
✅ **Understand memory layout**: Helps optimize cache performance  
✅ **Master fundamentals**: Arrays form basis for more advanced structures  

**Next Steps**: Master arrays before moving to Strings, Hash Tables, and more complex structures!

