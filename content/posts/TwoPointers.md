---
title: Two Pointers
date: 2025-01-11
draft: false
summary: A simple and adaptable technique that optimizes problem-solving by scanning arrays efficiently
math: true
ShowToc: false
tags: [Data Structures and Algorithms (DSA)]
---

# **What is Two Pointers?**
Two Pointers is a straightforward and flexible algorithmic technique used to solve problems efficiently, especially on arrays and strings. The basic idea is to use two pointers (or indices) to scan the data from different directions or at varying speeds.

<span style="font-size: 22px;"><strong>Key Characteristics:</strong></span>
- Usually works on **sorted arrays** or problems involving sequences.
- Helps reduce nested loops, making algorithms faster.
- Common in problems related to searching, comparing, or partitioning data.
- Time complexity: typically \(O(n)\) or \(O(n \log n)\) depending on the problem.

---

# **How to Apply Two Pointers**
<span style="font-size: 22px;"><strong>Steps:</strong></span>
1. **Decide the Purpose of Each Pointer**:
   - Will they move toward each other? At different speeds? Or scan simultaneously?
2. **Initialize the Pointers**:
   - Start pointers at the beginning and end of the array, or both at the start.
3. **Iterate Until a Condition is Met**:
   - Move the pointers based on the problem requirements.
   - Adjust their movement when conditions are satisfied.
4. **Exit Condition**:
   - Typically when the pointers cross or reach the end of the array.

## **Pseudocode**
<span style="font-size: 19px;"><strong>Basic Two Pointers Template:</strong></span>
```python
# Example: Check if an array has two numbers that sum to a target

def two_pointers_example(array, target):
    left = 0  # Start of the array
    right = len(array) - 1  # End of the array

    while left < right:
        current_sum = array[left] + array[right]

        if current_sum == target:
            return (left, right)  # Found the pair
        elif current_sum < target:
            left += 1  # Move left pointer to increase the sum
        else:
            right -= 1  # Move right pointer to decrease the sum

    return -1  # No pair found
```

---

# **Common Patterns**
Here are some popular problems solved using the Two Pointers technique:

## 1. **Finding a Pair with a Given Sum**
- Problem: Find two numbers in a sorted array that add up to a target value.
- Strategy: Use one pointer at the start and another at the end, adjust based on the sum.

## 2. **Remove Duplicates from Sorted Array**
- Problem: Remove duplicates in-place in a sorted array and return the new length.
- Strategy: Use one pointer to scan the array and another to track unique elements.

## 3. **Reversing a String or Array**
- Problem: Reverse the characters in a string or elements in an array.
- Strategy: Use two pointers, one at each end, and swap the elements.

## 4. **Checking for Palindrome**
- Problem: Check if a string is a palindrome.
- Strategy: Use two pointers, one at the start and one at the end, comparing characters.

## 5. **Merging Two Sorted Arrays**
- Problem: Merge two sorted arrays into one sorted array.
- Strategy: Use one pointer for each array and compare elements to decide which to add to the result.

---

# **Classic LeetCode Problems 🔗**

1. [Two Sum II](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)  
2. [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)  
3. [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)  
4. [Reverse String](https://leetcode.com/problems/reverse-string/)  
5. [Container With Most Water](https://leetcode.com/problems/container-with-most-water/)  
6. [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)  
7. [3Sum](https://leetcode.com/problems/3sum/)  
8. [Sort Colors](https://leetcode.com/problems/sort-colors/)  
9. [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)  
10. [Subarray Product Less Than K](https://leetcode.com/problems/subarray-product-less-than-k/)  

