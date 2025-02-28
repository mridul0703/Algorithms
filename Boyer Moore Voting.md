# **Boyer-Moore Voting Algorithm**

## **Introduction**
The **Boyer-Moore Voting Algorithm** is an efficient algorithm used to find the **majority element** in a sequence. A majority element is an element that appears **more than ⌊n/2⌋ times** in an array of size `n`.

This algorithm runs in **O(n) time** and uses **O(1) space**, making it highly efficient for large datasets.

---

## **Intuition & Working**
### **Key Idea**
The algorithm works by maintaining a **candidate** for the majority element and a **counter** that helps verify the candidate.

1. **Candidate Selection Phase:**
   - Traverse the array and maintain a **count** of occurrences of the current candidate.
   - If the count becomes `0`, select the current element as the new **candidate**.

2. **Candidate Verification Phase (Optional):**
   - Since the first pass does not guarantee correctness in cases where no majority element exists, a second pass may be required to verify the count.

---

## **Algorithm Steps**
1. Initialize two variables:
   - `candidate` (stores the potential majority element)
   - `count` (tracks the candidate’s frequency)
2. Iterate through the array:
   - If `count == 0`, set the **current element as candidate**.
   - If the current element is the **same as the candidate**, increment `count`.
   - Otherwise, decrement `count`.
3. (Optional) Verify if the candidate appears more than `⌊n/2⌋` times in a second pass.

---

## **Code Implementation**
### **C++ Implementation**
```cpp
#include <iostream>
#include <vector>
using namespace std;

class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int candidate = 0, count = 0;
        
        // Phase 1: Find a candidate
        for (int num : nums) {
            if (count == 0) {
                candidate = num;
            }
            count += (num == candidate) ? 1 : -1;
        }
        
        // Phase 2: Verify the candidate (Optional)
        int freq = 0;
        for (int num : nums) {
            if (num == candidate) freq++;
        }
        
        return (freq > nums.size() / 2) ? candidate : -1;  // -1 means no majority element
    }
};

int main() {
    Solution sol;
    vector<int> nums = {2, 2, 1, 1, 1, 2, 2};
    cout << "Majority Element: " << sol.majorityElement(nums) << endl;  // Output: 2
    return 0;
}
```

---

## **Time & Space Complexity**
- **Time Complexity:** `O(n)`, since we traverse the array once (or twice in the verification step).
- **Space Complexity:** `O(1)`, as we use only two variables.

---

## **Applications**
1. **Voting systems** – Finding the most voted candidate.
2. **Data stream processing** – Identifying dominant trends.
3. **Fraud detection** – Spotting frequently occurring transactions.
4. **Stock market analysis** – Recognizing patterns in stock price movements.

---

## **Advantages & Limitations**
### ✅ **Advantages**
- Runs in **linear time O(n)**.
- Uses **constant space O(1)**.
- Simple and elegant approach.

### ❌ **Limitations**
- Only works if a **majority element exists**.
- If no element appears more than `⌊n/2⌋` times, the result may be incorrect without verification.
- Requires a second pass for strict correctness in generic cases.

---

## **Example Walkthrough**
### **Example 1**
#### **Input:**
```cpp
nums = [3, 3, 4, 2, 3, 3, 3, 2, 3]
```
#### **Processing:**
1. `candidate = 3, count = 1`
2. `candidate = 3, count = 2`
3. `candidate = 3, count = 1` (decremented)
4. `candidate = 3, count = 0`
5. `candidate = 3 (new), count = 1`
6. `candidate = 3, count = 2`
7. `candidate = 3, count = 3`
8. `candidate = 3, count = 2` (decremented)
9. `candidate = 3, count = 3`

#### **Output:**
```cpp
Majority Element: 3
```

---

## **Final Thoughts**
- The **Boyer-Moore Voting Algorithm** is an optimal way to find the majority element in linear time with constant space.
- However, if a majority element is not guaranteed to exist, **verification is necessary**.
- It is widely used in **voting systems, large-scale data analysis, and fraud detection**.

**🚀 If you found this helpful, don't forget to ⭐ the repo!**
