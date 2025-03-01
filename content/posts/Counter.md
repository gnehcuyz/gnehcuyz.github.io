---
title: Counter in Python
date: 2025-02-28
draft: false
summary:  A special dictionary-like class for counting occurrences of elements
math: true
ShowToc: false
tags: [Data Structures and Algorithms (DSA)]
---

## What is `Counter`?

`Counter` is a special dictionary-like class in the `collections` module. It helps count occurrences of elements in a list, string, or iterable.

## How to Use `Counter`

### Importing `Counter`

```python
from collections import Counter
```

### Counting Elements in a List

```python
nums = [1, 1, 1, 2, 2, 3]
count = Counter(nums)
print(count)  # Output: Counter({1: 3, 2: 2, 3: 1})
```

### Counting Characters in a String

```python
word = "banana"
char_count = Counter(word)
print(char_count)  # Output: Counter({'a': 3, 'n': 2, 'b': 1})
```

### Getting Count of a Specific Element

```python
print(count[1])  # Output: 3
print(count[2])  # Output: 2
print(count[5])  # Output: 0 (returns 0 instead of KeyError)
```

### Finding the Most Common Elements

```python
nums = [1, 1, 1, 2, 2, 3]
count = Counter(nums)
print(count.most_common(2))  # Output: [(1, 3), (2, 2)]
```

### Converting `Counter` to a Dictionary

```python
count_dict = dict(count)
print(count_dict)  # Output: {1: 3, 2: 2, 3: 1}
```

## Arithmetic Operations with `Counter`

### Adding Two `Counter` Objects

```python
a = Counter("hello")
b = Counter("world")
print(a + b)  # Output: Counter({'l': 5, 'o': 2, 'h': 1, 'e': 1, 'w': 1, 'r': 1, 'd': 1})
```

### Subtracting Counts

```python
a.subtract(b)
print(a)  # Output: Counter({'l': 3, 'h': 1, 'e': 1, 'o': 0, 'w': -1, 'r': -1, 'd': -1})
```


## Summary Table

| Feature | `Counter` |
|---------|------------|
| Default value | Returns `0` for missing keys |
| Counting elements | `Counter(iterable)` |
| Get most frequent elements | `.most_common(k)` |
| Convert to dictionary | `dict(Counter(iterable))` |
| Supports arithmetic | `Counter + Counter` |

This covers the basics of `Counter`. It is useful for counting and analyzing data efficiently.
