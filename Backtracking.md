# Backtracking Algorithm Guide

## Introduction
Backtracking is a recursive algorithm used for solving problems by trying all possible solutions and eliminating those that fail to satisfy constraints. It follows a **depth-first search (DFS)** approach and is commonly used for combinatorial problems.

## How Backtracking Works
1. **Make a choice** – Add a candidate to the current solution.
2. **Check if it's valid** – If the solution is complete and meets constraints, store it.
3. **Recur** – Explore further by making additional choices.
4. **Backtrack** – If the choice leads to an invalid solution, undo the last step and try another option.

## General Pseudocode
```plaintext
Function Backtrack(currentState, result):
    If currentState is a complete solution:
        Store currentState in result
        Return
    
    For each possible choice:
        If choice is valid:
            Make choice
            Backtrack(currentState, result)
            Undo choice (backtrack)
```

---

# Backtracking Examples

## 1. **Subset Generation**
**Problem:** Generate all subsets of a given set `[1, 2, 3]`.

### **Pseudocode**
```plaintext
Function GenerateSubsets(index, currentSubset, nums, result):
    If index == size of nums:
        Store currentSubset in result
        Return
    
    // Include the current element
    Add nums[index] to currentSubset
    GenerateSubsets(index + 1, currentSubset, nums, result)
    Remove last element from currentSubset // Backtrack
    
    // Exclude the current element
    GenerateSubsets(index + 1, currentSubset, nums, result)
```

### **C++ Implementation**
```cpp
#include <iostream>
#include <vector>
using namespace std;

void generateSubsets(int index, vector<int>& subset, vector<int>& nums, vector<vector<int>>& result) {
    if (index == nums.size()) {
        result.push_back(subset);
        return;
    }
    
    // Include element
    subset.push_back(nums[index]);
    generateSubsets(index + 1, subset, nums, result);
    subset.pop_back(); // Backtrack
    
    // Exclude element
    generateSubsets(index + 1, subset, nums, result);
}

int main() {
    vector<int> nums = {1, 2, 3};
    vector<vector<int>> result;
    vector<int> subset;
    generateSubsets(0, subset, nums, result);
    
    for (auto subset : result) {
        for (int num : subset) cout << num << " ";
        cout << endl;
    }
    return 0;
}
```

---

## 2. **N-Queens Problem**
**Problem:** Place `N` queens on an `N×N` chessboard so that no two queens attack each other.

### **Pseudocode**
```plaintext
Function SolveNQueens(board, row, N, result):
    If row == N:
        Store board in result
        Return
    
    For each column in 0 to N-1:
        If placing queen at (row, col) is valid:
            Place queen at (row, col)
            SolveNQueens(board, row + 1, N, result)
            Remove queen from (row, col) // Backtrack
```

### **C++ Implementation**
```cpp
#include <iostream>
#include <vector>
using namespace std;

bool isSafe(vector<string>& board, int row, int col, int N) {
    for (int i = 0; i < row; i++)
        if (board[i][col] == 'Q') return false;
    
    for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
        if (board[i][j] == 'Q') return false;
    
    for (int i = row, j = col; i >= 0 && j < N; i--, j++)
        if (board[i][j] == 'Q') return false;
    
    return true;
}

void solveNQueens(int row, vector<string>& board, int N, vector<vector<string>>& result) {
    if (row == N) {
        result.push_back(board);
        return;
    }
    
    for (int col = 0; col < N; col++) {
        if (isSafe(board, row, col, N)) {
            board[row][col] = 'Q';
            solveNQueens(row + 1, board, N, result);
            board[row][col] = '.'; // Backtrack
        }
    }
}

int main() {
    int N = 4;
    vector<vector<string>> result;
    vector<string> board(N, string(N, '.'));
    
    solveNQueens(0, board, N, result);
    
    for (auto sol : result) {
        for (auto row : sol) cout << row << endl;
        cout << endl;
    }
    return 0;
}
```

---

## Complexity Analysis
- **Time Complexity:** Backtracking algorithms often have exponential time complexity `O(2^N)`, `O(N!)`, or `O(B^D)` depending on the branching factor and depth of recursion.
- **Space Complexity:** `O(N)` for storing recursive calls and `O(N^2)` for problems like N-Queens (storing board state).

## When to Use Backtracking?
✅ Problems with **multiple solutions** where all possibilities must be explored (e.g., N-Queens, Sudoku).  
✅ **Constraint satisfaction problems** where invalid solutions must be pruned early.  
✅ **Combinatorial problems** requiring **all possible arrangements**, subsets, or sequences.  

## Conclusion
Backtracking is a powerful technique for solving complex problems by exploring all possibilities and eliminating unfeasible paths. By understanding its structure and applying optimizations (e.g., pruning, memoization), we can make it more efficient.

**Happy Coding! 🚀**
