---
title: BFS - Breadth First Search
date: 2025-04-24
tags: [DSA]
draft: false
math: true
tags: [Data Structures and Algorithms (DSA)]
summary: A way to explore trees, graphs, or grids one level at a time.
---


**Breadth-First Search (BFS)** is a way to explore trees, graphs, or grids **one level at a time**. It starts at a point, checks all neighbors, then their neighbors, and so on.

---
## Key Concepts

- **Queue-Based Traversal**: BFS uses a queue to manage the order of exploration. Nodes are processed in the order they are discovered — first in, first out (FIFO).
- **Visited Tracking**: To avoid visiting the same node more than once (especially in graphs or grids), a visited set or array is used to keep track of what’s already been seen.
- **Level-by-Level Exploration**: BFS explores nodes one level at a time. It checks all immediate neighbors before going deeper, which is useful for finding the shortest path or tracking depth.

---

## Implementation

### Pseudocode

#### For trees:
```pseudo
FUNCTION BFS_Tree(root):
    IF root is NULL:
        RETURN

    INITIALIZE queue with root

    WHILE queue is not empty:
        SET size = length of queue

        FOR i FROM 1 TO size:
            node = REMOVE from queue
            PROCESS node (e.g., print or store node.value)

            IF node has left child:
                ADD node.left to queue

            IF node has right child:
                ADD node.right to queue
```

#### For graphs:
```pseudo
FUNCTION BFS(start):
    INITIALIZE queue with start
    INITIALIZE visited set with start

    WHILE queue is not empty:
        node = REMOVE from queue
        PROCESS node (e.g., print, record, etc.)

        FOR each neighbor of node:
            IF neighbor is not in visited:
                ADD neighbor to visited
                ADD neighbor to queue

```

#### For grids:
```pseudo
FUNCTION BFS(start_row, start_col):
    INITIALIZE queue with (start_row, start_col)
    INITIALIZE visited set with (start_row, start_col)

    WHILE queue is not empty:
        (r, c) = REMOVE from queue
        PROCESS (r, c)

        FOR each direction in [up, down, left, right]:
            new_r, new_c = r + dr, c + dc

            IF (new_r, new_c) is in bounds AND not in visited:
                ADD (new_r, new_c) to visited
                ADD (new_r, new_c) to queue

```
### Python Code

#### For trees:
```python
from collections import deque

def bfs_tree(root):
    if not root:
        return []

    result = []
    queue = deque([root])

    while queue:
        level = []
        for _ in range(len(queue)):
            node = queue.popleft()
            level.append(node.val)
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        result.append(level)

    return result

```

#### For graphs (Adjacency List):
```python
from collections import deque

def bfs_graph(graph, start):
    visited = set()
    queue = deque([start])
    visited.add(start)
    result = []

    while queue:
        node = queue.popleft()
        result.append(node)

        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)

    return result

```

#### For grids (2D matrix):
```python
from collections import deque

def bfs_grid(grid, start_row, start_col):
    rows, cols = len(grid), len(grid[0])
    visited = set()
    queue = deque([(start_row, start_col)])
    visited.add((start_row, start_col))

    directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]
    result = []

    while queue:
        r, c = queue.popleft()
        result.append((r, c))

        for dr, dc in directions:
            nr, nc = r + dr, c + dc
            if (0 <= nr < rows and 0 <= nc < cols and
                (nr, nc) not in visited and grid[nr][nc] == 0):
                visited.add((nr, nc))
                queue.append((nr, nc))

    return result

```

---

## Time and Space Complexity
| Operation | Time Complexity | Space Complexity |
| --------- | --------------- | ---------------- |
| Tree      | O(n)            | O(n)             |
| Graph     | O(V + E)        | O(V)             |
| Grid      | \(O(m \times n)\) | \(O(m \times n)\)  |

---

## Classic LeetCode Problems
- [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal)
- [Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree)
- [Cousins in Binary Tree](https://leetcode.com/problems/cousins-in-binary-tree)
- [Word Ladder](https://leetcode.com/problems/word-ladder)
- [All Nodes Distance K in Binary Tree](https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree)
- [Rotting Oranges](https://leetcode.com/problems/rotting-oranges)
- [Number of Islands](https://leetcode.com/problems/number-of-islands)
- [Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix)
- [Walls and Gates](https://www.lintcode.com/problem/663/)
---
<!-- 
## Common Mistakes and Tips
- Mistake 1: ...
- Tip 1: ...
- Debugging idea: ...

--- -->

## When to Use BFS
- "Shortest path"  
- "Minimum steps" / "Fewest moves"  
- "Find distance from..."  
- "Level-order traversal"  
- "Explore neighbors"  
- "All possible states"  
- "Reach all nodes / areas"  
- "Flood fill"  
- "First occurrence" / "Earliest time"  
- "From X to Y in a grid/maze"  
- "Multi-source traversal"  
- "Propagation" (infection, rumor, fire spread)

---
<!-- 
## Notes and Observations
- Observation 1: ...
- Something I didn’t understand at first: ...

--- -->

## Resources
- [Leetcode Pattern](https://medium.com/leetcode-patterns/leetcode-pattern-2-dfs-bfs-25-of-the-problems-part-2-a5b269597f52) 
- [Full LeetCode BFS Problem List](https://leetcode.com/problem-list/breadth-first-search/)