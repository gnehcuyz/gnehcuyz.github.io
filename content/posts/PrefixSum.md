---
title: Prefix Sum
date: 2025-03-01
draft: false
summary: A powerful technique for efficiently computing sum-related queries.
math: true
tags: [Data Structures and Algorithms (DSA)]
---

# **What is Prefix Sum?**
Prefix Sum is a technique used to **precompute cumulative sums** in an array, allowing sum-related queries to be answered efficiently.

[Prefix Sum Visualization](https://www.reddit.com/r/leetcode/comments/1ewxiqt/a_visual_guide_to_prefix_sums/)

---

# **How to Construct a Prefix Sum Array**
### **Steps:**
1. **Initialize an array `prefix`** of the same size as the input array.
2. **Compute cumulative sums:**
   
   \[
   \text{prefix}[i] = \text{prefix}[i-1] + arr[i]
   \]
   
3. **Use prefix sums for efficient range queries:**
   
   \[
   \text{Sum}(l, r) = \text{prefix}[r] - \text{prefix}[l-1]
   \]

### **Example**
```python
arr = [2, 4, 6, 8, 10]
prefix = [2, 6, 12, 20, 30]  # Precomputed sum array
```
- `prefix[2] = 2 + 4 + 6 = 12`
- `prefix[4] = 2 + 4 + 6 + 8 + 10 = 30`

**Efficient Query Example:**
Find sum from index **1 to 3**:
```python
Sum(1,3) = prefix[3] - prefix[0] = 20 - 2 = 18
```

---

# **Implementation of Prefix Sum**
```python
def prefix_sum(arr):
    n = len(arr)
    prefix = [0] * n
    prefix[0] = arr[0]
    
    for i in range(1, n):
        prefix[i] = prefix[i-1] + arr[i]
    
    return prefix

def range_sum(prefix, l, r):
    if l == 0:
        return prefix[r]
    return prefix[r] - prefix[l-1]

# Example usage
arr = [2, 4, 6, 8, 10]
prefix = prefix_sum(arr)

# Sum from index 1 to 3
print(range_sum(prefix, 1, 3))  # Output: 18
```

---

# **Time and Space Complexity**
### **Time Complexity**
- **Preprocessing step:** Constructing the prefix sum array takes **O(N)** time since each element is computed once.
- **Querying a range sum:** Once the prefix sum array is built, each query runs in **O(1)** time since it only involves a simple subtraction.

### **Space Complexity**
- If storing the prefix sum separately, it requires an additional **O(N)** space.
- If the input array itself is modified to store prefix sums, the space complexity is **O(1)**.

---

# **Classic LeetCode Problems**
- [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) (Medium)
- [Running Sum of 1D Array](https://leetcode.com/problems/running-sum-of-1d-array/) (Easy)
- [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/) (Medium)
- [Range Sum Query - Immutable](https://leetcode.com/problems/range-sum-query-immutable/) (Easy)