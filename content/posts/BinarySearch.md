---
title: Binary Search
date: 2025-01-02
draft: false
summary: A fast and precise method for finding targets in sorted arrays. 
math: true
tags: [Data Structures and Algorithms (DSA)]
---

# **What is Binary Search?**
Binary search is an efficient algorithm to find the position of a target value within a **sorted array** or list. It operates by dividing the search interval in half repeatedly:

1. Compare the target value to the middle element.
2. If the target matches the middle element, return its index.
3. If the target is smaller, search the left half of the array.
4. If the target is larger, search the right half of the array.
5. Repeat until the target is found or the search interval is empty.

<span style="font-size: 22px;"><strong>Key Characteristics:</strong></span>
- Requires a sorted array.
- Time complexity: \(O(\log n)\).
- Space complexity: \(O(1)\) for iterative implementation and \(O(\log n)\) for recursive implementation.

---

# **How to Apply Binary Search**
<span style="font-size: 22px;"><strong>Steps:</strong></span>
1. **Determine the Search Interval**:
   Identify the sorted array or range to search in.
2. **Set the Pointers**:
   - Initialize two pointers: `left` (start of the array) and `right` (end of the array).
3. **Iterate or Recur**:
   - Calculate the middle index: 
     \[
     \text{mid} = \text{left} + \frac{\text{right} - \text{left}}{2}
     \]
   - Compare the middle element with the target.
   - Update the pointers (`left` or `right`) to narrow the search interval.
4. **Exit Condition**:
   - If `left > right`, the target does not exist.
   - Otherwise, return the index of the target.


## **Pseudocode**
<span style="font-size: 19px;"><strong>Iterative Implementation:</strong></span>
```python
def binary_search(array, target):
    left = 0
    right = len(array) - 1
    
    while left <= right:
        mid = left + (right - left) // 2  # Avoid overflow
        if array[mid] == target:
            return mid
        elif array[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
            
    return -1  # Target not found
```

<span style="font-size: 19px;"><strong>Recurrsive Implementation</strong></span>

```python
def binary_search(array, target, left, right):
    if left > right:
        return -1  # Target not found
    
    mid = left + (right - left) // 2
    if array[mid] == target:
        return mid
    elif array[mid] < target:
        return binary_search(array, target, mid + 1, right)
    else:
        return binary_search(array, target, left, mid - 1)
```

## **Common Questions**
<span style="font-size: 23px;"><strong>1. Why is `mid` calculated like that?</strong></span>

In binary search, the formula for calculating the middle index is:

\[
\text{mid} = \text{left} + \frac{\text{right} - \text{left}}{2}
\]

This formula is designed to **avoid integer overflow** in programming languages where integers have a fixed range, such as C++ and Java. Here's a detailed explanation:

<span style="font-size: 19px;"><strong> Explanation</strong></span>
1. **Standard Calculation**:
   The straightforward way to compute the middle index is:
   \[
   \text{mid} = \frac{\text{left} + \text{right}}{2}
   \]
   While this formula is simple and works in many cases, it has a potential issue: if `left` and `right` are very large integers, their sum (`left + right`) can exceed the maximum integer value, causing integer overflow.

2. **Alternative Formula**:
   To prevent overflow, the formula is rewritten as:
   \[
   \text{mid} = \text{left} + \frac{\text{right} - \text{left}}{2}
   \]
   This calculates the middle index without directly adding `left` and `right`.

   - The term \((\text{right} - \text{left})\) represents the distance between `left` and `right`, which is much smaller than their sum.
   - Dividing this distance by 2 gives the offset from `left` to the midpoint.
   - Adding this offset back to `left` ensures the calculation remains within safe bounds.

---

# **Classic LeetCode Problems 🔗**

- [Basic Binary Search](https://leetcode.com/problems/binary-search/)  
- [Find First or Last Occurrence](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)  
- [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)  
- [Search Insert Position](https://leetcode.com/problems/search-insert-position/)  
- [Find a Peak Element](https://leetcode.com/problems/find-peak-element/)  
- [Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)  
- [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)  
- [Split Array into Parts](https://leetcode.com/problems/split-array-largest-sum/)  
- [Smallest Missing Positive Number](https://leetcode.com/problems/kth-missing-positive-number/)  
- [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)  
