# Comparator Function in C++

## 📌 Introduction
A **Comparator Function** in C++ is a function used to define custom sorting orders. It is commonly used with:
- `std::sort()`
- `std::priority_queue`
- `std::set` & `std::map`
- Custom data structures

A comparator function should return:
- **`true`** → if the first element should come **before** the second.
- **`false`** → if the first element should come **after** the second.

---

## 🔹 Syntax
A comparator function takes two elements as arguments and returns a boolean.

```cpp
bool compare(int a, int b) {
    return a < b;  // Ascending order
}
```

---

## 🔷 1. Sorting with `sort()`
The `sort()` function in C++ allows a custom comparator to define the sorting order.

### **🟢 Example 1: Sorting in Descending Order**
```cpp
#include <bits/stdc++.h>
using namespace std;

bool compare(int a, int b) {
    return a > b;  // Descending order
}

int main() {
    vector<int> arr = {5, 2, 9, 1, 5, 6};
    
    sort(arr.begin(), arr.end(), compare);
    
    for (int x : arr) cout << x << " ";  // Output: 9 6 5 5 2 1
}
```

---

### **🔷 2. Sorting a Vector of Pairs**
Sorting a vector of pairs based on:
1. First element in **ascending** order.
2. If first elements are equal, sort the second element in **descending** order.

```cpp
#include <bits/stdc++.h>
using namespace std;

bool compare(pair<int, int> a, pair<int, int> b) {
    if (a.first == b.first)
        return a.second > b.second; // Sort second value in descending order
    return a.first < b.first;  // Sort first value in ascending order
}

int main() {
    vector<pair<int, int>> v = {{3, 4}, {2, 3}, {3, 2}, {1, 5}};
    
    sort(v.begin(), v.end(), compare);
    
    for (auto p : v) cout << "(" << p.first << "," << p.second << ") ";
    // Output: (1,5) (2,3) (3,4) (3,2)
}
```

---

## 🔷 3. Using Comparator in `priority_queue`
### **🟢 Min Heap (Smallest element on top)**
```cpp
priority_queue<int, vector<int>, greater<int>> minHeap;
```

### **🔴 Max Heap with Custom Comparator**
```cpp
struct Compare {
    bool operator()(int a, int b) {
        return a < b;  // Max heap (reverse order)
    }
};

priority_queue<int, vector<int>, Compare> maxHeap;
```

---

## 🔷 4. Sorting Custom Structures
Comparators can be used for sorting custom data types.

```cpp
#include <bits/stdc++.h>
using namespace std;

struct Student {
    string name;
    int marks;
};

bool compare(Student a, Student b) {
    return a.marks > b.marks;  // Sort by marks in descending order
}

int main() {
    vector<Student> students = {{"Alice", 85}, {"Bob", 90}, {"Charlie", 80}};
    
    sort(students.begin(), students.end(), compare);
    
    for (auto s : students) cout << s.name << " " << s.marks << "\n";
    // Output: Bob 90
    //         Alice 85
    //         Charlie 80
}
```

---

## 🔹 Summary
✅ A **Comparator Function** defines custom sorting behavior.
✅ Used with `sort()`, `priority_queue`, `set`, `map`.
✅ Should return `true` if **first element should come before second**.
✅ Can be used with primitive types, pairs, or custom structures.

---

### 🚀 **Now you can implement custom sorting in your C++ programs!**
