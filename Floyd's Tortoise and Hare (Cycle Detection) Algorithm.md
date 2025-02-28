# Floyd's Tortoise and Hare (Cycle Detection) Algorithm

## **Introduction**
Floyd's Cycle Detection Algorithm, also known as the **Tortoise and Hare Algorithm**, is an efficient method to detect cycles in a sequence of values. It is widely used in computer science for problems involving linked lists, graph traversal, and numerical sequences.

This algorithm uses two pointers (a slow-moving "tortoise" and a fast-moving "hare") to traverse the sequence. If there is a cycle, the two pointers will eventually meet. Otherwise, the fast pointer will reach the end.

---

## **Working Principle**
### **Step 1: Initialize Two Pointers**
- Start with two pointers: `slow` (moves **one step** at a time) and `fast` (moves **two steps** at a time).

### **Step 2: Detect Cycle (Phase 1)**
- Move the `slow` pointer by one step and the `fast` pointer by two steps.
- If they meet at some point, a **cycle exists**.

### **Step 3: Find Cycle Start (Phase 2)**
- Reset the `slow` pointer to the **start** of the sequence.
- Move both `slow` and `fast` one step at a time.
- The meeting point is the **start of the cycle**.

---

## **Implementation in C++**
```cpp
#include <iostream>
#include <vector>

using namespace std;

int findDuplicate(vector<int>& nums) {
    int slow = nums[0], fast = nums[0];

    // Phase 1: Detect cycle
    do {
        slow = nums[slow];
        fast = nums[nums[fast]];
    } while (slow != fast);

    // Phase 2: Find the duplicate
    slow = nums[0];
    while (slow != fast) {
        slow = nums[slow];
        fast = nums[fast];
    }

    return slow;
}

int main() {
    vector<int> nums = {3, 1, 3, 4, 2};
    cout << "Duplicate Number: " << findDuplicate(nums) << endl;
    return 0;
}
```

---

## **Complexity Analysis**
- **Time Complexity:** `O(n)`, since each pointer moves at most `O(n)` times.
- **Space Complexity:** `O(1)`, as only two pointers are used.

---

## **Applications of Floyd's Cycle Detection Algorithm**
1. **Detecting cycles in linked lists** (e.g., checking if a linked list has a loop).
2. **Finding duplicate numbers in an array** (as in the example above).
3. **Graph cycle detection** in directed graphs.
4. **Periodicity detection** in pseudo-random number generators.
5. **Cycle detection in functional mappings** (e.g., solving mathematical problems involving repeated function application).

---

## **Advantages**
✅ Uses only **O(1) extra space** (constant memory usage).  
✅ Works in **O(n) time complexity**.  
✅ Simple and efficient compared to other cycle detection methods.

---

## **Conclusion**
Floyd's Cycle Detection Algorithm is an elegant and efficient method for detecting cycles in a sequence. Its wide range of applications, from linked lists to numerical sequences, makes it a fundamental concept in computer science. By understanding and implementing this algorithm, developers can efficiently handle cycle-related problems in various domains.

---

*Feel free to use this explanation in your GitHub repository or documentation!* 🚀
