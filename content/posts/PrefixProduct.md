---
title: Prefix Product
date: 2025-03-01
draft: false
summary: A powerful technique for efficiently computing product-related queries.
math: true
tags: [Data Structures and Algorithms (DSA)]
---

# **What is Prefix Product?**
Prefix Product is a technique used to **precompute cumulative products** in an array, allowing product-related queries to be answered efficiently.

---

# **How to Construct a Prefix Product Array**
### **Steps:**
1. **Initialize an array `prefix`** of the same size as the input array.
2. **Compute cumulative products:**  
   
   \[
   	\text{prefix}[i] = 	\text{prefix}[i-1] \cdot arr[i]
   \]
   
3. **Use prefix products for efficient range queries:**  
   
   \[
    \text{Product}(l, r) = \frac{\text{prefix}[r]}{\text{prefix}[l-1]} \quad \text{if} \hspace{0.2cm} l > 0 
   \]
   
   If \( l = 0 \), then \( 	\text{Product}(0, r) =  \text{prefix}[r] \).

### **Example**
```python
arr = [2, 3, 4, 5]
prefix = [2, 6, 24, 120]  # Precomputed product array
```
- `prefix[2] = 2 × 3 × 4 = 24`
- `prefix[3] = 2 × 3 × 4 × 5 = 120`

**Efficient Query Example:**
Find product from index **1 to 3**:
```python
Product(1,3) = prefix[3] / prefix[0] = 120 / 2 = 60
```

---

# **Implementation of Prefix Product**
```python
def prefix_product(arr):
    n = len(arr)
    prefix = [1] * n
    prefix[0] = arr[0]
    
    for i in range(1, n):
        prefix[i] = prefix[i-1] * arr[i]
    
    return prefix

def range_product(prefix, l, r):
    if l == 0:
        return prefix[r]
    return prefix[r] // prefix[l-1]

# Example usage
arr = [2, 3, 4, 5]
prefix = prefix_product(arr)

# Product from index 1 to 3
print(range_product(prefix, 1, 3))  # Output: 60
```

---

# **Time and Space Complexity**
### **Time Complexity**
- **Preprocessing step:** Constructing the prefix product array takes **O(N)** time since each element is computed once.
- **Querying a range product:** Once the prefix product array is built, each query runs in **O(1)** time since it only involves a simple division.

### **Space Complexity**
- If storing the prefix product separately, it requires an additional **O(N)** space.
- If the input array itself is modified to store prefix products, the space complexity is **O(1)**.

---

# **Classic LeetCode Problems**
- [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/) 
- [Range Product Query](https://leetcode.com/problems/range-product-query/)
- [Subarray Product Less Than K](https://leetcode.com/problems/subarray-product-less-than-k/)