---
title: Sliding Window
date: 2025-01-14
draft: false
summary: Sliding Window, an efficient technique for solving array problems
math: true
tags: [Data Structures and Algorithms (DSA]
---

# **What is Sliding Window?**
The sliding window is a technique used to solve problems that involve arrays, lists, or strings. It helps optimize performance by reducing the need for nested loops. Instead of processing the entire array multiple times, this method allows you to focus on a specific "window" of elements that moves as needed.

### Key Characteristics:
- Works with contiguous subarrays or substrings.
- Time complexity: \(O(n)\) in most cases.
- Space complexity: \(O(1)\) unless additional data structures are used.

---

# **How Sliding Window Works**
### Steps:
1. **Identify the Window Size**:
   - For fixed-size problems, the window size remains constant.
   - For variable-size problems, the window size changes dynamically.

2. **Initialize Variables**:
   - Set pointers for the start and end of the window.
   - Use variables to track the current state, such as the sum, maximum, or frequency of elements.

3. **Expand or Shrink the Window**:
   - Adjust the pointers (usually `start` and `end`) to include or exclude elements.
   - Update the state as elements are added or removed.

4. **Check for Conditions**:
   - Ensure the window meets the problem's requirements.
   - Adjust as needed to maintain the conditions.

---

# **Pseudocode**
### Fixed-Size Sliding Window:
```python
# Example: Maximum sum of a subarray of size k
def max_subarray_sum(arr, k):
    n = len(arr)
    if n < k:
        return -1  # Not enough elements

    max_sum = 0
    window_sum = sum(arr[:k])  # Initial window sum
    max_sum = window_sum

    for i in range(k, n):
        window_sum += arr[i] - arr[i - k]  # Slide the window
        max_sum = max(max_sum, window_sum)

    return max_sum
```

### Variable-Size Sliding Window:
```python
# Example: Smallest subarray with sum >= target
def min_subarray_len(target, arr):
    n = len(arr)
    min_len = float('inf')
    window_sum = 0
    start = 0

    for end in range(n):
        window_sum += arr[end]  # Expand the window

        while window_sum >= target:  # Shrink the window
            min_len = min(min_len, end - start + 1)
            window_sum -= arr[start]
            start += 1

    return min_len if min_len != float('inf') else 0
```

---

# **Common Sliding Window Patterns**
### 1. Fixed-Size Window
- Problems that involve finding maximum/minimum sums, averages, or other metrics for a fixed-size subarray.

### 2. Dynamic Window
- Problems where the size of the window depends on specific conditions, such as achieving a target sum or meeting frequency constraints.

### 3. Two Pointers
- Often combined with sliding window to adjust both ends of the window efficiently.

---

# **Classic LeetCode Problems 🔗**
1. [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
2. [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)
3. [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
4. [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)
5. [Permutation in String](https://leetcode.com/problems/permutation-in-string/)
6. [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)
7. [Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/)

---
