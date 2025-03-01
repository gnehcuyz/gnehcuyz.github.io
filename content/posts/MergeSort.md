---
title: Merge Sort
date: 2025-01-12
draft: false
summary: A reliable and efficient algorithm for sorting data using a divide-and-conquer approach.
math: true
tags: [Data Structures and Algorithms (DSA]
---

# **What is Merge Sort?**
Merge Sort is a **divide-and-conquer algorithm** used to sort an array or list. It splits the array into smaller parts, sorts them, and then merges the sorted parts back together. It is very efficient, especially for large datasets.

## **Key Characteristics**
- Time complexity: \(O(n \log n)\) for all cases (best, average, and worst).
- Space complexity: \(O(n)\) because it uses temporary arrays.
- Stable sorting: Keeps the relative order of equal elements.

---

# **How Merge Sort Works**
Merge Sort follows these steps:

1. **Divide**: Split the array into two halves.
2. **Conquer**: Recursively sort each half.
3. **Combine**: Merge the two sorted halves into a single sorted array.

---

## **Pseudocode**
```python
def merge_sort(array):
    if len(array) <= 1:
        return array

    # Step 1: Split the array
    mid = len(array) // 2
    left_half = merge_sort(array[:mid])
    right_half = merge_sort(array[mid:])

    # Step 2: Merge sorted halves
    return merge(left_half, right_half)

def merge(left, right):
    merged = []
    i = j = 0

    # Compare elements and merge
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            merged.append(left[i])
            i += 1
        else:
            merged.append(right[j])
            j += 1

    # Add remaining elements
    merged.extend(left[i:])
    merged.extend(right[j:])

    return merged
```

---

# **How the Merge Step Works**
The merge step combines two sorted arrays into one sorted array:

1. Compare the first elements of both arrays.
2. Add the smaller element to the result array.
3. Repeat until one array is empty.
4. Add all remaining elements from the non-empty array.

---

## **Common Questions**
### **1. What is the downside of Merge Sort?**
Merge Sort requires extra space to store temporary arrays during the merge process. This space complexity of \(O(n)\) can be a limitation in memory-constrained environments.

---

# **Classic Practice Problems**
1. [Sort an Array](https://leetcode.com/problems/sort-an-array/)

2. [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)

3. [Count Inversions](https://practice.geeksforgeeks.org/problems/inversion-of-array/0)

4. [Sort a Linked List](https://leetcode.com/problems/sort-list/)

5. [Kth Smallest Element](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)

