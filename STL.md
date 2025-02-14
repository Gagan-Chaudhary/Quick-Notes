# 🚀 C++ STL Cheat Sheet

**Last Updated:** 03 Feb, 2025  
The C++ STL Cheat Sheet provides concise notes on the Standard Template Library (STL) in C++. Designed for programmers looking to quickly understand key STL concepts, this cheat sheet covers containers, iterators, functors, and algorithms with syntax and examples.

---

## 📌 What is the Standard Template Library (STL)?

The **C++ Standard Template Library (STL)** is a collection of generic class and function templates that provide commonly used data structures and algorithms. It includes optimized and error-free implementations of containers like `vector`, `list`, `stack`, `queue`, etc. STL is a core part of the C++ standard library.

### 🛠 Components of STL

The C++ STL consists of four main components:

- **Containers** – Data structures like arrays, linked lists, trees, and hashmaps.
- **Iterators** – Objects used to traverse elements in containers.
- **Algorithms** – Functions for searching, sorting, and modifying data.
- **Functors** – Function objects that behave like functions.

---

## 📌 STL Containers

STL provides various container classes categorized as follows:

### 1️⃣ Sequential Containers

Used for ordered data storage with sequential access.

- `vector` – Dynamic array.
- `list` – Doubly linked list.
- `deque` – Double-ended queue.
- `array` – Fixed-size array.
- `forward_list` – Singly linked list.

### 2️⃣ Container Adapters

Simplify interfaces for specific use cases.

- `stack` – LIFO (Last In First Out).
- `queue` – FIFO (First In First Out).
- `priority_queue` – Elements sorted by priority.

### 3️⃣ Associative Containers

Store key-value pairs in sorted order for quick retrieval.

- `set` – Unique elements, sorted.
- `multiset` – Allows duplicate elements, sorted.
- `map` – Unique key-value pairs, sorted by key.
- `multimap` – Allows duplicate keys, sorted.

### 4️⃣ Unordered Containers

Similar to associative containers but unordered for faster access.

- `unordered_set` – Unique elements, hashed.
- `unordered_multiset` – Allows duplicate elements, hashed.
- `unordered_map` – Unique key-value pairs, hashed.
- `unordered_multimap` – Allows duplicate keys, hashed.

---

## 📌 STL Containers Deep Dive

### 🔹 **Vector** (`std::vector<T>`)

A dynamic array that can grow or shrink in size.

#### **Declaration:**

```cpp
vector<int> vec1;           // Empty vector
vector<int> vec2(5, 10);    // Vector of size 5 initialized with 10
vector<int> vec3 = {1, 2, 3, 4}; // Initialization list
```

#### **Common Operations:**

| Function        | Description                     | Complexity |
| --------------- | ------------------------------- | ---------- |
| `begin()`       | Iterator to first element       | O(1)       |
| `end()`         | Iterator past last element      | O(1)       |
| `size()`        | Returns number of elements      | O(1)       |
| `empty()`       | Checks if vector is empty       | O(1)       |
| `push_back(x)`  | Adds element at end             | O(1)       |
| `pop_back()`    | Removes last element            | O(1)       |
| `insert(it, x)` | Inserts `x` at iterator `it`    | O(n)       |
| `erase(it)`     | Erases element at iterator `it` | O(n)       |
| `clear()`       | Removes all elements            | O(n)       |

#### **Example:**

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v = {1, 2, 3, 4, 5};
    v.push_back(6);
    v.erase(v.begin() + 2);

    for (int num : v) cout << num << " ";
    return 0;
}
```

**Output:**

```
1 2 4 5 6
```

---

### 🔹 **List** (`std::list<T>`)

A doubly linked list for efficient insertions and deletions.

#### **Declaration:**

```cpp
list<int> lst1;           // Empty list
list<int> lst2(5, 100);   // List of size 5 with 100s
```

#### **Common Operations:**

| Function        | Description                     | Complexity |
| --------------- | ------------------------------- | ---------- |
| `push_back(x)`  | Adds element at end             | O(1)       |
| `push_front(x)` | Adds element at front           | O(1)       |
| `pop_back()`    | Removes last element            | O(1)       |
| `pop_front()`   | Removes first element           | O(1)       |
| `insert(it, x)` | Inserts `x` at iterator `it`    | O(n)       |
| `erase(it)`     | Erases element at iterator `it` | O(n)       |

#### **Example:**

```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    list<int> l = {10, 20, 30};
    l.push_front(5);
    l.push_back(40);
    l.pop_front();

    for (int num : l) cout << num << " ";
    return 0;
}
```

**Output:**

```
10 20 30 40
```

---

## 📌 STL Algorithms

STL provides various built-in algorithms for common operations. These functions operate on iterators.

### **Sorting (`sort`)**

```cpp
sort(vec.begin(), vec.end());  // Ascending order
sort(vec.rbegin(), vec.rend()); // Descending order
```

### **Searching (`find`, `binary_search`)**

```cpp
auto it = find(vec.begin(), vec.end(), 5);
bool exists = binary_search(vec.begin(), vec.end(), 3);
```

### **Min/Max (`min_element`, `max_element`)**

```cpp
int minVal = *min_element(vec.begin(), vec.end());
int maxVal = *max_element(vec.begin(), vec.end());
```

### **Accumulation (`accumulate`)**

```cpp
int sum = accumulate(vec.begin(), vec.end(), 0);
```

### **Reversing (`reverse`)**

```cpp
reverse(vec.begin(), vec.end());
```

---

## 📌 STL Iterators

Iterators allow traversal over STL containers.

### **Types of Iterators**

1. **Input Iterator** - Read-only, single-pass.
2. **Output Iterator** - Write-only, single-pass.
3. **Forward Iterator** - Read/write, single-pass.
4. **Bidirectional Iterator** - Read/write, both directions.
5. **Random Access Iterator** - Fast random access.

Example:

```cpp
vector<int>::iterator it;
for (it = vec.begin(); it != vec.end(); it++) {
    cout << *it << " ";
}
```

---

## 📌 STL Functors

A **functor** is an object that behaves like a function.

```cpp
struct Add {
    int operator()(int a, int b) { return a + b; }
};
int main() {
    Add add;
    cout << add(3, 4); // Output: 7
}
```

---

This structured STL cheat sheet ensures clarity and quick reference. Let me know if you need further refinements! 🚀
