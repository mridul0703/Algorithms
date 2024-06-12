# Dutch National Flag algorithm

The Dutch National Flag algorithm is designed to sort an array with three distinct values efficiently in one pass using constant extra space. It was proposed by Edsger W. Dijkstra and is particularly well-suited for problems like the "Sort Colors" problem where the values to be sorted are 0, 1, and 2.

### Key Idea:
The algorithm partitions the array into three sections:
1. Elements equal to 0.
2. Elements equal to 1.
3. Elements equal to 2.

The goal is to sort the array so that all 0s come first, followed by all 1s, and then all 2s.

### How It Works:
We use three pointers:
1. `low` - This pointer marks the boundary between the section of 0s and the section of 1s and 2s.
2. `mid` - This pointer is used to traverse the array.
3. `high` - This pointer marks the boundary between the section of 2s and the section of 0s and 1s.

### Steps:
1. **Initialization**:
   - Set `low` to the beginning of the array (`0`).
   - Set `mid` to the beginning of the array (`0`).
   - Set `high` to the end of the array (`n - 1`).

2. **Traversal**:
   - While `mid` is less than or equal to `high`, check the value at `nums[mid]`:
     - If `nums[mid] == 0`:
       - Swap `nums[low]` and `nums[mid]`.
       - Increment both `low` and `mid` because the element `0` is now in the correct section.
     - If `nums[mid] == 1`:
       - Simply increment `mid` because the element `1` is already in the correct section.
     - If `nums[mid] == 2`:
       - Swap `nums[mid]` and `nums[high]`.
       - Decrement `high` because the element `2` is now in the correct section.
       - Do not increment `mid` in this case because the swapped element at `mid` needs to be examined.

3. **Termination**:
   - The loop terminates when `mid` surpasses `high`, indicating that all elements are sorted into their respective sections.

### Example Walkthrough:
For an array `[2, 0, 2, 1, 1, 0]`:

- Initial state:
  ```
  low = 0, mid = 0, high = 5
  Array: [2, 0, 2, 1, 1, 0]
  ```

- First iteration (`nums[mid] == 2`):
  - Swap `nums[mid]` and `nums[high]`:
  ```
  low = 0, mid = 0, high = 4
  Array: [0, 0, 2, 1, 1, 2]
  ```

- Second iteration (`nums[mid] == 0`):
  - Swap `nums[low]` and `nums[mid]`:
  ```
  low = 1, mid = 1, high = 4
  Array: [0, 0, 2, 1, 1, 2]
  ```

- Third iteration (`nums[mid] == 0`):
  - Swap `nums[low]` and `nums[mid]`:
  ```
  low = 2, mid = 2, high = 4
  Array: [0, 0, 1, 1, 2, 2]
  ```

- Fourth iteration (`nums[mid] == 1`):
  - Increment `mid`:
  ```
  low = 2, mid = 3, high = 4
  Array: [0, 0, 1, 1, 2, 2]
  ```

- Fifth iteration (`nums[mid] == 1`):
  - Increment `mid`:
  ```
  low = 2, mid = 4, high = 4
  Array: [0, 0, 1, 1, 2, 2]
  ```

- Sixth iteration (`nums[mid] == 2`):
  - Swap `nums[mid]` and `nums[high]`:
  ```
  low = 2, mid = 4, high = 3
  Array: [0, 0, 1, 1, 2, 2]
  ```

- Loop terminates as `mid` (4) is now greater than `high` (3).

### Summary:
- The array is now sorted as `[0, 0, 1, 1, 2, 2]`.
- The algorithm runs in O(n) time complexity, as it makes a single pass through the array.
- It uses O(1) extra space, making it very space-efficient.

This algorithm ensures an efficient and optimal solution to the problem, meeting the constraints provided.
